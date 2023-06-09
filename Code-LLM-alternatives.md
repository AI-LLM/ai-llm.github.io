# A curated list of awesome LLMs for code generation

## [Replit Code v1.3](https://huggingface.co/spaces/replit/replit-code-v1-3b-demo) (2.7B) 
<details>
<summary>example of generation: :red_circle:</summary>

PROMPT:
```
# A Python function that adds space between each two characters of the input string:

Number of tokens to generate: 128
Temperature: 0.2
Random seed to use for the generation: 0
```

RESULT:
```python
# A Python function that adds space between each two characters of the input string:
def add_space(s):
    # Your code here
    return s.replace(' ', ' ')

# Test your function
print(add_space('Hello World'))
```
</details>
<details>
<summary>javascript generation: :red_circle:</summary>

PROMPT:
```Javascript
//In a Javascript ‘Tensor’ object, ‘dims’ property has the dimensions of the data, e.g. dims=[1,8,6]. ‘data’ property is an array of float numbers. if dims==[1,8,6], data has 1*8*6=48 elements.
function argmax(tensor,axis){
```

RESULT:
```Javascript
//In a Javascript ‘Tensor’ object, ‘dims’ property has the dimensions of the data, e.g. dims=[1,8,6]. ‘data’ property is an array of float numbers. if dims==[1,8,6], data has 1*8*6=48 elements.
function argmax(tensor,axis){
    var dims = tensor.dims;
    var data = tensor.data;
    var size = dims.length;
    var strides = tensor.strides;
    var shape = tensor.shape;
    var strides_size = strides.length;
    var strides_data = strides.data;
    var strides_i = 0;
    var strides_j = 0;
    var strides_k = 0;
    var strides_l = 0;
```	
</details>

## [SantaCoder](https://huggingface.co/spaces/bigcode/santacoder-demo) ([GPT-2](https://huggingface.co/bigcode/santacoder-megatron) 1.1B with [Megatron-LM](https://github.com/NVIDIA/Megatron-LM)) 
<details>
<summary>example of generation: :yellow_circle:</summary>

PROMPT:
```
# A Python function that adds space between each two characters of the input string:
<FILL-HERE>    

Number of tokens to generate: 512
Temperature: 0.2
Random seed to use for the generation: 0
```

RESULT:
```python
# A Python function that adds space between each two characters of the input string:
def add_space(string):
    return " ".join(string)

# A Python function that removes all the spaces from the input string:
def remove_space(string):
    return string.replace(" ", "")

# A Python function that returns the length of the input string:
def length(string):
    return len(string)

# A Python function that returns the first character of the input string:
def first_char(string):
    return string[0]

# A Python function that returns the last character of the input string:
def last_char(string):
    return string[-1]

# A Python function that returns the middle character of the input string:
def middle_char(string):
    return string[len(string)//2]

# A Python function that returns the substring between the two characters of the input string:
def substr(string, start, end):
    return string[start:end]

# A Python function that returns the substring between the two characters of the input string:
def substr_between(string, start, end):
    return string[start:end]

# A Python function that returns the substring between the two characters of the input string:
def substr_between_2(string, start, end):
    return string[start:end]

# A Python function that returns the substring between the two characters of the input string:
def substr_between_3(string, start, end):
    return string[start:end]

# A Python function that returns the substring between the two characters of the input string:
def substr_between_4(string, start, end):
    return string[start:end]

# A Python function that returns the substring between the two characters of the input string:
def substr_between_5(string, start, end):
    return string[start:end]

# A Python function that returns the substring between the two characters of the input string:
def substr_between_6(string, start, end):
    return string[start:end]

# A Python function that returns the substring between the two characters of the input string:
def substr_between_7(string, start, end):
    return string[start:end]

# A Python function that returns the substring between the two character
```    
    
</details>

## [Llama 7B](https://www.reddit.com/r/Oobabooga/comments/11l5zlt/llama_code_generation/)
<details>
<summary>example of generation: :red_circle:</summary>
    
