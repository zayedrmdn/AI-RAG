# 1 - Introduction
## Problem Statement
Firmware development often struggles with outdated and unoptimized code, leading to poor performance and inefficient resource use. This can result in hardware malfunctions and increased maintenance costs.
## Objectives
Improve Code Quality: Automatically analyze and optimize existing firmware code to enhance performance and reduce resource usage.
Automate Updates: Use AI to identify and fix outdated or incorrect firmware code without manual intervention.
Predict Hardware Failures: Develop models that analyze operational data to predict potential hardware issues and suggest preventive actions.
Enhance Device Lifespan: Optimize firmware adjustments to prolong the life of hardware devices.
Simplify Maintenance: Provide tools that facilitate easier and more efficient maintenance processes through predictive insights.
## Assumptions
The user already has a database of previously solved code errors, along with the original wrong code and their the correct solution code.
All firmware is written in C, the language.
## Pros and cons
**Pros:**
- Open-Source: Unlike ChatGPT, which requires a subscription or payment, our model is completely open-source and free to use.
- Better Quality Responses: Our model provides more accurate and relevant answers tailored to user queries since it reads directly from the specific dataset provided by the user.
- Highly Flexible: This model can be used by any firmware company. All they need to do is input their own dataset, making the model adaptable to various use cases.
- Customizable: Users can customize their own version of ChatGPT according to their specific needs.

**Cons:**
- High Computing Power Requirements: Running the model efficiently may require a high-performance GPU, such as those from Nvidia.
- Cost for Cloud Computing: If run on platforms like Google Colab or virtual machines, there may be associated costs.
- Prototype Stage: The model is still in its prototype phase, meaning it may not be fully optimized for all use cases.
- Basic User Interface: The user interface is currently quite simple and lacks polish.
# 2 - Solution Overview & Justification

An AI-powered website that highlights potential runtime/logic errors in C code, as well as providing solutions for them, based on a database of previously solved errors in code. Input is given in the form of text (the C code), which the website will transform (see section 2 for further details), before passing it to an AI model to generate a response for the user.

The response includes everything from:
- List of potential errors in the code
- Possible corrections
- General description of the code
- Summary of response

In the transformation phase, this is how it works:
1. **Inputting the Dataset:** the user provides a dataset, which is like a collection of information that they want the model to use.
2. **Making a Query:** the user asks a question or makes a request (called a query) to the open-source ChatGPT.
3. **Turning into Vectors:** both the dataset and the query are transformed into vectors. Think of vectors as a way to convert words into numbers that the computer can easily understand.
4. **Finding Similarities:** using a method called K-Nearest Neighbors (KNN), the model compares the numbers (vectors) from the query and the dataset to find which pieces of information in the dataset are most similar to the query. This helps improve the quality of the question.
5. **Improving the Query:** after reshaping the query, it’s sent to ChatGPT. With the improved question, ChatGPT can understand it better and give a more accurate and relevant response to the user.

This solution differs from the traditional way of simply pasting code into popular LLM models like Gemini, ChatGPT, Bard, etc and offers several benefits over them. One, the model is able to generate a response with up-to-date knowledge taken from the database. Two, the response will also be of better quality since RAG vectorizes the prompt which in turns . Lastly, this reduces redundant work done by programmers, as the model is able to generate a response based on past solutions.

# 3 - Implementation
In this project, we use the following dependencies: Gradient Client and Sentence Transformers. Specifically, we will import models from Hugging Face, including "yuntian-deng/ChatGPT" and 'sentence-transformers/all-MiniLM-L6-v2'. 

Hugging Face is a platform that allows the deployment of AI and machine learning models for free.
1. **Input the Dataset:** Users start by providing the dataset they want to feed into the embedding model.
2. **Query the Open-Source ChatGPT:** Once the dataset is uploaded, users can make a query to our open-source ChatGPT model. Both the dataset and the query are converted into vectors (numerical representations).
3. **Similarity Matching:** Using the K-Nearest Neighbors (KNN) algorithm, we compare the vectors of the query and the dataset to find similarities. This step helps reshape and refine the query, ensuring it is of higher quality before passing it to ChatGPT.
4. **Processing with ChatGPT:** After the refined query is passed to ChatGPT, the model processes it and provides a more accurate and relevant response to the user.

# 4 - Demonstration
How to use:
1. Open the Jupyter notebook from our repo.
2. If you don't have existing JSON data, download the sample JSON files from the repo.
3. Upload the text and json file into the dir “/content” (left sidebar)
4. Create an account in https://huggingface.co/
5. Navigate to the Settings -> Access Tokens.
6. Create a new Hugging Face token (read).
7. Copy the token and paste it on the third cell in the jupyter notebook.
8. Run every cell one by one and ensure the dependencies are properly installed.
9. Enter code for error checking into the prompt. This prompt appears after every cell has been run without errors.
10. Enter “Exit” to quit the session if you want.
