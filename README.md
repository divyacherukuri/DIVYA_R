# DIVYA_R
#nycflights13::flights
#nycflights13::planes
#nycflights13::airlines
flight_data <- nycflights13::flights %>%
 rename(flight_year = year) %>%
 left_join(planes, by = "tailnum") %>%
 rename(manf_year = year) %>%
 left_join(airlines, by = "carrier")
flight_data

flight_data %>%
 filter(origin== "JFK") %>%
 group_by(name)%>%
 summarise(avg_distance = mean(distance))
 
 flight_data %>%
 filter((name=="Southwest Airlines Co." | name=="JetBlue Airways") & engine !="NA" )%>%
 group_by(name,engine) %>%
 summarize(CountEngineType=n()) %>%
arrange(name,desc(CountEngineType))
`summarise()` regrouping output by 'name' (override with `.groups` argument)
