# Data Engineering Practice Cleaning Data with PySpark
As a Data Engineer at an electronics e-commerce company, Voltmart, you have been requested by a peer Machine Learning team to clean the data containing the information about orders made last year. They are planning to further use this cleaned data to build a demand forecasting model. To achieve this, they have shared their requirements regarding the desired output table format.

An analyst shared a parquet file called `"orders_data.parquet"` for you to clean and preprocess. 

You can see the dataset schema below along with the **cleaning requirements**:

## `orders_data.parquet`

| column | data type | description | cleaning requirements | 
|--------|-----------|-------------|-----------------------|
| `order_date` | `timestamp` | Date and time when the order was made | _Modify: Remove orders placed between 12am and 5am (inclusive); convert from timestamp to date_ |
| `time_of_day` | `string` | Period of the day when the order was made | _New column containing (lower bound inclusive, upper bound exclusive): "morning" for orders placed 5-12am, "afternoon" for orders placed 12-6pm, and "evening" for 6-12pm_ |
| `order_id` | `long` | Order ID | _N/A_ |
| `product` | `string` | Name of a product ordered | _Remove rows containing "TV" as the company has stopped selling this product; ensure all values are lowercase_ |
| `product_ean` | `double` | Product ID | _N/A_ |
| `category` | `string` | Broader category of a product | _Ensure all values are lowercase_ |
| `purchase_address` | `string` | Address line where the order was made ("House Street, City, State Zipcode") | _N/A_ |
| `purchase_state` | `string` | US State of the purchase address | _New column containing: the State that the purchase was ordered from_ |
| `quantity_ordered` | `long` | Number of product units ordered | _N/A_ |
| `price_each` | `double` | Price of a product unit | _N/A_ |
| `cost_price` | `double` | Cost of production per product unit | _N/A_ |
| `turnover` | `double` | Total amount paid for a product (quantity x price) | _N/A_ |
| `margin` | `double` | Profit made by selling a product (turnover - cost) | _N/A_ |

<br>