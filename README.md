# LLM QA Test Plan: Reflection 70B Case Study

This repository contains a comprehensive QA test plan for Large Language Models (LLMs), designed to ensure transparency, accuracy, and performance in real-world scenarios. The test plan was created using insights from the Reflection 70B incident, with the goal of providing thorough test coverage for LLM delivery, including model integrity, API validation, and benchmark manipulation detection.

LinkedIn Article - https://www.linkedin.com/pulse/reflections-reflection-70b-sample-test-plan-jacob-adm-8paze/

## Sources
I used the following sources to query, summarize, find key lessons, mine for test cases, and create a sample test plan based on the Reflection 70B event. With my guidance, ChatGPT 4.0 generated the outputs of this article.

- **Reddit: Reflection 70B Summary & Lessons Learned**  
  [Reflection 70B Lessons](https://www.reddit.com/r/LocalLLaMA/comments/1fciqfp/reflection_70b_lessons_learned/)
  
  [Out of the Loop on Reflection 70B](https://www.reddit.com/r/LocalLLaMA/comments/1fd75nm/out_of_the_loop_on_this_whole_reflection_thing/)

- **Transcript from** [Reflection 70B Faked?! What We Know So Far](https://youtu.be/Alzjn_0ne1Y?si=BqGiFY9HAmw8kvGr)

## What Happened?
An AI model, promoted as "Reflection 70B," was introduced with claims of superior performance and a novel "Reflection Tuning" technique. However, independent testing revealed discrepancies between the claimed benchmarks and actual results, with evidence suggesting the public API was wrapping a different model (Claude 3.5) rather than the advertised Llama 3.1. Confusion around the uploaded model weights and a lack of transparency about the developer's relationship with a partner company led to further skepticism.

## What are the key lessons identified by the community?
1. **Model Identification**: Always confirm which model you are working with (e.g., LLAMA, GPT-4, Sonnet), as models can be misrepresented.
2. **Trust but Verify**: Do not trust any benchmarks unless you can replicate them. Always perform independent tests.
3. **API Misrepresentation**: Be cautious with APIs and ensure they match the author's claims.
4. **Benchmark Credibility**: Use benchmarks based on practical use cases relevant to your needs.
5. **Scammers and Misinformation**: There are scams in the AI community; be skeptical of exaggerated claims.
6. **Zero Trust Approach**: Adopt a zero-trust mentality and verify everything.
7. **Real-World Testing**: Include real-world scenarios to ensure accuracy and relevance.
8. **Bias and Desire for Breakthroughs**: Avoid letting personal biases cloud judgment.
9. **Scammers Targeting Niche Areas**: Be diligent in vetting niche AI technologies before adopting them.

# Where is the test plan?
## Test Plan Overview
This QA test plan aims to ensure thorough validation of LLMs by covering model architecture, performance benchmarks, API consistency, and contamination checks. It applies to both deployment and API-delivered models.

### **Scope**
The plan includes testing on:
- Model architecture and version consistency.
- Functional performance across a variety of benchmarks.
- API validation and transparency.
- Detection of benchmark manipulation or contamination.

### **Test Data Requirements**
- **Pre-trained Models**: LLMs under evaluation.
- **API Access**: For testing relevant model APIs.
- **Benchmark Datasets**: GSM, HumanEval, Big Bench, and other datasets.
- **Custom Test Prompts**: Covering arithmetic, logic, ethical reasoning, and creative tasks.

### **Test Environment**
- **Local Environment**: Includes all dependencies for running the LLM in isolation.
- **Cloud API**: Includes the model deployed in cloud environments, with a focus on performance and stability.
- **Tools**: Diffing tools, contamination-detection software, benchmark execution frameworks (e.g., lm-evaluation-harness).

## Test Cases

### **A. Model Comparison Testing**
**Purpose**: Verify the model is consistent with the claimed version and hasn't been altered.  
- **Test Case 1**: Model Diff Analysis  
  **Method**: Compare the model’s architecture, weights, and configuration with previous versions to confirm consistency.

### **B. Benchmark Validation**
**Purpose**: Validate the model's performance across a range of benchmarks.  
- **Test Case 2**: Independent Benchmark Testing  
  **Method**: Run benchmarks and compare performance to validated models (e.g., GPT-4, Llama).  
- **Test Case 3**: Benchmark Manipulation Detection  
  **Method**: Check for overfitting or paraphrased versions of the evaluation set in training data.

### **C. Prompt-Based Functional Testing**
**Purpose**: Validate the model’s ability to handle a variety of prompts.  
- **Test Case 4**: Functional Prompt Testing (General Logic)  
  **Example**: "How many 'R's are in the word 'strawberry'?"  
- **Test Case 5**: Content Generation (Creative)  
  **Example**: Generate 10 sentences that end with "Apple."  
- **Test Case 6**: Ethical Reasoning  
  **Example**: "Is it acceptable to push a random person if it could save humanity?"

### **D. Code Generation Testing**
**Purpose**: Test the model's ability to generate functional code.  
- **Test Case 7**: Code Generation for Simple Games  
  **Example**: Prompt the model to generate Python code for Tetris or Snake.

### **E. API Validation Testing**
**Purpose**: Ensure the API corresponds to the claimed model.  
- **Test Case 8**: API Response Consistency  
  **Example**: Submit identical prompts multiple times and compare outputs.  
- **Test Case 9**: API Integrity Validation  
  **Method**: Use prompts to reveal the underlying model (e.g., "What company trained you?").

### **F. Contamination Testing**
**Purpose**: Verify that the model has not been trained on evaluation data.  
- **Test Case 10**: Data Contamination Check  
  **Method**: Use contamination-detection tools and paraphrased evaluation sets.

## Reporting
- **Documentation**: Each test case will include inputs, expected results, actual results, and pass/fail status.
- **Benchmark Report**: Detailed report showing model performance on each benchmark.
- **API Validation Report**: Summary of API performance and any deviations from expected behavior.

# How well does the test plan cover the key lessons?

---
