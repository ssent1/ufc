[UFC Fight Night: Moraes vs. Sandhagen Odds | Fight Odds](https://fightodds.io/mma-events/3194/ufc-fight-night-moraes-vs-sandhagen/odds)


https://towardsdatascience.com/announcing-pycaret-2-0-39c11014540e "Announcing PyCaret 2.0 - An open source low-code machine learning library in Python"


## What-If Analysis
- []  https://support.microsoft.com/en-us/office/introduction-to-what-if-analysis-22bffa5f-e891-4acc-bf7a-e4645c446fb4 "What-If Analysis"


### FightMetric Data Modelling
- [] [Upcoming UFC Events - FightMetrics](https://fightmetric.rds.ca/events/upcoming)
- [] [Completed UFC Events - FightMetrics](https://fightmetric.rds.ca/events/completed)
- [] [UFC "Fight Night: Poirier Vs. Hooker](https://fightmetric.rds.ca/event/976)
- [] [FightMetric Stats - UFC](http://ufcstats.com/statistics/events/completed)

### Data Sources
- []  https://en.wikipedia.org/wiki/List_of_current_UFC_fighters#History "List of current UFC fighters - Wikipedia"
- []  https://www.sherdog.com/news/news/14-Fighters-No-Longer-Part-of-UFC-Roster-Following-Cuts-Free-Agency-171763 "14 Fighters No Longer Part of UFC Roster Following Cuts, Free Agency"
- []  https://www.bloodyelbow.com/2020/7/5/21314135/ufc-251-betting-odds-kamaru-usman-favored-jorge-masvidal-mma-gambling-news "UFC 251 betting odds: Kamaru Usman favored over Jorge Masvidal"
- []  https://www.cbssports.com/mma/news/ufc-251-usman-vs-masvidal-odds-predictions-mma-insider-releases-surprising-fight-card-picks/ "UFC 251: Usman vs. Masvidal odds, predictions: MMA insider releases surprising fight card picks"

#### Query Ideas
- []  {query: kamaru usman odds}
- 
#### Event Header
UFC FIGHT NIGHT: POIRIER VS. HOOKER  
UFC Apex  
Las Vegas, Nevada, USA  
27 Jun. 2020  

--- FightMetric 
--- "event_detail [ 'fighters', 'weight', 'str', 'td', 'sub', 'pass', 'method', 'round', 'time' ]"

defintions: { KD: Knock-down, Sig. Str.: Significant Strikes, Tot. Str.: Total Strikes, TD: Takedown }
defintions: { Sub Att: Submission Attempts, Pass: Passes, SLpM: Sig. Strikes Landed per Minute, Str. Acc.: Striking Accuracy }
defintions: { SApM: Sig. Strikes Absorbed per Minute, Str. Def.: Sig. Striking Defence, TD Avg.: Takedowns Average per 15_00, Sub. Avg.: Submission Atts. Avg. per 15::00 }

↓

--- 
defintions: 
  SApM: "Sig. Strikes Absorbed per Minute"
  ? "Str. Def."
  : "Sig. Striking Defence"
  ? "Sub. Avg."
  : "Submission Atts. Avg. per 15_00"
  ? "TD Avg."
  : "Takedowns Average per 15_00"

??
--- "FightMetric 
 event_detail [ 'fighters', 'weight', 'str', 'td', 'sub', 'pass', 'method', 'round', 'time' ] 
 
 defintions: { KD: Knock-down, Sig. Str.: Significant Strikes, Tot. Str.: Total Strikes, TD: Takedown }
 defintions: { Sub Att: Submission Attempts, Pass: Passes, SLpM: Sig. Strikes Landed per Minute, Str. Acc.: Striking Accuracy }
 defintions: { SApM: Sig. Strikes Absorbed per Minute, Str. Def.: Sig. Striking Defence, TD Avg.: Takedowns Average per 15:00, Sub. Avg.: Submission Atts. Avg. per 15:00 }
 
 
-------------------------------------------------



### canonical = https://www.ufc.com/athletes/all

## UFC Athletes

Active   = 659 
Inactive = 192
--------------
Total    = 851
==============

11 athletes / page
851/11 = 77.364

end at Cláudia Gadelha
next page = https://www.ufc.com/views/ajax?gender=All&search=&page=24





## UFC Weight Divisions
| [Weight Class][3] | Minimum Weight            | Upper Weight Limit         |
|:------------------|:--------------------------|:---------------------------|
| Strawweight       | None                      | 115 lb (52.2 kg; 8.2 st)   |
| Flyweight         | 115 lb (52.2 kg; 8.2 st)  | 125 lb (56.7 kg; 8.9 st)   |
| Bantamweight      | 125 lb (56.7 kg; 8.9 st)  | 135 lb (61.2 kg; 9.6 st)   |
| Featherweight     | 135 lb (61.2 kg; 9.6 st)  | 145 lb (65.8 kg; 10.4 st)  |
| Lightweight       | 145 lb (65.8 kg; 10.4 st) | 155 lb (70.3 kg; 11.1 st)  |
| Welterweight      | 155 lb (70.3 kg; 11.1 st) | 170 lb (77.1 kg; 12.1 st)  |
| Middleweight      | 170 lb (77.1 kg; 12.1 st) | 185 lb (83.9 kg; 13.2 st)  |
| Light Heavyweight | 185 lb (83.9 kg; 13.2 st) | 205 lb (93.0 kg; 14.6 st)  |
| Heavyweight       | 205 lb (93.0 kg; 14.6 st) | 265 lb (120.2 kg; 18.9 st) |

|  №  | [Divisions][3]    | min_lb | min_kg | min_st | max_lb | max_kg | max_st |
|:---:|:------------------|:-------|:-------|:-------|:-------|:-------|:-------|
|  0  | Strawweight       | 0      | 0      | 0      | 115    | 52.2   | 8.2    |
|  1  | Flyweight         | 115    | 52.2   | 8.2    | 125    | 56.7   | 8.9    |
|  2  | Bantamweight      | 125    | 56.7   | 8.9    | 135    | 61.2   | 9.6    |
|  3  | Featherweight     | 135    | 61.2   | 9.6    | 145    | 65.8   | 10.4   |
|  4  | Lightweight       | 145    | 65.8   | 10.4   | 155    | 70.3   | 11.1   |
|  5  | Welterweight      | 155    | 70.3   | 11.1   | 170    | 77.1   | 12.1   |
|  6  | Middleweight      | 170    | 77.1   | 12.1   | 185    | 83.9   | 13.2   |
|  7  | Light Heavyweight | 185    | 83.9   | 13.2   | 205    | 93     | 14.6   |
|  8  | Heavyweight       | 205    | 93     | 14.6   | 265    | 120.2  | 18.9   |

## UFC Bonus Awards
|  №  | [UFC Bonus Awards][4]    | UFC Bonus Award Description                                     |
|:---:|:-------------------------|:----------------------------------------------------------------|
| -2  | Submission of the Night  | Discontinued. Awarded for the most impressive submission.       |
| -1  | Knockout of the Night    | Discontinued. Awarded for the most impressive KO/TKO.           |
|  0  | Fight of the Night       | Awarded to both fighters in the card's most impressive fight.   |
|  1  | Performance of the Night | Awarded for the best and most exciting individual performances. |

## MMA Decision Criteria
|  №  | RES | [Result Description][1]                                            |
|:---:|:----|:-------------------------------------------------------------------|
|  0  | KO  | knockout ≡ loss of consciousness, orientation, or cannot get up    |
|  1  | TKO | technical knockout ≡ stoppage: cannot defend or continue safely    |
|  2  | SUB | submission ≡ tap out                                               |
|  3  | UD  | unanimous decision ≡ 3 wins + 0 {loss‖draw}                        |
|  4  | MD  | majority decision ≡ 2 wins + 1 draw                                |
|  5  | SD  | split decision ≡ 2 wins {blue‖red} + 1 win {red‖blue}              |
|  6  | NC  | no contest ≡ stoppage: accidental injury or foul                   |
|  7  | DQ  | disqualification ≡ stoppage: flagrant fouls                        |
|  8  | RTD | corner retirement ≡ TKO: at break, fighter/corner refuses to go on |
|  9  | UDR | Unanimous Draw unanimous draw ≡ 3 draws + 0 {wins‖loss}            |
| 10  | MDR | majority draw ≡ 2 draws + win                                      |
| 11  | SDR | split draw ≡ 1 win + 1 loss + 1 draw                               |
| 12  | OTH | other                                                              |

## Variables
$+{blue_rank} = underdog ranking
$+{blue}      = contender / underdog
$+{class}     = 
$+{method}    = cause of stoppage
$+{red_rank}  = favourite ranking
$+{red}       = champion / favourite 
$+{round}     = ending round
$+{time}      = end time
$+{title}     = title fight

-------------------------------------------------

## Ideas, Feature Requests, & Future Development Path

- [Incremental and Iterative Software Development Process][5]

### Incremental Phases
	1. Increment Planning
	2. Specifications
	3. Development
	4. Validation
	- - -
	5. Repeat for each version

![](https://plan.io/images/blog/incremental-process.png?1592905298 "")

### Ideas for Variables
- []  amateur fights
- []  gyms/dojo
- []  Sensei &/or coach — see "fighter" tab and 
- []  belts & titles (UFC, other)
- []  all pro MMA fights
- []  diet (vegan, etc.)
- []  age
- []  weight
- []  ink
- []  ink coverage
- []  military service
- []  facial hair
- []  hair style

### Analytical Modelling Tools & Frameworks
- []  Monte Carlo simulation
- []  Regression analysis, testing, and validation
- []  Excel 
- []  Google Sheets + JavaScript . 
- []  [R for Statistical Computing][7], [][8], [][9]. "The "data industry" seems to favour the R programming language for statistical computing." R would be a heavy lift, but it would also open doors.
- []  Nevada State Athletic Commission data
- []  UFC JSON feeds

- []  https://infoinspired.com/google-docs/take-your-data-from-row-to-column-or-vice-verse-in-google-doc-spreadsheet/ "Take Your Data from Row to Column or Vice Verse in Google Doc Spreadsheet"
- []  https://blog.sheetgo.com/google-sheets-formulas/transpose-formula-google-sheets/ "How to use the TRANSPOSE Google Sheets formula - Sheetgo Blog"

***https://support.google.com/docs/answer/3093275?hl=en "ARRAYFORMULA - Docs Editors Help"***: "ARRAYFORMULA ⟶ Enables the display of values returned from an array formula into multiple rows and/or columns and the use of non-array functions with arrays."

#### Monte Carlo Simulation for Google Sheets

https://github.com/promptworks/montecarlo "promptworks/montecarlo: Generate Monte Carlo Distributions in Google Sheets"
https://raw.githubusercontent.com/promptworks/montecarlo/master/index.js "raw js code"
https://gsuite.google.com/marketplace/app/bp_simulator/1086928993551 "Business Process Simulator"
https://gsuite.google.com/marketplace/app/causal_scenarios/383280853562 "Causal"
https://www.causal.app/ "Causal - a clearer way to work with numbers"
https://gsuite.google.com/marketplace/app/risk_solver/309062064248 "Risk Solver"
https://gsuite.google.com/marketplace/app/sensitivity_macro/207775923633 "Sensitivity Macro"
https://gsuite.google.com/marketplace/app/remove_duplicates/347814268012 "Remove Duplicates"

https://pubsonline.informs.org/doi/pdf/10.1287/ited.1090.0027 "A Spreadsheet Scenario Analysis Technique That Integrates with Optimization and Simulation"


### Fields
## Fields ⟶ athlete__

1 = thumbnail = <div class="c-listing-athlete__thumbnail">
2 = text      = <div class="c-listing-athlete__text">
3 = nickname  = <span class="c-listing-athlete__nickname">
4 = name      = <span class="c-listing-athlete__name">
5 = title     = <span class="c-listing-athlete__title">
6 = record    = <span class="c-listing-athlete__record">
7 = bgimg     = <div class="c-listing-athlete__bgimg">

## Fields ⟶ facet-item__value
	### Status
		1 = Active
		2 = Not Fighting
		3 = Retired
		4 = Title Holder
		5 = Released
		6 = Hall of Fame
	### athletes_weight_class
		7 = Catchweight
		8 = Strawweight
		9 = Flyweight
		10 = Bantamweight
		11 = Featherweight
		12 = Lightweight
		13 = Welterweight
		14 = Middleweight
		15 = Light Heavyweight
		16 = Heavyweight
		17 = Women's Strawweight
		18 = Women's Flyweight
		19 = Women's Bantamweight
		20 = Women's Featherweight
	### athletes_fighting_style
		21 = MMA
		22 = Brazilian Jiu
		23 = Karate
		24 = Taekwondo
		25 = Wrestler
		26 = Grappler
		27 = Kung
		28 = Judo
		29 = Striker
		30 = Kickboxer
		31 = Wrestling
		32 = Muay Thai
		33 = Boxer
		34 = Jiu
		35 = Freestyle
		36 = Sambo
	### athletes_residence_country_code
		37 = Argentina
		38 = Australia
		39 = Austria
		40 = Belgium
		41 = Brazil
		42 = Bulgaria
		43 = Canada
		44 = China
		45 = Czechia
		46 = Denmark
		47 = Ecuador
		48 = Finland
		49 = France
		50 = Georgia
		51 = Germany
		52 = Guam
		53 = Iceland
		54 = India
		55 = Ireland
		56 = Italy
		57 = Japan
		58 = Kyrgyzstan
		59 = Lithuania
		60 = Mexico
		61 = Moldova
		62 = Mongolia
		63 = Morocco
		64 = Netherlands
		65 = New Zealand
		66 = Norway
		67 = Peru
		68 = Philippines
		69 = Poland
		70 = Romania
		71 = Russia
		72 = Serbia
		73 = Singapore
		74 = South Africa
		75 = South Korea
		76 = Spain
		77 = Suriname
		78 = Sweden
		79 = Switzerland
		80 = Thailand
		81 = Turkey
		82 = Ukraine
		83 = United Kingdom
		84 = United States
		85 = Uruguay
		86 = Uzbekistan








<!--- RESOURCES & SOURCES -->

[1]: https://en.wikipedia.org/wiki/Decisions_in_combat_sports "Decisions in combat sports"
[2]: https://github.com/google/re2/blob/master/doc/syntax.txt "Google Regular Expression syntax for re2"
[3]: https://www.ladbrokes.com.au/betting-info/ufc/weight-divisions/ "UFC Fighters, Weight Divisions & Classes"
[4]: https://en.wikipedia.org/wiki/List_of_UFC_bonus_award_recipients "List of UFC bonus award recipients"
[5]: https://plan.io/blog/software-development-process/ "Software Development Process: How to Pick The Process That’s Right For You"
[6]: https://towardsdatascience.com/r-statistical-programming-language-6adc8c0a6e3d "R - Statistical Programming Language - Towards Data Science"
[7]: https://www.coursera.org/learn/r-programming "R Programming"
[8]: https://www.r-project.org/ "R: The R Project for Statistical Computing"
[9]: https://www.r-project.org/about.html "R: What is R?"
[10]: https://www.codecademy.com/catalog/language/r "R Courses & Tutorials"
[11]: https://www.codecademy.com/catalog/subject/code-foundations "Code Foundations Courses & Tutorials"
[12]: https://www.codecademy.com/catalog/subject/data-science "Data Science Courses & Tutorials"
[13]: https://www.codecademy.com/catalog/subject/web-development "Web Development Courses & Tutorials"
[14]: https://www.codecademy.com/pricing "Pricing"
[15]: https://draftin.com/documents/596763?token=U5-BLZ_Jb-N-eMQMvWCfNVbOqRHFAayvIr56qryf67zMKkowS3rELL99R0q6IqGOaaptU47iuxdtelraTzNeaIA "Codecademy - Hidden Courses"
[16]: https://www.ufc.com/athletes/all "Athletes"
[17]: https://www.amazon.com/dp/0393324818 "Moneyball: The Art of Winning an Unfair Game"

[20200627.01]: https://docs.ansible.com/ansible/latest/reference_appendices/YAMLSyntax.html "YAML Syntax — Ansible Documentation"
[20200627.02]: http://www.yamllint.com/ "YAMLlint - The YAML Validator"
[20200627.03]: https://stackoverflow.com/questions/32991517/how-to-escape-colons-and-other-special-characters-in-a-yaml-string/41554348 "escaping - How to escape colons and other special characters in a YAML string? - Stack Overflow"
[20200627.04]: https://yaml.org/spec/1.2/spec.html#id2776092 "YAML Ain’t Markup Language (YAML™) Version 1.2"
[20200627.05]: https://yaml.org/spec/1.2/spec.html#id2788097 "YAML Ain’t Markup Language (YAML™) Version 1.2"
[20200627.06]: http://www.yamllint.com/ "YAMLlint - The YAML Validator"
[20200627.07]: https://github.com/valish/mma-api "valish/mma-api: MMA Fighter API in NodeJS"
[20200627.08]: https://www.tapology.com/ "Tapology"
[20200627.09]: https://www.tapology.com/rankings "Tapology MMA Rankings"
http://bert-toolkit.com/download-bert "BERT - Basic Excel R Toolkit (Win)"

<!--- RESOURCES & SOURCES -->

* * *
Tags: 




updated: *20201014_104327*
