# Final-Project-Transforming-and-Analyzing-Data-with-SQL

## Project/Goals

Create database ecommerce to extract, transform and analyse the data to create meaningful business insights for the website owner.

## data process  

>* Extracting data from a SQL database
>
>* Cleaning, transforming and analyzing data
>
>* Loading data into a database
>
>* Developing and implementing a QA process to validate transformed data against raw data


## Analyzing Results

#### Question 1: Which cities and countries have the highest level of transaction revenues on the site?
* Top city
```
"city"	"transaction_revenues"
"Mountain View"	47333200000
"New York"	19880210000
"San Francisco"	15841040000
"Sunnyvale"	13959810000
"San Jose"	8080470000
```
* Top country
```
"country"	"transaction_revenues"
"United States"	161066150000
"India"	8854600000
"United Kingdom"	6097710000
"Canada"	5259000000
"Australia"	3619580000
```

#### Question 2: What is the average number of products ordered from visitors in each city and country?

* top 10 city
```
"city"	"avgproductordered"
"San Bruno"	52.67
"Mountain View"	16.17
"San Jose"	8.57
"Salem"	7.55
"New York"	6.9
"Chicago"	6.19
"Nashville"	5.33
"Jersey City"	5.27
"Charlotte"	4.65
"Sunnyvale"	4.07
```
* top 10 country
```
"country"	"avgproductordered"
"United States"	7.54
"Canada"	2.14
"Germany"	1.45
"Hong Kong"	1.25
"India"	1.25
"France"	1
"Chile"	1
"Indonesia"	1
"Finland"	1
"Colombia"	1
```
#### Question 3: Is there any pattern in the types (product categories) of products ordered from visitors in each city and country?