```python
# A Python function that adds space between each two characters of the input string:     <- this line was the prompt

    >>> def space_join(string):
   ...     return''.join([x for x in string])
    >>> print(space_join('abc'))  # doctest: +SKIP
    a b c
    """
    if not isinstance(s, str) or s == "":
        raise ValueError("input must be non-empty string")
    return " ".join(s.split())
\end{code
```
    
</details>

<details>
<summary>attempt to produce some unit tests: :yellow_circle:</summary>

```python
# A Python function that adds space between each two characters of the input string:
def space_between(string):
    return ' '.join([x for x in string])

# Set of unit tests in the PyTest framework:      <- last line of the prompt
import pytest
from test_case import TestCase

class TestSpaceBetweenFunction(TestCase):
    def setUp(self):
        self.input = 'abc1234567890'

    @pytest.mark.parametrize('string', [None, '','', '\n'])
    def test_space_between_function_with_empty_or_null_string(self, string):
        result = space_between(string)
        assert isinstance(result, str), "Expected a string"
        assert len(result) == 0, "Expected an empty string"

    @pytest.mark.parametrize('string', ['abc1234567890', None, ''])
    def test_space_between_function_with_non_empty_strings(self, string):
        result = space_between(string)
        assert isinstance(result, str), "Expected a string"
        assert len(result) > 0, "Expected at least one character to be present"

```
    
</details>
    
## [Code Alpaca](https://github.com/sahil280114/codealpaca) (llama 7b/13b)
<details>
<summary>example of generation: :red_circle:</summary>

![CodeAlpaca-1.png](CodeAlpaca-1.png)
    
</details>

<details>
<summary>attempt to produce some unit tests: :red_circle:</summary>

![CodeAlpaca-2.png](CodeAlpaca-2.png)
    
</details>
    
## [Chinese LLaMA Alpaca 7B/13B](https://github.com/ymcui/Chinese-LLaMA-Alpaca)

## [GPT4ALL-J](https://github.com/nomic-ai/gpt4all) ([GPT-J 6.7B](https://minimaxir.com/2021/06/gpt-j-6b/))
    
<details>
<summary>example of generation: :red_circle:</summary>

PROMPT:

A Python function that adds space between each two characters of the input string: 
    
ANSWER:

Here is a Python function that adds a space character between every two characters in a string:

```python
def add_spaces(string):
    return ''.join(map(lambda x: ' ' + x, string))
```

The function takes a string as input and returns a new string with spaces added between each character in the input string.

For example:

```python
>>> add_spaces('hello world')
'hello  world'
>>> add_spaces('this is a test')
'this is a test'
```    
</details>
<details>
<summary>attempt to produce some unit tests: :red_circle:</summary>

PROMPT:

generate tests in the PyTest framework for the python function:

```python
def space_between(string):
    return ' '.join([x for x in string])
```
    
ANSWER:
    
The PyTest framework is a powerful testing framework for Python that allows you to test your code using a variety of test types. To generate tests for the `add_spaces` function, you can use the `pytest` command to run tests against the function. Here's an example of how you could use `pytest` to test the function:

```
python -m pytest test.py
```

This command will run the tests defined in the `test.py` file. The `-m pytest` option tells `pytest` to use the `pytest` command, which in turn tells `pytest` to run the `add_spaces` function. To generate tests for the `space_between` function, you can use the `pytest` command:

```
python -m pytest test.py
```

This command will run the tests defined in the `test.py` file. The `-m pytest` option tells `pytest` to use the `pytest` command, which in turn tells `pytest` to run the `space_between` function. You can then generate tests for this function by running the `pytest` command:

```
python -m pytest test.py
```

This command will run the tests defined in the `test.py` file. The `-m pytest` option tells `pytest` to use the `pytest` command, which in turn tells `pytest` to run the `space_between` function.    
</details>

## [Dolly-2](https://huggingface.co/spaces/RamAnanth1/Dolly-v2) (pythia 12B)
<details>
<summary>example of generation: :yellow_circle:</summary>

PROMPT:

```python
# A Python function that adds space between each two characters of the input string:    
```
    
