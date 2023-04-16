# 大语言模型的代码生成能力调研

## [Llama 7B](https://www.reddit.com/r/Oobabooga/comments/11l5zlt/llama_code_generation/)
<details>
<summary>example of generation:</summary>
    
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
<summary>attempt to produce some unit tests:</summary>

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
<summary>example of generation:</summary>

![CodeAlpaca-1.png](CodeAlpaca-1.png)
    
</details>

<details>
<summary>attempt to produce some unit tests:</summary>

![CodeAlpaca-2.png](CodeAlpaca-2.png)
    
</details>
    
## [CodeGeex](https://codegeex.cn/zh-CN/playground) (ChatGLM 13B)
<details>
<summary>example of generation:</summary>
        
```python
#A Python function that adds space between each two characters of the input string:
def addSpace(s):
    return''.join(s)

#Example use:
print addSpace("hello")# 代码生成完毕，修改此注释后可继续生成。
```

</details>
    
## [Dolly-2](https://huggingface.co/spaces/RamAnanth1/Dolly-v2) (pythia 12B)
<details>
<summary>example of generation:</summary>

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
    
</details>
        
## [GPT4ALL-J](https://github.com/nomic-ai/gpt4all) (GPT-J 6.7B)
    
...seems better (becuz [GPT-J is not bad](https://minimaxir.com/2021/06/gpt-j-6b/)?)
    
## AWS CodeWhisperer
<details>
<summary>code and test generation:</summary>
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
    
```mermaid
graph TD;
    Start-->Q1{需要生成比较复杂的代码?};
```
