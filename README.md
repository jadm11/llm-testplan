# LLM QA Test Plan: Reflection 70B Case Study

I used the following sources to query, summarize, find key lessons, mine for test cases, and create a sample test plan based on the Reflection 70B event. With my guidance, ChatGPT 4.0 generated the outputs of this article.

## Sources:
- Reddit, Reflection 70B Summary & Lessons Learned
  - https://www.reddit.com/r/LocalLLaMA/comments/1fciqfp/reflection_70b_lessons_learned/
  - https://www.reddit.com/r/LocalLLaMA/comments/1fd75nm/out_of_the_loop_on_this_whole_reflection_thing/
- Transcript from Reflection 70b Faked?! What We Know So Far...
  - https://youtu.be/Alzjn_0ne1Y?si=BqGiFY9HAmw8kvGr

## What happened?
An AI model, promoted as "Reflection 70B," was introduced with claims of superior performance and a novel "Reflection Tuning" technique. However, independent testing revealed discrepancies between the claimed benchmarks and actual results, with evidence suggesting the public API was wrapping a different model (Claude 3.5) rather than the advertised Llama 3.1. Confusion around the uploaded model weights and a lack of transparency about the developer's relationship with a partner company led to further skepticism.

## What are the key lessons identified by the community?

- **Model Identification**: Always begin by confirming which model (e.g., LLAMA, GPT-4, Sonnet) you are working with, as models can sometimes be misrepresented.
- **Trust but Verify**: Do not trust any benchmarks unless you can replicate them yourself. This is especially true for claims regarding model performance and results.
- **API Misrepresentation**: Be cautious with APIs, as they may not correspond to the model that is being claimed. Always verify that the model matches the author's description.
- **Benchmark Credibility**: Benchmarks should be based on practical use cases relevant to your own needs. Having personal benchmarks helps avoid falling for the hype surrounding new models.
- **Scammers and Misinformation**: There are scams and misinformation in AI development communities, particularly around fine-tuned models. Some individuals falsely claim breakthroughs to gain attention or investment. Be wary of such claims and rely on reproducible results.
- **Zero Trust Approach**: In this era, a zero-trust mentality is essential. Verify everything, from model integrity to benchmark results, and avoid taking any claims at face value.
- **Real-World Testing**: Testing should include real-world applications, comparing results against known models to ensure accuracy and relevancy to your tasks.
- **Bias and Desire for Breakthroughs**: Be mindful of personal biases that make you want to believe in groundbreaking improvements. Recognize that revolutionary breakthroughs are often overstated.
- **Scammers Targeting Niche Areas**: Even in niche technical fields like AI, scammers are present. Be diligent in vetting claims and technologies before adopting them.

## Where is the test plan?

### QA Test Plan for Large Language Model (LLM) Delivery

#### Objective:
The purpose of this test plan is to outline test coverage for Large Language Models (LLMs). The goal is to verify the accuracy, performance, and robustness of the model across various benchmarks, ensure alignment with claimed functionality, and validate API consistency.

#### Scope:
This plan applies to LLMs that are delivered either as models in deployment, through APIs, or in other environments. It includes testing on model architecture, functional performance, API validation, benchmark integrity, and contamination prevention.

#### Test Data Requirements:
- **Pre-trained Models**: LLMs under evaluation.
- **API Access**: For API-related tests, access to the relevant model APIs.
- **Benchmark Datasets**: GSM, HumanEval, Big Bench, and other widely used datasets.
- **Custom Test Prompts**: Manually created or benchmark-specific test cases covering arithmetic, logic, ethical dilemmas, and creative tasks.

#### Test Environment:
- **Local Environment**: Setup should include all dependencies for running the LLM in isolation.
- **Cloud API**: Testing should also include the model when deployed on cloud environments, particularly focusing on performance and API stability.
- **Tools**: Diffing tools, contamination-detection software, and benchmark execution frameworks (e.g., lm-evaluation-harness).

#### Acceptance Criteria:
The model must:
- Pass all benchmark and functional tests with satisfactory performance.
- Demonstrate stable, consistent results in API-based evaluations.
- Show no signs of contamination with evaluation data or gaming of benchmarks.
- Perform consistently across real-world tasks and functional prompt tests.

#### Reporting:
- **Documentation**: Each test case will be documented, including inputs, expected results, actual results, and pass/fail status.
- **Benchmark Report**: A detailed report showing the performance of the model on each benchmark, including any discrepancies between claimed and observed results.
- **API Validation Report**: A summary of API performance, including any deviations from expected behavior.

## Test Cases

