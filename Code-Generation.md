# All Roads Lead To Code in the age of AI 条条大路通代码

```mermaid
graph TD;
    S((Requirement))-->Q1{"More complex than a \nfunction/method body\n to generate?"};
    S-->Q2{Code to understand?};
    Q1 -- Yes --> Q1a{"Have a model defined in \nhigher level of abstraction?"}
    Q1a -- No --> P1["GPT-3.5,4\nClaude"];
    Q1a -- Yes --> P100[MBE]
    P100 -. GPT-aided .-> P100
    P100 --> Q1b{To be deterministic?} 
    Q1b -- No --> P12["NN(<a target='_blank' href='https://modeling-languages.com/lstm-neural-network-model-transformations/'>LSTM</a>) for \nModel Transformations"]
    Q1b -- Yes --> P21
    Q1 -- No -->P2[Other LMs may work too];
    Q2 -- Yes -->P1
    Q2 -- No -->P2;
    P1 --> Q3{"Special \nAPI/Library/Framework used?"};
    Q3 -- No -->P10["<a href='https://ai-llm.github.io/prompt-patterns/'>Prompt engineering</a>"];
    Q3 -- Yes -->P11["Retrieval (embedding) + \n<a href='https://github.com/AI-LLM/ai-llm.github.io/blob/main/doc-code.md'>Prompt engineering</a>"];
    P2 --> Q4{On-premise required?};
    Q4 -- Yes --> Q5{To be deterministic?};
    Q4 -- No --> P23["GitHub Copilot, \nAWS CodeWhisperer alike"]
    Q5 -- Yes --> P21["Templates and rule based generator \ngenerated with GPT-4, MTBE, etc."]
    Q5 -- No --> P22["Fine-tune <a href='https://github.com/AI-LLM/ai-llm.github.io/blob/main/Code-LLM-alternatives.md'>LMs < 100B</a>"]
    P10 --> Code{{Code}}
    P11 --> Code
    P12 --> Code
    P21 --> Code
    P22 --> Code
    P23 --> Code
```

The way of expressing the **Requirement** is needed to be studied with the level of abstraction varying from user story and use case to docstring and comments.

**Metrics** are also needed to measure the benefits of using LLM for code generation, like *length of prompt to length of generated code*, etc.

代码生成领域的需求痛点：
1. 实用化的评测缺失
   1. **需求**以何种方式表达？从user story, use case到函数签名和注释，抽象程度差异很大。
      <details>
        <summary>ideas</summary>
        利用LLM提高抽象程度的核心思想可以是：让LLM来补全缺失的细节。根据它掌握的上下文知识，还不足的反过来问用户。这样才能最大程度地降低认知负担，提高人的生产效率。怎么尽量避免它乱猜？可以找(Semantic search)相应地设计模式或样板代码让它<a href="https://github.com/AI-LLM/ai-llm.github.io/blob/main/doc-code.md">参照</a>，发现需要什么细节信息，用户当前的prompt里和上下文里有没有？有就自己填进去，没有再问用户要。
      </details>    
   2. 基于应用目标的**评价指标**，比如评价 *程序员编码的效率* 可计算 *生成代码长度与prompt键入长度的比值*，等等。
2. 使用公共大模型的信息泄漏问题，除了改用内部部署小模型外还有什么办法？
   1. [Anonymization](https://github.com/AI-LLM/AnonymizedGPT) (WIP)
   2. [Use of dummies](https://privacypatterns.org/patterns/Use-of-dummies)
3. 训练coding小模型的难点
   1. 除了1，似乎数据已经耗尽了也是个大问题，github用完了还有什么办法？而且github中的数据质量并不非常高，比如程序员自己编写的注释可能[过于简单和抽象](https://arxiv.org/abs/2302.00288)。
      1. 用[Codex](https://dl.acm.org/doi/abs/10.1145/3501385.3543957)、[GPT-Neo等模型生成](https://arxiv.org/abs/2207.14502)
      2. 基于规则的合成，参考[法律NER的经验](https://towardsdatascience.com/why-we-switched-from-spacy-to-flair-to-anonymize-french-legal-cases-e7588566825f)和[医疗领域经验](https://xamat.medium.com/data-as-prior-innate-knowledge-for-deep-learning-models-23898363a71a)。
   2. 13B的CodeGen和CodeGeex基本耗尽了Java、C++等热门编程语言数据，但是[跟ChatGPT还是有不小的差距](Code-LLM-alternatives.md)，那么
      1. Fine tune 13B with 高质量专有数据集，能达到什么效果？
      2. 增加world knowledge训练13B或以上模型，成本对多数企业不现实。而且于以上1有关。
      3. <13B的模型，但只训练一种编程语言，能接近chatgpt吗？
   3. 超越chatgpt的路径？
      1. 训练更高抽象度的NL表达。tokenizer能否兼顾代码元素命名的语义和唯一性标识？
4. 最新的代码、文档不会运用
5. 高阶技术（训练数据中出现少，或者需要复杂的推理过程才能找到正确的方案）不会运用
6. 其他生成代码的缺陷类型和分布与[人类程序员相似](https://arxiv.org/abs/2205.10583)

为解决以上三点，可以设计如下多次迭代的闭环提示工程：

```mermaid
graph TD;
classDef INV fill:black,color:white;
S((Requirement)) -- task description --> Pre-processing
S -- I/O examples --> Pre-processing
doc[(Doc and example)] -- Retrieval --> Pre-processing
LLMparaphrase[[LLM for paraphrase]] -- task description CoT, effective naming --> Pre-processing
LLMcodet[["LLM for <a href='https://arxiv.org/pdf/2207.10397v2.pdf'>CodeT</a>"]] -- generated tests --> Pre-processing

subgraph SYNTHESIZE
Pre-processing -- prompt --> LLMsynth[[LLM for draft programs]]
LLMsynth --> PN[/N Program candidates/]
end

PN --> Execution
PN --> Evaluation[Human evaluation]

subgraph EVAL
Execution --> Suc{Pass?} -- No -->Ranking
Evaluation --> Suc
end

Suc -- Yes --> End((End));class End INV
Ranking --> PS[/W program selected/]

subgraph DEBUG
Execution -- stderr --> noerr{empty stderr?}
noerr -- No --> PT1["Prompt template:\nFix{stderr}"] 
PT1 -- prompt --> LLMdebug
subgraph INSTRUCT
PT2["Prompt template:\n{task} {program} make {I} -> {O}, ..."]
LLMsum[[LLM for bug summary]]
end
Execution -- return and expected I/O --> PT2
Execution -- return and expected I/O --> LLMsum
noerr -- Yes --> PT2
Pre-processing -- task description --> PT2
Pre-processing -- task description --> LLMsum
PS --> PT2
PS --> LLMsum
PT2 -- prompt --> LLMdebug[[LLM for debugging]]
LLMsum -- prompt --> LLMdebug
PS --> Correction[Human correction]
LLMdebug -- update --> PN
end

Correction --> LLMcorrect[[LLM for correction learning]]
LLMcorrect --> PN
```
