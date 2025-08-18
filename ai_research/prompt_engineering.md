Based on this article from Google: https://cloud.google.com/discover/what-is-prompt-engineering

Give the AI instructions to guide it to a desired response 

Prompt to AI is the input 
- Format - different models may function better with different prompts, such as natural language, direct commands, or structured prompts
- Context and examples - helps AI understand end goal 
- Fine-tuning and adaptation
- Multi-turn conversations - allows user to interact with AI continuously 

Types of prompts
- Zero-shot - gives the AI direct instruction without any examples or guidance, useful for creativity/brainstorming. Can also be used for summarization and translation
- One-, few-, and multi-shot prompts - provide one or more examples of desired output before presenting the actual prompt to enhance understanding and accuracy of the response
- Chain of thought - Encourages the model to break down complex output into a series of intermediate steps
- Zero-shot CoT - combines Cot with zero-shot, which may produce better output by performing reasoning steps

Strategies for writing better prompts:
1. Set clear goals and objectives
  - use action verbs to specify desired action
  - define desired length and format of output
  - specify target audience
2. Provide context and background information
  - include relevant facts and data
  - reference specific sources or documents
  - define key terms and concepts
3. Use few-shot prompts
  - provide examples of input-output pairs
  - demonstrate the desired style or tone
  - show the desired level of detail
4. Be specific
  - use precise language (avoid ambuguity)
  - quantify where possible
  - break down complex processes into smaller steps
5. iterate and experiment
  - try different phrases or keywords
  - adjust level of detail and specificity
  - test different prompt lengths
6. leverage chain of thought prompting
  - encourage step-by-step reasoning
  - ask the model to explain reasoning process
  - guide the model using logical sequence of thought