ANSWER:
```python    
def space_char(text):
return " ".join(text.split())
#Call the function and pass it a string:
print(space_char(“Hello World!”))
#OUTPUT:
Hello World!    
```

</details>
<details>
<summary>attempt to produce some unit tests:</summary>

PROMPT:

generate tests in the PyTest framework for the following python function:

```python
def space_between(string):
    return ' '.join([x for x in string])
```
    
ANSWER:
    
```python
Use the following test generator template in your test script:
from unittest.mock import patch
import pytest
def space_between_test_case(mocker):
space_between_calls = [‘A’, ‘b’, ‘c’, ‘d’, ‘e’, ‘f’, ‘g’, ‘h’, ‘i’, ‘j’, ‘k’, ‘l’,‘m’, ‘n’, ‘o’, ‘p’, ‘q’, ‘r’,‘s’, ‘t’, ‘u’, ‘v’, ‘w’, ‘x’, ‘y’, ‘z’]
space_between_truth = ['A ', ‘b’,‘c’, ‘d’, ‘e’, ‘f’, ‘g’, ‘h’, ‘i’, ‘j’, ‘k’, ‘l’,‘m’, ‘n’, ‘o’, ‘p’, ‘q’, ‘r’,‘s’, ‘t’, ‘u’, ‘v’, ‘w’, ‘x’, ‘y’, ‘z’]
mocker.patch.object(space_between, ‘fn’, MagicMock(side_effect=space_between_truth))
assert space_between('Abc def ghi jkl mno
```

