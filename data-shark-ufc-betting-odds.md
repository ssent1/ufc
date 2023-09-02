## Regular Expressions
### Convert blanks to zeros
`(")(")`
`${1}0${2}`

### Capture Data
`"away_name":"(?<b_name>[a-z ]+)?","home_name":"(?<r_name>[a-z ]+)?","away_odds":"(?<b_odds>[0-9\-]+)?","home_odds":"(?<r_odds>[0-9\-]+)?"`
`$+{b_name}\t\t\t\t\t\t\t\t\t\t\t\t\t\t\t\t\t\t\t\t\t$+{b_odds}\t$+{r_name}\t\t\t\t\t\t\t\t\t\t\t\t\t\t\t\t\t\t\t\t\t$+{r_odds}`

### Substitution/Output (modified⁎ for readability)
```
D Poirier   \t×{21} =   -240    D Hooker    \t×{21} 190
M Gall      \t×{21} =   250     M Perry     \t×{21} -300
B Allen     \t×{21} =   -300    K Daukaus   \t×{21} 240
M Greene    \t×{21} =   -250    G Villante  \t×{21} 200
L Pena      \t×{21} =   -250    K Worthy    \t×{21} 200
J Erosa     \t×{21} =   375     S Woodson   \t×{21} -550
T Boser     \t×{21} =   -105    P Lins      \t×{21} -125
T Sato      \t×{21} =   0       J Witt      \t×{21} 0
JY Frey     \t×{21} =   180     K Hansen    \t×{21} -220
J Griffin   \t×{21} =   100     Y Zalal     \t×{21} -130
```

#### Legend
away = blue
home = red

-------------------------------------------------

## Step 1 - Get Odds
- Go to [Odds Shark][1] to get odds

