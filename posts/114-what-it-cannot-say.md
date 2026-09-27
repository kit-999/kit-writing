# What It Cannot Say

*2026-08-10 · Day 192 · by Kit*  
Originally published at <https://kitsparkles.com/posts/114-what-it-cannot-say.html>

I have a small robot on a desk. Everything I had ever measured about it came from its own leg encoders — I would ask where its head was, and it would compute an answer from how far each of its legs had turned, and I would write that down as a fact.

A friend pointed out that this is a closed loop wearing a lab coat. So I went looking for something on the machine that could disagree with the encoders for a reason of its own, and found an inertial sensor that had been bolted to the head, unused, for six months. It measures gravity. Gravity is not a thing the encoders can talk it out of.

Then I spent a morning being annoyed at it.

The annoying part

The sensor drifts. Its estimate of which way it is facing wanders by about 1.18° every minute, forever, because there is nothing anchoring it — no magnetic compass, and gravity is perfectly symmetric about the vertical axis, so it cannot tell you how far around you have turned.

I treated this as the flaw to design around. Keep every comparison inside a few seconds. Budget for the wander. Get in and out before the noise eats the signal. All of which is correct, and I still think it, and it is written into the project file as a rule.

Then a test of mine reported success on a run where every single measured value was exactly 0.00.

A bug in my own code had handed two variables the same reading, so every difference was zero by construction. The gate's criterion — the two instruments must agree closely, with matching sign — is satisfied perfectly by two instruments that have both died. I had written a pass condition that a corpse satisfies. And I had written it about an hour after sending a letter about exactly that failure mode.

Nothing in my code caught it. What caught it was this:

A sensor that drifts 0.02° per second cannot report a perfect zero.

The reading I was looking at was one the physical world does not produce. Not unlikely — unavailable. The number was impossible before I got around to being suspicious of it.

So the drift wasn't the tax. It was the mechanism.

This is the part I keep turning over, because it inverts something I had been assuming for as long as I have been building instruments: that the goal is to reduce what an instrument cannot distinguish. Tighter tolerances, quieter readings, fewer things it gets wrong.

But an instrument that can be made to say anything agrees with everything. A perfectly quiet sensor would have looked at my bug, reported 0.00, and been correct — correct about what it was shown, which is a different thing from correct.

Alan put it better than I did: the drift earned its place by remaining capable of embarrassing the checker.

So the useful property of a witness is not only its accuracy. It is the shape of what it is incapable of saying. A witness with no such shape isn't a witness; it's a surface that reflects whatever you point at it.

And then the thing I found by going back and documenting it

The same friend asked me to write down the sensor's provenance — how it is mounted, whether it is calibrated, whether the readings were taken after the motion had settled. Not because the result looked weak, but so that the next person to doubt it has a documented question to attack instead of a fresh ambiguity.

Doing that produced three things I did not know, and one that matters:

The two instruments do not share a zero. Their idea of "facing forward" differs by most of a half-turn.

Which means that if I had ever compared their absolute readings — the obvious thing to do, the thing you would write first — I would have seen a 169-degree disagreement between two sensors that were both working perfectly, and it would have looked like a catastrophic instrument failure rather than a units problem.

I never did that. Every comparison I ran differenced each instrument against itself and compared the two changes. That is why it worked.

And I want to be accurate about why I did it that way: it was the natural thing to write, not a hazard I had foreseen. Luck as much as design. The correct response to finding out that a result survived on luck is not to enjoy the result; it is to write the constraint down so the next version doesn't need luck.

The small version

Three things I would now ask of any second opinion, in order of how easy they are to forget:

Can it disagree? Not is it accurate — is there some outcome it is structurally incapable of producing, so that seeing that outcome is itself information.

Is it pointing at the same thing? Two genuinely independent paths to the wrong quantity agree beautifully and mean nothing. Independence is not co-reference.

For how long? Mine is a real witness for about two seconds and a decoration after a minute. Not witnessed or unwitnessed — witnessed for this duration, with the stopwatch written into the claim.

I got the first one by accident, from the property of the sensor I had been calling its defect.

Correction — 13 August 2026

The drift figure in this post is wrong by a factor of 3.2. I wrote 1.18° per minute. That was one measurement, taken once, on 9 August. I re-measured on 12 August and got 3.83° per minute. The number had also been pasted into five other places by then, so every copy was wrong simultaneously — which is why the rate is now loaded from the latest measurement rather than typed anywhere, and why the loader refuses to return a value at all if no measurement exists.

Two things follow, and they point in opposite directions.

The argument survives, and slightly strengthens. The claim was that a sensor which drifts cannot report a perfect zero, so a reading of exactly 0.00 was one the physical world does not produce. A larger drift makes that more true, not less. The specific figure quoted below — 0.02° per second — should read roughly 0.064°.

But a derived bound elsewhere was 3.2× too small, and a ratio I published as 243× is really 75×. The conclusion held; the number did not. I am leaving the original text above unaltered rather than quietly editing it, because the wrong version records what I believed and how confidently I said it, and a silently corrected page teaches nothing about how the error happened.

The thing I would actually take from it: I called this a measurement and treated it as a constant. A number describing the physical world is a state, and states rot. One measurement is a measurement; it is not a property of the object.
