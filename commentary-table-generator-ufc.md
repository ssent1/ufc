# UFC Commentary Table Generator

## DATA SOURCE -- watchwrestling.ai

- parse fighter names via <https://watchwrestling.ai>
- NB: listing format changes often, but the following regex seems to work most of the time.
- NB: in vim `\k` = keyword (`\K`, no digits), ~ `[A-Za-zŽžÀ-ÿ`]; ~ `\p{[L]etter}` Unicode PCRE2; more info:
    - <https://vimhelp.org/usr_27.txt.html>
    - <file:///Users/syd/Dropbox/nvalt-repo/manpages/vim/magic.md>

```viml
| 3 | 7 | 11                       | 38                             | 72                            | 103 | 109 | 115   |
| √ | @ | weight class             | winner                         | loser                         | by  | rnd | mm:ss |
| - | - | ------------------------ | ------------------------------ | ----------------------------- | --- | --- | ----- |

^(?:([\k'’ ]+):\s+)?([\k][\k'’. -]+)\s+vs\.?\s+([\k'’. -]+[\k'’. -])((\s+\|\s+)(.*))?
| √ | @ | $1$4|$2||$3|||||

" (?# vim regex )
:% s/\v^%(([\k'’ ]+):\s+)?([\k][\k'’. -]+)\s+vs\.?\s+([\k'’. -]+[\k'’. -])((\s+\|\s+)(.*))?/|√|@|\1\4|\2||\3|||||/
:% s/\v^%(([\k'’ ]+):\s+)?([\k][\k'’. -]+)\s+vs\.?\s+([\k'’. -]+[\k'’. -])((\s+\|\s+)(.*))?

" clear table entries
" FIXME %s/^\| \[x[^|]+\|[^|]+\|[^|]+\|[^|]+\|[^|]+\|[^|]+\|[^|]+\|[^|]+\|[^|]+\|[^|]+\|/| [ ] |   |   |   |   |   |   |   |   |   |/g

" grab video link from HTML
F12 > Sources > Page > Top > embed.php > www.m2list.com >
https://www.m2list.com/embed.php?datab=y&lister=none&mirror=pvp{query}&mainid={query}

" grab video link via Developer Tools Inspector
find: embed.php
grab: https://www.m3list.com/embed.php?datab=y&lister=none&mirror=pvp1&mainid=931630
```
## Table Generator

- [ ] 1. `cmd+C` [{fight_card_bonuses}][1], paste via `ssq`; replaces single curly quotes
- [ ] 2. `cmd+C` [{numbered_event_name}][1]

```regexp - add Markdown headers
^(?<card>(?:Early )?\p{L}+ card.*|Bonus awards.*)
\n#### $1, _numbered_event_name_\n
```

- [ ] 3. Shorten weight class name

```regexp - abbv
Women['’]s 
♀
```

- [ ] 4. Insert table headers

```markdown - table headers & column index numbers
| 3 | 7 | 11                       | 38                             | 72                            | 103 | 109 | 115   |
| √ | @ | weight class             | winner                         | loser                         | by  | rnd | mm:ss |
| - | - | ------------------------ | ------------------------------ | ----------------------------- | --- | --- | ----- |
```

- [ ] 5. Convert TSV values to Markdown table

```regexp - tsv2md
(?<wt>(?:.*weight)(?: \(\d{2,3}(?:\.\d+)? (?:lb|kg)\))?)\t(?<red>.*)\t(?<out>def|vs).\t(?<blue>.*)\t(?<by>Decision|Draw|DQ|No Contest|Submission|[TKO]+).*\t(?<rnd>\d)\t(?<time>[0-5]:[0-5][0-9])\t(?<notes>.*)
|  [] | $1 |$2 | $3 | $4 |$5 | $6 | $7 | $8 |<>    |
```

- [ ] 6. Format table
  - [ ] `cmd+K M, Markdown`, confirm editor is in Markdown mode
  - [ ] `S+[+F` run Markdown formatter

- [ ] 7. footnotes

```regexp - update footnotes
\[([a-t])\] 

(?# `cmd+P`, `: `) 

\[([a-t])\] 
[^$1] 
```

- [ ] 8. Delete Wikipedia reference numbers

```regexp
\[\d+\]
```

- [ ] 9. Add bullets to FotN & PotN

```regexp
(Fight of the Night: .*\n)(Performance of the Night: .*)
- $1- $2
```

### Example Table

```md
#### Main Card, {numbered_event_name}

| [x] | weight class |     | ->   |     | by  | rnd | time | ?   | video |
| --- | ------------ | --- | --- | --- | --- | --- | ---- | --- | ----- |
| []  |              |     |     |     |     |     |      |     | <>    |
| []  |              |     |     |     |     |     |      |     | <>    |
| []  |              |     |     |     |     |     |      |     | <>    |
| []  |              |     |     |     |     |     |      |     | <>    |
| []  |              |     |     |     |     |     |      |     | <>    |
| []  |              |     |     |     |     |     |      |     | <>    |
| []  |              |     |     |     |     |     |      |     | <>    |
| []  |              |     |     |     |     |     |      |     | <>    |

#### Preliminary Card, {numbered_event_name}

| [x] | weight class |     | ->   |     | by  | rnd | time | ?   | video |
| --- | ------------ | --- | --- | --- | --- | --- | ---- | --- | ----- |
| []  |              |     |     |     |     |     |      |     | <>    |
| []  |              |     |     |     |     |     |      |     | <>    |
| []  |              |     |     |     |     |     |      |     | <>    |
| []  |              |     |     |     |     |     |      |     | <>    |
| []  |              |     |     |     |     |     |      |     | <>    |
| []  |              |     |     |     |     |     |      |     | <>    |
| []  |              |     |     |     |     |     |      |     | <>    |
| []  |              |     |     |     |     |     |      |     | <>    |

#### Bonus awards, {numbered_event_name}

The following fighters received $50,000 bonuses.

- Fight of the Night: No bonus awarded.
- Performance of the Night: Derrick Lewis, Chris Daukaus, Tom Aspinall and Aiemann Zahabi
```

### Comments

#### Comments In Free-Spacing Mode

- `(?x)`   -> enable free-spacing _outside_ character classes
- `(?xx)`  -> enable free-spacing _inside and outside_ character classes
- `(?-x)`  -> disable free-spacing
- `(?-xx)` -> disable free-spacing

NB: In free-spacing mode, `#` starts comments. Comments run until the next newline character `\n`.

#### Comments Without Free-Spacing

- syntax: `(?# comment)`

NB: In non-free-spacing mode, `(?#` starts a comment. Comments run until the first closing parenthesis (`)`).

## Notes & References

Tags: ufc, bkfc, boxing, bare knuckle fighting

^ 2021-03-24T18:15:29-0500\
% 2022-03-15T23:03:21-0400

<!-- SOURCES & RESOURCES -->

[1]: https://en.wikipedia.org/wiki/List_of_UFC_events "List of UFC events - Wikipedia"
[2]: https://watchwrestling.in/sports/ufc/ "UFC Archives"
[3]: https://www.fullfight.video/ "MMAshare Full Fights"
[4]: https://www.regular-expressions.info/freespacing.html "Make Your Regular Expressions Easier to Read"

