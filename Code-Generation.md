# All Roads Lead To Code in the age of AI
    
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
    Q3 -- No -->P10["<a href='/prompt-patterns/'>Prompt engineering</a>"];
    Q3 -- Yes -->P11["Retrieval (embedding) + \n<a href='/prompt-patterns/'>Prompt engineering</a>"];
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

The way of expressing the **Requirement** is needed to be studied with the level of abstraction varying form user story and use case to docstring and comments.

Metrics is also needed to measure the benefits of using LLM for code generation, like *length of prompt to length of generated code*, etc.

代码生成领域的需求痛点：
1. 实用化的评测缺失
2. 使用公共大模型的信息泄漏问题，除了改用内部部署小模型外还有什么办法没？
3. 训练coding小模型的难点
  - 除了1，似乎数据已经耗尽了也是个大问题，github用完了还有什么办法，用chatgpt生成？
  - 13B的CodeGen和CodeGeex基本耗尽了Java、C++等热门编程语言数据，但是[跟ChatGPT还是有不小的差距](Code-LLM-alternatives.md)，那么
    - Fine tune 13B：高质量专有数据集，能达到什么效果？
    - 增加world knowledge训练13B或以上模型，成本对多数企业不现实。而且于以上Requirement表达方式的问题有关：希望用什么prompt方式？追求的目标是什么（Metrics）？
    - <13B的模型，但只训练一种编程语言，能接近chatgpt吗？