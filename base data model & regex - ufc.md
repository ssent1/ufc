## Event Info
event_id |event_num | event_label |  event_date | event_time | event_loc |


MAIN CARD / PRELIMS / EARLY PRELIMS
SAT, JUN 6 / 10:00 PM EDT


UFC 250
NUNES
VS
SPENCER
Sat, Jun 6 / 10:00 PM EDT
UFC APEX, Las Vegas United States
MAIN CARD
(ACTIVE TAB)
PRELIMS
EARLY PRELIMS
FIGHT PASS PPV
SAT, JUN 6 / 10:00 PM EDT
ORDER ON FIGHT PASS

-------------------------------------------------

## Field Descriptions
award
blue_fname
blue_lname
blue_odds
blue_outcome
divi
method
red_fname
red_lname
red_odds
red_outcome
round
time

-------------------------------------------------

## Event Info
event_id |event_num | event_label |  event_date | event_time | event_loc |

## Bout Info
bout_card | bout_divi | bout_order | bout_round | bout_time | bout_method | bout_award |

## Fighter Info
red_fname | red_lname | red_odds | red_outcome_num |red_outcome | blue_fname | blue_lname | blue_odds | blue_outcome_num |blue_outcome |

## Database
event_id |event_num | event_label |  event_date | event_time | event_loc | bout_card | bout_divi | bout_order | bout_round | bout_time | bout_method | bout_award | red_fname | red_lname | red_odds | red_outcome_num |red_outcome | blue_fname | blue_lname | blue_odds | blue_outcome_num |blue_outcome |

-------------------------------------------------

event_id ≡ unique identifier
event_num ≡ UFC xxx
event_label ≡ red v. blue  ==> red_lname v. blue_lname
event_loc ≡ event location
appearance ≡ MAIN CARD / PRELIMS / EARLY PRELIMS
order ≡ 0 = main, 1 = co-main, … 4? = first of five?


fight | red | -n | blue | +n | 
--|

regular
main event
title

-------------------------------------------------

