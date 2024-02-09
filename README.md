# [Instacart SQL Data Analytics Case Study](https://datalemur.com/sql-tutorial/instacart-sql-data-analytics-case-study)

### Contents:
- [Introduction](#introduction)
- [About Instacart](#case-study-background-about-instacart)
- [The Data Analysis Task](#case-study-background-the-data-analysis-task)
- [Instacart Grocery Orders Data](#case-study-background-instacart-grocery-orders-data)
  - [ic_order_products_curr](#ic_order_products_curr)
  - [ic_order_products_prior](#ic_order_products_prior)
  - [ic_products](#ic_products)
  - [ic_departments](#ic_departments)
  - [ic_aisles](#ic_aisles)

## Introduction
Let's apply all we've learned across the 30+ past SQL lessons to a real-world case study where we'll analyze data from Instacart. While there's no one correct solution to this open-ended Data Analytics problem, we've included a few sample SQL queries to help you get started.

## Case Study Background: About Instacart
[Instacart](https://www.instacart.com/) is a grocery delivery and pickup service. Users can select items from local grocery stores through the Instacart app or website, and then either have them delivered to their doorstep by a personal shopper or prepared for pickup at the store.

## Case Study Background: The Data Analysis Task
You’re a data analyst at Instacart. Aside from the discounted groceries, you also get the benefit of solving interesting data problems.

In your 1-1 call this morning, your manager tells you that leadership wants to analyze the Instacart market data over time, to understand how the business is changing or staying the same.

Unfortunately, data engineering found some logging errors in the pipeline, and there are currently no date fields in the market data tables 🙃.

Your manager has a call with engineering tomorrow to work on fixing this so the team can track changes more closely in the future. But you’re already mid-way through Q3 and the data pipeline can’t be refreshed again until Q4. So for now, you’re stuck with the data you have.

**The Task:**  
Find a way to understand how Instacart's business changed over time…without using explicit dates!

Before you panic about time-series data analysis without time-series data, take a deep breath, it's all going to be okay. Take a look at the data you have access to... things will start to click!

## Case Study Background: Instacart Grocery Orders [Data](https://www.kaggle.com/competitions/instacart-market-basket-analysis/data)
Here are the schemas for all 5 tables in the Instacart market data. You’ll decide which ones are relevant and how to best use them throughout this case study.

### ic_order_products_curr
This table specifies which products were purchased in each Instacart order.

| Column Name        | Type     |
|--------------------|----------|
| order_id           | integer  |
| product_id         | integer  |
| add_to_cart_order  | integer  |
| reordered          | integer boolean (1 or 0) |

Notes:
- The 'reordered' field indicates that the customer has a previous order that contains the product.
- Some orders will have no reordered items.
- None of these fields are unique to this table, but the combination of order_id and product_id is unique!

### ic_order_products_prior
This table contains previous order contents for all customers. This data was collected in Q2, verus ic_order_products_currwhich is data from the current quarter (Q3).

| Column Name        | Type     |
|--------------------|----------|
| order_id           | integer  |
| product_id         | integer  |
| add_to_cart_order  | integer  |
| reordered          | integer boolean (1 or 0) |

**Note:**  
The table ic_order_products_prior has the same exact schema as ic_order_products_curr. You'll likely want to compare these two tables!

### ic_products
Info about each item in the Instacart product catalog

| Column Name   | Type    |
|---------------|---------|
| product_id    | integer |
| product_name  | string  |
| aisle_id      | integer |
| department_id | integer |

### ic_departments
Info about each department

| Column Name   | Type    |
|---------------|---------|
| department_id | integer |
| department    | string  |

### ic_aisles
Info about each aisle in a grocery store

| Column Name   | Type    |
|---------------|---------|
| aisle_id      | integer |
| aisle         | string  |

Before you make any assumptions, explore the tables below and make sure you understand their structures. You can explore the Instacart data [here](link to explore the Instacart data)!

## Practice Problem
Explore Instacart case study data.

## Your Turn: Start Analyzing with SQL!
Given the above data and the task mentioned earlier, go to town and come up with a solution. There's no more instructions, rules, or constraints, go nuts!

Just remember – it's not really about finding the “right” answer; it's about finding some business insights that you can defend with confidence!

## Our Solution
Here's how we'd approach this ambiguous data case study. Feel free to follow this approach, or adapt it to derive your own insights!

### Our Solution: High-Level Overview
1. Identify the two specific tables you should focus on to understand broad trends over time.
2. Consider a phenomenon in the data that may have changed over time. Choose something practical that you can highlight to your manager.
3. Define in plain ol' English how you plan to investigate the data to solve the data analysis task.
4. Express that approach in SQL.
5. If your observed phenomenon has changed over time, develop 2 or more hypotheses to explain potential causes of that change. If your observed phenomenon has not changed over time, develop 2 or more hypotheses to explain why this phenomenon has remained stagnant.
6. Consider other relevant factors aside from just the Instacart data, such as food trends, seasonality, supply chain, etc.
7. **BONUS:** Based on your hypotheses, write a recommendation to leadership explaining how they should either:
   - Support this phenomenon if it’s helpful to Instacart business, or
   - Combat this phenomenon if it’s harmful to Instacart business.
If you want to check your work against our solution, scroll down to check the answer key below.

Remember, a successful case study simply means you developed a coherent process with a data-driven conclusion and defended your method! It doesn’t have to be the same as ours; it just needs to be similarly rigorous!
