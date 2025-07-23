---
title: Build Next js app with Tinybird
author: Alejandro de Cora
date: 2025-07-22
tag: [Tinybird, Next.js]
category: tinybird
layout: post
---

After my initial foray into Tinybird, I decided to continue exploring by building a Next.js app that consumes Tinybird endpoints. I based this project on the [Build a data-intensive Next.js app with Tinybird and Cursor][1] demo.

<!--more-->

I created a [movie app][2] (repo linked for those who want to test it locally), using Copilot in agent mode with Claude Sonnet 4.

![Copilot Agent working]({{ '/resource/day_one_and_a_half/next-movie-app.png' | relative_url }})

I then used the `--prompt` option with the `tb create` command to generate the Tinybird project structure.

![Tinybird CLI working]({{ '/resource/day_one_and_a_half/tinybird-movie-app.png' | relative_url }})

Everything was pretty straightforward so far.  The agents generated good code, requiring only minor tweaks. 

I could have passed the `.cursorrules` file directly to Copilot as context, but I decided to translate these rules into GitHub instructions instead.

![Cursor rules to Copilot instructions]({{ '/resource/day_one_and_a_half/cursor-to-copilot.png' | relative_url }})

This worked surprisingly well!  When I asked Copilot about the context, it quickly found the `rules.md` file under the `.github/instructions` folder.

![Read Copilot instructions]({{ '/resource/day_one_and_a_half/read-copilot-instructions.png' | relative_url }})

With the Tinybird context established, I asked Copilot to connect the Next.js app to the Tinybird endpoints.  Again, it performed admirably, requiring only a few small fixes.

> Here's the prompt I gave to Copilot:
>
> "I've created a Tinybird endpoint called `top_ten_movies`. Update the movie application to fetch data from this endpoint. You'll need to create `.env` files to store the Tinybird host URL and token.  You'll also need to pass `start_year`, `end_year`, and `movie_type` from the filter elements to the Tinybird endpoint."

Finally, I mocked some data using the following command:

```bash
$ tb mock movies --rows 1000 --prompt "Generate movies, movie id must be unique with release_year between 1970 and 2025, type be tween MOVIE or SHOW and score between 1 and 10 with 2 decimals and score should have a median around 6.00"
```

Here's the final app in action:

![Movie App]({{ '/resource/day_one_and_a_half/movies-app.gif' | relative_url }})

./Conclusion
------------

* Once again, the `tb dev` playground proved to be a fantastic tool.
* Setting up endpoints with query parameters was a breeze thanks to Tinybird's dynamic querying (starting a query with `%`).
* As always, the more specific you are when prompting your AI agent, the better the results.  In my first attempt at mocking data, I didn't specify the score range or unique IDs, which led to some… interesting movie scores.


[1]: https://www.youtube.com/watch?v=oe__vyW6NtQ
[2]: https://github.com/adecora/Next-Js-app-with-Tinybird