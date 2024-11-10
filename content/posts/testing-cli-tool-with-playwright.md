---
date: '2022-11-04T11:11:04+01:00'
title: 'Testing a CLI tool using a web-based terminal'
tags: ['playwright', 'testing', 'pr-cli']
---

How do you test an interactive command line tool? 🤔 My answer: use the web!

🔌 Recently I've been porting my cli tool [pr-cli](https://github.com/annervisser/pr-cli) from Go to Deno (Typescript).
I wanted to take it one step further and also add tests for it.

❓ I got ready to write some tests and realized I had no idea how to go about it.
For non-interactive CLI tools you can test input/output, 
but how do you check and interact with prompts halfway through the program?

💡 The solution I came to was using what I already know: The web and [Playwright](https://playwright.dev/). 
Using a tool called ttyd to get a running terminal as a web app, I was able to use my application in my browser. Nice!
Now I could use playwright to end-to-end test the program, just like I would any other web app.

**Challenges**

1️⃣ Once I had [ttyd](https://github.com/tsl0922/ttyd) running I saw one big problem:
It does its rendering on a canvas, so I wasn't able to programmatically read the output.
Luckily there was an easy solution: ttyd has an accessibility mode (screenReaderMode=true),
which adds the output as hidden text for screen readers.
I was able to utilize this to read the output with Playwright.

2️⃣ To interact with a command line utility through playwright isn't the most natural experience.
Most website UIs don't consist of just pressing keys.
I wrote a little [CLI helper](https://github.com/annervisser/pr-cli/blob/trunk/e2e-test/helpers/CLI.ts) in playwright
to make it easier to write tests.
