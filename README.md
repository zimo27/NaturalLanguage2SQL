# Naural Language to SQL Query Task
## how to run the code

I ran all my code in the given ipynb file on Google Colab. To run the code, please upload the given data file in which I renamed to "src.csv". Write the natural language description of the desired query into variable "input_query". Run all the code blocks in order, the result query would be generated at the end. 


## reflections

With more time, I would improve the model with few shot learning examples and try the second approach of using langChain. 

I experimented with different models of GPT, 4 is the best.

My work flow is included in the PDF file.

## examples

Some generayed samples are listed below:

Find total contributions by each contributor:

```SQL
SELECT contrib, SUM(CAST(REPLACE(REPLACE(amount, '$', ''), ',', '') AS INT)) as total_contrib FROM contributions
GROUP BY contrib;
```

List all contributions made in the year 2022:

```SQL
SELECT * FROM contributions
WHERE strftime('%Y', date) = '2022';
```

Find the top 5 recipients who received the highest total contributions:

```SQL
SELECT recipient, SUM(CAST(REPLACE(REPLACE(amount, '$', ''), ',', '') AS INT)) as total_contrib FROM contributions
GROUP BY recipient
ORDER BY total_contrib DESC
LIMIT 5;
```
Count the number of contributions made by contributors from the state of California (CA):

```SQL
SELECT COUNT(*) FROM contributions
WHERE state = 'CA';
```

Find the average contribution amount:

```SQL
SELECT AVG(CAST(REPLACE(REPLACE(amount, '$', ''), ',', '') AS INT)) as Avg_contrib FROM contributions;
```

Maximum donation done by SBF:

```SQL
SELECT MAX(CAST(REPLACE(REPLACE(amount, '$', ''), ',', '') AS INT)) AS Max_donation FROM contributions
WHERE contribid = 'SBF';
``` 
