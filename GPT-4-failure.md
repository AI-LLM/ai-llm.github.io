modify the following function markElements and related code to mark elements belonging to different cluster of mergedTxt with different colors.

‘’’JavaScript
function markElements(elements) {
  const styleId = chrome.runtime.id+'_highlight';
  // 检查是否已经添加了样式
  if (!document.getElementById(styleId)) {
    // 如果没有，创建一个新的style元素并添加到head中
    const style = document.createElement('style');
    style.id = styleId; // 设置一个唯一的ID
    document.head.appendChild(style);
    style.sheet.insertRule(`
      .highlighted-element {
        border: 2px dashed red !important; /* 使用红色虚线边框，!important 确保覆盖其他边框样式 */
      }
    `, 0);
  }

  // 为每个元素添加这个样式类
  elements.forEach(element => {
    element.classList.add('highlighted-element');
  });
}

function findContentElements() {
  const elements = document.querySelectorAll('p, span, li, h1, h2, h3, h4, h5, h6, pre, code, b, i, u'/*, section, article'*/); //similar to https://docs.llamaindex.ai/en/stable/module_guides/loading/node_parsers/modules.html#htmlnodeparser
  const largeElements = [];

  elements.forEach(el => {
    const area = el.offsetWidth * el.offsetHeight;
    if (area > 6000) {
      let isDescendant = false;
      for (let parentElement of largeElements) {
        if (parentElement.contains(el)) {
          isDescendant = true;
          break;
        }
      }
      if (!isDescendant) {
        largeElements.push(el);
      }
    }
  });

  return largeElements;
}

function main(){
  const elems = findContentElements();
  markElements(elems);
  const txts = elems.map(el => (el.textContent || el.innerText).trim());

  console.log("chunking text of elements "+txts.length);
  (async function () {
    const tokenizer = await LLMSingleton.getTokenizer();
    async function lengthFunction(text){
      const { input_ids } = await tokenizer(text);
      return input_ids.size;
    }
    let start = performance.now();
    let embeddings = await WebGPUSingleton.infer(txts);
    let end = performance.now();
    //console.log(embeddings);
    console.log(`WebGPU Batch Execution time: ${end - start} ms`);
    //前后句子之cos_sim,小于一定值的组合到不超过max_seq_length
    start = performance.now();
    let pvector;
    const scores = embeddings.tolist().map(
      (embedding, i) => {
        if (i>0)
          return 1 - cos_sim(pvector, embedding);
        pvector = embedding;
        return 0;
      }
    );
    end = performance.now();
    console.log(`Score calculation time: ${end - start} ms`);
    scores.shift();
    //console.log(txts, scores);
    const threshold = percentile(75,scores);
    console.log(threshold);
    const max_seq_length = LLMSingleton.getMaxSeqLength();
    let mergedTxts = [];
    let brk_score=0, brk_length=0;
    let i = 0;
    while (i < txts.length) {
      let currentTxt = txts[i];
  
      // Attempt to merge the current chunk with the next one if conditions are met
      while (i < scores.length && scores[i] < threshold) {
        const nextTxtContent = (i + 1 < txts.length) ? txts[i + 1] : "";
        const concatenatedContent = currentTxt + "\n"+ nextTxtContent;
        const concatenatedLength = await lengthFunction(concatenatedContent);
  
        if (concatenatedLength < max_seq_length) {
          currentTxt = concatenatedContent;
          i++; // Move to the next chunk as it has been merged
        } else {
          brk_length++;
          break; // If concatenated length exceeds max_seq_length, stop trying to merge further
        }
      }
      if (i < scores.length && scores[i] >= threshold) brk_score++;
  
      mergedTxts.push(currentTxt); // Add the merged/current document to mergedTxts
  
      i++; // If no merge happened, move to the next document
    }
    console.log(mergedTxts);
    console.log(`break by score:${brk_score}, break by length:${brk_length}`);
        
    let vs = await WebGPUSingleton.infer(mergedTxts);
    vs = vs.tolist();
    let kmeans = new KMEANS();
    // parameters: 3 - number of clusters
    let clusters = kmeans.run(vs, 2);
    clusters.sort(function(a, b) {
      return Math.max(...(b.map(i => mergedTxts[i].length))) - Math.max(...(a.map(i => mergedTxts[i].length)));
    });
    console.log(clusters);
    for (let c=0; c<clusters.length;c++){
      for (let i =0; i<Math.min(clusters[c].length,5);i++)
        console.log(`c${c+1} ${i+1}/${clusters[c].length} ${mergedTxts[clusters[c][i]]}`)
    }
  })();
}

❌GPT-4
Mark Elements…

❌Gemini
https://gemini.google.com/app/ab0d4c547b182903