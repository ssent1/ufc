# Betting Payout Calculators

# Contents

- [Betting Payout Calculators](#betting-payout-calculators)
- [Contents](#contents)
    - [UFC/MMA Betting Payout Calculator](#ufcmma-betting-payout-calculator)
    - [Definitions and Assumptions](#definitions-and-assumptions)
    - [Future Projects](#future-projects)

## UFC/MMA Betting Payout Calculator

```vim
# VARIABLES
bet  = $100                   // @risk

# 🏆 FAVOURITE (-###)
odds = -230%                  // US odds
dec  = 1-(100/odds)           // decomal
pays = bet*dec                // payout
π    = pays-bet               // profit
pfav = (odds/(odds-100)*100)% // implied
rfav = ((π/bet)*100)%         // ROI

# 🐶 UNDERDOG (+###)
odds = +190%                  // US odds
dec  = 1+odds                 // decimal
pays = bet*dec                // payout
π    = pays-bet               // profit
pdog = (10k/(odds+100))%      // implied
rdog = ((π/bet)*100)%         // ROI

Pr   = pfav+pdog               // joint
vig  = Pr-100%                 // fee

# US odds ≡ American odds &/or moneyline odds
# @risk ≡ bet amount or risk capital
```

## Definitions and Assumptions

payout ≡ FV = PV (1 + r/m) ^ mt
Where:
FV - the future value of the investment
PV - the initial balance (the present value of the investment)
r - the annual interest rate (in decimal)
m - the number of times the interest is compounded per year (compounding frequency)⁎
t - the numbers of years the money is invested for.
⁎if m > 1, then r ≡ CAGR (compound annual growth rate)

For calculating betting odds,
Let
m = 1 & t =1
∴ FV = PV (1 + r/m) ^ mt, where r/m = CAGR
FV = PV (1 + r)

odds = r ≡ CAGR
Let
PV = $1
∴ decimal odds ≡ (1 + CAGR)

bet amount: bet = PV = $n

payout = FV = PV (1 + r)
profit = payout - bet

implied probability ≡ odds: implied

A -140 favorite has about a 58.34% chance of winning, while a +120 underdog has a 45.45% chance.
58.34% + 45.45% = 103.79% ∵ vig = 3.79%

For positive numbers (underdogs):

Pᵢ = 100 / (odds + 100) * 100
Where:
odds >= 100

∴ Pᵢ = 10000 / (odds +100)

## Future Projects

- calculate and compare odds
- scrape fighter data
- compile fight PPV and revenue metrics

- - -
<!-- sources -->

[1]: https://actionnetwork.com/betting-calculators/betting-odds-calculator "Betting Odds Calculator & Converter"
[2]: https://en.wikipedia.org/wiki/Vigorish "Vigorish"
[3]: https://mathpapa.com/equation-solver/ "Equation Solver"
[4]: https://omnicalculator.com/finance/cagr?advanced=1&v= "CAGR Calculator"
[5]: https://omnicalculator.com/finance/roi#roe-vs-roi "ROI Calculator"
[6]: https://www.calculator.net/probability-calculator.html "Probability Calculator"
[7]: https://www.wikihow.com/Calculate-Probability "4 Ways to Calculate Probability"
[8]: https://www.sportsinsights.com/how-to-bet-on-sports/calculating-sports-betting-roi/ "Calculating Betting ROI"
[9]: https://www.playcanada.com/sports-betting/moneyline-vs-spread/ "Moneyline vs. Spread Betting"
[10]: https://news.sportsinteraction.com/guide/moneyline-betting-explained "Moneyline Betting Explained"

Tags: ufc, mma, betting, odds, calculator 

^ 2020-06-15T14:35:34-0500\
% 2023-09-02T15:49:07-0400
