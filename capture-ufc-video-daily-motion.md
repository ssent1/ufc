# Capture UFC Video

> 2023-08-27: <https://watchwrestling.store/sport/ufc/> is the best domain.

# Contents

- [Capture UFC Video](#capture-ufc-video)
- [Contents](#contents)
   - [Dood HD](#dood-hd)
   - [NetU](#netu)
   - [Dailymotion HD](#dailymotion-hd)
   - [PvP HD](#pvp-hd)
   - [Parse Daily Motion URLs](#parse-daily-motion-urls)

## Dood HD

Format: Prelims Part 1 Part 2 Part 3
Base URL: <https://dengerdj.net/cgi/do.php?v=cxhnajk7u1zv>
Source: <https://dood.yt/d/cxhnajk7u1zv>

N.B. The video player has limited playback functionality.

## NetU

Format: Prelims Part 1 Part 2 Part 3
Base URL: <https://dengerdj.net/cgi/wa.php?v=7L95z6rpBbsY>

N.B. Overlay play button. Playback speed flaky.

## Dailymotion HD

> www.android-devs.top refused to connect.

Format: Prelims Part 1 Part 2 Part 3

<https://www.m2list.com/2023update/embed.php?mirror=Mirrorid&mainid=20230826UPR> ==> This page will work only inside embed page.
<https://www.m2list.com/2023update/embed.php?mirror=fscrep_2&mainid=20230826UPR> ==> This page will work only inside embed page.
<https://www.dailymotion.com/embed/20230826UPR/> ==> Page not found

## PvP HD

> www.android-devs.top refused to connect.

Format: Prelims Part 1 Part 2 Part 3

## Parse Daily Motion URLs

1. Go to `https://watchwrestling.in/watch-ufc-{event-desc}`.
2. <LeftMouse> on video link; { "Early Prelim", "Prelim", "Part <n>" }, opens in a new tab.
3. <RightMouse> video, <LeftMouse> `View Frame Source`; opens in a new tab.
4. Copy link from Location Bar; <⌘ L>, <⌘ C>. See example below.
5. Paste in editor; <⌘ P> 
6. Run following regex to grab video.

```vim
:s/\v%(view-source:)?(https:\/\/www.dailymotion.com\/embed\/video\/\w{19}).*/\1/

" raw video link, parsed link
view-source:https://www.dailymotion.com/embed/video/k20YyyxkhotpMWzhnQJ?logo=0&autoPlay=0&quality=720&playlist=x79ac2
https://www.dailymotion.com/embed/video/[\w{19}]
https://www.dailymotion.com/embed/video/k20YyyxkhotpMWzhnQJ
```

- - -
<!-- sources -->

[1]: https://watchwrestling.in/sports/ufc/ "UFC Archives"

```vim
x  " watched
⌫  " not available
/  " in progress
```

Tags: ufc

^ 2020-10-05T21:20:25-0400\
% 2023-08-27T22:34:28-0400
