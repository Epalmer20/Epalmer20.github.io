#Impeachment Analysis
##October 30, 2020


## run this to load the data for this assignment
## it will create a dataframe called "impeach," with all House Democrats
impeach <- read_csv("https://docs.google.com/spreadsheets/d/e/2PACX-1vRh8d5JaDqBtByzNw2JZF3idaACobDhhk-p7chJoktA0HawELHFOvjQOqCpzGA4MGONvPlR7GASqW-K/pub?gid=1765341510&single=true&output=csv")


# FOR EACH OF THE QUESTIONS BELOW, WRITE YOUR WORKING R CODE TO RETURN THE REQUESTED RESULTS
# USE COMMENTS (PREFACED BY THE #) BEFORE THE WORKING CODE TO EXPLAIN WHAT YOU'RE DOING FOR EACH STEP



# 1) The column "for_impeachment" indicates whether the member has publicly called for
# an impeachment inquiry. Filter to return only the ones where the answer is NO.    

# Used Impeach dataframe name with the pipe to bring up the data set.
# Then I used filter function to locate the column name for impeachment and put the == "NO" response in quotes. 

impeach %>% 
  filter(for_impeachment == "NO")



# 2) Filter to return only results where a member is both against impeachment, and comes from a 
# district that President Trump won in 2016 (which is noted in the "p16winningparty" column)

# Used Impeach dataframe with the pipe bring up the data set, 
# And then I used filter function to locate the column name for_impeachment and put the == "NO" response in quotes and added another pipe. 
# Then I used the filter function again for p16winningparty to sort for == "R" response in quotes. R would correlate to a district that Trump won. 


impeach %>% 
  filter(for_impeachment == "NO") %>%
  filter (p16winningparty == "R")


# 3) Filter for only results where a member is against impeachment, comes from a 
# district that President Trump won in 2016 (which is noted in the "p16winningparty" column),
# and also comes from a district that Mitt Romney won in 2012 ("p12winningparty").

# Use Impeach dataframe with the pipe bring up the data set, 
# I used filter function to locate the column name for_impeachment and put the == "NO" response in quotes and added another pipe. 
# Then I used the filter function again for p16winningparty to sort for == "R" response in quotes. R would correlate to a district that Trump won, and added another pipe.  
# Then I used the filter function again for p12winningparty  to sort for == "R" response in quotes. R would correlate to a district that Romney won (added another pipe.)
# Then I used select to view the columns that were being filtered, and separated column names by commas.
# I also added the column last_name to view members associated with the data. 

impeach %>% 
  filter(for_impeachment == "NO") %>%
  filter (p16winningparty == "R") %>%
  filter (p12winningparty == "R") %>%
  select(for_impeachment,last_name,p16winningparty,p12winningparty)



# 4) Filter for only results from September 2019 where a member is a YES for impeachment. 

# Use Impeach dataframe with the pipe bring up the data set, 
# I used filter function to locate the column name for_impeachment and put the == "YES" response in quotes and added another pipe. 
# Then I used the filter function again for date_month to sort for == "9" response in quotes for September (added another pipe).
# Then I used the filter function again for date_year to sort for == "2019" response in quotes. (added another pipe.)
# Then I used select to view the columns that were being filtered, and separated column names by commas.
# I also added the column last_name to view members associated with the data. 

impeach %>% 
  filter(for_impeachment == "YES") %>%
  filter(date_month == "9") %>%
  filter (date_year == "2019") %>%
  select(for_impeachment,last_name,date_month,date_year)



# 4) Filter for only results where a member is a YES for impeachment and is from a district
# where Clinton won more than 70 percent of the vote in 2016 (found in column "clinton_percent")

# Used Impeach dataframe with the pipe bring up the data set, 
# I used filter function to locate the column name for_impeachment and put the == "YES" response in quotes and added a pipe. 
# Then I used the filter function for clinton_percent with the greater than or equal to sign >== of 70 (no need for quotes since its a number)(added another pipe).
# Then I used select to view the columns that were being filtered, and separated column names by commas.
# I also added the column last_name to view members associated with the data. 

impeach %>% 
  filter(for_impeachment == "YES") %>%
  filter(clinton_percent >= 70)%>%
  select(for_impeachment,last_name,clinton_percent)
  

# 5) Sort the entire dataframe based on the percentage of a district that has a 
# bachelor's degree or higher ("pct_bachelors"), from lowest to highest

