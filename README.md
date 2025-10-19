# SQL-PBI_Inventory_Controlling 
Utilize BigQuery SQL to extract inventory data, connect to Power BI to modeling and build dashboard
# SQL-PBI_Inventory_Controlling 
Please see the pdf files attached above  
  
## I. Introduction     
### 1. Business question
The sales department wants to know the overview of inventory status and look up the product inventory by category and location to come up with an appropriate sales and marketing strategy.
### 2. Dataset
Dataset: **adventureworks2019** (public Google BigQuery dataset)  
  
Dataset dictionary: Please reach file "Data Dictionary" attached above
  
Dataset Schema: https://i0.wp.com/improveandrepeat.com/wp-content/uploads/2018/12/AdvWorksOLTPSchemaVisio.png?ssl=1
   
Dataset access:   
- Log in to your Google Cloud Platform account and create a new project.  
- Navigate to the BigQuery console and select your newly created project. 
- In the navigation panel, select "Add Data" and then "Star a project by name".
- Enter the project name "adventurework2019"   
   
## II. Apply design thinking mindset   
**1. Empathize**

![image](https://github.com/mylam7/SQL-PBI_Inventory_Controlling/assets/133579378/bfe5fe0a-5e62-414b-a729-fbedd19a8e78)

 
**2. Define point of view**

![image](https://github.com/mylam7/SQL-PBI_Inventory_Controlling/assets/133579378/e3f860a6-0cea-4c11-81e3-800a795578ff)

 
**3. Ideate***

![image](https://github.com/mylam7/SQL-PBI_Inventory_Controlling/assets/133579378/ec257ef1-b064-46ab-907e-f6d91f2f816a)


**4&5. Prototype and review**

![image](https://github.com/mylam7/SQL-PBI_Inventory_Controlling/assets/133579378/560b15ce-ed28-41f3-a677-f3249775c5c2)


## III. Main Process
### 1. Extract data with Google BigQuery
#### Output total produced quantity and total sold quantity by month/year/quarter (Fact_Built_&_Sold table)

![image](https://github.com/mylam7/SQL-PBI_Inventory_Controlling/assets/133579378/959b97e4-4d8b-4096-965c-0e7e8d02be9e)


![image](https://github.com/mylam7/SQL-PBI_Inventory_Controlling/assets/133579378/0127f14b-ad43-46c1-98e5-e471f932c7a2)

#### Output product ID, product name, sub-category, category (dim_category table)

![image](https://github.com/mylam7/SQL-PBI_Inventory_Controlling/assets/133579378/5bc81dd5-6f66-424e-8492-e8cba641dac2)
![image](https://github.com/mylam7/SQL-PBI_Inventory_Controlling/assets/133579378/b4659d30-32df-4abe-a512-6cd6e8078452)


#### Output total inventory quantity by product ID (dim_inventory_by_product table)

![image](https://github.com/mylam7/SQL-PBI_Inventory_Controlling/assets/133579378/2b1abad8-ca22-4e32-897e-91312e5b3ac5)



### 2. Connect data to PBI and modelling

- Connect queries above and available tables of dataset to PBI
- Modelling
![image](https://github.com/mylam7/SQL-PBI_Inventory_Controlling/assets/133579378/b398d244-2b92-4e9b-97e9-852dc07f7601)



### 3. Build dashboard

- Using DAX to create measures and calculated columns
- Build 2 report pages

**Overview of inventory by time/location/product**

![image](https://github.com/mylam7/SQL-PBI_Inventory_Controlling/assets/133579378/00205739-d79d-4e38-be72-2883221b5ef6)


**Look up inventory status of each product**

![image](https://github.com/mylam7/SQL-PBI_Inventory_Controlling/assets/133579378/9ab8ab27-9217-4155-8e04-8a9c16f6fcaa)



## IV. Insights
#### 1. Revenue - Inventory overview
- Revenue tends to increase steadily from 2011 to the end of 2013. Every year, revenue usually peaks in the third quarter and gradually declines in the fourth quarter.
- Stock to sales ratio (average inventory value/sales) tends to increase gradually => Inventory efficiency is decreasing
#### 2. Revenue - Inventory by Category
- Current revenue is only recorded from 2 categories: Bikes and Components 
- The largest revenue comes from the Bikes category at $145M (88%), 7 times more than the Components category 
- The Bikes category has the largest inventory value of 24M (70%), nearly 4 times higher than the Components industry (9M). 
- Components have a higher proportion of inventory value than revenue => Overstocking
#### 3. Revenue - Inventory by Subcategory
- Top 3 Subcategory belong to Bikes category, the rest belong to Components category 
- Subcategory Road Bikes, Mountain Bikes, Touring Bikes has a ratio of inventory value to sales ranging from 15 to 21%, higher than Mountain Frames 37% 
- The highest is Subcategory Wheels (210%) => Overstocking
#### 4. Revenue - Inventory by Product
- Top 2 products in the Components category, the rest in the Bikes category 
- These products have a high inventory-to-sales ratio: HL Mountain Frame - Black, 38 (127%), HL Mountain Frame - Silver, 38 (61%), Road-150 Red, 44 (51%) => Overstocking
- Currently, the company has 69 types of products with inventory below the safe level -> Understocking. In which, most products belong to the Other category (55 products).
#### 5. Inventory by Location
- Locations that are occupying the highest amount of inventory are Subassembly (95K units) and Miscellaneous Storage (83K units), but have low total inventory values (3.3M and 1.5M, respectively) => Store many items that are low-value 
- Location Final Assembly and Finished Goods Storage, although not having a high inventory volume (20K and 17K, respectively), have the highest total inventory value (13.6M and 12.2M respectively) => Store items that are high-value.
## V. Recommendations
- Adjusting the amount of inventory to increase or decrease in proportion to the rate of revenue fluctuations, with an increase in the third quarter of each year and a gradual decrease beginning in the fourth quarter.
- Research more about the reason the stock-to-sales ratio tends to rise in order to find solutions to lower inventory costs.
- Make a new marketing plan for Accesories, clothing, and Other categories because they are currently not bringing in revenue.
- Focus on promoting sales of HL Mountain Frame - Black, 38, HL Mountain Frame - Silver, 38 and Road-150 Red, 44 products, as well as products in Subcategory Wheels to resolve inventory backlog
- Notify and check with the production and purchasing departments about the products that are currently out of stock and adjust the Safety Stock level to suit the profitability of each product line.
- Many items are out of stock, so it is recommended to collect more opportunity cost data when an item is out of stock, which can be used to control and forecast future sales.