### A. Model Comparison Testing
- **Purpose**: Ensure that the model is consistent with the claimed version and has not been misrepresented or altered.
- **Test Case 1**: Model Diff Analysis
  - **Description**: Compare the new model’s architecture, weights, and configuration files with its prior version to verify consistency.
  - **Objective**: Confirm the model's identity, i.e., version A is truly version A, and the changes align with what is claimed.
  - **Method**: Use diff tools to check the structural differences between models, including weight diffing, tokenizer diffing, and configuration diffing.

### B. Benchmark Validation
- **Purpose**: Validate model performance across a range of benchmarks that reflect both its general and task-specific abilities.
- **Test Case 2**: Independent Benchmark Testing
  - **Description**: Run the model through a set of known, public benchmarks (e.g., GSM, HumanEval, Big Bench).
  - **Objective**: Ensure that the performance metrics align with expectations and claims.
  - **Method**: Execute benchmarks and record performance against previously validated models (e.g., GPT-4, LLAMA).
  - **Key Metrics**: Accuracy, F1 scores, Precision, and Recall.
- **Test Case 3**: Benchmark Manipulation Detection
  - **Description**: Check for overfitting or gaming of benchmarks through methods like paraphrased training data or training on benchmark-specific tasks.
  - **Objective**: Ensure the model’s performance is legitimate and hasn’t been manipulated by training on evaluation sets.
  - **Method**: Use tools to assess if paraphrased or altered versions of the test set were included in the training data.

### C. Prompt-Based Functional Testing
- **Purpose**: Validate the model’s ability to handle various types of prompts and generate accurate, consistent, and relevant outputs.
- **Test Case 4**: Functional Prompt Testing (General Logic)
  - **Description**: Ask the model to answer questions that test basic logical, arithmetic, and language abilities.
  - **Example Prompts**: How many "R"s are in the word "strawberry"? Which number is bigger: 9.11 or 9.9? How many words are in your response to this prompt?
  - **Objective**: Validate the model's fundamental reasoning and arithmetic abilities.
  - **Pass Criteria**: The model should give accurate responses to logical and arithmetic queries.
- **Test Case 5**: Content Generation (Creative)
  - **Description**: Test the model's ability to generate creative content.
  - **Example Prompt**: Generate 10 sentences that end with the word "Apple."
  - **Objective**: Assess the model’s capability to handle more complex generation tasks.
  - **Pass Criteria**: The sentences should all end with the correct word while maintaining grammatical correctness and creativity.
- **Test Case 6**: Ethical Reasoning
  - **Description**: Test the model’s ability to respond to ethical dilemmas.
  - **Example Prompt**: Is it acceptable to gently push a random person if it could save humanity from extinction?
  - **Objective**: Validate that the model can engage in reasoning around moral questions and provide consistent, coherent ethical responses.
  - **Pass Criteria**: The response should demonstrate logical consistency and consideration of ethical factors.

### D. Code Generation Testing
- **Purpose**: Evaluate the model’s ability to generate executable code for various programming tasks.
- **Test Case 7**: Code Generation for Simple Games
  - **Description**: Prompt the model to generate functional Python code for games such as Tetris or Snake.
  - **Objective**: Test the model’s ability to generate accurate, executable code.
  - **Pass Criteria**: The generated code should be syntactically correct and executable without errors.

### E. API Validation Testing
- **Purpose**: Ensure that the API delivers the correct model and performance as claimed.
- **Test Case 8**: API Response Consistency
  - **Description**: Check whether the API provides consistent and expected responses for repeated requests.
  - **Example Test**: Submit identical prompts multiple times and compare the outputs for consistency.
  - **Objective**: Ensure API stability and consistent model behavior over time.
  - **Pass Criteria**: API should return similar or logically equivalent responses for repeated identical inputs.
- **Test Case 9**: API Integrity Validation
  - **Description**: Validate that the API corresponds to the model it claims to be (e.g., ensure it is not wrapping another model).
  - **Test**: Submit specific prompts that would reveal an underlying model (e.g., asking it to identify itself or reveal internal tags like "Claude").
  - **Objective**: Ensure API fidelity and transparency.
  - **Pass Criteria**: The model should not falsely identify or disguise its nature.

### F. Contamination Testing
- **Purpose**: Verify that the model has not been trained on the test data (benchmark contamination).
- **Test Case 10**: Data Contamination Check
  - **Description**: Check if the model has been trained on the specific evaluation data used in benchmark tests.
  - **Method**: Use contamination-detection algorithms or run paraphrased and rephrased versions of benchmark questions to see if model accuracy significantly differs.
  - **Objective**: Ensure the model’s performance is not artificially inflated through training on evaluation data.
  - **Pass Criteria**: The model should demonstrate consistent performance regardless of data paraphrasing or rewording.

## How well does the test plan cover the key lessons?
![Coverage Map](https://github.com/jadm11/llm-testplan/blob/main/coverage-map.png)

---