# Used Impeach dataframe with the pipe bring up the data set, 
# Then I used the arrange function for pct_bachelors which automatically sorts the pct from lowest to highest. (added pipe). 
# Then I used select to view the columns that were being filtered/arranged, and separated column names by commas.
# I also added the column district. 

impeach %>% 
  arrange(pct_bachelors)%>%
  select(pct_bachelors,state,district)
  

# 6) Sort the just those who are NO on impeachment based on the percentage of a district that has a 
# bachelor's degree or higher ("pct_bachelors"), from lowest to highest

# Used Impeach dataframe with the pipe bring up the data set. 
# I used filter function to locate the column name for_impeachment and put the == "NO" response in quotes and added a pipe. 
# Then I used the arrange function for pct_bachelors which automatically sorts the pct from lowest to highest. (added pipe). 
# Then I used select to view the columns that were being filtered/arranged, and separated column names by commas.
# I also added the column last_name to view members associated with the data. 

impeach %>% 
  filter(for_impeachment == "NO")%>%
  arrange(pct_bachelors) %>%
  select(for_impeachment,last_name,pct_bachelors)



# 7) Sort the just those who are NO on impeachment based on the percentage of a district that has a 
# bachelor's degree or higher ("pct_bachelors"), from lowest to highest.
# Then filter those records by only those whose bachelor's percentage is below the national average (found
# in the "pct_bachelors_compared_to_national" column).

# Used Impeach dataframe with the pipe bring up the data set. 
# I used filter function to locate the column name for_impeachment and put the == "NO" response in quotes and added a pipe.
# Then I used filter function to locate the column name pct_bachelors_compared_to_national and put the == "BELOW" response in quotes and added a pipe. 
# Then I used the arrange function for pct_bachelors which automatically sorts the pct from lowest to highest. (added pipe). 
# Then I used select to view the columns that were being filtered/arranged, and separated column names by commas.
# I also added the column last_name to view members associated with the data. 

impeach %>% 
  filter(for_impeachment == "NO")%>%
  filter(pct_bachelors_compared_to_national =="BELOW")%>%
  arrange(pct_bachelors) %>%
  select(for_impeachment,last_name,pct_bachelors,pct_bachelors_compared_to_national)


# 8) Filter for only members from New Jersey who are NO on impeachment

# Used Impeach dataframe with the pipe bring up the data set. 
# I used filter function to locate the column name for_impeachment and put the == "NO" response in quotes and added a pipe.
# Then I used filter function to locate the column name state and put the == "NJ" response in quotes and added a pipe. 
# Then I used select to view the columns that were being filtered and separated column names by commas.
# I also added the column last_name to view members associated with the data. 

impeach %>%
  filter(for_impeachment == "NO")%>%
  filter(state == "NJ") %>%
  select(for_impeachment,last_name,state) 


# 9) Filter for those who were YES on impeachment, with a declared date prior to 2019. So only
# those with dates before 2019.  Then sort those so that the highest Clinton vote percentages are 
# at the top. 

# Used Impeach dataframe with the pipe bring up the data set. 
# I used filter function to locate the column name for_impeachment and put the == "YES" response in quotes and added a pipe.
# Then I used filter function to locate the column name date_year and put the less than sign (<) 2019 (no quotes) and added a pipe. 
# Then I used arrange(desc) to view clinton_percent from highest to lowest. (added pipe)
# Then I used select to view the columns that were being filtered and separated column names by commas.
# I also added the column last_name to view members associated with the data. 
 


impeach %>%
  filter(for_impeachment == "YES")%>%
  filter(date_year < 2019)%>%
  arrange(desc(clinton_percent))%>%
  select(for_impeachment,last_name,clinton_percent,date_year)
  


# 10) Answer this question with a single numeric answer, and show the R code you
# used to reach that answer: How many members in the dataset who are holdouts on impeachment
# comes from districts with a GDP below the national figure?

# Used Impeach dataframe with the pipe bring up the data set. 
# I used filter function to locate the column name for_impeachment and put the == "NO" response in quotes and added a pipe.
# Then I used filter function to locate the column name gdo_above_national and put == "BELOW" response in quotes and added a pipe. 
# Then I used select to view the columns that were being filtered and separated column names by commas.
# I also added the column last_name to view members associated with the data. 
#There were 19 returns so the answer is 19 members. 


impeach %>%
  filter(for_impeachment == "NO")%>%
  filter(gdp_above_national == "BELOW")%>%
  select(for_impeachment,last_name, gdp_above_national)

#Answer: 19



