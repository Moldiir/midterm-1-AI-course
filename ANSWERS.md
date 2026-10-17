# Midterm 1: answers

GitHub username:moldiir
Session code:zebra-28
Fingerprint:57ba74f6

> Fill in the three lines above from `my_data/DATA.md`. Do not rename headings or table columns: a script reads the numbers.
> Write only in the empty cells and lines. Percentages as 0.78 or 78 %, money as plain numbers.

## AI-use declaration

I used ChatGPT as a study assistant while working on this midterm. At first, I needed help understanding the instructions and figuring out what each part required. I asked questions about Recall@k, MRR, Wilson intervals, and model pricing because I wanted to understand how the calculations worked, not just get the final numbers.

I used Google Colab to generate my personal dataset and run Python code for the calculations. ChatGPT helped me understand how to use the results to compare the retrieval configurations and make a decision based on accuracy and budget. It also helped me understand the purpose of comparing the two document pipelines.

I checked the outputs from my own notebook and transferred the results into ANSWERS.md. This process helped me practise using Python for data analysis and understand how cost, retrieval quality, and data privacy can affect technical decisions.



## Part 1: Retrieval and cost decision

### 1a. Metrics (all 60 questions)

| config | recall@1 | recall@3 | recall@5 | MRR@10 |
| ------ | -------- | -------- | -------- | ------ |
| A      | 0.5833   | 0.6500   | 0.7167   | 0.6443 |
| B      | 0.5167   | 0.6667   | 0.9167   | 0.6440 |


### 1b. Recall and 95 % Wilson interval of each candidate (recall at its own k)

| candidate | recall@k | lower  | upper  |
| --------- | -------- | ------ | ------ |
| A, k=3    | 0.6500   | 0.5236 | 0.7583 |
| A, k=5    | 0.7167   | 0.5923 | 0.8149 |
| B, k=3    | 0.6667   | 0.5406 | 0.7727 |
| B, k=5    | 0.9167   | 0.8193 | 0.9639 |


### 1c. Annual model cost in USD

| candidate | annual cost |
| --------- | ----------: |
| A, k=3    |     9650.86 |
| A, k=5    |    12464.25 |
| B, k=3    |     6488.72 |
| B, k=5    |     7194.01 |


### 1d. Decision (at most 150 words)

Chosen candidate: B, k=5

I choose B, k=5 because its recall@5 is 0.9167, with a 95% Wilson interval of 0.8193–0.9639. Its annual cost is $7,194.01, which is within the $11,100 budget. Its recall is 0.9000 for EN, 0.9500 for RU, and 0.9000 for KK. It offers high retrieval recall at a reasonable cost.


### 1e. Next measurement (at most 60 words)

I would test the chosen configuration on a larger set of real user questions in EN, RU, and KK. This would help confirm that the recall results are reliable, especially for Kazakh, and check performance on different question types.


## Part 2: A document pipeline you can defend

### 2a. Numbers

| pipeline | overall accuracy | weakest cell (language, condition) | accuracy there |  lower |  upper | annual cost |
| -------- | ---------------: | ---------------------------------- | -------------: | -----: | -----: | ----------: |
| H        |           0.8611 | KK, Clean                          |         0.7333 | 0.5555 | 0.8582 |   $6,190.40 |
| L        |           0.8556 | KK, Degraded                       |         0.8000 | 0.6269 | 0.9049 |  $10,800.00 |



Personal-data pages per year sent abroad under H:481800


### 2b. Memo (at most 300 words)
**Memo: Choosing a Document Processing Pipeline**

I recommend Pipeline L for processing documents because it provides better privacy and more consistent results across different conditions.

Pipeline H has a slightly higher overall accuracy of 86.11%, compared to 85.56% for Pipeline L. However, Pipeline H performs poorly in its weakest case, with only 73.33% accuracy for clean Kazakh documents. Pipeline L has a higher minimum accuracy of 83.33%, making its performance more consistent.

Pipeline H costs $6,190.40 per year, while Pipeline L costs $10,800 per year. Although Pipeline L is $4,609.60 more expensive annually, it keeps document processing within Kazakhstan.

This is important because 33% of the 4,000 daily pages contain names and IINs. With Pipeline H, approximately 481,800 personal-data pages would be sent abroad each year. Pipeline L avoids this additional privacy risk because the documents are processed locally.

Pipeline L can also handle up to 8,000 pages per day, which is enough for our current volume of 4,000 pages per day.

Overall, I recommend Pipeline L because its accuracy is nearly the same as Pipeline H, its weakest-case performance is better, and it protects personal data by keeping processing local. The additional annual cost is reasonable considering the privacy benefits and more consistent performance.


## Part 3: Explain your own numbers

### Q1

Number:
Why (at most 40 words):

### Q2

Number:
Why (at most 40 words):

### Q3

Number:
Why (at most 40 words):

### Q4

Number:
Why (at most 40 words):

### Q5

Number:
Why (at most 40 words):
