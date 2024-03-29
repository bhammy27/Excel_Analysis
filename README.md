# Excel_Analysis
Using Excel to analyze Fantasy Football stats allowed me to realize my passion for data analytics. The evolution of my analysis using Excel began with manually entering hundreds of players names and fantasy point values for draft analysis. As I learned new Excel skills at work, I would apply them to fantasy football. Follow along to see some of the many things I have learned!

# Skills Demonstrated:
- Lookup functions: Vlookup, Xlookup
- Pivot Tables & Charts
- Conditional formatting
- Sparklines
- Named Ranges
- Formatting 
- Formulas Used:
  - **=MID([@Player], FIND("(", [@Player]) + 1, FIND(")", [@Player] [@Player])- FIND("(", [@Player]) - 1)**
    - [@Player] provides reference cell, here it is the Player column
    - Start location is found with FIND ( and adding 1 to get the first space after the (
    - Number of spaces is calculated by first FINDing the position of ) and then subtracting that from the start location
        - That difference provides the number of spaces for the last argument in MID
  - **=IFERROR(ROUND(AVERAGE(tbl_qb_weekly[@[Week 1]:[Week 18]]),2),0)**
    - AVERAGE and named ranges to calculate weekly average
    - ROUND rounds the average to 2 places after the decimal point
    - IFEROR will return 0 if the formula tries to divide by 0 at some point
  - **=IFERROR(VLOOKUP([@Player],tbl_qb_wk1[[Player]:[FPTS]],15,0),"         --")**
    - Vlookup pulls FPTS value (located in the 15th column) from the table tbl_qb_wk1 (week 1 sheet) for the player in Player column
        -  This formula was copied and pasted in each week column when new data became available
        -  By using a consistent table naming format, I could change the 1 in tbl_qb_1 to 2 and pull in info from the week 2 sheet
    - IFERROR will insert -- in the center of the cell when the player did not play due to a Bye or injury
        - I then manually entered BYE for players on Bye Weeks so I could see how many games a player lost due to injury
  - **=XLOOKUP([@Player],tbl_qb_wk18[Player],tbl_qb_wk18[FPTS],"          --")**
        - Using Xlookup eliminates the need to specify row column 15 and the need to use IFERROR

## Weekly Analysis Workbook
-  Identifying weekly trends helps identify player performance trends
  - Underperforming players can be replaced by adding available players from the waiver wire
  - By identifying overper formers, you can trade the player and fill gaps in your roster
      - **I used this info to trade a hot CeeDee Lamb in week 6 for CJ Stroud and Sam LaPorta giving me better production from my quarterback and tight end**
          - I had a very strong collection of wide receivers
          - The points gained from Stroud and LaPorta were greater than Lamb's production
          - After this trade, my team increased 4 positions in the rankings which allowed me to make the playoffs
- I used the following workbook for this analysis:
  
  ![Screenshot (120)](https://github.com/bhammy27/Excel_Analysis/assets/154477061/44d71514-602e-452d-ad04-7c19adc643f5)


  This landing page has hyperlinks to each position workbook embedded in the corresponding position football.
  Clicking on the Quarterback football will take you to the following workbook.

  ### Week stats table
  The data was downloaded from [FantasyPros](https://www.fantasypros.com/nfl/stats/qb.php)
  - The stats for each week of the season were assigned to their own sheet 
  - A table was created and named with the prefix "tbl_qb_" followd up by wk number making it easy to reference in lookup functions
  
 ![Screenshot (121)](https://github.com/bhammy27/Excel_Analysis/assets/154477061/a2ac4471-fcc4-45d4-9b2c-dff9a55165e2)


  ### Weekly Analysis
  
  ![Screenshot (122)](https://github.com/bhammy27/Excel_Analysis/assets/154477061/1f794142-cb2d-474f-9505-e9ee04b888fa)

### this weekly analysis table provided:
-  Easy identification of my current players by highlighting players with red or yellow fill identifying my two legues 
-  Team column makes filtering players by team easier
-  Sparklines provides a quick visual trend reference
-  Total column shows players with the most points
-  Comparing Average points to Total points provides a better measure of players performance
-  Applying conditional formatting quickly points out top players for each week
-  Conditional formatting chart:
    - Green = Highest fantasy points
    - Yellow = Score in Top 5% 
    - Orange = Score in Top 10%
    - Red = Score in Top 25%
    - Blue = Score above weekly or season average
      - Drafting or acquiring as many players with above average scores or greater will guarantee success!
  # Pivot Table Analysis
  Utilizing pivot tables provides better understanding on how each player earns Fantasy Points
  I created a pivot table to display the fantasy point breakdown for each player by scoring category using these calculations
  
![Screenshot (124)](https://github.com/bhammy27/Excel_Analysis/assets/154477061/7ad1f2f6-66f0-4c85-81df-3b0db5df0691)


![Screenshot (125)](https://github.com/bhammy27/Excel_Analysis/assets/154477061/d7448b9b-1254-4aa3-ad16-29a025475f2f)



### **Converting the values to Percent of Total and inserting a Pie Chart brings the data to life**
In the Pie Chart below shows a breakdown of Aaron Jones Fantasy Points distribution 
- Notice most points comes from yards gained
  -  Gaining yards after a catch or by running is the easiest way to accumulate point
  -  A player earns 1 point for every 10 yards gained
-  Aaron Jones has a similar distribution of points from receptions and touchdowns
  -  Receptions are only worth a half point per reception
      -  It would be very alarming if a player had more points from receptions than from total yards
  -  Each touchdown is worth 6 points although they are hard to come by


![Screenshot (128)](https://github.com/bhammy27/Excel_Analysis/assets/154477061/3b5fec8e-d4da-40f5-9c47-59642d0aa24d)



The next Pie Chart shows a breakdown of Zander Horvath's Fantasy Points distribution.
- Zander has a very high percentage of points from touchdowns, which is the stat that produces the most fantasy points 
- Having a decent reception rate and low percent of points from total yards says he is only used near the goal line
  - That tells me he is used in a limited role and could be a boom or bust player each week
-  Due to Zander's strong dependency on touchdowns, **I would avoid having him on my roster**

![Screenshot (127)](https://github.com/bhammy27/Excel_Analysis/assets/154477061/49d91b5c-85ef-4129-a9e4-43bfb74364cc)


  
