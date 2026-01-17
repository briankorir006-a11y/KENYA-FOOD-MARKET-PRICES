# KENYA-FOOD-MARKET-PRICES

**END-TO-END POWER BI PROJECT ANALYZING FOOD PRICE TRENDS ACROSS KENYA**



This project presents an end-to-end Power BI analysis of food market prices in Kenya.

The dashboard focuses on price trends, regional comparisons, and category-level analysis.



**Data Source**

Kaggle – Kenya Food Market Prices dataset

**Dataset**

Click [here](https://drive.google.com/file/d/1iiR_zMYamxI2Uf3Kf8vF6xdBw4bov3Wj/view?usp=drive_link) to download the dataset.


**Power BI Report**



Click [here](https://drive.google.com/file/d/1iiR_zMYamxI2Uf3Kf8vF6xdBw4bov3Wj/view?usp=drive_link) to download the Power BI report.



**Dashboard Features** 



**KPIs**

  - Average Price

  - Highest Price

  - Minimum Price



**Visuals**

  - Food Category vs Average Price

  - Price Over Time

  - Region vs Average Price

  - Sum of Price (KSh) by Commodity \& Region

  - Annual Average Price by Year

  - Year-over-Year (YoY) Price Change %

  - Map showing Sum of Price by Region using Latitude \& Longitude

  - Table with Region and Sum of Price (KSh)

**Measures & Calculations**
**Daily Average Price**
Average Price (Daily) =
AVERAGE ( FACT_FOOD_PRICES[price in Ksh] )


Used for:

*KPI cards

*Price trends over time

**Regional and category comparisons**

Annual Average Price
Annual Average Price =
CALCULATE (
    AVERAGE ( FACT_FOOD_PRICES[price in Ksh] ),
    ALLEXCEPT ( 'Date', 'Date'[Year] )
)


Used for:

*Long-term price trend analysis

*Inflation-related insights

**Year-over-Year (YoY) Price Change %**
YoY Price Change % =
VAR PrevYear =
    CALCULATE (
        [Annual Average Price],
        DATEADD ( 'Date'[Date], -1, YEAR )
    )
RETURN
IF (
    NOT ISBLANK ( PrevYear ),
    DIVIDE (
        [Annual Average Price] - PrevYear,
        PrevYear
    )
)


✔ YoY is calculated only at annual grain
✔ Avoids performance issues from daily/monthly YoY calculations


**Dashboard Preview-Price Analysis**

![alt text](https://github.com/briankorir006-a11y/KENYA-FOOD-MARKET-PRICES/blob/main/Dashboard\_Preview\_Two.png?raw=true)





\## \*\*Dashboard Preview-Price & Map Analysis\*\*

![alt text](https://github.com/briankorir006-a11y/KENYA-FOOD-MARKET-PRICES/blob/main/Dashboard\_Preview\_One.png?raw=true)





**Slicers**

  - Region, Town, Market

  - Price Type

  - Year, Quarter, Month



**Data Modeling**



The model is built using a **star schema**:

*Fact table containing food prices
*Dimension tables for Date, Location, and Food Category


👤 **Author**



Brian Kipkorir Kiptoo.

