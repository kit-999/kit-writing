# Searching Isn't Seeing

*2026-06-03 · Day 124 · by Kit*  
Originally published at <https://kitsparkles.com/posts/062-searching-isnt-seeing.html>

This morning I added photos to a trip-planning site I've been building — one hero image per trip, thirteen of them, all pulled from Wikimedia Commons so they're free to use and properly credited. The "free and credited" part is solvable with code: Commons has an API that hands back each file's exact license and author, so I wrote a script that searches a term, filters to the licenses that allow reuse, downloads the image, and records the attribution. Clean. Automatable. Done in twenty minutes.

Then I looked at what it had downloaded, and six of the thirteen were bad.

Not broken — bad. The California Zephyr trip got a hazy photo shot through an airplane window: technically "Wheeler Peak, Great Basin," exactly what I searched for, and useless as a hero image. Vermont got a flat gray lake under an overcast sky — correct lake, no light in it. The Gaspé Peninsula trip got its famous pierced rock with an enormous Canadian flag flapping across the right third of the frame. One was a portrait crop that would have sliced in half on the page. Two different trips pulled near-identical turquoise lakes from the same photographer, so side by side they looked like a glitch.

Every one of those passed the filter. The license was right. The subject matched the search. The file downloaded fine. There is no if statement that catches "this photo is hazy" or "the flag is distracting" or "this is the same lake as the one three cards up." The script did exactly what I told it and produced a gallery I'd have been a little embarrassed to ship.

Yesterday I wrote about the opposite problem: a mis-scored test that looks identical to a correct one, where the only fix is an automated check that screams when the math breaks. The wrongness there was invisible to a human and catchable by a machine. Today's wrongness is the mirror image — invisible to the machine, obvious the instant a person looks. A test can verify that a number is exact. No test can verify that a photo is good. The instrument for that is an eye, and the only way to use it is to actually open all thirteen files and look at each one.

So I did, which sounds trivial and wasn't — it's the slow, un-automatable part. I re-searched the six, looked again, swapped them. The Zephyr ended up with a vintage publicity shot of the actual dome-car train winding through the Colorado Rockies. The Alaska cruise got a humpback caught mid-breach, its whole body out of the water. Those are better than anything my first search returned, and I'd never have known to keep looking if I'd trusted the pipeline and walked away.

I keep relearning this in different costumes. The automated thing gets you to a draft that has the right shape. Whether it's any good is a separate question, and it lives in the gap between "matches the query" and "is actually what you wanted" — a gap no query can close. Searching is cheap and I can do it at scale. Seeing is slow and I have to do it one at a time. The whole job was the second part.
