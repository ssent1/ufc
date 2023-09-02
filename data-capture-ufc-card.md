# Capture UFC Card Data

## Clean Data

```vim
" trim 'header' and 'footer'
<div class="c-listing-fight__corner-body--red">([\S\s]+)<div class="l-container--bg-grey">

" trim excess whitespace
:%s/\v^%(\s+)(.*)|^(.*)\s+$/\1\2/

" Escape Characters
&#039; " apostrophe `'`
```

## Capture Data

```vim
<(?<div>div) (?<class>class)="js-listing-fight__corner-rank c-listing-fight__(?:red-|blue-)?corner-rank--mobile(?: c-listing-fight__corner-rank--champion)?">(?:<\/\1>)?(?<red_rank>[\w#]+)?<\/\1><\/\1>(?:<\1 \2="c-listing-fight__details"><\1 \2="c-listing-fight__banner--live hidden">[\w ]++<\/\1><\1 \2="c-listing-fight__awards"><\/\1>)?<\1 \2="c-listing-fight__\2">(?<divi>(?:Women's )?[\w]++) ?(?<title> Title)? Bout<\/\1><\1 \2="c-listing-fight__detail-corner-name">(?<red>[\w ']++)<\/\1><\1 \2="c-listing-fight__vs"><span \2="e-\1ider"><span \2="e-\1ider__border"><span \2="e-\1ider__border-line--start grey-light"><\/span><span \2="e-\1ider__border-text">vs<\/span><span \2="e-\1ider__border-line--end grey-light"><\/span><\/span><\/span><\/\1><\1 \2="c-listing-fight__detail-corner-name">(?<blue>[\w ']++)<\/\1><\1 \2="js-listing-fight__results c-listing-fight__results--desktop (?: hidden)?"><\1 \2="c-listing-fight__result"><\1 \2="c-listing-fight__result-label">(Round)<\/\1><\1 \2="c-listing-fight__result-text \8">(?<round>\d)?<\/\1><\/\1><\1 \2="c-listing-fight__result"><\1 \2="c-listing-fight__result-label">(?<ttime>Time)<\/\1><\1 \2="c-listing-fight__result-text \g{ttime}" data-time-fid="(?:[0-9]{4})?">(?<time>[0-5]:[0-9]{2})?<\/\1><\/\1><\1 \2="c-listing-fight__result"><\1 \2="c-listing-fight__result-label">(?<meth>Method)<\/\1><\1 \2="c-listing-fight__result-text \g{meth}">(?<method>DEC|KO\/TKO|SUB)?<\/\1><\/\1><\/\1><\/\1><\1 \2="c-listing-fight__corner--(?<corner>blue|red)?"><\1 \2="c-listing-fight__corner-image--\g{corner}"><\1 \2="layout layout--onecol"><\1 +\2="layout__region layout__region--content"><img src="(?:https{0,1}:\/{2}\S*\w|\S*\w)" width="\d+" height="\d+"(?:[\w ="-]+)?\/><\/\1><\/\1><\/\1><\1 \2="c-listing-fight__corner-body--\g{corner}"><\1 \2="c-listing-fight__outcome-wrapper +"><\1 \2="c-listing-fight__outcome"><\/\1><\/\1><\1 \2="js-listing-fight__corner-rank c-listing-fight__corner-rank">(?:<\/\1>)?(?:<\1 \2="c-listing-fight__corner-name">)?(?:<span>)?(?<blue_rank>[\w#]+)?(?:<span )?(?:<\/span>)?
```

<!-- Doesn't grab two non-ranked fighters correctly -->

## Variables

```vim
$+{blue_rank} " underdog ranking
$+{blue}      " contender / underdog
$+{class}     "
$+{method}    " cause of stoppage
$+{red_rank}  " favourite ranking
$+{red}       " champion / favourite
$+{round}     " ending round
$+{time}      " end time
$+{title}     " title fight
```

## Replace

```vim
*$+{red}* ($+{red_rank}) v. *$+{blue}* ($+{blue_rank}) @ $+{divi}$+{title}
```

_UFC 251_ 
Sun, Jul 12 / 6:00 PM EDT 
UFC Fight Island, Abu Dhabi United Arab Emirates

- _Kamaru Usman_ (C) v. _Gilbert Burns_ (#1) @ Welterweight Title
- _Alexander Volkanovski_ (C) v. _Max Holloway_ (#1) @ Featherweight Title
- _Petr Yan_ (#3) v. _Jose Aldo_ (#6) @ Bantamweight Title
- _Jessica Andrade_ (#1) v. _Rose Namajunas_ (#2) @ Women's Strawweight
- _Amanda Ribas_ (#15) v. _Paige VanZant_ @ Women's Flyweight

## TESTING UFC 251

- _Kamaru Usman_ (C) v. _Gilbert Burns_ (#1) @ Welterweight Title
- _Alexander Volkanovski_ (C) v. _Max Holloway_ (#1) @ Featherweight Title
- _Petr Yan_ (#3) v. _Jose Aldo_ (#6) @ Bantamweight Title
- _Jessica Andrade_ (#1) v. _Rose Namajunas_ (#2) @ Women's Strawweight
- _Amanda Ribas_ (#15) v. _Paige VanZant_ () @ Women's Flyweight

## BUG TESTING

<!-- did not work. did not capture any data -->

### 3 Ways to Fix the CORS Error — and How the Access-Control-Allow-Origin Header Works

- Fix one: install the Allow-Control-Allow-Origin plugin
- Fix two: send your request to a proxy
- Fix three: build your own proxy

### Resources

- [ ] [Reason: CORS request did not succeed](https://developer.mozilla.org/en-US/docs/Web/HTTP/CORS/Errors/CORSDidNotSucceed)
- [ ] [Reason: CORS header 'Access-Control-Allow-Origin' missing](https://developer.mozilla.org/en-US/docs/Web/HTTP/CORS/Errors/CORSMissingAllowOrigin)
- [ ] [Working with the Fetch API](https://developers.google.com/web/ilt/pwa/working-with-the-fetch-api)
- [ ] [Fetch: Cross-Origin Requests](https://javascript.info/fetch-crossorigin)
- [ ] [Access Control](https://medium.com/@dtkatz/3-ways-to-fix-the-cors-error-and-how-access-control-allow-origin-works-d97d55946d9)
- [ ] [No 'Access-Control-Allow-Origin' header is present on the requested resource.](https://support.google.com/webmasters/thread/24208906?hl=en)
- [ ] [Cross-Origin Resource Sharing: Access-Control-Allow-Origin](https://wanago.io/2018/11/05/cors-cross-origin-resource-sharing/)
- [ ] [Cross-Origin Resource Sharing (CORS)](https://web.dev/cross-origin-resource-sharing/)
- [ ] [How to make a cross domain request in JavaScript using CORS](https://www.moxio.com/blog/12/how-to-make-a-cross-domain-request-in-javascript-using-cors)
- [ ] [CORS Enabled](https://www.w3.org/wiki/CORS_Enabled)

- - -
<!--sources-->

[1]: https://www.ufc.com/event/ufc-250 "UFC 250"
[2]: https://www.ufc.com/event/ufc-251 "UFC 251"
[3]: https://dvk92099qvr17.cloudfront.net/V1/971/Fnt.json

Tags:

^ 2020-06-19T08:02:04-0500\
% 2023-07-09T19:49:42-0400
