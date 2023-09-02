### FIGHT HISTORY - PRO [Summary Data Schema][1]
Result  
Fighter  
Event  
Method/Referee  
R  
Time  

address  
addressLocality  
adr  
age  
association  
big_flag  
bio  
birth_info  
birthDate  
birthday  
birthplace  
Country  
dob  
height  
http  
locality  
name  
nationality  
size_info  
title  
wclass  
weight  
weightclass  

### Athlete Data Schema
[Athlete Data Schema][4]

field       = Header  
id          = ID  
name        = Name  
birth_date  = Date of Birth  
weight_kg   = Weight (KG)  
height_cm   = Height (CM)  
locality    = Locality  
nationality = Nationality  
camp_team   = Association  
wins        = Wins  
losses      = Losses  
draws       = Draws  
last_fight  = Last Fight  

wld {[ "wins","losses","draws" ]}

### Bout (Match) Data Schema
[Bout (Match) Data Schema][5]

winner    = Winner  
loser     = Loser  
method    = Method  
method_by = Method_by  
referee   = Referee  
round_num = Round_num  
time      = Time  
event     = Event  
date      = Date  
location  = Location  

### Event Data Schema
[Event Data Schema][6]

b_id = \d{4,5}  
b_fighter_url = '/fighter/`b_fname`-`b_lname`-`b_id`  

r_id = \d{4,5}  
r_fighter_url = '/fighter/`r_fname`-`r_lname`-`b_id`  

organization = [{"UFC","StrikeForce"}]  
org_id = \d{}  

event_id = \d{5}  
event_num = 146  
event_link = `org`-`event_num`-`b_lname`-vs-`r_lname`-`event_id`  
event_label = `org` `event_num`: `b_lname` v. `r_lname`  

#### [Athlete Data Schema][6]
name  
birthday  
height  
city  
country  
country_flag_url  
wins  
losses  
image_url  

#### [Event Data Schema][6]
name  
organization  
date  
venue  
location  
fights  

#### [Main Event Result Data Schema][6]
fighters  
winner  
match  
method  
referee  
round  
time  

#### [Event Result Data Schema][6]
fighters  
winner  
match  
method  
round  
time  
referee  


[1]: https://www.sherdog.com/fighter/Roxanne-Modafferi-8785 "Roxanne The Happy Warrior' Modafferi MMA Stats, Pictures, News, Videos, Biography - Sherdog.com"
[2]: https://www.sherdog.com/pictures/json/8785/f/0/1/
[3]: https://www.sherdog.com/radio/ajax-beatdown
[4]: https://github.com/paddycarey/sherdog-fighter-scraper
[5]: https://github.com/ethandjay/sherdog-scraper
[6]: https://github.com/jc0n/sherdog-scraper