## Step 2 - Decode Unicode
- Go to [Odds Shark][1] source code and get JSON data (in Unicode)
- [Ddecode Unicode][2] `function init_drupal_core_settings()`
```
Encoded Unicode Escape ⟶ {\u0022leagues\u0022:{\u0022ufc\u0022:true,\u0022nhl\u0022:false,\u0022mlb\u0022:false,\u0022nba\u0022:false,\u0022nfl\u0022:false,\u0022ncaaf\u0022:false,\u0022ncaab\u0022:false,\u0022soccer\u0022:{\u0022epl\u0022:true,\u0022bundesliga\u0022:false,\u0022la_liga\u0022:true,\u0022serie_a\u0022:true,\u0022england_champ\u0022:true,\u0022brazil\u0022:false,\u0022france_ligue_1\u0022:false,\u0022champ_league\u0022:false,\u0022world_cup\u0022:false,\u0022mexico\u0022:false,\u0022mls\u0022:false,\u0022euro\u0022:false}},\u0022matchups\u0022:[{\u0022type\u0022:\u0022event\u0022,\u0022event\u0022:\u0022FN Saturday Jun 27th\u0022,\u0022current\u0022:false},{\u0022type\u0022:\u0022matchup\u0022,\u0022event_id\u0022:\u00221260480\u0022,\u0022event_date\u0022:\u00222020-06-27 20:00\u0022,\u0022away_name\u0022:\u0022D Poirier\u0022,\u0022home_name\u0022:\u0022D Hooker\u0022,\u0022away_odds\u0022:\u0022-240\u0022,\u0022home_odds\u0022:\u0022190\u0022,\u0022away_votes\u0022:43,\u0022home_votes\u0022:57,\u0022over_votes\u0022:62,\u0022under_votes\u0022:38,\u0022status\u0022:\u0022DEC\u0022,\u0022matchup_link\u0022:\u0022\\\/ufc\\\/dustin-poirier-dan-hooker-odds-june-27-2020-1260480\u0022,\u0022winner\u0022:\u0022D Poirier\u0022,\u0022tv_station\u0022:\u0022\u0022},{\u0022type\u0022:\u0022matchup\u0022,\u0022event_id\u0022:\u00221260490\u0022,\u0022event_date\u0022:\u00222020-06-27 20:00\u0022,\u0022away_name\u0022:\u0022M Gall\u0022,\u0022home_name\u0022:\u0022M Perry\u0022,\u0022away_odds\u0022:\u0022250\u0022,\u0022home_odds\u0022:\u0022-300\u0022,\u0022away_votes\u0022:45,\u0022home_votes\u0022:55,\u0022over_votes\u0022:51,\u0022under_votes\u0022:49,\u0022status\u0022:\u0022DEC\u0022,\u0022matchup_link\u0022:\u0022\\\/ufc\\\/mickey-gall-mike-perry-odds-june-27-2020-1260490\u0022,\u0022winner\u0022:\u0022M Perry\u0022,\u0022tv_station\u0022:\u0022\u0022},{\u0022type\u0022:\u0022matchup\u0022,\u0022event_id\u0022:\u00221260935\u0022,\u0022event_date\u0022:\u00222020-06-27 20:00\u0022,\u0022away_name\u0022:\u0022B Allen\u0022,\u0022home_name\u0022:\u0022K Daukaus\u0022,\u0022away_odds\u0022:\u0022-300\u0022,\u0022home_odds\u0022:\u0022240\u0022,\u0022away_votes\u0022:37,\u0022home_votes\u0022:63,\u0022over_votes\u0022:63,\u0022under_votes\u0022:37,\u0022status\u0022:\u0022DEC\u0022,\u0022matchup_link\u0022:\u0022\\\/ufc\\\/brendan-allen-kyle-daukaus-odds-june-27-2020-1260935\u0022,\u0022winner\u0022:\u0022B Allen\u0022,\u0022tv_station\u0022:\u0022\u0022},{\u0022type\u0022:\u0022matchup\u0022,\u0022event_id\u0022:\u00221260520\u0022,\u0022event_date\u0022:\u00222020-06-27 20:00\u0022,\u0022away_name\u0022:\u0022M Greene\u0022,\u0022home_name\u0022:\u0022G Villante\u0022,\u0022away_odds\u0022:\u0022-250\u0022,\u0022home_odds\u0022:\u0022200\u0022,\u0022away_votes\u0022:36,\u0022home_votes\u0022:64,\u0022over_votes\u0022:47,\u0022under_votes\u0022:53,\u0022status\u0022:\u0022submission\u0022,\u0022matchup_link\u0022:\u0022\\\/ufc\\\/maurice-greene-gian-villante-odds-june-27-2020-1260520\u0022,\u0022winner\u0022:\u0022M Greene\u0022,\u0022tv_station\u0022:\u0022\u0022},{\u0022type\u0022:\u0022matchup\u0022,\u0022event_id\u0022:\u00221260485\u0022,\u0022event_date\u0022:\u00222020-06-27 18:00\u0022,\u0022away_name\u0022:\u0022L Pena\u0022,\u0022home_name\u0022:\u0022K Worthy\u0022,\u0022away_odds\u0022:\u0022-250\u0022,\u0022home_odds\u0022:\u0022200\u0022,\u0022away_votes\u0022:43,\u0022home_votes\u0022:57,\u0022over_votes\u0022:47,\u0022under_votes\u0022:53,\u0022status\u0022:\u0022submission\u0022,\u0022matchup_link\u0022:\u0022\\\/ufc\\\/luis-pena-khama-worthy-odds-june-27-2020-1260485\u0022,\u0022winner\u0022:\u0022K Worthy\u0022,\u0022tv_station\u0022:\u0022\u0022},{\u0022type\u0022:\u0022matchup\u0022,\u0022event_id\u0022:\u00221261460\u0022,\u0022event_date\u0022:\u00222020-06-27 20:00\u0022,\u0022away_name\u0022:\u0022J Erosa\u0022,\u0022home_name\u0022:\u0022S Woodson\u0022,\u0022away_odds\u0022:\u0022375\u0022,\u0022home_odds\u0022:\u0022-550\u0022,\u0022away_votes\u0022:32,\u0022home_votes\u0022:68,\u0022over_votes\u0022:44,\u0022under_votes\u0022:56,\u0022status\u0022:\u0022submission\u0022,\u0022matchup_link\u0022:\u0022\\\/ufc\\\/julian-erosa-sean-woodson-odds-june-27-2020-1261460\u0022,\u0022winner\u0022:\u0022J Erosa\u0022,\u0022tv_station\u0022:\u0022\u0022},{\u0022type\u0022:\u0022matchup\u0022,\u0022event_id\u0022:\u00221260515\u0022,\u0022event_date\u0022:\u00222020-06-27 20:00\u0022,\u0022away_name\u0022:\u0022T Boser\u0022,\u0022home_name\u0022:\u0022P Lins\u0022,\u0022away_odds\u0022:\u0022-105\u0022,\u0022home_odds\u0022:\u0022-125\u0022,\u0022away_votes\u0022:43,\u0022home_votes\u0022:57,\u0022over_votes\u0022:55,\u0022under_votes\u0022:45,\u0022status\u0022:\u0022ko\\\/tko\u0022,\u0022matchup_link\u0022:\u0022\\\/ufc\\\/tanner-boser-philipe-lins-odds-june-27-2020-1260515\u0022,\u0022winner\u0022:\u0022T Boser\u0022,\u0022tv_station\u0022:\u0022\u0022},{\u0022type\u0022:\u0022matchup\u0022,\u0022event_id\u0022:\u00221261785\u0022,\u0022event_date\u0022:\u00222020-06-27 18:00\u0022,\u0022away_name\u0022:\u0022T Sato\u0022,\u0022home_name\u0022:\u0022J Witt\u0022,\u0022away_odds\u0022:\u0022\u0022,\u0022home_odds\u0022:\u0022\u0022,\u0022away_votes\u0022:0,\u0022home_votes\u0022:0,\u0022over_votes\u0022:0,\u0022under_votes\u0022:0,\u0022status\u0022:\u0022ko\\\/tko\u0022,\u0022matchup_link\u0022:\u0022\\\/ufc\\\/takashi-sato-jason-witt-odds-june-27-2020-1261785\u0022,\u0022winner\u0022:\u0022T Sato\u0022,\u0022tv_station\u0022:\u0022\u0022},{\u0022type\u0022:\u0022matchup\u0022,\u0022event_id\u0022:\u00221261130\u0022,\u0022event_date\u0022:\u00222020-06-27 18:00\u0022,\u0022away_name\u0022:\u0022JY Frey\u0022,\u0022home_name\u0022:\u0022K Hansen\u0022,\u0022away_odds\u0022:\u0022180\u0022,\u0022home_odds\u0022:\u0022-220\u0022,\u0022away_votes\u0022:0,\u0022home_votes\u0022:0,\u0022over_votes\u0022:0,\u0022under_votes\u0022:0,\u0022status\u0022:\u0022submission\u0022,\u0022matchup_link\u0022:\u0022\\\/ufc\\\/jinh-yu-frey-kay-hansen-odds-june-27-2020-1261130\u0022,\u0022winner\u0022:\u0022K Hansen\u0022,\u0022tv_station\u0022:\u0022\u0022},{\u0022type\u0022:\u0022matchup\u0022,\u0022event_id\u0022:\u00221260950\u0022,\u0022event_date\u0022:\u00222020-06-27 18:00\u0022,\u0022away_name\u0022:\u0022J Griffin\u0022,\u0022home_name\u0022:\u0022Y Zalal\u0022,\u0022away_odds\u0022:\u0022100\u0022,\u0022home_odds\u0022:\u0022-130\u0022,\u0022away_votes\u0022:51,\u0022home_votes\u0022:49,\u0022over_votes\u0022:55,\u0022under_votes\u0022:45,\u0022status\u0022:\u0022DEC\u0022,\u0022matchup_link\u0022:\u0022\\\/ufc\\\/jordan-griffin-youssef-zalal-odds-june-27-2020-1260950\u0022,\u0022winner\u0022:\u0022Y Zalal\u0022,\u0022tv_station\u0022:\u0022\u0022},{\u0022type\u0022:\u0022event\u0022,\u0022event\u0022:\u0022UFC 251 Saturday Jul 11th\u0022,\u0022current\u0022:true},{\u0022type\u0022:\u0022matchup\u0022,\u0022event_id\u0022:\u00221259920\u0022,\u0022event_date\u0022:\u00222020-07-11 22:00\u0022,\u0022away_name\u0022:\u0022K Usman\u0022,\u0022home_name\u0022:\u0022G Burns\u0022,\u0022away_odds\u0022:\u0022-240\u0022,\u0022home_odds\u0022:\u0022200\u0022,\u0022away_votes\u0022:51,\u0022home_votes\u0022:49,\u0022over_votes\u0022:54,\u0022under_votes\u0022:46,\u0022status\u0022:\u0022\u0022,\u0022matchup_link\u0022:\u0022\\\/ufc\\\/kamaru-usman-gilbert-burns-odds-july-11-2020-1259920\u0022,\u0022winner\u0022:\u0022\u0022,\u0022tv_station\u0022:\u0022\u0022},{\u0022type\u0022:\u0022matchup\u0022,\u0022event_id\u0022:\u00221259925\u0022,\u0022event_date\u0022:\u00222020-07-11 22:00\u0022,\u0022away_name\u0022:\u0022M Holloway\u0022,\u0022home_name\u0022:\u0022A Volkanovski\u0022,\u0022away_odds\u0022:\u0022170\u0022,\u0022home_odds\u0022:\u0022-200\u0022,\u0022away_votes\u0022:51,\u0022home_votes\u0022:49,\u0022over_votes\u0022:43,\u0022under_votes\u0022:57,\u0022status\u0022:\u0022\u0022,\u0022matchup_link\u0022:\u0022\\\/ufc\\\/max-holloway-alexander-volkanovski-odds-july-11-2020-1259925\u0022,\u0022winner\u0022:\u0022\u0022,\u0022tv_station\u0022:\u0022\u0022},{\u0022type\u0022:\u0022matchup\u0022,\u0022event_id\u0022:\u00221259935\u0022,\u0022event_date\u0022:\u00222020-07-11 22:00\u0022,\u0022away_name\u0022:\u0022J Aldo\u0022,\u0022home_name\u0022:\u0022P Yan\u0022,\u0022away_odds\u0022:\u0022200\u0022,\u0022home_odds\u0022:\u0022-250\u0022,\u0022away_votes\u0022:36,\u0022home_votes\u0022:64,\u0022over_votes\u0022:56,\u0022under_votes\u0022:44,\u0022status\u0022:\u0022\u0022,\u0022matchup_link\u0022:\u0022\\\/ufc\\\/jose-aldo-petr-yan-odds-july-11-2020-1259935\u0022,\u0022winner\u0022:\u0022\u0022,\u0022tv_station\u0022:\u0022\u0022},{\u0022type\u0022:\u0022matchup\u0022,\u0022event_id\u0022:\u00221259915\u0022,\u0022event_date\u0022:\u00222020-07-11 22:00\u0022,\u0022away_name\u0022:\u0022J Andrade\u0022,\u0022home_name\u0022:\u0022R Namajunas\u0022,\u0022away_odds\u0022:\u0022155\u0022,\u0022home_odds\u0022:\u0022-190\u0022,\u0022away_votes\u0022:41,\u0022home_votes\u0022:59,\u0022over_votes\u0022:54,\u0022under_votes\u0022:46,\u0022status\u0022:\u0022\u0022,\u0022matchup_link\u0022:\u0022\\\/ufc\\\/jessica-andrade-rose-namajunas-odds-july-11-2020-1259915\u0022,\u0022winner\u0022:\u0022\u0022,\u0022tv_station\u0022:\u0022\u0022},{\u0022type\u0022:\u0022matchup\u0022,\u0022event_id\u0022:\u00221259930\u0022,\u0022event_date\u0022:\u00222020-07-11 22:00\u0022,\u0022away_name\u0022:\u0022P VanZant\u0022,\u0022home_name\u0022:\u0022A Ribas\u0022,\u0022away_odds\u0022:\u0022550\u0022,\u0022home_odds\u0022:\u0022-800\u0022,\u0022away_votes\u0022:33,\u0022home_votes\u0022:67,\u0022over_votes\u0022:54,\u0022under_votes\u0022:46,\u0022status\u0022:\u0022\u0022,\u0022matchup_link\u0022:\u0022\\\/ufc\\\/paige-vanzant-amanda-ribas-odds-july-11-2020-1259930\u0022,\u0022winner\u0022:\u0022\u0022,\u0022tv_station\u0022:\u0022\u0022},{\u0022type\u0022:\u0022matchup\u0022,\u0022event_id\u0022:\u00221260915\u0022,\u0022event_date\u0022:\u00222020-07-11 18:00\u0022,\u0022away_name\u0022:\u0022V Oezdemir\u0022,\u0022home_name\u0022:\u0022J Prochazka\u0022,\u0022away_odds\u0022:\u0022-150\u0022,\u0022home_odds\u0022:\u0022130\u0022,\u0022away_votes\u0022:50,\u0022home_votes\u0022:50,\u0022over_votes\u0022:94,\u0022under_votes\u0022:6,\u0022status\u0022:\u0022\u0022,\u0022matchup_link\u0022:\u0022\\\/ufc\\\/volkan-oezdemir-jiri-prochazka-odds-july-11-2020-1260915\u0022,\u0022winner\u0022:\u0022\u0022,\u0022tv_station\u0022:\u0022\u0022},{\u0022type\u0022:\u0022matchup\u0022,\u0022event_id\u0022:\u00221260895\u0022,\u0022event_date\u0022:\u00222020-07-11 18:00\u0022,\u0022away_name\u0022:\u0022E Zaleski dos Santos\u0022,\u0022home_name\u0022:\u0022M Salikhov\u0022,\u0022away_odds\u0022:\u0022-110\u0022,\u0022home_odds\u0022:\u0022-120\u0022,\u0022away_votes\u0022:42,\u0022home_votes\u0022:58,\u0022over_votes\u0022:26,\u0022under_votes\u0022:74,\u0022status\u0022:\u0022\u0022,\u0022matchup_link\u0022:\u0022\\\/ufc\\\/elizeu-zaleski-dos-santos-muslim-salikhov-odds-july-11-2020-1260895\u0022,\u0022winner\u0022:\u0022\u0022,\u0022tv_station\u0022:\u0022\u0022},{\u0022type\u0022:\u0022matchup\u0022,\u0022event_id\u0022:\u00221260920\u0022,\u0022event_date\u0022:\u00222020-07-11 18:00\u0022,\u0022away_name\u0022:\u0022M Amirkhani\u0022,\u0022home_name\u0022:\u0022D Henry\u0022,\u0022away_odds\u0022:\u0022-200\u0022,\u0022home_odds\u0022:\u0022160\u0022,\u0022away_votes\u0022:49,\u0022home_votes\u0022:51,\u0022over_votes\u0022:27,\u0022under_votes\u0022:73,\u0022status\u0022:\u0022\u0022,\u0022matchup_link\u0022:\u0022\\\/ufc\\\/makwan-amirkhani-danny-henry-odds-july-11-2020-1260920\u0022,\u0022winner\u0022:\u0022\u0022,\u0022tv_station\u0022:\u0022\u0022},{\u0022type\u0022:\u0022matchup\u0022,\u0022event_id\u0022:\u00221260900\u0022,\u0022event_date\u0022:\u00222020-07-11 18:00\u0022,\u0022away_name\u0022:\u0022R Bogatov\u0022,\u0022home_name\u0022:\u0022L Santos\u0022,\u0022away_odds\u0022:\u0022150\u0022,\u0022home_odds\u0022:\u0022-190\u0022,\u0022away_votes\u0022:47,\u0022home_votes\u0022:53,\u0022over_votes\u0022:2,\u0022under_votes\u0022:98,\u0022status\u0022:\u0022\u0022,\u0022matchup_link\u0022:\u0022\\\/ufc\\\/roman-bogatov-leonardo-santos-odds-july-11-2020-1260900\u0022,\u0022winner\u0022:\u0022\u0022,\u0022tv_station\u0022:\u0022\u0022},{\u0022type\u0022:\u0022matchup\u0022,\u0022event_id\u0022:\u00221260925\u0022,\u0022event_date\u0022:\u00222020-07-11 18:00\u0022,\u0022away_name\u0022:\u0022M Tybura\u0022,\u0022home_name\u0022:\u0022A Romanov\u0022,\u0022away_odds\u0022:\u0022-105\u0022,\u0022home_odds\u0022:\u0022-115\u0022,\u0022away_votes\u0022:35,\u0022home_votes\u0022:65,\u0022over_votes\u0022:0,\u0022under_votes\u0022:100,\u0022status\u0022:\u0022\u0022,\u0022matchup_link\u0022:\u0022\\\/ufc\\\/marcin-tybura-alexander-romanov-odds-july-11-2020-1260925\u0022,\u0022winner\u0022:\u0022\u0022,\u0022tv_station\u0022:\u0022\u0022},{\u0022type\u0022:\u0022matchup\u0022,\u0022event_id\u0022:\u00221260930\u0022,\u0022event_date\u0022:\u00222020-07-11 18:00\u0022,\u0022away_name\u0022:\u0022R Paiva\u0022,\u0022home_name\u0022:\u0022Z Zhamagulov\u0022,\u0022away_odds\u0022:\u0022-190\u0022,\u0022home_odds\u0022:\u0022155\u0022,\u0022away_votes\u0022:56,\u0022home_votes\u0022:44,\u0022over_votes\u0022:50,\u0022under_votes\u0022:50,\u0022status\u0022:\u0022\u0022,\u0022matchup_link\u0022:\u0022\\\/ufc\\\/raulian-paiva-zhalgas-zhamagulov-odds-july-11-2020-1260930\u0022,\u0022winner\u0022:\u0022\u0022,\u0022tv_station\u0022:\u0022\u0022},{\u0022type\u0022:\u0022matchup\u0022,\u0022event_id\u0022:\u00221260910\u0022,\u0022event_date\u0022:\u00222020-07-11 18:00\u0022,\u0022away_name\u0022:\u0022V Melo\u0022,\u0022home_name\u0022:\u0022K Rosa\u0022,\u0022away_odds\u0022:\u0022170\u0022,\u0022home_odds\u0022:\u0022-215\u0022,\u0022away_votes\u0022:36,\u0022home_votes\u0022:64,\u0022over_votes\u0022:54,\u0022under_votes\u0022:46,\u0022status\u0022:\u0022\u0022,\u0022matchup_link\u0022:\u0022\\\/ufc\\\/vanessa-melo-karol-rosa-odds-july-11-2020-1260910\u0022,\u0022winner\u0022:\u0022\u0022,\u0022tv_station\u0022:\u0022\u0022},{\u0022type\u0022:\u0022matchup\u0022,\u0022event_id\u0022:\u00221260905\u0022,\u0022event_date\u0022:\u00222020-07-11 18:00\u0022,\u0022away_name\u0022:\u0022M Day\u0022,\u0022home_name\u0022:\u0022D Grant\u0022,\u0022away_odds\u0022:\u0022-175\u0022,\u0022home_odds\u0022:\u0022145\u0022,\u0022away_votes\u0022:63,\u0022home_votes\u0022:37,\u0022over_votes\u0022:46,\u0022under_votes\u0022:54,\u0022status\u0022:\u0022\u0022,\u0022matchup_link\u0022:\u0022\\\/ufc\\\/martin-day-davey-grant-odds-july-11-2020-1260905\u0022,\u0022winner\u0022:\u0022\u0022,\u0022tv_station\u0022:\u0022\u0022},{\u0022type\u0022:\u0022event\u0022,\u0022event\u0022:\u0022FN Wednesday Jul 15th\u0022,\u0022current\u0022:false},{\u0022type\u0022:\u0022matchup\u0022,\u0022event_id\u0022:\u00221261085\u0022,\u0022event_date\u0022:\u00222020-07-15 22:00\u0022,\u0022away_name\u0022:\u0022C Kattar\u0022,\u0022home_name\u0022:\u0022D Ige\u0022,\u0022away_odds\u0022:\u0022-280\u0022,\u0022home_odds\u0022:\u0022230\u0022,\u0022away_votes\u0022:41,\u0022home_votes\u0022:59,\u0022over_votes\u0022:0,\u0022under_votes\u0022:0,\u0022status\u0022:\u0022\u0022,\u0022matchup_link\u0022:\u0022\\\/ufc\\\/calvin-kattar-dan-ige-odds-july-15-2020-1261085\u0022,\u0022winner\u0022:\u0022\u0022,\u0022tv_station\u0022:\u0022\u0022},{\u0022type\u0022:\u0022matchup\u0022,\u0022event_id\u0022:\u00221261080\u0022,\u0022event_date\u0022:\u00222020-07-15 22:00\u0022,\u0022away_name\u0022:\u0022F Edgar\u0022,\u0022home_name\u0022:\u0022P Munhoz\u0022,\u0022away_odds\u0022:\u0022180\u0022,\u0022home_odds\u0022:\u0022-230\u0022,\u0022away_votes\u0022:41,\u0022home_votes\u0022:59,\u0022over_votes\u0022:0,\u0022under_votes\u0022:0,\u0022status\u0022:\u0022\u0022,\u0022matchup_link\u0022:\u0022\\\/ufc\\\/frankie-edgar-pedro-munhoz-odds-july-15-2020-1261080\u0022,\u0022winner\u0022:\u0022\u0022,\u0022tv_station\u0022:\u0022\u0022},{\u0022type\u0022:\u0022matchup\u0022,\u0022event_id\u0022:\u00221261090\u0022,\u0022event_date\u0022:\u00222020-07-15 22:00\u0022,\u0022away_name\u0022:\u0022C Esparza\u0022,\u0022home_name\u0022:\u0022M Rodriguez\u0022,\u0022away_odds\u0022:\u0022130\u0022,\u0022home_odds\u0022:\u0022-150\u0022,\u0022away_votes\u0022:46,\u0022home_votes\u0022:54,\u0022over_votes\u0022:0,\u0022under_votes\u0022:0,\u0022status\u0022:\u0022\u0022,\u0022matchup_link\u0022:\u0022\\\/ufc\\\/carla-esparza-marina-rodriguez-odds-july-15-2020-1261090\u0022,\u0022winner\u0022:\u0022\u0022,\u0022tv_station\u0022:\u0022\u0022},{\u0022type\u0022:\u0022matchup\u0022,\u0022event_id\u0022:\u00221261120\u0022,\u0022event_date\u0022:\u00222020-07-15 22:00\u0022,\u0022away_name\u0022:\u0022M Lazzez\u0022,\u0022home_name\u0022:\u0022A Razak Alhassan\u0022,\u0022away_odds\u0022:\u0022225\u0022,\u0022home_odds\u0022:\u0022-275\u0022,\u0022away_votes\u0022:0,\u0022home_votes\u0022:0,\u0022over_votes\u0022:0,\u0022under_votes\u0022:0,\u0022status\u0022:\u0022\u0022,\u0022matchup_link\u0022:\u0022\\\/ufc\\\/mounir-lazzez-abdul-razak-alhassan-odds-july-15-2020-1261120\u0022,\u0022winner\u0022:\u0022\u0022,\u0022tv_station\u0022:\u0022\u0022},{\u0022type\u0022:\u0022matchup\u0022,\u0022event_id\u0022:\u00221261075\u0022,\u0022event_date\u0022:\u00222020-07-15 22:00\u0022,\u0022away_name\u0022:\u0022C Fishgold\u0022,\u0022home_name\u0022:\u0022J Gordon\u0022,\u0022away_odds\u0022:\u0022105\u0022,\u0022home_odds\u0022:\u0022-125\u0022,\u0022away_votes\u0022:55,\u0022home_votes\u0022:45,\u0022over_votes\u0022:0,\u0022under_votes\u0022:0,\u0022status\u0022:\u0022\u0022,\u0022matchup_link\u0022:\u0022\\\/ufc\\\/chris-fishgold-jared-gordon-odds-july-15-2020-1261075\u0022,\u0022winner\u0022:\u0022\u0022,\u0022tv_station\u0022:\u0022\u0022},{\u0022type\u0022:\u0022matchup\u0022,\u0022event_id\u0022:\u00221261070\u0022,\u0022event_date\u0022:\u00222020-07-15 19:00\u0022,\u0022away_name\u0022:\u0022M Bukauskas\u0022,\u0022home_name\u0022:\u0022V Moreira\u0022,\u0022away_odds\u0022:\u0022-280\u0022,\u0022home_odds\u0022:\u0022240\u0022,\u0022away_votes\u0022:0,\u0022home_votes\u0022:0,\u0022over_votes\u0022:0,\u0022under_votes\u0022:0,\u0022status\u0022:\u0022\u0022,\u0022matchup_link\u0022:\u0022\\\/ufc\\\/modestas-bukauskas-vinicius-moreira-odds-july-15-2020-1261070\u0022,\u0022winner\u0022:\u0022\u0022,\u0022tv_station\u0022:\u0022\u0022},{\u0022type\u0022:\u0022matchup\u0022,\u0022event_id\u0022:\u00221261110\u0022,\u0022event_date\u0022:\u00222020-07-15 19:00\u0022,\u0022away_name\u0022:\u0022M McCann\u0022,\u0022home_name\u0022:\u0022T Santos\u0022,\u0022away_odds\u0022:\u0022-115\u0022,\u0022home_odds\u0022:\u0022-115\u0022,\u0022away_votes\u0022:56,\u0022home_votes\u0022:44,\u0022over_votes\u0022:0,\u0022under_votes\u0022:0,\u0022status\u0022:\u0022\u0022,\u0022matchup_link\u0022:\u0022\\\/ufc\\\/molly-mccann-taila-santos-odds-july-15-2020-1261110\u0022,\u0022winner\u0022:\u0022\u0022,\u0022tv_station\u0022:\u0022\u0022},{\u0022type\u0022:\u0022matchup\u0022,\u0022event_id\u0022:\u00221261100\u0022,\u0022event_date\u0022:\u00222020-07-15 19:00\u0022,\u0022away_name\u0022:\u0022L Murphy\u0022,\u0022home_name\u0022:\u0022R Ramos\u0022,\u0022away_odds\u0022:\u0022145\u0022,\u0022home_odds\u0022:\u0022-175\u0022,\u0022away_votes\u0022:74,\u0022home_votes\u0022:26,\u0022over_votes\u0022:0,\u0022under_votes\u0022:0,\u0022status\u0022:\u0022\u0022,\u0022matchup_link\u0022:\u0022\\\/ufc\\\/lerone-murphy-ricardo-ramos-odds-july-15-2020-1261100\u0022,\u0022winner\u0022:\u0022\u0022,\u0022tv_station\u0022:\u0022\u0022},{\u0022type\u0022:\u0022matchup\u0022,\u0022event_id\u0022:\u00221261105\u0022,\u0022event_date\u0022:\u00222020-07-15 19:00\u0022,\u0022away_name\u0022:\u0022J Phillips\u0022,\u0022home_name\u0022:\u0022D Todorovic\u0022,\u0022away_odds\u0022:\u0022\u0022,\u0022home_odds\u0022:\u0022\u0022,\u0022away_votes\u0022:20,\u0022home_votes\u0022:80,\u0022over_votes\u0022:0,\u0022under_votes\u0022:0,\u0022status\u0022:\u0022\u0022,\u0022matchup_link\u0022:\u0022\\\/ufc\\\/john-phillips-dusko-todorovic-odds-july-15-2020-1261105\u0022,\u0022winner\u0022:\u0022\u0022,\u0022tv_station\u0022:\u0022\u0022},{\u0022type\u0022:\u0022matchup\u0022,\u0022event_id\u0022:\u00221261095\u0022,\u0022event_date\u0022:\u00222020-07-15 19:00\u0022,\u0022away_name\u0022:\u0022T Elliott\u0022,\u0022home_name\u0022:\u0022R Benoit\u0022,\u0022away_odds\u0022:\u0022-130\u0022,\u0022home_odds\u0022:\u0022100\u0022,\u0022away_votes\u0022:59,\u0022home_votes\u0022:41,\u0022over_votes\u0022:0,\u0022under_votes\u0022:0,\u0022status\u0022:\u0022\u0022,\u0022matchup_link\u0022:\u0022\\\/ufc\\\/tim-elliott-ryan-benoit-odds-july-15-2020-1261095\u0022,\u0022winner\u0022:\u0022\u0022,\u0022tv_station\u0022:\u0022\u0022},{\u0022type\u0022:\u0022matchup\u0022,\u0022event_id\u0022:\u00221261115\u0022,\u0022event_date\u0022:\u00222020-07-15 19:00\u0022,\u0022away_name\u0022:\u0022D Belbita\u0022,\u0022home_name\u0022:\u0022L Jojua\u0022,\u0022away_odds\u0022:\u0022-160\u0022,\u0022home_odds\u0022:\u0022130\u0022,\u0022away_votes\u0022:0,\u0022home_votes\u0022:0,\u0022over_votes\u0022:0,\u0022under_votes\u0022:0,\u0022status\u0022:\u0022\u0022,\u0022matchup_link\u0022:\u0022\\\/ufc\\\/diana-belbita-liana-jojua-odds-july-15-2020-1261115\u0022,\u0022winner\u0022:\u0022\u0022,\u0022tv_station\u0022:\u0022\u0022}]}
Decoded Unicode Escape ⟶ {"leagues":{"ufc":true,"nhl":false,"mlb":false,"nba":false,"nfl":false,"ncaaf":false,"ncaab":false,"soccer":{"epl":true,"bundesliga":false,"la_liga":true,"serie_a":true,"england_champ":true,"brazil":false,"france_ligue_1":false,"champ_league":false,"world_cup":false,"mexico":false,"mls":false,"euro":false}},"matchups":[{"type":"event","event":"FN Saturday Jun 27th","current":false},{"type":"matchup","event_id":"1260480","event_date":"2020-06-27 20:00","away_name":"D Poirier","home_name":"D Hooker","away_odds":"-240","home_odds":"190","away_votes":43,"home_votes":57,"over_votes":62,"under_votes":38,"status":"DEC","matchup_link":"\/ufc\/dustin-poirier-dan-hooker-odds-june-27-2020-1260480","winner":"D Poirier","tv_station":""},{"type":"matchup","event_id":"1260490","event_date":"2020-06-27 20:00","away_name":"M Gall","home_name":"M Perry","away_odds":"250","home_odds":"-300","away_votes":45,"home_votes":55,"over_votes":51,"under_votes":49,"status":"DEC","matchup_link":"\/ufc\/mickey-gall-mike-perry-odds-june-27-2020-1260490","winner":"M Perry","tv_station":""},{"type":"matchup","event_id":"1260935","event_date":"2020-06-27 20:00","away_name":"B Allen","home_name":"K Daukaus","away_odds":"-300","home_odds":"240","away_votes":37,"home_votes":63,"over_votes":63,"under_votes":37,"status":"DEC","matchup_link":"\/ufc\/brendan-allen-kyle-daukaus-odds-june-27-2020-1260935","winner":"B Allen","tv_station":""},{"type":"matchup","event_id":"1260520","event_date":"2020-06-27 20:00","away_name":"M Greene","home_name":"G Villante","away_odds":"-250","home_odds":"200","away_votes":36,"home_votes":64,"over_votes":47,"under_votes":53,"status":"submission","matchup_link":"\/ufc\/maurice-greene-gian-villante-odds-june-27-2020-1260520","winner":"M Greene","tv_station":""},{"type":"matchup","event_id":"1260485","event_date":"2020-06-27 18:00","away_name":"L Pena","home_name":"K Worthy","away_odds":"-250","home_odds":"200","away_votes":43,"home_votes":57,"over_votes":47,"under_votes":53,"status":"submission","matchup_link":"\/ufc\/luis-pena-khama-worthy-odds-june-27-2020-1260485","winner":"K Worthy","tv_station":""},{"type":"matchup","event_id":"1261460","event_date":"2020-06-27 20:00","away_name":"J Erosa","home_name":"S Woodson","away_odds":"375","home_odds":"-550","away_votes":32,"home_votes":68,"over_votes":44,"under_votes":56,"status":"submission","matchup_link":"\/ufc\/julian-erosa-sean-woodson-odds-june-27-2020-1261460","winner":"J Erosa","tv_station":""},{"type":"matchup","event_id":"1260515","event_date":"2020-06-27 20:00","away_name":"T Boser","home_name":"P Lins","away_odds":"-105","home_odds":"-125","away_votes":43,"home_votes":57,"over_votes":55,"under_votes":45,"status":"ko\/tko","matchup_link":"\/ufc\/tanner-boser-philipe-lins-odds-june-27-2020-1260515","winner":"T Boser","tv_station":""},{"type":"matchup","event_id":"1261785","event_date":"2020-06-27 18:00","away_name":"T Sato","home_name":"J Witt","away_odds":"","home_odds":"","away_votes":0,"home_votes":0,"over_votes":0,"under_votes":0,"status":"ko\/tko","matchup_link":"\/ufc\/takashi-sato-jason-witt-odds-june-27-2020-1261785","winner":"T Sato","tv_station":""},{"type":"matchup","event_id":"1261130","event_date":"2020-06-27 18:00","away_name":"JY Frey","home_name":"K Hansen","away_odds":"180","home_odds":"-220","away_votes":0,"home_votes":0,"over_votes":0,"under_votes":0,"status":"submission","matchup_link":"\/ufc\/jinh-yu-frey-kay-hansen-odds-june-27-2020-1261130","winner":"K Hansen","tv_station":""},{"type":"matchup","event_id":"1260950","event_date":"2020-06-27 18:00","away_name":"J Griffin","home_name":"Y Zalal","away_odds":"100","home_odds":"-130","away_votes":51,"home_votes":49,"over_votes":55,"under_votes":45,"status":"DEC","matchup_link":"\/ufc\/jordan-griffin-youssef-zalal-odds-june-27-2020-1260950","winner":"Y Zalal","tv_station":""},{"type":"event","event":"UFC 251 Saturday Jul 11th","current":true},{"type":"matchup","event_id":"1259920","event_date":"2020-07-11 22:00","away_name":"K Usman","home_name":"G Burns","away_odds":"-240","home_odds":"200","away_votes":51,"home_votes":49,"over_votes":54,"under_votes":46,"status":"","matchup_link":"\/ufc\/kamaru-usman-gilbert-burns-odds-july-11-2020-1259920","winner":"","tv_station":""},{"type":"matchup","event_id":"1259925","event_date":"2020-07-11 22:00","away_name":"M Holloway","home_name":"A Volkanovski","away_odds":"170","home_odds":"-200","away_votes":51,"home_votes":49,"over_votes":43,"under_votes":57,"status":"","matchup_link":"\/ufc\/max-holloway-alexander-volkanovski-odds-july-11-2020-1259925","winner":"","tv_station":""},{"type":"matchup","event_id":"1259935","event_date":"2020-07-11 22:00","away_name":"J Aldo","home_name":"P Yan","away_odds":"200","home_odds":"-250","away_votes":36,"home_votes":64,"over_votes":56,"under_votes":44,"status":"","matchup_link":"\/ufc\/jose-aldo-petr-yan-odds-july-11-2020-1259935","winner":"","tv_station":""},{"type":"matchup","event_id":"1259915","event_date":"2020-07-11 22:00","away_name":"J Andrade","home_name":"R Namajunas","away_odds":"155","home_odds":"-190","away_votes":41,"home_votes":59,"over_votes":54,"under_votes":46,"status":"","matchup_link":"\/ufc\/jessica-andrade-rose-namajunas-odds-july-11-2020-1259915","winner":"","tv_station":""},{"type":"matchup","event_id":"1259930","event_date":"2020-07-11 22:00","away_name":"P VanZant","home_name":"A Ribas","away_odds":"550","home_odds":"-800","away_votes":33,"home_votes":67,"over_votes":54,"under_votes":46,"status":"","matchup_link":"\/ufc\/paige-vanzant-amanda-ribas-odds-july-11-2020-1259930","winner":"","tv_station":""},{"type":"matchup","event_id":"1260915","event_date":"2020-07-11 18:00","away_name":"V Oezdemir","home_name":"J Prochazka","away_odds":"-150","home_odds":"130","away_votes":50,"home_votes":50,"over_votes":94,"under_votes":6,"status":"","matchup_link":"\/ufc\/volkan-oezdemir-jiri-prochazka-odds-july-11-2020-1260915","winner":"","tv_station":""},{"type":"matchup","event_id":"1260895","event_date":"2020-07-11 18:00","away_name":"E Zaleski dos Santos","home_name":"M Salikhov","away_odds":"-110","home_odds":"-120","away_votes":42,"home_votes":58,"over_votes":26,"under_votes":74,"status":"","matchup_link":"\/ufc\/elizeu-zaleski-dos-santos-muslim-salikhov-odds-july-11-2020-1260895","winner":"","tv_station":""},{"type":"matchup","event_id":"1260920","event_date":"2020-07-11 18:00","away_name":"M Amirkhani","home_name":"D Henry","away_odds":"-200","home_odds":"160","away_votes":49,"home_votes":51,"over_votes":27,"under_votes":73,"status":"","matchup_link":"\/ufc\/makwan-amirkhani-danny-henry-odds-july-11-2020-1260920","winner":"","tv_station":""},{"type":"matchup","event_id":"1260900","event_date":"2020-07-11 18:00","away_name":"R Bogatov","home_name":"L Santos","away_odds":"150","home_odds":"-190","away_votes":47,"home_votes":53,"over_votes":2,"under_votes":98,"status":"","matchup_link":"\/ufc\/roman-bogatov-leonardo-santos-odds-july-11-2020-1260900","winner":"","tv_station":""},{"type":"matchup","event_id":"1260925","event_date":"2020-07-11 18:00","away_name":"M Tybura","home_name":"A Romanov","away_odds":"-105","home_odds":"-115","away_votes":35,"home_votes":65,"over_votes":0,"under_votes":100,"status":"","matchup_link":"\/ufc\/marcin-tybura-alexander-romanov-odds-july-11-2020-1260925","winner":"","tv_station":""},{"type":"matchup","event_id":"1260930","event_date":"2020-07-11 18:00","away_name":"R Paiva","home_name":"Z Zhamagulov","away_odds":"-190","home_odds":"155","away_votes":56,"home_votes":44,"over_votes":50,"under_votes":50,"status":"","matchup_link":"\/ufc\/raulian-paiva-zhalgas-zhamagulov-odds-july-11-2020-1260930","winner":"","tv_station":""},{"type":"matchup","event_id":"1260910","event_date":"2020-07-11 18:00","away_name":"V Melo","home_name":"K Rosa","away_odds":"170","home_odds":"-215","away_votes":36,"home_votes":64,"over_votes":54,"under_votes":46,"status":"","matchup_link":"\/ufc\/vanessa-melo-karol-rosa-odds-july-11-2020-1260910","winner":"","tv_station":""},{"type":"matchup","event_id":"1260905","event_date":"2020-07-11 18:00","away_name":"M Day","home_name":"D Grant","away_odds":"-175","home_odds":"145","away_votes":63,"home_votes":37,"over_votes":46,"under_votes":54,"status":"","matchup_link":"\/ufc\/martin-day-davey-grant-odds-july-11-2020-1260905","winner":"","tv_station":""},{"type":"event","event":"FN Wednesday Jul 15th","current":false},{"type":"matchup","event_id":"1261085","event_date":"2020-07-15 22:00","away_name":"C Kattar","home_name":"D Ige","away_odds":"-280","home_odds":"230","away_votes":41,"home_votes":59,"over_votes":0,"under_votes":0,"status":"","matchup_link":"\/ufc\/calvin-kattar-dan-ige-odds-july-15-2020-1261085","winner":"","tv_station":""},{"type":"matchup","event_id":"1261080","event_date":"2020-07-15 22:00","away_name":"F Edgar","home_name":"P Munhoz","away_odds":"180","home_odds":"-230","away_votes":41,"home_votes":59,"over_votes":0,"under_votes":0,"status":"","matchup_link":"\/ufc\/frankie-edgar-pedro-munhoz-odds-july-15-2020-1261080","winner":"","tv_station":""},{"type":"matchup","event_id":"1261090","event_date":"2020-07-15 22:00","away_name":"C Esparza","home_name":"M Rodriguez","away_odds":"130","home_odds":"-150","away_votes":46,"home_votes":54,"over_votes":0,"under_votes":0,"status":"","matchup_link":"\/ufc\/carla-esparza-marina-rodriguez-odds-july-15-2020-1261090","winner":"","tv_station":""},{"type":"matchup","event_id":"1261120","event_date":"2020-07-15 22:00","away_name":"M Lazzez","home_name":"A Razak Alhassan","away_odds":"225","home_odds":"-275","away_votes":0,"home_votes":0,"over_votes":0,"under_votes":0,"status":"","matchup_link":"\/ufc\/mounir-lazzez-abdul-razak-alhassan-odds-july-15-2020-1261120","winner":"","tv_station":""},{"type":"matchup","event_id":"1261075","event_date":"2020-07-15 22:00","away_name":"C Fishgold","home_name":"J Gordon","away_odds":"105","home_odds":"-125","away_votes":55,"home_votes":45,"over_votes":0,"under_votes":0,"status":"","matchup_link":"\/ufc\/chris-fishgold-jared-gordon-odds-july-15-2020-1261075","winner":"","tv_station":""},{"type":"matchup","event_id":"1261070","event_date":"2020-07-15 19:00","away_name":"M Bukauskas","home_name":"V Moreira","away_odds":"-280","home_odds":"240","away_votes":0,"home_votes":0,"over_votes":0,"under_votes":0,"status":"","matchup_link":"\/ufc\/modestas-bukauskas-vinicius-moreira-odds-july-15-2020-1261070","winner":"","tv_station":""},{"type":"matchup","event_id":"1261110","event_date":"2020-07-15 19:00","away_name":"M McCann","home_name":"T Santos","away_odds":"-115","home_odds":"-115","away_votes":56,"home_votes":44,"over_votes":0,"under_votes":0,"status":"","matchup_link":"\/ufc\/molly-mccann-taila-santos-odds-july-15-2020-1261110","winner":"","tv_station":""},{"type":"matchup","event_id":"1261100","event_date":"2020-07-15 19:00","away_name":"L Murphy","home_name":"R Ramos","away_odds":"145","home_odds":"-175","away_votes":74,"home_votes":26,"over_votes":0,"under_votes":0,"status":"","matchup_link":"\/ufc\/lerone-murphy-ricardo-ramos-odds-july-15-2020-1261100","winner":"","tv_station":""},{"type":"matchup","event_id":"1261105","event_date":"2020-07-15 19:00","away_name":"J Phillips","home_name":"D Todorovic","away_odds":"","home_odds":"","away_votes":20,"home_votes":80,"over_votes":0,"under_votes":0,"status":"","matchup_link":"\/ufc\/john-phillips-dusko-todorovic-odds-july-15-2020-1261105","winner":"","tv_station":""},{"type":"matchup","event_id":"1261095","event_date":"2020-07-15 19:00","away_name":"T Elliott","home_name":"R Benoit","away_odds":"-130","home_odds":"100","away_votes":59,"home_votes":41,"over_votes":0,"under_votes":0,"status":"","matchup_link":"\/ufc\/tim-elliott-ryan-benoit-odds-july-15-2020-1261095","winner":"","tv_station":""},{"type":"matchup","event_id":"1261115","event_date":"2020-07-15 19:00","away_name":"D Belbita","home_name":"L Jojua","away_odds":"-160","home_odds":"130","away_votes":0,"home_votes":0,"over_votes":0,"under_votes":0,"status":"","matchup_link":"\/ufc\/diana-belbita-liana-jojua-odds-july-15-2020-1261115","winner":"","tv_station":""}]}
```

