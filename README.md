# E-Commerce
### Database Tables
<details>
  <summary>User Profiles Table</summary>
  
  | Column Name        | Data Type        | Description                       |
  |--------------------|-----------------|-----------------------------------|
  | id                 | INT             | Primary key, auto-incrementing     |
  | first_name         | VARCHAR(50)      | User's first name                 |
  | middle_name        | VARCHAR(50)      | User's middle name                |
  | last_name          | VARCHAR(50)      | User's last name                  |
  | gender             | ENUM('male', 'female', 'other') | User's gender       |
  | birthdate          | DATE            | User's date of birth              |
  | contact_number     | VARCHAR(15)      | User's contact number             |
  | avatar             | VARCHAR(100)     | Link or path to user's avatar      |
  | user_address_id    | INT             | Foreign key to user_addresses      |
  | social_media_links_id | INT          | Foreign key to social_media_links |
</details>

<details>
<summary>User Credentials Table</summary>

| Column Name     | Data Type | Description                            |
|-----------------|-----------|----------------------------------------|
| id              | INT       | Primary key, auto-incrementing          |
| username        | VARCHAR(50) | User's username                       |
| password        | VARCHAR(100) | User's password (hashed for security) |
| is_online          | BOOLEAN   | User's online status (true/false)      |
| user_type       | ENUM('standard', 'staff', 'admin') | User's type       |
| user_profile_id | INT       | Foreign key to user_profiles            |
</details>

<details>
  <summary>User Addresses Table</summary>
  
  | Column Name   | Data Type  | Description                          |
  |---------------|------------|--------------------------------------|
  | id            | INT        | Primary key, auto-incrementing        |
  | country       | VARCHAR(50) | Country                              |
  | province      | VARCHAR(50) | Province or state                    |
  | city          | VARCHAR(50) | City or municipality                 |
  | postal_code   | VARCHAR(10) | Postal code                          |
  | barangay      | VARCHAR(50) | Barangay or neighborhood              |
  | street        | VARCHAR(50) | Street name                          |
  | purok         | VARCHAR(50) | Purok or subdivision (if applicable) |
  | house_number  | VARCHAR(20) | House number or building name        |
</details>
  
<details>
  <summary>Social Media Links Table</summary>
  
  | Column Name          | Data Type | Description                              |
  |----------------------|-----------|------------------------------------------|
  | id                   | INT       | Primary key, auto-incrementing            |
  | facebook_link        | VARCHAR(100) | User's Facebook profile link            |
  | instagram_link       | VARCHAR(100) | User's Instagram profile link           |
  | twitter_link         | VARCHAR(100) | User's Twitter profile link             |
  | tiktok_link          | VARCHAR(100) | User's TikTok profile link              |
  | youtube_channel_link | VARCHAR(100) | User's YouTube channel link             |
  | email_address        | VARCHAR(50) | User's email address for social media    |
</details>

<details>
  <summary>Products Table</summary>
  
  | Column Name      | Data Type        | Description                                  |
  |------------------|-----------------|----------------------------------------------|
  | id               | INT             | Primary key, auto-incrementing                |
  | model            | VARCHAR(50)     | Model of the product                         |
  | brand            | VARCHAR(50)     | Brand of the product                         |
  | description      | TEXT            | Description of the product                    |
  | status           | ENUM('pending', 'approved', 'declined') | Product status |
  | price            | DECIMAL(10, 2)   | Price of the product (decimal format)        |
  | seller_profile_id | INT             | Foreign key to user_profiles table           |
  | category_id      | INT             | Foreign key to categories table               |
</details>

<details>
  <summary>Product Images Table</summary>
  
  | Column Name     | Data Type                       | Description                                   |
  |-----------------|--------------------------------|-----------------------------------------------|
  | id              | INT                            | Primary key, auto-incrementing                 |
  | image           | VARCHAR(100)                    | Link or file path for the image                |
  | image_category  | ENUM('main_image', 'secondary_image', 'additional_image') | Category of the image |
  | product_id      | INT                            | Foreign key to products table                  |
</details>

<details>
  <summary>Product Variants Table</summary>
  
  | Column Name   | Data Type | Description                                     |
  |---------------|-----------|-------------------------------------------------|
  | id            | INT       | Primary key, auto-incrementing                   |
  | color         | VARCHAR(50) | Color variant of the product                   |
  | is_available  | BOOLEAN | Availability status  |
  | stock         | INT       | Quantity in stock                               |
  | description   | TEXT      | Description of the product variant               |
| product_id    | INT       | Foreign key to products table                    |
</details>