* Top average ordered product by visitors with category in cities
```
"city"	"productcategory"	"productname"	"avgprooductordered"
"Mountain View"	"Home/Accessories/Stickers/"	"Waze Baby on Board Window Decal"	193.57
"Sunnyvale"	"Home/Office/Notebooks & Journals/"	"Google Hard Cover Journal"	167
"San Jose"	"Home/Drinkware/Water Bottles and Tumblers/"	"22 oz Android Bottle"	115.67
"Seattle"	"Home/Accessories/Fun/"	"Google Luggage Tag"	100
"San Bruno"	"Home/Shop by Brand/YouTube/"	"22 oz YouTube Bottle Infuser"	99.79
"New York"	"(not set)"	"Collapsible Shopping Bag"	30.65
"Atlanta"	"Home/Drinkware/"	"20 oz Stainless Steel Insulated Tumbler"	25
"Chicago"	"Home/Shop by Brand/"	"Google Alpine Style Backpack"	15.32
"Austin"	"Home/Office/Notebooks & Journals/"	"YouTube RFID Journal"	8.53
"Salem"	"Home/Apparel/Men's/Men's-Outerwear/"	"Google Men's  Zip Hoodie"	8.2
"Los Angeles"	"Home/Electronics/"	"Basecamp Explorer Powerbank Flashlight"	5.62
"Nashville"	"Nest-USA"	"Nest® Learning Thermostat 3rd Gen-USA - Stainless Steel"	5.33
"Jersey City"	"Home/Bags/Backpacks/"	"Google Laptop Tech Backpack"	5.27
"Milpitas"	"Home/Nest/Nest-USA/"	"Nest® Protect Smoke + CO Black Battery Alarm-USA"	5.25
"Charlotte"	"Home/Bags/"	"Google Lunch Bag"	4.65
"Pittsburgh"	"Home/Office/Notebooks & Journals/"	"YouTube Hard Cover Journal"	4
"Paris"	"Home/Apparel/Women's/Women's-Outerwear/"	"Google Women's Quilted Insulated Vest Black"	3.5
"Cambridge"	"Home/Electronics/Electronics Accessories/"	"Galaxy Screen Cleaning Cloth"	3.32
"San Francisco"	"Home/Nest/Nest-USA/"	"Nest® Learning Thermostat 3rd Gen-USA - Stainless Steel"	3
"Kirkland"	"Home/Apparel/Women's/"	"Google Women's Long Sleeve Tee Lavender"	2.94
"Toronto"	"Apparel"	"Google Men's 3/4 Sleeve Raglan Henley Grey"	2.6
"Houston"	"${escCatTitle}"	"Google Sunglasses"	2.5
"Hyderabad"	"Home/Accessories/Stickers/"	"Keyboard DOT Sticker"	2
"Denver"	"Home/Apparel/Headgear/"	"Google Twill Cap"	2
"Palo Alto"	"Home/Nest/Nest-USA/"	"Nest® Learning Thermostat 3rd Gen-USA - Stainless Steel"	1.83
"Hamburg"	"Home/Drinkware/"	"22 oz YouTube Bottle Infuser"	1.71
"Santa Monica"	"Home/Bags/"	"Google Slim Utility Travel Bag"	1.4
"Hong Kong"	"Home/Electronics/Electronics Accessories/"	"Google Device Stand"	1.28
"Kitchener"	"Home/Apparel/Headgear/"	"Google 5-Panel Cap"	1
"Madrid"	"(not set)"	"Nest® Protect Smoke + CO White Wired Alarm-USA"	1
"Jakarta"	"Home/Shop by Brand/Android/"	"Windup Android"	1
"Minato"	"Home/Apparel/Headgear/"	"Google 5-Panel Snapback Cap"	1
"Montevideo"	"Home/Apparel/Men's/Men's-T-Shirts/"	"Google Vintage Henley Grey/Black"	1
"Irvine"	"(not set)"	"Google Women's Convertible Vest-Jacket Sea Foam Green"	1
"Munich"	"Home/Apparel/Headgear/"	"Google Twill Cap"	1
"Helsinki"	"(not set)"	"Android Onesie Gold"	1
"Osaka"	"Home/Apparel/Kid's/Kid's-Infant/"	"Google Infant Short Sleeve Tee Red"	1
"Fremont"	"Home/Nest/Nest-USA/"	"Nest® Protect Smoke + CO White Battery Alarm-USA"	1
"Dublin"	"Home/Bags/"	"Google Laptop Backpack"	1
"Phoenix"	"Home/Apparel/Men's/"	"Google Men's Short Sleeve Hero Tee Heather"	1
"Detroit"	"Drinkware"	"Google 22 oz Water Bottle"	1
"Dallas"	"Home/Shop by Brand/YouTube/"	"YouTube Leatherette Notebook Combo"	1
"Cupertino"	"Home/Nest/Nest-USA/"	"Nest® Protect Smoke + CO White Wired Alarm-USA"	1
"San Diego"	"Home/Accessories/Stickers/"	"Google Doodle Decal"	1
"Courbevoie"	"Home/Shop by Brand/"	"Android Wool Heather Cap Heather/Black"	1
"Bogota"	"Home/Apparel/Men's/Men's-T-Shirts/"	"YouTube Men's 3/4 Sleeve Henley"	1
"Santa Clara"	"Home/Accessories/Fun/"	"Android Luggage Tag"	1
"Ahmedabad"	"(not set)"	"Google Youth Short Sleeve T-shirt Royal Blue"	1
"Santiago"	"Home/Bags/"	"Sport Bag"	1
"Berlin"	"Home/Office/"	"Google Doodle Decal"	1
"Seoul"	"Home/Apparel/"	"Waze Dress Socks"	1
"Singapore"	"(not set)"	"Google Men's Short Sleeve Performance Badge Tee Navy"	1
"South San Francisco"	"Home/Bags/Backpacks/"	"Google Rucksack"	1
"Stockholm"	"Home/Drinkware/Mugs and Cups/"	"Android Rise 14 oz Mug"	1
"Bangkok"	"Home/Drinkware/"	"26 oz Double Wall Insulated Bottle"	1
"Sydney"	"(not set)"	"Google Women's Short Sleeve Hero Tee Sky Blue"	1
"Tel Aviv-Yafo"	"Home/Apparel/Men's/Men's-T-Shirts/"	"Google Men's Vintage Tank"	1
"Ann Arbor"	"Home/Apparel/Men's/Men's-T-Shirts/"	"Google Men's Vintage Badge Tee Black"	1
"Washington"	"Home/Apparel/Kid's/Kid's-Infant/"	"Google Bib White"	1
"Yokohama"	"Home/Shop by Brand/Google/"	"Google Rucksack"	1
"Zhongli District"	"(not set)"	"Spiral Notebook and Pen Set"	1
"London"	"(not set)"	"Google Men's Lightweight Microfleece Jacket Black"	1
"Zurich"	"Home/Accessories/Stickers/"	"Waze Mood Ninja Window Decal"	1
```
* Top average ordered product by visitors with category in countries
```
"country"	"productcategory"	"productname"	"avgprooductordered"
"United States"	"Home/Accessories/Stickers/"	"Waze Baby on Board Window Decal"	176.06
"Czechia"	"(not set)"	"Google Snapback Hat Black"	15.18
"Canada"	"(not set)"	"Waze Pack of 9 Decal Set"	10
"Japan"	"(not set)"	"Rubber Grip Ballpoint Pen 4 Pack"	5
"India"	"Home/Accessories/Stickers/"	"Keyboard DOT Sticker"	2
"Mexico"	"Home/Nest/Nest-USA/"	"Nest® Cam Indoor Security Camera - USA"	2
"Germany"	"Home/Drinkware/"	"22 oz YouTube Bottle Infuser"	1.71
"Bulgaria"	"Home/Apparel/Men's/Men's-T-Shirts/"	"YouTube Men's Vintage Tank"	1.5
"Hong Kong"	"Home/Electronics/Electronics Accessories/"	"Google Device Stand"	1.28
"Finland"	"(not set)"	"Android Onesie Gold"	1
"France"	"Home/Apparel/Headgear/"	"YouTube Wool Heather Cap Heather/Black"	1
"Guatemala"	"Home/Apparel/Headgear/"	"YouTube Twill Cap"	1
"Indonesia"	"Home/Bags/Backpacks/"	"Google Rucksack"	1
"Ireland"	"Home/Bags/"	"Google Laptop Backpack"	1
"Israel"	"Home/Apparel/Men's/Men's-T-Shirts/"	"Google Men's Vintage Tank"	1
"Maldives"	"Home/Apparel/Men's/Men's-Outerwear/"	"Google Men's Performance Full Zip Jacket Black"	1
"Netherlands"	"Home/Shop by Brand/YouTube/"	"YouTube Hard Cover Journal"	1
"Norway"	"Home/Apparel/Women's/Women's-T-Shirts/"	"Google Women's Short Sleeve Hero Tee Black"	1
"Portugal"	"Home/Bags/"	"Large Zipper Top Tote Bag"	1
"Romania"	"(not set)"	"8 pc Android Sticker Sheet"	1
"Russia"	"Home/Accessories/Housewares/"	"YouTube Luggage Tag"	1
"Singapore"	"(not set)"	"Google Men's Short Sleeve Performance Badge Tee Navy"	1
"South Korea"	"Home/Apparel/"	"Waze Dress Socks"	1
"Spain"	"(not set)"	"Nest® Protect Smoke + CO White Wired Alarm-USA"	1
"Sri Lanka"	"Home/Apparel/Men's/Men's-T-Shirts/"	"YouTube Men's 3/4 Sleeve Henley"	1
"Sweden"	"(not set)"	"Google Women's Short Sleeve Hero Tee Sky Blue"	1
"Switzerland"	"Home/Accessories/Stickers/"	"Waze Mood Ninja Window Decal"	1
"Taiwan"	"(not set)"	"Spiral Notebook and Pen Set"	1
"Thailand"	"Home/Bags/"	"Waterproof Backpack"	1
"United Kingdom"	"(not set)"	"Android Sticker Sheet Ultra Removable"	1
"Uruguay"	"Home/Apparel/Men's/Men's-T-Shirts/"	"Google Vintage Henley Grey/Black"	1
"Australia"	"Home/Shop by Brand/YouTube/"	"22 oz YouTube Bottle Infuser"	1
"Vietnam"	"Home/Shop by Brand/YouTube/"	"YouTube RFID Journal"	1
"Austria"	"Home/Accessories/Housewares/"	"Google Car Clip Phone Holder"	1
"Belarus"	"Home/Shop by Brand/Google/"	"Google Stylus Pen w/ LED Light"	1
"Belgium"	"Home/Drinkware/Water Bottles and Tumblers/"	"Google 17 oz Double Wall Stainless Steel Insulated Bottle"	1
"Chile"	"Home/Bags/"	"Sport Bag"	1
"Colombia"	"Home/Apparel/Men's/Men's-T-Shirts/"	"YouTube Men's 3/4 Sleeve Henley"	1
"Denmark"	"Home/Drinkware/"	"26 oz Double Wall Insulated Bottle"	1
"Dominican Republic"	"Home/Apparel/Men's/Men's-T-Shirts/"	"Google Men's Vintage Badge Tee Black"	1
"Egypt"	"Home/Shop by Brand/Android/"	"Android RFID Journal"	1
```
* Top selling product with category in cities
```
"city"	"productcategory"	"productname"	"totalprooductordered"
"Mountain View"	"Home/Accessories/Stickers/"	"Waze Baby on Board Window Decal"	5807
"New York"	"(not set)"	"Collapsible Shopping Bag"	1410
"San Bruno"	"Home/Shop by Brand/YouTube/"	"22 oz YouTube Bottle Infuser"	1397
"Charlotte"	"Home/Bags/"	"Google Lunch Bag"	776
"Sunnyvale"	"Home/Office/Notebooks & Journals/"	"Google Hard Cover Journal"	501
"San Jose"	"Home/Drinkware/Water Bottles and Tumblers/"	"22 oz Android Bottle"	347
"Chicago"	"Home/Shop by Brand/"	"Google Alpine Style Backpack"	337
"Salem"	"Home/Apparel/Men's/Men's-Outerwear/"	"Google Men's  Zip Hoodie"	246
"Los Angeles"	"Home/Electronics/"	"Basecamp Explorer Powerbank Flashlight"	163
"Austin"	"Home/Office/Notebooks & Journals/"	"YouTube RFID Journal"	162
"Hong Kong"	"Home/Electronics/Electronics Accessories/"	"Google Device Stand"	120
"Seattle"	"Home/Accessories/Fun/"	"Google Luggage Tag"	100
"Ann Arbor"	"Home/Electronics/"	"Recycled Mouse Pad"	74
"Cambridge"	"Home/Electronics/Electronics Accessories/"	"Galaxy Screen Cleaning Cloth"	63
"Jersey City"	"Home/Bags/Backpacks/"	"Google Laptop Tech Backpack"	58
"Kirkland"	"Home/Apparel/Women's/"	"Google Women's Long Sleeve Tee Lavender"	50
"Milpitas"	"Home/Apparel/Women's/Women's-T-Shirts/"	"Google Women's Short Sleeve Hero Dark Grey"	33
"Toronto"	"Apparel"	"Google Men's 3/4 Sleeve Raglan Henley Grey"	26
"Atlanta"	"Home/Drinkware/"	"20 oz Stainless Steel Insulated Tumbler"	25
"San Francisco"	"Home/Apparel/Women's/Women's-T-Shirts/"	"Google Women's Scoop Neck Tee White"	22
"Yokohama"	"Home/Shop by Brand/Google/"	"Google Rucksack"	20
"Zhongli District"	"(not set)"	"Spiral Notebook and Pen Set"	16
"Nashville"	"Nest-USA"	"Nest® Learning Thermostat 3rd Gen-USA - Stainless Steel"	16
"Minato"	"Home/Apparel/Headgear/"	"Google 5-Panel Snapback Cap"	14
"Paris"	"Home/Apparel/Women's/Women's-Outerwear/"	"Google Women's Quilted Insulated Vest Black"	14
"Palo Alto"	"Home/Nest/Nest-USA/"	"Nest® Cam Outdoor Security Camera - USA"	13
"Pittsburgh"	"Home/Office/Notebooks & Journals/"	"YouTube Hard Cover Journal"	12
"Hamburg"	"Home/Drinkware/"	"22 oz YouTube Bottle Infuser"	12
"Irvine"	"Home/Apparel/Men's/Men's-T-Shirts/"	"Google Men's Vintage Badge Tee Sage"	10
"Santa Monica"	"Home/Bags/"	"Google Slim Utility Travel Bag"	7
"Osaka"	"Home/Apparel/Kid's/Kid's-Infant/"	"Google Infant Short Sleeve Tee Red"	7
"Fremont"	"Home/Nest/Nest-USA/"	"Nest® Protect Smoke + CO White Battery Alarm-USA"	6
"Bogota"	"Home/Apparel/Men's/Men's-T-Shirts/"	"YouTube Men's 3/4 Sleeve Henley"	6
"South San Francisco"	"Home/Bags/Backpacks/"	"Google Rucksack"	6
"Denver"	"Home/Apparel/Headgear/"	"Google Twill Cap"	6
"London"	"Home/Bags/"	"Google Rucksack"	5
"Houston"	"${escCatTitle}"	"Google Sunglasses"	5
"Helsinki"	"(not set)"	"Android Onesie Gold"	5
"Santa Clara"	"Home/Electronics/"	"Clip-on Compact Charger"	5
"Cupertino"	"Home/Nest/Nest-USA/"	"Nest® Protect Smoke + CO White Wired Alarm-USA"	4
"Zurich"	"Home/Apparel/Men's/Men's-T-Shirts/"	"YouTube Men's 3/4 Sleeve Henley"	4
"Bangkok"	"Home/Drinkware/"	"26 oz Double Wall Insulated Bottle"	3
"Dallas"	"Home/Shop by Brand/YouTube/"	"YouTube Leatherette Notebook Combo"	3
"Detroit"	"Drinkware"	"Google 22 oz Water Bottle"	3
"Seoul"	"Home/Apparel/"	"Waze Dress Socks"	2
"Dublin"	"Home/Bags/"	"Google Laptop Backpack"	2
"Munich"	"Home/Apparel/Men's/Men's-T-Shirts/"	"Google Men's 100% Cotton Short Sleeve Hero Tee Red"	2
"Ahmedabad"	"(not set)"	"Google Youth Short Sleeve T-shirt Royal Blue"	2
"Santiago"	"Home/Bags/"	"Sport Bag"	2
"Hyderabad"	"Home/Accessories/Stickers/"	"Keyboard DOT Sticker"	2
"San Diego"	"Home/Accessories/Stickers/"	"Google Doodle Decal"	1
"Jakarta"	"Home/Shop by Brand/Android/"	"Windup Android"	1
"Singapore"	"(not set)"	"Google Men's Short Sleeve Performance Badge Tee Navy"	1
"Kitchener"	"Home/Apparel/Headgear/"	"Google 5-Panel Cap"	1
"Stockholm"	"Home/Drinkware/Mugs and Cups/"	"Android Rise 14 oz Mug"	1
"Courbevoie"	"Home/Shop by Brand/"	"Android Wool Heather Cap Heather/Black"	1
"Sydney"	"(not set)"	"Google Women's Short Sleeve Hero Tee Sky Blue"	1
"Tel Aviv-Yafo"	"Home/Apparel/Men's/Men's-T-Shirts/"	"Google Men's Vintage Tank"	1
"Montevideo"	"Home/Apparel/Men's/Men's-T-Shirts/"	"Google Vintage Henley Grey/Black"	1
"Washington"	"Home/Apparel/Kid's/Kid's-Infant/"	"Google Bib White"	1
"Madrid"	"(not set)"	"Nest® Protect Smoke + CO White Wired Alarm-USA"	1
"Berlin"	"Home/Office/"	"Google Doodle Decal"	1
"Phoenix"	"Home/Apparel/Men's/"	"Google Men's Short Sleeve Hero Tee Heather"	1
```
* Top selling product with categoty in countries
```
"country"	"productcategory"	"productname"	"totalprooductordered"
"United States"	"Home/Accessories/Stickers/"	"Waze Baby on Board Window Decal"	5807
"Hong Kong"	"Home/Electronics/Electronics Accessories/"	"Google Device Stand"	120
"Canada"	"Apparel"	"Google Men's 3/4 Sleeve Raglan Henley Grey"	26
"Japan"	"Home/Shop by Brand/Google/"	"Google Rucksack"	20
"Taiwan"	"(not set)"	"Spiral Notebook and Pen Set"	16
"Germany"	"Home/Drinkware/"	"22 oz YouTube Bottle Infuser"	12
"Colombia"	"Home/Apparel/Men's/Men's-T-Shirts/"	"YouTube Men's 3/4 Sleeve Henley"	6
"Finland"	"(not set)"	"Android Onesie Gold"	5
"United Kingdom"	"Home/Bags/"	"Google Rucksack"	5
"Switzerland"	"Home/Apparel/Men's/Men's-T-Shirts/"	"YouTube Men's 3/4 Sleeve Henley"	4
"Thailand"	"Home/Drinkware/"	"26 oz Double Wall Insulated Bottle"	3
"South Korea"	"Home/Apparel/"	"Waze Dress Socks"	2
"India"	"(not set)"	"Google Youth Short Sleeve T-shirt Royal Blue"	2
"Chile"	"Home/Bags/"	"Sport Bag"	2
"Ireland"	"Home/Bags/"	"Google Laptop Backpack"	2
"Uruguay"	"Home/Apparel/Men's/Men's-T-Shirts/"	"Google Vintage Henley Grey/Black"	1
"France"	"Home/Shop by Brand/"	"Android Wool Heather Cap Heather/Black"	1
"Indonesia"	"Home/Shop by Brand/Android/"	"Windup Android"	1
"Israel"	"Home/Apparel/Men's/Men's-T-Shirts/"	"Google Men's Vintage Tank"	1
"Singapore"	"(not set)"	"Google Men's Short Sleeve Performance Badge Tee Navy"	1
"Spain"	"(not set)"	"Nest® Protect Smoke + CO White Wired Alarm-USA"	1
"Sweden"	"Home/Drinkware/Mugs and Cups/"	"Android Rise 14 oz Mug"	1
"Australia"	"Home/Apparel/Men's/"	"Google Men's Vintage Tank"	1
```

