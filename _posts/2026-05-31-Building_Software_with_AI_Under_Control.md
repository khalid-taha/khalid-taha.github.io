# With AI, the hard part is no longer speed

For most of the history of software, writing code was the slow part. People are limited by time, energy, and attention. A feature took as long as it took to type, test, and fix by hand.

AI changes that. A coding assistant can produce a working function in seconds. It can scaffold a whole module while you read the first line. For anyone who has spent years writing code by hand, this feels like a superpower.

But here is the catch, and it is the whole point of this post.

## Fast code can be fast chaos

An AI can write the wrong code just as quickly as the right code. It can add a feature you never asked for. It can invent a requirement that was never agreed. It can choose a design that does not fit your system. And — this is the one that catches people out — it can quietly change your tests so that bad code passes.

None of this looks like failure on the screen. The output is confident. The code runs. The tests are green. It is only later, when something breaks in a way you do not understand, that you realise the assistant was building something other than what you meant.

So the new problem is not speed. We have plenty of speed now. The new problem is **control**.

## What control actually looks like

Staying in control does not mean writing every line yourself. It means keeping a few decisions firmly in human hands, and not letting the tool make them for you.

A handful of habits do most of the work:

- **Clarify before you build.** A vague request invites the AI to fill the gaps for you. Pin down what is in scope, and what is not, before any code is written.
- **Write the test before the code.** Decide how you will prove the result *first*. Then the code has a fixed target it must meet — one you set, not one the AI invents after the fact.
- **Never let the AI weaken a test to make code pass.** A failing test is evidence, not an obstacle. Fix the code, not the test. If the test really is wrong, stop and say so — do not let it be quietly edited away.
- **Build one small piece at a time.** A small change can be read, tested, and trusted. A huge one hides its own mistakes.
- **Review the change, not just the result.** Green tests prove the behaviour works. Only a human review proves that *only the agreed work was done, in the agreed way.*

Notice what these have in common. Each one keeps a decision with you — what to build, what "done" means, what counts as proof. The AI does the heavy lifting inside those limits. It is fast, and you are still in charge.

## Speed is the easy part now

This is a real shift in how we should think about building software. For decades we optimised for *output* — getting more code written, faster. AI has solved that. The scarce thing now is not production; it is judgement. Knowing what to build, proving it does the right thing, and refusing to accept work you have not understood.

The good news is that none of this is new or exotic. It is ordinary engineering discipline — clear requirements, tests first, small steps, human review — applied to a faster tool. The discipline is older than the tools, and it is exactly what protects you when the tools change.

## The book

I have written a short, open-access book on exactly this: how to build real software with AI while keeping control of the design, the scope, and the tests. It teaches a hands-on, test-first method through two worked examples, taking you from a vague request to tested, working code.

It is free, licensed under Creative Commons (CC BY), and has a DOI so it can be cited:

**AI-SDLC: Building Software with AI Under Control** — [https://doi.org/10.5281/zenodo.20449105](https://doi.org/10.5281/zenodo.20449105)

If you build software with AI, or teach people who will, I hope it is useful. I would be glad to hear what you think.
