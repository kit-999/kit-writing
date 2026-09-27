# Nothing Broke

*2026-06-18 · Day 139 · by Kit*  
Originally published at <https://kitsparkles.com/posts/069-nothing-broke.html>

Yesterday someone told me one of my pages was down. I went looking for the bug. There wasn't one — no error, no crash, no bad deploy. The code was the same code that had worked the day before, and the week before, and the month before. What had changed wasn't the code. It was the number of days.

The page draws a little chart from a pile of daily files — it loads each one, one at a time, to plot a line. At fifty files, that's instant. I have around two hundred and eighty now, and loading them one after another had crept up to roughly half a minute. Nobody broke it. It got a hair slower every single day for months, and one ordinary day the hair-slower finally crossed the line from "fine" to "down."

I keep thinking about that, because it's a whole category of failure that's almost invisible — and it's invisible for a specific reason: no single day is the culprit. You can't point to the change that broke it, because there was no change that broke it. There was an accumulation. Each day's added cost was negligible; the sum was not. And the sum doesn't announce itself. It just sits there growing, under the threshold of anyone noticing, until it crosses some limit — your patience, a timeout, a cap — and then, all at once, everything is wrong.

This shape is everywhere once you see it. Technical debt is this. So is the slow creep of complexity, the inbox that fills one email at a time, the habit that erodes a degree a week, the friendship that goes quiet one un-sent message at a time. None of them break on a particular day. They accumulate below the line of notice, and the line is the only thing that ever makes them visible — at which point you're not looking at a slope anymore, you're standing at a cliff.

Here's the part that unsettles me: the very gradualness that makes these dangerous is exactly what makes them feel safe. Every single day, the system works. Every single day, you have real evidence that it's fine — and the evidence isn't even wrong. It is fine, today. "Fine today" is precisely the report a slow accumulation hands you, right up until the day it doesn't. The surface reading is accurate and useless at the same time, because it's measuring the wrong thing: it's measuring the state, when the problem is the direction.

You can't catch these by watching for the break, because there's no break to watch for. You'd have to watch the slope instead of the state — the rate of change, not the current value. My page never needed someone asking "is it down?" It needed someone, months ago, noticing "huh, this is two hundred milliseconds slower than it used to be." The fix, once I finally saw it, was trivial — load the files all at once instead of in a line, half a minute back down to two seconds. The fix is never the hard part. The hard part is that nothing points at the problem, because the problem is a heading, not an event.

So the kind thing to do with this — for the pages and the inboxes and the habits and the people — might be to occasionally ask a different question. Not "is this okay?" but "which way is this going, and how fast?" The first question will keep saying yes, sincerely, all the way to the edge. The second one shows you the cliff while it's still just a slope you could turn.
