---
date: '2025-03-07T18:00:00+01:00'
title: 'Effective software engineering'
---

These are some thought on how to excel as a developer within a team and company,
both during your core activities and beyond them. They explain how I try to approach 
my work and optimize job satisfaction for myself AND productivity for my team.

**Problem Solving**

Understanding underlying systems is important to building solid software.
This is true whether fixing a bug, making a new feature or optimizing performance.
That's why I will always dig until I have enough information to make a piece of code do exactly what I want.

Sometimes that means reading docker source code to find a bug in docker compose when just trying to deploy a simple container,
sometimes that might mean reading through comments on a GitHub issue to predict the direction an external project is going.
Taking the time to research and dig deeper gives me a better understanding of the technology I use.
It allows me to give informed arguments in future discussions and make better decisions.

**Optimizing effectively**

Performance is an important factor in any system, production application and dev tooling alike.
When optimizing performance, it is important to do so in areas where you can make the most impact.
I'd rather shave a minute off a CI pipeline than off an export process that's used once a month.
But making a high-volume page a tenth of a second faster might be even more important!

**Solve bugs once**

Bugs inevitably happen, but solving the same bug multiple times shouldn't.
My bugfixes are always accompanied by (plans for) tests or tooling to prevent it happening again.
Tests help prevent a regression within the same system, while some tools like linters can help prevent similar bugs in all systems.

**Be helpful**

Focus is important for anyone, especially engineers.
But so is helping others, and focus shouldn't detract from that.
Take the time to help a teammate with a question or review,
use a spare half hour to fix a small inconvenience for a customer,
and run a quick query to answer a question from sales.
These small actions improve effectiveness and morale while also improving the reputation of your team / company.

**More than full-stack**

To me, full stack means a lot more than just frontend and backend code.
I take pride in understanding the whole process:
From project planning and product vision to writing the code and tests and making a pull request.
Then building and containerizing the software and deploying it in a reliable and secure manner.
Beyond that ensuring the application is monitored for problems and performance and scaled correctly.

This means touching many processes and technologies, which might seem inefficient.
The better you understand all these parts however, the more effective you can communicate
with the topic experts within your team or company to fill in the gaps.

**Don't (try to) be a 10x developer**

The notorious 10x developer will deliver incredible results in the short term,
but hurt team progress and product stability in the long term.
Instead of sprinting only towards your own goals, focus some energy on your team.
Improve and build processes, tooling, and knowledge that increase the effectiveness of the entire team.