<details>
  <summary>Categories Table</summary>
  
  | Column Name | Data Type | Description                    |
  |-------------|-----------|--------------------------------|
  | id          | INT       | Primary key, auto-incrementing  |
  | name        | VARCHAR(50) | Name of the category          |
</details>

<details>
  <summary>Transactions Table</summary>
  
  | Column Name   | Data Type      | Description                                      |
  |---------------|----------------|--------------------------------------------------|
  | id            | INT            | Primary key, auto-incrementing                    |
  | time_and_date | DATETIME       | Date and time of the transaction                   |
  | total_price   | DECIMAL(10, 2) | Total price of the transaction (decimal format)   |
  | total_payment | DECIMAL(10, 2) | Total payment made (decimal format)                |
  | total_change  | DECIMAL(10, 2) | Total change returned (decimal format)            |
  | total_discount | DECIMAL(10, 2) | Total discount applied (decimal format)           |
  | customer_id   | INT            | Foreign key to user_profiles table                     |
</details>

<details>
  <summary>Purchases Table</summary>
  
  | Column Name        | Data Type      | Description                                        |
  |--------------------|----------------|----------------------------------------------------|
  | id                 | INT            | Primary key, auto-incrementing                      |
  | price              | DECIMAL(10, 2) | Price of the purchased product (decimal format)    |
  | discount           | DECIMAL(10, 2) | Discount applied to the purchase (decimal format)  |
  | product_count      | INT            | Quantity of the product purchased                   |
  | product_variant_id | INT            | Foreign key to product_variants table               |
  | transaction_id     | INT            | Foreign key to transactions table                   |
</details>

<details>
  <summary>Product Purchase Progresses Table</summary>
  
  | Column Name         | Data Type        | Description                                      |
  |---------------------|-----------------|--------------------------------------------------|
  | id                  | INT             | Primary key, auto-incrementing                    |
  | delivery_start_date  | DATE            | Start date of delivery                           |
  | delivery_end_date    | DATE            | End date of delivery                             |
  | status              | ENUM('on_warehouse', 'delivering', 'delivered', 'approved_by_buyer') | Status of the purchase progress  |
  | purchase_id         | INT             | Foreign key to purchases table                    |
  | delivery_address_id  | INT             | Foreign key to delivery_addresses table          |
</details>

<details>
  <summary>Delivery Addresses Table</summary>
  
  | Column Name   | Data Type  | Description                          |
  |---------------|------------|--------------------------------------|
  | id            | INT        | Primary key, auto-incrementing        |
  | country       | VARCHAR(50) | Country                              |
  | province      | VARCHAR(50) | Province or state                    |
  | city          | VARCHAR(50) | City or municipality                 |
  | postal_code   | VARCHAR(10) | Postal code                          |
  | barangay      | VARCHAR(50) | Barangay or neighborhood              |
  | street        | VARCHAR(50) | Street name                          |
  | purok         | VARCHAR(50) | Purok or subdivision (if applicable) |
  | house_number  | VARCHAR(20) | House number or building name        |
</details>

<details>
  <summary>Vouchers Table</summary>
  
  | Column Name   | Data Type  | Description                              |
  |---------------|------------|------------------------------------------|
  | id            | INT        | Primary key, auto-incrementing            |
  | code          | VARCHAR(20) | Voucher code                             |
  | discount      | DECIMAL(5, 2) | Discount amount (decimal format)         |
  | expiration_date | DATE      | Expiration date of the voucher           |
  | description   | TEXT       | Description or terms of the voucher      |
  | is_active     | BOOLEAN    | Indicates if the voucher is active       |
</details>

<details>
  <summary>Reviews Table</summary>
  
  | Column Name   | Data Type      | Description                                     |
  |---------------|----------------|-------------------------------------------------|
  | id            | INT            | Primary key, auto-incrementing                   |
  | rating        | INT            | Rating given by the user (out of 5)              |
  | comment       | TEXT           | User's comment or review                         |
  | product_id    | INT            | Foreign key to products table                    |
  | reviewer_id       | INT            | Foreign key to user_profiles table                       |
</details>

<details>
  <summary>Activity Logs Table</summary>
  
  | Column Name   | Data Type      | Description                                     |
  |---------------|----------------|-------------------------------------------------|
  | id            | INT            | Primary key, auto-incrementing                   |
  | user_id       | INT            | Foreign key to user_profiles table                       |
  | activity      | TEXT   | Description of the activity                      |
  | timestamp     | DATETIME       | Date and time of the activity  |
</details>