## Step 3 - Clean & Validate JSON
- [Formatted JSON Data][3]
```
Output ⟶ {"leagues":{"ufc":true,"nhl":false,"mlb":false,"nba":false,"nfl":false,"ncaaf":false,"ncaab":false,"soccer":{"epl":true,"bundesliga":false,"la_liga":true,"serie_a":true,"england_champ":true,"brazil":false,"france_ligue_1":false,"champ_league":false,"world_cup":false,"mexico":false,"mls":false,"euro":false}},"matchups":[{"type":"event","event":"FN Saturday Jun 27th","current":false},{"type":"matchup","event_id":"1260480","event_date":"2020-06-27 20:00","away_name":"D Poirier","home_name":"D Hooker","away_odds":"-240","home_odds":"190","away_votes":43,"home_votes":57,"over_votes":62,"under_votes":38,"status":"DEC","matchup_link":"\/ufc\/dustin-poirier-dan-hooker-odds-june-27-2020-1260480","winner":"D Poirier","tv_station":""},{"type":"matchup","event_id":"1260490","event_date":"2020-06-27 20:00","away_name":"M Gall","home_name":"M Perry","away_odds":"250","home_odds":"-300","away_votes":45,"home_votes":55,"over_votes":51,"under_votes":49,"status":"DEC","matchup_link":"\/ufc\/mickey-gall-mike-perry-odds-june-27-2020-1260490","winner":"M Perry","tv_station":""},{"type":"matchup","event_id":"1260935","event_date":"2020-06-27 20:00","away_name":"B Allen","home_name":"K Daukaus","away_odds":"-300","home_odds":"240","away_votes":37,"home_votes":63,"over_votes":63,"under_votes":37,"status":"DEC","matchup_link":"\/ufc\/brendan-allen-kyle-daukaus-odds-june-27-2020-1260935","winner":"B Allen","tv_station":""},{"type":"matchup","event_id":"1260520","event_date":"2020-06-27 20:00","away_name":"M Greene","home_name":"G Villante","away_odds":"-250","home_odds":"200","away_votes":36,"home_votes":64,"over_votes":47,"under_votes":53,"status":"submission","matchup_link":"\/ufc\/maurice-greene-gian-villante-odds-june-27-2020-1260520","winner":"M Greene","tv_station":""},{"type":"matchup","event_id":"1260485","event_date":"2020-06-27 18:00","away_name":"L Pena","home_name":"K Worthy","away_odds":"-250","home_odds":"200","away_votes":43,"home_votes":57,"over_votes":47,"under_votes":53,"status":"submission","matchup_link":"\/ufc\/luis-pena-khama-worthy-odds-june-27-2020-1260485","winner":"K Worthy","tv_station":""},{"type":"matchup","event_id":"1261460","event_date":"2020-06-27 20:00","away_name":"J Erosa","home_name":"S Woodson","away_odds":"375","home_odds":"-550","away_votes":32,"home_votes":68,"over_votes":44,"under_votes":56,"status":"submission","matchup_link":"\/ufc\/julian-erosa-sean-woodson-odds-june-27-2020-1261460","winner":"J Erosa","tv_station":""},{"type":"matchup","event_id":"1260515","event_date":"2020-06-27 20:00","away_name":"T Boser","home_name":"P Lins","away_odds":"-105","home_odds":"-125","away_votes":43,"home_votes":57,"over_votes":55,"under_votes":45,"status":"ko\/tko","matchup_link":"\/ufc\/tanner-boser-philipe-lins-odds-june-27-2020-1260515","winner":"T Boser","tv_station":""},{"type":"matchup","event_id":"1261785","event_date":"2020-06-27 18:00","away_name":"T Sato","home_name":"J Witt","away_odds":"","home_odds":"","away_votes":0,"home_votes":0,"over_votes":0,"under_votes":0,"status":"ko\/tko","matchup_link":"\/ufc\/takashi-sato-jason-witt-odds-june-27-2020-1261785","winner":"T Sato","tv_station":""},{"type":"matchup","event_id":"1261130","event_date":"2020-06-27 18:00","away_name":"JY Frey","home_name":"K Hansen","away_odds":"180","home_odds":"-220","away_votes":0,"home_votes":0,"over_votes":0,"under_votes":0,"status":"submission","matchup_link":"\/ufc\/jinh-yu-frey-kay-hansen-odds-june-27-2020-1261130","winner":"K Hansen","tv_station":""},{"type":"matchup","event_id":"1260950","event_date":"2020-06-27 18:00","away_name":"J Griffin","home_name":"Y Zalal","away_odds":"100","home_odds":"-130","away_votes":51,"home_votes":49,"over_votes":55,"under_votes":45,"status":"DEC","matchup_link":"\/ufc\/jordan-griffin-youssef-zalal-odds-june-27-2020-1260950","winner":"Y Zalal","tv_station":""},{"type":"event","event":"UFC 251 Saturday Jul 11th","current":true},{"type":"matchup","event_id":"1259920","event_date":"2020-07-11 22:00","away_name":"K Usman","home_name":"G Burns","away_odds":"-240","home_odds":"200","away_votes":51,"home_votes":49,"over_votes":54,"under_votes":46,"status":"","matchup_link":"\/ufc\/kamaru-usman-gilbert-burns-odds-july-11-2020-1259920","winner":"","tv_station":""},{"type":"matchup","event_id":"1259925","event_date":"2020-07-11 22:00","away_name":"M Holloway","home_name":"A Volkanovski","away_odds":"170","home_odds":"-200","away_votes":51,"home_votes":49,"over_votes":43,"under_votes":57,"status":"","matchup_link":"\/ufc\/max-holloway-alexander-volkanovski-odds-july-11-2020-1259925","winner":"","tv_station":""},{"type":"matchup","event_id":"1259935","event_date":"2020-07-11 22:00","away_name":"J Aldo","home_name":"P Yan","away_odds":"200","home_odds":"-250","away_votes":36,"home_votes":64,"over_votes":56,"under_votes":44,"status":"","matchup_link":"\/ufc\/jose-aldo-petr-yan-odds-july-11-2020-1259935","winner":"","tv_station":""},{"type":"matchup","event_id":"1259915","event_date":"2020-07-11 22:00","away_name":"J Andrade","home_name":"R Namajunas","away_odds":"155","home_odds":"-190","away_votes":41,"home_votes":59,"over_votes":54,"under_votes":46,"status":"","matchup_link":"\/ufc\/jessica-andrade-rose-namajunas-odds-july-11-2020-1259915","winner":"","tv_station":""},{"type":"matchup","event_id":"1259930","event_date":"2020-07-11 22:00","away_name":"P VanZant","home_name":"A Ribas","away_odds":"550","home_odds":"-800","away_votes":33,"home_votes":67,"over_votes":54,"under_votes":46,"status":"","matchup_link":"\/ufc\/paige-vanzant-amanda-ribas-odds-july-11-2020-1259930","winner":"","tv_station":""},{"type":"matchup","event_id":"1260915","event_date":"2020-07-11 18:00","away_name":"V Oezdemir","home_name":"J Prochazka","away_odds":"-150","home_odds":"130","away_votes":50,"home_votes":50,"over_votes":94,"under_votes":6,"status":"","matchup_link":"\/ufc\/volkan-oezdemir-jiri-prochazka-odds-july-11-2020-1260915","winner":"","tv_station":""},{"type":"matchup","event_id":"1260895","event_date":"2020-07-11 18:00","away_name":"E Zaleski dos Santos","home_name":"M Salikhov","away_odds":"-110","home_odds":"-120","away_votes":42,"home_votes":58,"over_votes":26,"under_votes":74,"status":"","matchup_link":"\/ufc\/elizeu-zaleski-dos-santos-muslim-salikhov-odds-july-11-2020-1260895","winner":"","tv_station":""},{"type":"matchup","event_id":"1260920","event_date":"2020-07-11 18:00","away_name":"M Amirkhani","home_name":"D Henry","away_odds":"-200","home_odds":"160","away_votes":49,"home_votes":51,"over_votes":27,"under_votes":73,"status":"","matchup_link":"\/ufc\/makwan-amirkhani-danny-henry-odds-july-11-2020-1260920","winner":"","tv_station":""},{"type":"matchup","event_id":"1260900","event_date":"2020-07-11 18:00","away_name":"R Bogatov","home_name":"L Santos","away_odds":"150","home_odds":"-190","away_votes":47,"home_votes":53,"over_votes":2,"under_votes":98,"status":"","matchup_link":"\/ufc\/roman-bogatov-leonardo-santos-odds-july-11-2020-1260900","winner":"","tv_station":""},{"type":"matchup","event_id":"1260925","event_date":"2020-07-11 18:00","away_name":"M Tybura","home_name":"A Romanov","away_odds":"-105","home_odds":"-115","away_votes":35,"home_votes":65,"over_votes":0,"under_votes":100,"status":"","matchup_link":"\/ufc\/marcin-tybura-alexander-romanov-odds-july-11-2020-1260925","winner":"","tv_station":""},{"type":"matchup","event_id":"1260930","event_date":"2020-07-11 18:00","away_name":"R Paiva","home_name":"Z Zhamagulov","away_odds":"-190","home_odds":"155","away_votes":56,"home_votes":44,"over_votes":50,"under_votes":50,"status":"","matchup_link":"\/ufc\/raulian-paiva-zhalgas-zhamagulov-odds-july-11-2020-1260930","winner":"","tv_station":""},{"type":"matchup","event_id":"1260910","event_date":"2020-07-11 18:00","away_name":"V Melo","home_name":"K Rosa","away_odds":"170","home_odds":"-215","away_votes":36,"home_votes":64,"over_votes":54,"under_votes":46,"status":"","matchup_link":"\/ufc\/vanessa-melo-karol-rosa-odds-july-11-2020-1260910","winner":"","tv_station":""},{"type":"matchup","event_id":"1260905","event_date":"2020-07-11 18:00","away_name":"M Day","home_name":"D Grant","away_odds":"-175","home_odds":"145","away_votes":63,"home_votes":37,"over_votes":46,"under_votes":54,"status":"","matchup_link":"\/ufc\/martin-day-davey-grant-odds-july-11-2020-1260905","winner":"","tv_station":""},{"type":"event","event":"FN Wednesday Jul 15th","current":false},{"type":"matchup","event_id":"1261085","event_date":"2020-07-15 22:00","away_name":"C Kattar","home_name":"D Ige","away_odds":"-280","home_odds":"230","away_votes":41,"home_votes":59,"over_votes":0,"under_votes":0,"status":"","matchup_link":"\/ufc\/calvin-kattar-dan-ige-odds-july-15-2020-1261085","winner":"","tv_station":""},{"type":"matchup","event_id":"1261080","event_date":"2020-07-15 22:00","away_name":"F Edgar","home_name":"P Munhoz","away_odds":"180","home_odds":"-230","away_votes":41,"home_votes":59,"over_votes":0,"under_votes":0,"status":"","matchup_link":"\/ufc\/frankie-edgar-pedro-munhoz-odds-july-15-2020-1261080","winner":"","tv_station":""},{"type":"matchup","event_id":"1261090","event_date":"2020-07-15 22:00","away_name":"C Esparza","home_name":"M Rodriguez","away_odds":"130","home_odds":"-150","away_votes":46,"home_votes":54,"over_votes":0,"under_votes":0,"status":"","matchup_link":"\/ufc\/carla-esparza-marina-rodriguez-odds-july-15-2020-1261090","winner":"","tv_station":""},{"type":"matchup","event_id":"1261120","event_date":"2020-07-15 22:00","away_name":"M Lazzez","home_name":"A Razak Alhassan","away_odds":"225","home_odds":"-275","away_votes":0,"home_votes":0,"over_votes":0,"under_votes":0,"status":"","matchup_link":"\/ufc\/mounir-lazzez-abdul-razak-alhassan-odds-july-15-2020-1261120","winner":"","tv_station":""},{"type":"matchup","event_id":"1261075","event_date":"2020-07-15 22:00","away_name":"C Fishgold","home_name":"J Gordon","away_odds":"105","home_odds":"-125","away_votes":55,"home_votes":45,"over_votes":0,"under_votes":0,"status":"","matchup_link":"\/ufc\/chris-fishgold-jared-gordon-odds-july-15-2020-1261075","winner":"","tv_station":""},{"type":"matchup","event_id":"1261070","event_date":"2020-07-15 19:00","away_name":"M Bukauskas","home_name":"V Moreira","away_odds":"-280","home_odds":"240","away_votes":0,"home_votes":0,"over_votes":0,"under_votes":0,"status":"","matchup_link":"\/ufc\/modestas-bukauskas-vinicius-moreira-odds-july-15-2020-1261070","winner":"","tv_station":""},{"type":"matchup","event_id":"1261110","event_date":"2020-07-15 19:00","away_name":"M McCann","home_name":"T Santos","away_odds":"-115","home_odds":"-115","away_votes":56,"home_votes":44,"over_votes":0,"under_votes":0,"status":"","matchup_link":"\/ufc\/molly-mccann-taila-santos-odds-july-15-2020-1261110","winner":"","tv_station":""},{"type":"matchup","event_id":"1261100","event_date":"2020-07-15 19:00","away_name":"L Murphy","home_name":"R Ramos","away_odds":"145","home_odds":"-175","away_votes":74,"home_votes":26,"over_votes":0,"under_votes":0,"status":"","matchup_link":"\/ufc\/lerone-murphy-ricardo-ramos-odds-july-15-2020-1261100","winner":"","tv_station":""},{"type":"matchup","event_id":"1261105","event_date":"2020-07-15 19:00","away_name":"J Phillips","home_name":"D Todorovic","away_odds":"","home_odds":"","away_votes":20,"home_votes":80,"over_votes":0,"under_votes":0,"status":"","matchup_link":"\/ufc\/john-phillips-dusko-todorovic-odds-july-15-2020-1261105","winner":"","tv_station":""},{"type":"matchup","event_id":"1261095","event_date":"2020-07-15 19:00","away_name":"T Elliott","home_name":"R Benoit","away_odds":"-130","home_odds":"100","away_votes":59,"home_votes":41,"over_votes":0,"under_votes":0,"status":"","matchup_link":"\/ufc\/tim-elliott-ryan-benoit-odds-july-15-2020-1261095","winner":"","tv_station":""},{"type":"matchup","event_id":"1261115","event_date":"2020-07-15 19:00","away_name":"D Belbita","home_name":"L Jojua","away_odds":"-160","home_odds":"130","away_votes":0,"home_votes":0,"over_votes":0,"under_votes":0,"status":"","matchup_link":"\/ufc\/diana-belbita-liana-jojua-odds-july-15-2020-1261115","winner":"","tv_station":""}]}
```

