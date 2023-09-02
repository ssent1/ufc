# Betting Odds/Payout Calculator

"▶︎Bet amount◀︎" bet = $100 = $100  
# 👍FAVOURITE — Negative Odds (-n)  
"▶︎american odds◀︎" odds = -230 in percent = -230 %  
"⚙︎decimal odds" dec_odds = 1 - (100 / odds) = 1.435  
"payout" payout = bet * dec_odds = $143.478  
"profit" π = payout - bet     = $43.478  
"implied odds" p₋ = ((odds/(odds - 100))*100) in percent = 69.697 %  
"return on bet" rob₋ = ((π/bet)*100) in percent = 43.478 %  

# 👎UNDERDOG — Positive Odds (+n)  
"▶︎american odds◀︎" odds = +190 in percent = 190 %  
"⚙︎decimal odds" dec_odds = 1 + odds = 2.9  
"payout" payout = bet * dec_odds = $290  
"profit" π = payout - bet     = $190  
"implied odds" p₊ = (10000 / (odds + 100)) in percent = 34.483 %  
"return on bet" rob₊ = ((π/bet)*100) in percent = 190 %  

"joint probability" P = p₊ + p₋ = 104.18 %  
"bookmaker's fee" vig = P - 100% = 4.18 %  

## Definitions and Assumptions  

payout ≡ FV = PV (1 + r/m) ^ mt  
Where:  
FV - the future value of the investment  
PV - the initial balance (the present value of the investment)  
r  - the annual interest rate (in decimal)  
m  - the number of times the interest is compounded per year (compounding frequency)⁎  
t  - the numbers of years the money is invested for.  
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

implied probability ≡ implied odds  

A -140 favorite has about a 58.34% chance of winning, while a +120 underdog has a 45.45% chance.  
58.34% + 45.45% = 103.79% ∵ vig = 3.79%  

For positive numbers (underdogs):  

Pᵢ = 100 / (odds + 100) * 100  
Where:  
odds >= 100  

∴ Pᵢ = 10000 / (odds +100)  

## Future Projects  
- calculate & compare odds  
- scrape fighter data  
- compile fight PPV & revenue metrics  

## Notes & References

Tags: ufc, bkfc, boxing, bare knuckle fighting

^ 2019-03-04T17:44:32-0500\
% 2022-04-05T15:00:12-0400

<!-- SOURCES & RESOURCES -->

[1]: https://actionnetwork.com/betting-calculators/betting-odds-calculator "Betting Odds Calculator & Converter"
[2]: https://en.wikipedia.org/wiki/Vigorish "Vigorish"
[3]: https://mathpapa.com/equation-solver/ "Equation Solver"
[4]: https://omnicalculator.com/finance/cagr?advanced=1&v= "CAGR Calculator"
[5]: https://omnicalculator.com/finance/roi#roe-vs-roi "ROI Calculator"
[6]: https://www.calculator.net/probability-calculator.html "Probability Calculator"
[7]: https://www.wikihow.com/Calculate-Probability "4 Ways to Calculate Probability"

