---
title: Mexico Toy Sales Project
toc: true
toc_sticky: true
tags: powerbi sql dashboard
draft: false
---

# Mexico Toy Sales

Data project from Mexico toy sales dataset from a fictional company from mavenanalytics.io.

Dataset: https://mavenanalytics.io/data-playground?order=date_added%2Cdesc&search=mexico%20toy

### Data Stack Used:
> MySQL, DBngin, dBeaver, PowerBI


## Problem Statement
Maven Toys, a fictional toy company with 50 stores in Mexico and 35 different products wants to leverage their sales and inventory data to drive data-driven decision making. 

## Objectives
### Business Objectives
- Create a dashboard with the Key Performing Indicators (KPIs) of the company such as revenue and margin, performance comparisson between products and stores.
- Inventory dashboard report with reorder points by store.
- Sales forecast.

### Personal Objectives
- Practice SQL: Data cleaning, querying, Exploratory Data Analysis (EDA).
- Practice dashboard creation, creating clean, understandable and well designed visualizations.
- Learn and apply Time Series Analysis.

## Insights Found
- Revenue and Profit have an upward trend. The main driver is the increase in overall number of units sold; the margin percetage has remained fairly unchanged.
- Toys are the best performing product category, consistenlty being among the top two categories with the most revenue every month.
	- Art and Crafts products have recently gained popularity. This category has been the most profitable for the last six months.
- Sports & Outdoors is the worst performing category. The margin % is on par with the Toys category. The bad performance is due to the low volume of units sold.
	- There are stores where up to 30% of their stock at hand corresponds to this category, reducing Sports & Outdoors shelf space is adviced.
- The CDMX 2 store is by far the store with that brings the most revenue (about 20% more than the next best store). 
	- This performance is driven by a mix of having a slightly better margin percentage (4% better than the average margin) as well as selling more product units (almost 10K more units sold than the secund best store)
	- An interesting fact is that the CDMX 2 location is located in an airport. There are only 3 locations located in an airport: CDMX 2 that ranks 1st in revenue, Guadalajara 3 that ranks 2nd and Monterrey 3 that, even though ranks much lower than the other two, is still within the best 50% of locations.
	- An interesting opportunity would be to identify other busy airports where the company can open a new store such as Cancun or maybe even Tijuana.

## Steps Followed

### Download and clean data
1. [Download data](https://mavenanalytics.io/data-playground?order=date_added%2Cdesc&search=mexico%20toy).
2. Create MySQL server using DBngin.
3. Connect to server using dBeaver.
4. Load the products, stores, sales and inventory tables to the database.
5. Explore the raw tables for data cleaning needs: missing values, wrong data types and formats, total records, duplicate values.
6. Create clean tables:
    1. No missing values were found.
    2. Dates and currency values were strings originally, transformed to date and numeric values accordingly

```sql
create table maven_toys_sales.fact_sales as (
    select 
		Sale_ID as sale_id,
		DATE(`Date`) as sale_date,
		Store_ID as store_id,
		Product_ID as product_id,
		Units as units
    from maven_toys_sales.sales 
);

create table maven_toys_sales.dim_stores as (
	select
		store_id,
		store_name,
		store_city,
		store_location,
		DATE(store_open_date) as store_open_date
	from maven_toys_sales.stores
);

create table maven_toys_sales.dim_product as (
	select 
		product_id,
		product_name,
		product_category,
		convert(REPLACE(Product_Cost, '$', ''), float) as product_cost,
		convert(REPLACE(Product_Price, '$', ''), float) as product_price
	from maven_toys_sales.products 
);
```
### Creating a Dashboard using PowerBI
7. Export the clean tables to csv.
8. Create the .pbix file, import the data and create the data model with all four tables.
9. Create the *profit* and *revenue* measures using DAX.

```dax
```

10. Create the summary view.

[Summary Dashboard]()

11. Create other supporting views with more details.

<figure class="third">
	<img src="/images/image-filename-1.jpg">
	<img src="/images/image-filename-2.jpg">
	<img src="/images/image-filename-3.jpg">
	<figcaption>Caption describing these three images.</figcaption>
</figure>