## Regular Expression
	(?<red_outcome>WIN)?(?:(\n)(?<red_fname>[\w ]+)\2(?<red_lname>[\w '']+))?(\2(?<award>PERFORMANCE OF THE NIGHT))?\2(?<divi>[\w' ]+ BOUT)\2VS\2ROUND\2(?<round>\d)\2TIME\2(?<time>[0-5]:[0-9]{2})\2METHOD\2(?<method>DEC|KO\/TKO|SUB)\2+(?<blue_outcome>WIN)?\2(?<blue_fname>[\w ]+)\2(?<blue_lname>[\w '']+)\2(?<red_odds>[\+\-]\d+)\2(?:ODDS)\2(?<blue_odds>[\+\-]\d+)
	//

https://regex101.com/r/V2YmSU/1 "UFC data modelling"

## Test String
```
WIN
AMANDA
NUNES
WOMEN'S FEATHERWEIGHT TITLE BOUT
VS
ROUND
5
TIME
5:00
METHOD
DEC

FELICIA
SPENCER
-600
ODDS
+450

RAPHAEL
ASSUNCAO
PERFORMANCE OF THE NIGHT
BANTAMWEIGHT BOUT
VS
ROUND
2
TIME
4:59
METHOD
KO/TKO

WIN
CODY
GARBRANDT
-145
ODDS
+125

WIN
ALJAMAIN
STERLING
PERFORMANCE OF THE NIGHT
BANTAMWEIGHT BOUT
VS
ROUND
1
TIME
1:28
METHOD
SUB

CORY
SANDHAGEN
-115
ODDS
-105

WIN
NEIL
MAGNY
WELTERWEIGHT BOUT
VS
ROUND
3
TIME
5:00
METHOD
DEC

ANTHONY ROCCO
MARTIN
-135
ODDS
+115

EDDIE
WINELAND
PERFORMANCE OF THE NIGHT
BANTAMWEIGHT BOUT
VS
ROUND
1
TIME
1:54
METHOD
KO/TKO

WIN
SEAN
O'MALLEY
+400
ODDS
-500
```

## Substitution
```
WIN


AMANDA
NUNES
WOMEN'S FEATHERWEIGHT TITLE BOUT
5
5:00
DEC
FELICIA
SPENCER
-600
+450


RAPHAEL
ASSUNCAO

PERFORMANCE OF THE NIGHT
PERFORMANCE OF THE NIGHT
BANTAMWEIGHT BOUT
2
4:59
KO/TKO
WIN
CODY
GARBRANDT
-145
+125
WIN


ALJAMAIN
STERLING

PERFORMANCE OF THE NIGHT
PERFORMANCE OF THE NIGHT
BANTAMWEIGHT BOUT
1
1:28
SUB
CORY
SANDHAGEN
-115
-105
WIN


NEIL
MAGNY
WELTERWEIGHT BOUT
3
5:00
DEC
ANTHONY ROCCO
MARTIN
-135
+115


EDDIE
WINELAND

PERFORMANCE OF THE NIGHT
PERFORMANCE OF THE NIGHT
BANTAMWEIGHT BOUT
1
1:54
KO/TKO
WIN
SEAN
O'MALLEY
+400
-500
```

## Match Information


#### Match 1
Full match	0-113	WIN
AMANDA
NUNES
WOMEN'S FEATHERWEIGHT TITLE BOUT
VS...
Group `red_outcome`	0-3	WIN
Group 2.	3-4	
Group `red_fname`	4-10	AMANDA
Group `red_lname`	11-16	NUNES
Group `divi`	17-49	WOMEN'S FEATHERWEIGHT TITLE BOUT
Group `round`	59-60	5
Group `time`	66-70	5:00
Group `method`	78-81	DEC
Group `blue_fname`	83-90	FELICIA
Group `blue_lname`	91-98	SPENCER
Group `red_odds`	99-103	-600
Group `blue_odds`	109-113	+450

#### Match 2
Full match	114-244	
RAPHAEL
ASSUNCAO
PERFORMANCE OF THE NIGHT
BANTAMWEIGHT BOUT...
Group 2.	114-115	
Group `red_fname`	115-122	RAPHAEL
Group `red_lname`	123-131	ASSUNCAO
Group 5.	131-156	
PERFORMANCE OF THE NIGHT
Group `award`	132-156	PERFORMANCE OF THE NIGHT
Group `divi`	157-174	BANTAMWEIGHT BOUT
Group `round`	184-185	2
Group `time`	191-195	4:59
Group `method`	203-209	KO/TKO
Group `blue_outcome`	211-214	WIN
Group `blue_fname`	215-219	CODY
Group `blue_lname`	220-229	GARBRANDT
Group `red_odds`	230-234	-145
Group `blue_odds`	240-244	+125

#### Match 3
Full match	246-373	WIN
ALJAMAIN
STERLING
PERFORMANCE OF THE NIGHT
BANTAMWEIGHT BOUT...
Group `red_outcome`	246-249	WIN
Group 2.	249-250	
Group `red_fname`	250-258	ALJAMAIN
Group `red_lname`	259-267	STERLING
Group 5.	267-292	
PERFORMANCE OF THE NIGHT
Group `award`	268-292	PERFORMANCE OF THE NIGHT
Group `divi`	293-310	BANTAMWEIGHT BOUT
Group `round`	320-321	1
Group `time`	327-331	1:28
Group `method`	339-342	SUB
Group `blue_fname`	344-348	CORY
Group `blue_lname`	349-358	SANDHAGEN
Group `red_odds`	359-363	-115
Group `blue_odds`	369-373	-105

#### Match 4
Full match	375-476	WIN
NEIL
MAGNY
WELTERWEIGHT BOUT
VS...
Group `red_outcome`	375-378	WIN
Group 2.	378-379	
Group `red_fname`	379-383	NEIL
Group `red_lname`	384-389	MAGNY
Group `divi`	390-407	WELTERWEIGHT BOUT
Group `round`	417-418	3
Group `time`	424-428	5:00
Group `method`	436-439	DEC
Group `blue_fname`	441-454	ANTHONY ROCCO
Group `blue_lname`	455-461	MARTIN
Group `red_odds`	462-466	-135
Group `blue_odds`	472-476	+115

#### Match 5
Full match	477-604	
EDDIE
WINELAND
PERFORMANCE OF THE NIGHT
BANTAMWEIGHT BOUT...
Group 2.	477-478	
Group `red_fname`	478-483	EDDIE
Group `red_lname`	484-492	WINELAND
Group 5.	492-517	
PERFORMANCE OF THE NIGHT
Group `award`	493-517	PERFORMANCE OF THE NIGHT
Group `divi`	518-535	BANTAMWEIGHT BOUT
Group `round`	545-546	1
Group `time`	552-556	1:54
Group `method`	564-570	KO/TKO
Group `blue_outcome`	572-575	WIN
Group `blue_fname`	576-580	SEAN
Group `blue_lname`	581-589	O'MALLEY
Group `red_odds`	590-594	+400
Group `blue_odds`	600-604	-500