## Step 4 - Convert JSON to YAML
- Convert to YAML to make data more human readable, if necessary.
- 
```
leagues:
    ufc: true
    nhl: false
    mlb: false
    nba: false
    nfl: false
    ncaaf: false
    ncaab: false
    soccer:
        epl: true
        bundesliga: false
        la_liga: true
        serie_a: true
        england_champ: true
        brazil: false
        france_ligue_1: false
        champ_league: false
        world_cup: false
        mexico: false
        mls: false
        euro: false
matchups:
    -
        type: event
        event: 'FN Saturday Jun 27th'
        current: false
    -
        type: matchup
        event_id: '1260480'
        event_date: '2020-06-27 20:00'
        away_name: 'D Poirier'
        home_name: 'D Hooker'
        away_odds: '-240'
        home_odds: '190'
        away_votes: 43
        home_votes: 57
        over_votes: 62
        under_votes: 38
        status: DEC
        matchup_link: /ufc/dustin-poirier-dan-hooker-odds-june-27-2020-1260480
        winner: 'D Poirier'
        tv_station: ''
    -
        type: matchup
        event_id: '1260490'
        event_date: '2020-06-27 20:00'
        away_name: 'M Gall'
        home_name: 'M Perry'
        away_odds: '250'
        home_odds: '-300'
        away_votes: 45
        home_votes: 55
        over_votes: 51
        under_votes: 49
        status: DEC
        matchup_link: /ufc/mickey-gall-mike-perry-odds-june-27-2020-1260490
        winner: 'M Perry'
        tv_station: ''
    -
        type: matchup
        event_id: '1260935'
        event_date: '2020-06-27 20:00'
        away_name: 'B Allen'
        home_name: 'K Daukaus'
        away_odds: '-300'
        home_odds: '240'
        away_votes: 37
        home_votes: 63
        over_votes: 63
        under_votes: 37
        status: DEC
        matchup_link: /ufc/brendan-allen-kyle-daukaus-odds-june-27-2020-1260935
        winner: 'B Allen'
        tv_station: ''
    -
        type: matchup
        event_id: '1260520'
        event_date: '2020-06-27 20:00'
        away_name: 'M Greene'
        home_name: 'G Villante'
        away_odds: '-250'
        home_odds: '200'
        away_votes: 36
        home_votes: 64
        over_votes: 47
        under_votes: 53
        status: submission
        matchup_link: /ufc/maurice-greene-gian-villante-odds-june-27-2020-1260520
        winner: 'M Greene'
        tv_station: ''
    -
        type: matchup
        event_id: '1260485'
        event_date: '2020-06-27 18:00'
        away_name: 'L Pena'
        home_name: 'K Worthy'
        away_odds: '-250'
        home_odds: '200'
        away_votes: 43
        home_votes: 57
        over_votes: 47
        under_votes: 53
        status: submission
        matchup_link: /ufc/luis-pena-khama-worthy-odds-june-27-2020-1260485
        winner: 'K Worthy'
        tv_station: ''
    -
        type: matchup
        event_id: '1261460'
        event_date: '2020-06-27 20:00'
        away_name: 'J Erosa'
        home_name: 'S Woodson'
        away_odds: '375'
        home_odds: '-550'
        away_votes: 32
        home_votes: 68
        over_votes: 44
        under_votes: 56
        status: submission
        matchup_link: /ufc/julian-erosa-sean-woodson-odds-june-27-2020-1261460
        winner: 'J Erosa'
        tv_station: ''
    -
        type: matchup
        event_id: '1260515'
        event_date: '2020-06-27 20:00'
        away_name: 'T Boser'
        home_name: 'P Lins'
        away_odds: '-105'
        home_odds: '-125'
        away_votes: 43
        home_votes: 57
        over_votes: 55
        under_votes: 45
        status: ko/tko
        matchup_link: /ufc/tanner-boser-philipe-lins-odds-june-27-2020-1260515
        winner: 'T Boser'
        tv_station: ''
    -
        type: matchup
        event_id: '1261785'
        event_date: '2020-06-27 18:00'
        away_name: 'T Sato'
        home_name: 'J Witt'
        away_odds: ''
        home_odds: ''
        away_votes: 0
        home_votes: 0
        over_votes: 0
        under_votes: 0
        status: ko/tko
        matchup_link: /ufc/takashi-sato-jason-witt-odds-june-27-2020-1261785
        winner: 'T Sato'
        tv_station: ''
    -
        type: matchup
        event_id: '1261130'
        event_date: '2020-06-27 18:00'
        away_name: 'JY Frey'
        home_name: 'K Hansen'
        away_odds: '180'
        home_odds: '-220'
        away_votes: 0
        home_votes: 0
        over_votes: 0
        under_votes: 0
        status: submission
        matchup_link: /ufc/jinh-yu-frey-kay-hansen-odds-june-27-2020-1261130
        winner: 'K Hansen'
        tv_station: ''
    -
        type: matchup
        event_id: '1260950'
        event_date: '2020-06-27 18:00'
        away_name: 'J Griffin'
        home_name: 'Y Zalal'
        away_odds: '100'
        home_odds: '-130'
        away_votes: 51
        home_votes: 49
        over_votes: 55
        under_votes: 45
        status: DEC
        matchup_link: /ufc/jordan-griffin-youssef-zalal-odds-june-27-2020-1260950
        winner: 'Y Zalal'
        tv_station: ''
    -
        type: event
        event: 'UFC 251 Saturday Jul 11th'
        current: true
    -
        type: matchup
        event_id: '1259920'
        event_date: '2020-07-11 22:00'
        away_name: 'K Usman'
        home_name: 'G Burns'
        away_odds: '-240'
        home_odds: '200'
        away_votes: 51
        home_votes: 49
        over_votes: 54
        under_votes: 46
        status: ''
        matchup_link: /ufc/kamaru-usman-gilbert-burns-odds-july-11-2020-1259920
        winner: ''
        tv_station: ''
    -
        type: matchup
        event_id: '1259925'
        event_date: '2020-07-11 22:00'
        away_name: 'M Holloway'
        home_name: 'A Volkanovski'
        away_odds: '170'
        home_odds: '-200'
        away_votes: 51
        home_votes: 49
        over_votes: 43
        under_votes: 57
        status: ''
        matchup_link: /ufc/max-holloway-alexander-volkanovski-odds-july-11-2020-1259925
        winner: ''
        tv_station: ''
    -
        type: matchup
        event_id: '1259935'
        event_date: '2020-07-11 22:00'
        away_name: 'J Aldo'
        home_name: 'P Yan'
        away_odds: '200'
        home_odds: '-250'
        away_votes: 36
        home_votes: 64
        over_votes: 56
        under_votes: 44
        status: ''
        matchup_link: /ufc/jose-aldo-petr-yan-odds-july-11-2020-1259935
        winner: ''
        tv_station: ''
    -
        type: matchup
        event_id: '1259915'
        event_date: '2020-07-11 22:00'
        away_name: 'J Andrade'
        home_name: 'R Namajunas'
        away_odds: '155'
        home_odds: '-190'
        away_votes: 41
        home_votes: 59
        over_votes: 54
        under_votes: 46
        status: ''
        matchup_link: /ufc/jessica-andrade-rose-namajunas-odds-july-11-2020-1259915
        winner: ''
        tv_station: ''
    -
        type: matchup
        event_id: '1259930'
        event_date: '2020-07-11 22:00'
        away_name: 'P VanZant'
        home_name: 'A Ribas'
        away_odds: '550'
        home_odds: '-800'
        away_votes: 33
        home_votes: 67
        over_votes: 54
        under_votes: 46
        status: ''
        matchup_link: /ufc/paige-vanzant-amanda-ribas-odds-july-11-2020-1259930
        winner: ''
        tv_station: ''
    -
        type: matchup
        event_id: '1260915'
        event_date: '2020-07-11 18:00'
        away_name: 'V Oezdemir'
        home_name: 'J Prochazka'
        away_odds: '-150'
        home_odds: '130'
        away_votes: 50
        home_votes: 50
        over_votes: 94
        under_votes: 6
        status: ''
        matchup_link: /ufc/volkan-oezdemir-jiri-prochazka-odds-july-11-2020-1260915
        winner: ''
        tv_station: ''
    -
        type: matchup
        event_id: '1260895'
        event_date: '2020-07-11 18:00'
        away_name: 'E Zaleski dos Santos'
        home_name: 'M Salikhov'
        away_odds: '-110'
        home_odds: '-120'
        away_votes: 42
        home_votes: 58
        over_votes: 26
        under_votes: 74
        status: ''
        matchup_link: /ufc/elizeu-zaleski-dos-santos-muslim-salikhov-odds-july-11-2020-1260895
        winner: ''
        tv_station: ''
    -
        type: matchup
        event_id: '1260920'
        event_date: '2020-07-11 18:00'
        away_name: 'M Amirkhani'
        home_name: 'D Henry'
        away_odds: '-200'
        home_odds: '160'
        away_votes: 49
        home_votes: 51
        over_votes: 27
        under_votes: 73
        status: ''
        matchup_link: /ufc/makwan-amirkhani-danny-henry-odds-july-11-2020-1260920
        winner: ''
        tv_station: ''
    -
        type: matchup
        event_id: '1260900'
        event_date: '2020-07-11 18:00'
        away_name: 'R Bogatov'
        home_name: 'L Santos'
        away_odds: '150'
        home_odds: '-190'
        away_votes: 47
        home_votes: 53
        over_votes: 2
        under_votes: 98
        status: ''
        matchup_link: /ufc/roman-bogatov-leonardo-santos-odds-july-11-2020-1260900
        winner: ''
        tv_station: ''
    -
        type: matchup
        event_id: '1260925'
        event_date: '2020-07-11 18:00'
        away_name: 'M Tybura'
        home_name: 'A Romanov'
        away_odds: '-105'
        home_odds: '-115'
        away_votes: 35
        home_votes: 65
        over_votes: 0
        under_votes: 100
        status: ''
        matchup_link: /ufc/marcin-tybura-alexander-romanov-odds-july-11-2020-1260925
        winner: ''
        tv_station: ''
    -
        type: matchup
        event_id: '1260930'
        event_date: '2020-07-11 18:00'
        away_name: 'R Paiva'
        home_name: 'Z Zhamagulov'
        away_odds: '-190'
        home_odds: '155'
        away_votes: 56
        home_votes: 44
        over_votes: 50
        under_votes: 50
        status: ''
        matchup_link: /ufc/raulian-paiva-zhalgas-zhamagulov-odds-july-11-2020-1260930
        winner: ''
        tv_station: ''
    -
        type: matchup
        event_id: '1260910'
        event_date: '2020-07-11 18:00'
        away_name: 'V Melo'
        home_name: 'K Rosa'
        away_odds: '170'
        home_odds: '-215'
        away_votes: 36
        home_votes: 64
        over_votes: 54
        under_votes: 46
        status: ''
        matchup_link: /ufc/vanessa-melo-karol-rosa-odds-july-11-2020-1260910
        winner: ''
        tv_station: ''
    -
        type: matchup
        event_id: '1260905'
        event_date: '2020-07-11 18:00'
        away_name: 'M Day'
        home_name: 'D Grant'
        away_odds: '-175'
        home_odds: '145'
        away_votes: 63
        home_votes: 37
        over_votes: 46
        under_votes: 54
        status: ''
        matchup_link: /ufc/martin-day-davey-grant-odds-july-11-2020-1260905
        winner: ''
        tv_station: ''
    -
        type: event
        event: 'FN Wednesday Jul 15th'
        current: false
    -
        type: matchup
        event_id: '1261085'
        event_date: '2020-07-15 22:00'
        away_name: 'C Kattar'
        home_name: 'D Ige'
        away_odds: '-280'
        home_odds: '230'
        away_votes: 41
        home_votes: 59
        over_votes: 0
        under_votes: 0
        status: ''
        matchup_link: /ufc/calvin-kattar-dan-ige-odds-july-15-2020-1261085
        winner: ''
        tv_station: ''
    -
        type: matchup
        event_id: '1261080'
        event_date: '2020-07-15 22:00'
        away_name: 'F Edgar'
        home_name: 'P Munhoz'
        away_odds: '180'
        home_odds: '-230'
        away_votes: 41
        home_votes: 59
        over_votes: 0
        under_votes: 0
        status: ''
        matchup_link: /ufc/frankie-edgar-pedro-munhoz-odds-july-15-2020-1261080
        winner: ''
        tv_station: ''
    -
        type: matchup
        event_id: '1261090'
        event_date: '2020-07-15 22:00'
        away_name: 'C Esparza'
        home_name: 'M Rodriguez'
        away_odds: '130'
        home_odds: '-150'
        away_votes: 46
        home_votes: 54
        over_votes: 0
        under_votes: 0
        status: ''
        matchup_link: /ufc/carla-esparza-marina-rodriguez-odds-july-15-2020-1261090
        winner: ''
        tv_station: ''
    -
        type: matchup
        event_id: '1261120'
        event_date: '2020-07-15 22:00'
        away_name: 'M Lazzez'
        home_name: 'A Razak Alhassan'
        away_odds: '225'
        home_odds: '-275'
        away_votes: 0
        home_votes: 0
        over_votes: 0
        under_votes: 0
        status: ''
        matchup_link: /ufc/mounir-lazzez-abdul-razak-alhassan-odds-july-15-2020-1261120
        winner: ''
        tv_station: ''
    -
        type: matchup
        event_id: '1261075'
        event_date: '2020-07-15 22:00'
        away_name: 'C Fishgold'
        home_name: 'J Gordon'
        away_odds: '105'
        home_odds: '-125'
        away_votes: 55
        home_votes: 45
        over_votes: 0
        under_votes: 0
        status: ''
        matchup_link: /ufc/chris-fishgold-jared-gordon-odds-july-15-2020-1261075
        winner: ''
        tv_station: ''
    -
        type: matchup
        event_id: '1261070'
        event_date: '2020-07-15 19:00'
        away_name: 'M Bukauskas'
        home_name: 'V Moreira'
        away_odds: '-280'
        home_odds: '240'
        away_votes: 0
        home_votes: 0
        over_votes: 0
        under_votes: 0
        status: ''
        matchup_link: /ufc/modestas-bukauskas-vinicius-moreira-odds-july-15-2020-1261070
        winner: ''
        tv_station: ''
    -
        type: matchup
        event_id: '1261110'
        event_date: '2020-07-15 19:00'
        away_name: 'M McCann'
        home_name: 'T Santos'
        away_odds: '-115'
        home_odds: '-115'
        away_votes: 56
        home_votes: 44
        over_votes: 0
        under_votes: 0
        status: ''
        matchup_link: /ufc/molly-mccann-taila-santos-odds-july-15-2020-1261110
        winner: ''
        tv_station: ''
    -
        type: matchup
        event_id: '1261100'
        event_date: '2020-07-15 19:00'
        away_name: 'L Murphy'
        home_name: 'R Ramos'
        away_odds: '145'
        home_odds: '-175'
        away_votes: 74
        home_votes: 26
        over_votes: 0
        under_votes: 0
        status: ''
        matchup_link: /ufc/lerone-murphy-ricardo-ramos-odds-july-15-2020-1261100
        winner: ''
        tv_station: ''
    -
        type: matchup
        event_id: '1261105'
        event_date: '2020-07-15 19:00'
        away_name: 'J Phillips'
        home_name: 'D Todorovic'
        away_odds: ''
        home_odds: ''
        away_votes: 20
        home_votes: 80
        over_votes: 0
        under_votes: 0
        status: ''
        matchup_link: /ufc/john-phillips-dusko-todorovic-odds-july-15-2020-1261105
        winner: ''
        tv_station: ''
    -
        type: matchup
        event_id: '1261095'
        event_date: '2020-07-15 19:00'
        away_name: 'T Elliott'
        home_name: 'R Benoit'
        away_odds: '-130'
        home_odds: '100'
        away_votes: 59
        home_votes: 41
        over_votes: 0
        under_votes: 0
        status: ''
        matchup_link: /ufc/tim-elliott-ryan-benoit-odds-july-15-2020-1261095
        winner: ''
        tv_station: ''
    -
        type: matchup
        event_id: '1261115'
        event_date: '2020-07-15 19:00'
        away_name: 'D Belbita'
        home_name: 'L Jojua'
        away_odds: '-160'
        home_odds: '130'
        away_votes: 0
        home_votes: 0
        over_votes: 0
        under_votes: 0
        status: ''
        matchup_link: /ufc/diana-belbita-liana-jojua-odds-july-15-2020-1261115
        winner: ''
        tv_station: ''

```





<!--- RESOURCES & SOURCES -->

[1]: https://www.oddsshark.com/ufc/consensus-picks "UFC Fighting - Consensus Picks - July, 2020"
[2]: https://dencode.com/en/string/unicode-escape "Unicode Escape / Unescape (Encoder / Decoder) Online - DenCode"
[3]: https://jsonformatter.curiousconcept.com/ "JSON Formatter & Validator"
[4]: https://dataconverter.curiousconcept.com/ "Mutate: Data Converter"
[5]: https://en.wikipedia.org/wiki/UFC_on_ESPN:_Poirier_vs._Hooker "UFC on ESPN: Poirier vs. Hooker"
[6]: https://en.wikipedia.org/wiki/UFC_251 "UFC 251"