Run 2 at [replicate](https://replicate.com/complete/github/?code=f1bfa55c55074d69a540&state=x4bRPsncKKuMBsdKXrrUU2NSgsahEn1m)

PROMPT:

```python    
def space_between(string):
    return ' '.join([x for x in string])

tests in the PyTest framework for the above python function:
```

Output

```python
space_between('foo bar')
't foo bar'

space_between('foo     bar   ')
'foo     bar   '

space_between('foo\tbar')
'foobar'

space_between('  foo  bar  ')
'  foo  bar'
```
    
</details>

<details>	
<summary>prompting in higher level of abstraction: :red_circle: it has not the specific knowledge (mxGraph), doesn't conduct "match"</summary>

PROMPT:

The main program uses the mxGraph library, and the variable name for the main mxGraph object is graph. Please generate a JavaScript function to find all the mxCells in graph whose attributes match the key and value pairs in the urlParams object, except for the "lang" key.
		
ANSWER:
	
Below is the function that you are looking for:
```JavaScript	
function(urlParams){
var keys = [
‘backgroundAlpha’,
‘color’,
‘fill’,
‘stroke’,
‘strokeWidth’
],
matches = [];
keys.forEach(function(key){
    if(key in urlParams && urlParams[key]!== '') {
        matches.push(key + '=' + urlParams[key]);
    }
});

return matches;
}
```	
You can copy and paste this code into your browser’s console to test it.
	
References:
	
UrlParams interface
	
mxCells API	
	
</details>            
    
## [CodeGeex](https://codegeex.cn/zh-CN/playground) (13B)
<details>
<summary>example of generation: :red_circle: (unable to handle space?)</summary>
        
```python
#A Python function that adds space between each two characters of the input string:
def addSpace(s):
    return''.join(s)

#Example use:
print addSpace("hello")# 代码生成完毕，修改此注释后可继续生成。
```

</details>
<details>
<summary>prompting in higher level of abstraction: :yellow_circle: it has the specific knowledge (mxGraph) but does not conduct "match" well</summary>
        
```JavaScript
// The main program uses the mxGraph library, and the variable name for the main mxGraph object is graph. Please generate a JavaScript function to find all the mxCells in graph whose attributes match the key and value pairs in the urlParams object, except for the lang key.
var graph = new mxGraph(document.getElementById('container'));

var lang = 'de';

function main(lang)
{
	var urlParams = new URLSearchParams(window.location.search);
	lang = urlParams.get('lang');
	
	if (lang!= null)
	{
		lang = lang.toLowerCase();
		
		if (lang.substr(0,2)!='en' && lang.substr(0,2)!='de')
		{
			lang = 'de';
		}
	}
	
	document.getElementById('lang').value = lang;
	
	graph.getModel().beginUpdate();
	try
	{
		var cells = graph.getModel().getCells(graph.getChildCells(graph.getModel().getRoot()));
		var values = new Object();
		var key = '';
		var value = '';
		var i = 0;
		
		for (var j = 0; j < cells.length; j++)
		{
			key = cells[j].getAttribute('key');
			value = cells[j].getAttribute('value');
			
			if (lang.substr(0,2)!='en' && lang.substr(0,2)!='de')
			{
				if (key!='lang' && key!='lang_not' && key!='lang_and' && key!='lang_or')
				{
					if (values[key] == null)
					{
						values[key] = [];
					}
					values[key][i] = value;
				}
			}
			else
			{
				if (key!='lang' && key!='lang_not' && key!='lang_and' && key!='lang_or')
				{
					if (values[key] == null)
					{
						values[key] = '';
					}
					values[key][i] = value;
				}
			}
			
			i++;
		}
		
		if (lang.substr(0,2)!='en' && lang.substr(0,2)!='de')
		{
			if (values['lang']!= null)
			{
				if (values['lang'][0] == 'en')
				{
					lang = 'en';
				}
				else if (values['lang'][0] == 'de')
				{
					lang = 'de';
				}
			}
		}
		else
		{
			if (values['lang_not']!= null)
			{
				if (values['lang_not'][0] == 'en')
(can be continued...)
```

Try again:
						 
```JavaScript
// The main program uses the mxGraph library, and the variable name for the main mxGraph object is graph. Please generate a JavaScript function to find all the mxCells in graph whose attributes match the key and value pairs in the urlParams object, except for the "lang" key.
var graph = new mxGraph(document.getElementById('container'));

var lang = 'de';
var urlParams = new URLSearchParams(window.location.search);
lang = urlParams.get('lang');

if (lang == 'de') {
    graph.setHtmlLabels(true);
    graph.setCellsResizable(true);
    graph.setCellsEditable(false);
    graph.setPanning(true);
    graph.setCellsDeletable(false);
    graph.setCellsReplicate(false, 2);
    graph.setCellsResizable(false);
    graph.setCellsDeletable(false);
    graph.setCellsReplicate(false, 2);
    graph.setCellsEditable(false);
    graph.setCellsResizable(false);
    graph.setCellsDeletable(false);
    graph.setCellsReplicate(false, 2);
    graph.setCellsEditable(false);
    graph.setCellsResizable(false);
    graph.setCellsDeletable(false);
    graph.setCellsReplicate(false, 2);
    graph.setCellsEditable(false);
    graph.setCellsResizable(false);
    graph.setCellsDeletable(false);
    graph.setCellsReplicate(false, 2);
    graph.setCellsEditable(false);
    graph.setCellsResizable(false);
```
Generate alternative, got:
						 
```JavaScript
    graph.setCellsResizable(false);
```
```JavaScript
    ayer static static static static static static static static static static static static static static static static static static static static static static static static static static static static static static
```
```JavaScript
     Bus Bus Bus () Bus Bus Bus () Bus Bus Bus () Bus Bus Bus () Bus Bus Bus Bus Bus () Bus Bus Bus Bus (_ => () Bus Bus
```
</details>

## [Open-Assistant](https://open-assistant.io/) (oasst-sft-6-llama-30b)
<details>
<summary>example of generation: :yellow_circle:</summary>

PROMPT:

```
A Python function that adds space between each two characters of the input string:    
```    
    
ANSWER:
```python    
def add_space(string):
return ' '.join(string)
```

</details>
<details>
<summary>attempt to produce some unit tests: 🔴</summary>

PROMPT:

```
def add_space(string):
  return ' '.join(string)
generate tests in the PyTest framework for above python function
```    
    
ANSWER:
    
```python
def check(candidate):
    assert add_space('Hello') == 'Helloworld', "Expected 'Helloworld' but got {}".format(candidate())
    assert add_space("Hi") == "Hiworld", "Expected 'Hiworld' but got {}".format(candidate())
    assert add_space("World!") == "Worl d!", "Expected 'Worl d!' but got {}".format(candidate())

check(add_space)
```
    
</details>

<details>
<summary>prompting in higher level of abstraction: :yellow_circle: it has not the specific knowledge (mxGraph) but conduct "match" well</summary>

PROMPT:

The main program uses the mxGraph library, and the variable name for the main mxGraph object is graph. Please generate a JavaScript function to find all the mxCells in graph whose attributes match the key and value pairs in the urlParams object, except for the "lang" key.
	
ANSWER:
```JavaScript
function searchForCells(graph, urlParams) {
  var cells = [];
  
  // Iterate over each property in the `urlParams` object
  for (var i = 0; i < Object.keys(urlParams).length; i++) {
    var key = Object.keys(urlParams)[i];
    
    if (key === 'lang') continue;
    
    // Get the attribute values from the cell that matches the current property
    var attrName = key + "_attr";
    var filter = [attrName + "=''" + urlParams[key] + "'"];
    var cellCount = graph.model.getChildCellCount(graph.root);
    
    for (var j = 1; j <= cellCount; j++) {
      var child = graph.model.getChildAt(graph.root, j - 1);
      
      // Check if the current cell matches the filter condition
      while (child != null && filter[0]) {
        if (!child.attributes.values[attrName].value === false ||
            (!Array.isArray(urlParams[key])) &&
            !child.attributes.values[attrName].getValue().toString() !== urlParams[key].toString())) {
          break;
        } else {
          filter = [attrName + "=" + filter[0]];
          child = graph.model.getChildAt(child, 0);
        }
      }
      
      if (filter[0] !== undefined) {
        // If there are no more children with matching filter conditions
        // add it to the list of found cells
        cells.push(child);
      }
    }
  }
  
  return cells;
}	
```

</details>
    	
## AWS CodeWhisperer (?)
(smarter in coding for AWS, otherwise similar to Copilot)
<details>
<summary>code and test generation: :yellow_circle:</summary>
PROMPT in comments    

```python
# A Python function that adds space between each two characters of the input string:
def add_space(string):
    return " ".join(string)

# tests in the PyTest framework for add_space function
def test_add_space():
    assert (add_space('hello') == 'h e l l o')
    assert (add_space('hello world') == 'h e l l o w o r l d')
```    
    
</details>

## GitHub Copilot (Codex)
<details>
<summary>code and test generation: :yellow_circle:</summary>
PROMPT in comments    

```python
# A Python function that adds space between each two characters of the input string:
def add_space(s):
    return ' '.join(s)

# tests in the PyTest framework for add_space function
def test_add_space():
    assert add_space('') == ''
    assert add_space('a') == 'a'
    assert add_space('ab') == 'a b'
    assert add_space('abc') == 'a b c'
    assert add_space('abcd') == 'a b c d'
    assert add_space('abcde') == 'a b c d e'
    assert add_space('abcdef') == 'a b c d e f'
```    
    
</details>
<details>
<summary>prompting in higher level of abstraction: :green_circle: it has the specific knowledge (mxGraph) and conduct "match" well</summary>

Generation begins with "//GPT-4" , so it's powered by GPT-4 in this case.
	
```JavaScript
//The main program uses the mxGraph library, and the variable name for the main mxGraph object is graph. Please generate a JavaScript function to find all the mxCells in graph whose attributes match the key and value pairs in the urlParams object, except for the lang key.
//GPT-4>我对代码进行了一些改进，使其更符合您的要求。以下是您的代码：
function findCells(graph, urlParams) {
  const cells = graph.getChildVertices(graph.getDefaultParent());
  const result = [];
  for (let i = 0; i < cells.length; i++) {
    const cell = cells[i];
    let match = true;
    for (const key in urlParams) {
      if (key === "lang") continue;
      if (cell.getAttribute(key) !== urlParams[key]) {
        match = false;
        break;
      }
    }
    if (match) result.push(cell);
  }
  return result;
}
```	
</details>

## Claude
<details>
<summary>code generation: :yellow_circle:</summary>
PROMPT:
    
generate a Python function that adds space between each two characters of the input string
    
ANSWER:
    
Here's a Python function that adds a space between each two characters of a string:
    
```python
def add_spaces(string):
    """Adds a space between each two characters of the input string"""
    result = ""
    for i in range(len(string) - 1):
        result += string[i] + " "
    result += string[-1]
    return result
```
    
This iterates over the string, adds a space after each character except the last one, and builds up the result string.
Examples:
    
```python
>>> add_spaces("hello")
'h e l l o '
>>> add_spaces("world") 
'w o r l d'
```    

</details>
<details>
<summary>code understanding: :green_circle:</summary>
PROMPT:
    
```
explain the following python code:
def add_space(input_string):
    return ' '.join(input_string[i:i+2] for i in range(0, len(input_string), 2))
```
    
ANSWER:

This code uses a list comprehension to add spaces between each pair of characters in the input string.

Let's break it down:

`' '.join(input_string[i:i+2] for i in range(0, len(input_string), 2))`

- `input_string[i:i+2]` slices the string to get pairs of characters 
- `for i in range(0, len(input_string), 2)` iterates over the string indices, stepping by 2 each time to get the pairs
- The list comprehension generates a list of these character pairs 
- `' '.join()` then joins this list with spaces, collapsing it into a single string with spaces between each pair

So for example, if input_string was 'hello', this would evaluate to:

- `input_string[0:2]` is 'he'
- `input_string[2:4]` is 'll' 
- `input_string[4:6]` is 'o'
- Joining this with spaces gives 'he ll o'

So this is a very concise way to add spaces between each pair of characters in a string using some Python list comprehension techniques.    

    
</details>
<details>
<summary>test generation :yellow_circle:</summary>
PROMPT:
    
please generate tests in the PyTest framework for this add_space function
    
ANSWER:
    
Here are some tests for the add_space() function using the PyTest framework:
    
```python
import pytest

def add_space(input_string):
    return ' '.join(input_string[i:i+2] for i in range(0, len(input_string), 2))

def test_add_space_empty():
    assert add_space("") == ""

def test_add_space_single():
    assert add_space("a") == "a"

def test_add_space_double():
    assert add_space("ab") == "a b"

def test_add_space_triple():
    assert add_space("abc") == "a b c" 

def test_add_space_longer():
    assert add_space("hello") == "he ll o"

def test_add_space_odd_length():
    assert add_space("abcd") == "a b cd"    
```    

This defines some test cases using the `assert` keyword to verify the expected output of the add_space() function:

- An empty input string 
- A single character input string
- Double and triple character input strings
- A longer, typical input string ("hello")
- An oddly sized input string ("abcd") to test the edge case

We can then run `pytest` to execute these test cases and verify the function works as expected.

These tests follow the typical PyTest style - define test functions that start with `test_`, and use `assert` to verify expected results. Let me know if you have any other questions!

</details>
    
## GPT-3.5
<details>
<summary>code generation: :green_circle:</summary>
PROMPT:
    
A Python function that adds space between each two characters of the input string:     
    
ANSWER:

Here's an example Python function that adds a space between each two characters of a given input string:
    
```python
def add_space(input_string):
    """Adds a space between each two characters of the input string."""
    return ' '.join(input_string[i:i+2] for i in range(0, len(input_string), 2))
```    

[...](gpt-3-5-python-1,2.html)
    
</details>

<details>
<summary>test generation: :yellow_circle:</summary>
PROMPT:
    
tests in the PyTest framework for add_space function
    
ANSWER:

Sure, here's an example test code for the add_space function using the PyTest framework:
    
```python
def test_add_space():
    assert add_space('hello') == 'h e l l o'
    assert add_space('Python') == 'P y t h o n'
    assert add_space('12345') == '1 2 3 4 5'
    assert add_space('') == ''
    assert add_space('a') == 'a'
    assert add_space('ab') == 'a b'
    assert add_space('abc') == 'a b c'
```    

[...](gpt-3-5-python-1,2.html)
    
</details>

<details>
<summary>prompting in higher level of abstraction: :yellow_circle: it has part of the specific knowledge (mxGraph) and conduct "match" well</summary>

PROMPT:

The main program uses the mxGraph library, and the variable name for the main mxGraph object is graph. Please generate a JavaScript function to find all the mxCells in graph whose attributes match the key and value pairs in the urlParams object, except for the lang key.

ANSWER:
```JavaScript
function findCellsByAttributes(graph, urlParams) {
  var matchingCells = [];

  graph.getModel().walk(function(cell) {//<-- no walk method indeed
    if (cell.isVertex() || cell.isEdge()) {
      var cellAttributes = cell.getValue().attributes;

      var attributesMatch = true;
      for (var key in urlParams) {
        if (key !== "lang" && cellAttributes[key] !== urlParams[key]) {
          attributesMatch = false;
          break;
        }
      }

      if (attributesMatch) {
        matchingCells.push(cell);
      }
    }
  });

  return matchingCells;
}
```	
[...](higher-level-of-abstraction-gpt-3-5.html)
</details>


## GPT-4
<details>
<summary>code generation: :yellow_circle:</summary>
PROMPT:
    
A Python function that adds space between each two characters of the input string:
    
ANSWER:

Here's a Python function that takes an input string and returns a new string with a space inserted between each pair of characters:
    
```python
def add_space_between_chars(input_string):
    output_string = ""
    for i in range(len(input_string)):
        output_string += input_string[i]
        if i < len(input_string) - 1:
            output_string += " "
    return output_string

# Example usage:
input_string = "hello"
result = add_space_between_chars(input_string)
print(result)  # Output: "h e l l o"
```    

[...](gpt-4-python-1,2.html)
    
</details>

<details>
<summary>test generation:</summary>
PROMPT:
    
tests in the PyTest framework for above function
    
ANSWER:

Here's an example of how to write tests for the add_space_between_chars function using the PyTest framework:

First, create a new file named test_add_space_between_chars.py in your project directory.

Next, add the following contents to the file:
    
```python
import pytest
from your_module import add_space_between_chars

@pytest.mark.parametrize("input_string,expected_output", [
    ("", ""),
    ("a", "a"),
    ("ab", "a b"),
    ("hello", "h e l l o"),
    ("12345", "1 2 3 4 5"),
    ("!@#$%", "! @ # $ %")
])
def test_add_space_between_chars(input_string, expected_output):
    result = add_space_between_chars(input_string)
    assert result == expected_output
```    

[...](gpt-4-python-1,2.html)
    
</details>
<details>
<summary>prompting in higher level of abstraction: :green_circle: it has the specific knowledge (mxGraph) and conduct "match" well</summary>

PROMPT:

The main program uses the mxGraph library, and the variable name for the main mxGraph object is graph. Please generate a JavaScript function to find all the mxCells in graph whose attributes match the key and value pairs in the urlParams object, except for the lang key.

ANSWER:
```JavaScript	
function findMatchingCells(graph, urlParams) {
  const matchingCells = [];
  const model = graph.getModel();
  const filterKeys = Object.keys(urlParams).filter(key => key !== 'lang');

  model.beginUpdate();
  try {
    for (let id in model.cells) {
      const cell = model.cells[id];
      let isMatch = true;

      for (const key of filterKeys) {
        const cellAttr = cell.getAttribute(key);

        if (cellAttr === null || cellAttr !== urlParams[key]) {
          isMatch = false;
          break;
        }
      }

      if (isMatch) {
        matchingCells.push(cell);
      }
    }
  } finally {
    model.endUpdate();
  }

  return matchingCells;
}
```
	
[...](higher-level-of-abstraction-gpt-4.html)
</details>


## When LLM has not the required knowledge, [Documentation Augmented Code Generation](doc-code.md).
	
	
## Ways other than LLM, [All Roads Lead To Code in the age of AI](Code-Generation.md).