#### Question 4: What is the top-selling product from each city/country? Can we find any pattern worthy of noting in the products sold?

* top selling product in each country
```
"country"	"productname"	"totalproductordered"	
"United States"	"Waze Baby on Board Window Decal"	5807	
"Hong Kong"	"Google Device Stand"	120	
"Canada"	"Google Men's 3/4 Sleeve Raglan Henley Grey"	26	
"Japan"	"Google Rucksack"	20	
"Taiwan"	"Spiral Notebook and Pen Set"	16	
"Germany"	"22 oz YouTube Bottle Infuser"	12	
"Colombia"	"YouTube Men's 3/4 Sleeve Henley"	6	
"Finland"	"Android Onesie Gold"	5	
"United Kingdom"	"Google Rucksack"	5	
"Switzerland"	"YouTube Men's 3/4 Sleeve Henley"	4	
"Thailand"	"26 oz Double Wall Insulated Bottle"	3	
"South Korea"	"Waze Dress Socks"	2	
"India"	"Keyboard DOT Sticker"	2	
"Chile"	"Sport Bag"	2	
"Ireland"	"Google Laptop Backpack"	2	
"Uruguay"	"Google Vintage Henley Grey/Black"	1	
"France"	"Android Lunch Kit"	1	
"Indonesia"	"Windup Android"	1	
"Israel"	"Google Men's Vintage Tank"	1	
"Singapore"	"Google Men's Short Sleeve Performance Badge Tee Navy"	1	
"Spain"	"Nest® Protect Smoke + CO White Wired Alarm-USA"	1	
"Sweden"	"Android Rise 14 oz Mug"	1	
"Australia"	"Google Men's Vintage Tank"	1	
```
* top selling product in each city
```
"city"	"productname"	"totalproductordered"
"Mountain View"	"Waze Baby on Board Window Decal"	5807
"New York"	"Collapsible Shopping Bag"	1410
"San Bruno"	"22 oz YouTube Bottle Infuser"	1397
"Charlotte"	"Google Lunch Bag"	776
"Sunnyvale"	"Google Hard Cover Journal"	501
"San Jose"	"22 oz Android Bottle"	347
"Chicago"	"Google Alpine Style Backpack"	337
"Salem"	"Google Men's  Zip Hoodie"	246
"Los Angeles"	"Basecamp Explorer Powerbank Flashlight"	163
"Austin"	"YouTube RFID Journal"	162
"Hong Kong"	"Google Device Stand"	120
"Seattle"	"Google Luggage Tag"	100
"Ann Arbor"	"Recycled Mouse Pad"	74
"Cambridge"	"Galaxy Screen Cleaning Cloth"	63
"Jersey City"	"Google Laptop Tech Backpack"	58
"Kirkland"	"Google Women's Long Sleeve Tee Lavender"	50
"Milpitas"	"Google Women's Short Sleeve Hero Dark Grey"	33
"Toronto"	"Google Men's 3/4 Sleeve Raglan Henley Grey"	26
"Atlanta"	"20 oz Stainless Steel Insulated Tumbler"	25
"San Francisco"	"Google Women's Scoop Neck Tee White"	22
"Yokohama"	"Google Rucksack"	20
"Zhongli District"	"Spiral Notebook and Pen Set"	16
"Nashville"	"Nest® Learning Thermostat 3rd Gen-USA - Stainless Steel"	16
"Minato"	"Google 5-Panel Snapback Cap"	14
"Paris"	"Google Women's Quilted Insulated Vest Black"	14
"Palo Alto"	"Nest® Cam Outdoor Security Camera - USA"	13
"Pittsburgh"	"YouTube Hard Cover Journal"	12
"Hamburg"	"22 oz YouTube Bottle Infuser"	12
"Irvine"	"Google Men's Vintage Badge Tee Sage"	10
"Santa Monica"	"Google Slim Utility Travel Bag"	7
"Osaka"	"Google Infant Short Sleeve Tee Red"	7
"Fremont"	"Nest® Protect Smoke + CO White Battery Alarm-USA"	6
"Bogota"	"YouTube Men's 3/4 Sleeve Henley"	6
"South San Francisco"	"Google Rucksack"	6
"Denver"	"Google Twill Cap"	6
"London"	"Google Rucksack"	5
"Houston"	"Google Sunglasses"	5
"Helsinki"	"Android Onesie Gold"	5
"Santa Clara"	"Clip-on Compact Charger"	5
"Cupertino"	"Nest® Protect Smoke + CO White Wired Alarm-USA"	4
"Zurich"	"YouTube Men's 3/4 Sleeve Henley"	4
"Bangkok"	"26 oz Double Wall Insulated Bottle"	3
"Dallas"	"YouTube Leatherette Notebook Combo"	3
"Detroit"	"Google 22 oz Water Bottle"	3
"Seoul"	"Waze Dress Socks"	2
"Dublin"	"Google Laptop Backpack"	2
"Munich"	"Google Men's 100% Cotton Short Sleeve Hero Tee Red"	2
"Ahmedabad"	"Google Youth Short Sleeve T-shirt Royal Blue"	2
"Santiago"	"Sport Bag"	2
"Hyderabad"	"Keyboard DOT Sticker"	2
"San Diego"	"Google Doodle Decal"	1
"Jakarta"	"Windup Android"	1
"Singapore"	"Google Men's Short Sleeve Performance Badge Tee Navy"	1
"Kitchener"	"Google 5-Panel Cap"	1
"Stockholm"	"Android Rise 14 oz Mug"	1
"Courbevoie"	"Android Wool Heather Cap Heather/Black"	1
"Sydney"	"Google Women's Short Sleeve Hero Tee Sky Blue"	1
"Tel Aviv-Yafo"	"Google Men's Vintage Tank"	1
"Montevideo"	"Google Vintage Henley Grey/Black"	1
"Washington"	"Google Bib White"	1
"Madrid"	"Nest® Protect Smoke + CO White Wired Alarm-USA"	1
"Berlin"	"Google Doodle Decal"	1
"Phoenix"	"Google Men's Short Sleeve Hero Tee Heather"	1

```
#### Question 5: Can we summarize the impact of revenue generated from each city/country?

* top 10 city with biggest impact on generating revenue
```
"city"	"total_revenue"
"Mountain View"	10549490000
"San Bruno"	4230990000
"New York"	3485790200
"Sunnyvale"	3039259600
"Chicago"	1383630100
"Charlotte"	1161390100
"Kirkland"	1103520000
"San Francisco"	987450000
"Los Angeles"	943000060
"Jersey City"	933850000

```

* top 5 country with biggest impact on generating revenue
```
"country"	"total_revenue"
"United States"	115229245000
"Canada"	487670020
"Germany"	69980000
"Japan"	30880000
"Switzerland"	16990000

```

## Challenges 
(discuss challenges you faced in the project)

## Future Goals
(what would you do if you had more time?)
