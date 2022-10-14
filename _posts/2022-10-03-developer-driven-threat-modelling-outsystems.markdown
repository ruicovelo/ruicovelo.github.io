---
layout: post
title:  "Developer-driven threat modelling at OutSystems"
date:   2022-10-03 08:45:00 +0100
categories: security, threat modelling
---


We first started threat modelling at OutSystems when the whole R&D Team could fit in a large room. Now, the team is 10 times larger and spread around the world. Still, threat modelling remains part of our secure development lifecycle. Here is why we started threat modelling, how we still do it, and the bumpy but invaluable ride it has been.

<a href="https://labs.openai.com/s/FRhZAiJ3ebHxNMaV4k4JmClC">
<img width="300" src="/assets/img/DALLE-20220930-hackers_looking_at_a_diagram.jpg" style="float: right;">
</a>

Let’s start with the basics. Threat modelling is a structured, iterative approach to identifying, qualifying, and addressing security problems in a system or application based on a four-question framework (Shostack, 2014):

* What are we building?
* What can go wrong?
* What can we do about it?
* Have we done a good job?

These four questions allow you to gather context about the Development team’s work to really understand what the team is building and think about possible problems and potential solutions. You can then re-evaluate your solutions until you feel comfortable that you have addressed all relevant issues. In more elaborate projects, you can go into more detail and use more structure, tools, and documentation.

The more complex your application is, the more complex your threat model can be. Regardless of that, if you are answering these questions, you are threat modelling, even if you’re in a team of one like I was.
## The obvious choice for a growing problem
I joined OutSystems eight years ago. We had just launched our cloud offering in record time, and I was eager to bring in my systems engineering skills seasoned with a security mindset. The team was small, and we didn’t even have a security team, so I started to list what I would like to change on the security front. It was a big list.

I showed it to my manager and asked for a budget to “fix all the things.” As a small team doing a lot of work for our cloud offering, my manager had no choice but to ask me to prioritise and plan to implement the most critical security fixes first.

For me, someone who had barely scratched the surface of a career in security, this sounded outrageous. It’s security! Everything is important, right? Not really. This simple act of leadership from my manager turned out to be one of the most crucial turning points in my career. How do I prioritise security issues? What are the most critical issues?

Being new to the company, my first step was to get more information about everything to better understand the risks involved. Before I proposed solutions, I broke down each problem as simply as I could so that anyone could understand them. Then I offered solutions based on what I discovered — and that’s when it hit me. I was answering some very familiar questions:

* What are we building?
* What can go wrong?
* What can we do about it?

We prioritised based on risk, selected the top ones, and planned the fixes. We could then answer the last remaining question:

* Have we done a good job?

Yes, I was threat modelling. The methodology caught the attention of a few leaders in the company, tired of endless debates around security, often leading to over-engineered solutions to fix minor problems. Threat modelling allowed Engineering teams to have structured conversations around security, identify relevant issues, and then focus on the most important ones first.

Now, all we had to do was have every team do it early in the development process to maximise the value of the methodology by hopefully finding problems before development starts. And that’s when the bumpy ride began.
## Getting Buy-In From Developers
OutSystems was a very small company at the time. We didn’t have a security team and we had a single threat modelling champion (me). There was no way this would work without developers' buy-in and help. The first bump you may encounter when implementing threat modelling is getting that buy-in from developers. To them, threat modelling will sound like yet another process to follow on the path to delivering software. A delay. An annoyance. And it will continue this way until developers see the methodology's value.

You can help them do this by surprising the team with newfound problems they didn’t know they had or showing how threat modelling can help fix the problems they know they have. The absence of an established security team at the time worked to my advantage. The methodology sounded like an idea coming from one developer to another.

We started small, focusing on a few teams with clearly defined security issues, exposed assets, or other identified security concerns that needed prioritisation. Then we rolled out the process to more teams. And the following feedback was consistent:


1.  **“We don’t know anything about security or how to do threat modelling.”**

    Not knowing about security or threat modelling is easy to tackle with documentation, guidelines, examples, and an introductory session. In no time, I saw developers chiming in with security problems that security-savvy engineers weren’t aware of. How do you create this mindset? I advise focusing on whatever can go wrong rather than trying to think like a hacker. Hackers invest in tools that we don’t have while using their creativity. So, instead, look at what impacts users, the company, and the business, and start from there. As soon as someone starts identifying one of these, the whole team usually chimes in, offering solutions and more things that can go wrong.

2. **“We don’t have time to do threat modelling.”**

    The feeling of being pressured to deliver soon is a common reason for not making the time for threat modelling. This argument can be addressed by having the initiative’s sponsor or team-lead state it as imperative right from the start. These are also the same people who can help reprioritise items to ensure this event takes place. Threat modelling should be part of the design process and if you are estimating effort for designing, include threat modelling.


Having overcome these two hurdles, the biggest challenge for me was defining _when_threat modelling is relevant. But more on that later.

## Teaching How to Threat Model
As I pointed out before, we didn’t have a security team in the early days, and the R&D Team was growing quickly. There’s only so much one security-savvy developer can do, so it was vital to get help from other security-savvy developers and turn them into **security champions** — these champions led by example, teaching and asking questions across all teams. Sometimes asking, “Have you threat modelled?” goes a long way.

Our first approach to teaching teams was to create high-level guidelines, point out some training sessions, and let the teams autonomously decide what worked for them in terms of process, format, and risk scoring for prioritisation.

Guess what? It didn’t work.

The feedback from developers was that high-level documentation and freedom of choice gave them too much to decide and waste time on. What helped was step-by-step documentation, which we posted on our internal wiki, with real-life examples and a few one-hour recorded training sessions. We also shared some training courses anyone could take to learn more about the methodology.

Examples include complete and real threat models from other teams and requirements, assumptions, and threat lists that developers can check and use if relevant to their project. [STRIDE](https://en.wikipedia.org/wiki/STRIDE_(security)) can be helpful, but it still confuses some developers that prefer actual threat examples.

However, some teams feel the need for an introductory face-to-face session so that they can ask questions. The help from our security champions and, later on, from security engineers was invaluable in getting the word across. We handled these sessions on an _ad hoc_ basis, proactively scheduling meetings with teams who had many questions or promptly accepting meeting requests from those looking for answers.


## Prioritising Threats

A critical output of threat modelling is a prioritised list of threats so that you can focus on the most critical first. There are plenty of scoring frameworks that can help create some objectivity and common language around the risks involved, prioritising the threat list in a way everyone can understand. You’ve probably heard about [DREAD](https://en.wikipedia.org/wiki/DREAD_(risk_assessment_model)), [CVSS](https://www.first.org/cvss/), or [OWASP’s risk rating methodology](https://owasp.org/www-community/OWASP_Risk_Rating_Methodology).

On the other hand, risk frameworks have some caveats. There is no one-size-fits-all risk framework. Some are overly complicated, and others are too simple. If you take them too seriously, you might still end up prioritising risks wrongly, dismissing important ones, or focusing on those that are unlikely to occur.

I’ve seen developers spend copious amounts of time trying to get the score right and still get it wrong. When you have a threat shortlist you will address anyway, it does not make sense to waste time trying to obtain the perfect score.

Still, they are a valuable tool if you need to establish priorities. One team created its own risk framework as the existing ones did not cater to their concerns. Since they used a customised framework that wasn’t familiar to other teams and lacked documentation and examples, understanding it could be somewhat challenging. Still, for that group, it helped them achieve their particular purpose.


## When Is Threat Modelling Relevant?

This is a relatively common question. You will find many tips and rules of thumb online from looking at changes in your attack surface (the entry points of your organisation or system that are susceptible to hacking), dataflow, new APIs, new assets, or, sometimes, features. But they basically usually tell you that you only need to do threat modelling when you have “relevant changes” to your application or system.

Unless you use these tips to focus on the particular changes that are more likely to create threats, such advice can be either too generic or too specific and often hard to follow or even lead to not looking at problems. In my experience, there are plenty of things that can go wrong with very simple changes to your system.

On the other hand, more than following a formal process, threat modelling creates the right security-by-design mindset, which pertains to delivering products and capabilities that are foundationally secure, with security strategies imbued right from the software design stage and a thought-structuring methodology.

**The trick relies on starting simple and getting more complex as needed.** Making the threat modelling process lean and fast so that simple projects get a simple threat model process. You should always think about what you are building and ask yourself what can go wrong. And that is already part of threat modelling. The more detailed threat modelling happens when you have a complex system where more attention is needed.

Here are some lessons learned over the years about threat modelling in a fast-growing and fast-changing environment.


## How We Do Threat Modelling at OutSystems

I have to confess: our original dream of having all developers on board doing threat modelling regularly and autonomously didn’t come to fruition. Not entirely, at least. The Development Team keeps growing, and we can’t afford to release anything without ensuring all security practices are in place.

**A security review is a mandatory requirement for everything reaching the production stage.** Threat modelling is one of the practices within the security review process.

Fortunately, we now have a skilled Security Team that can help. But some things have remained the same: **developers are at the heart of the threat modelling and security review processes.** What started as a workaround is now an essential part of the process.

The reason for this is simple. **Security is everyone’s job** and developers _know_ what they are building better than anyone. At the same time, the most significant value of threat modelling is not the resulting formal documents or sign-offs but in learning about the security implications of what you are building.

**At OutSystems, we do threat modelling at the design phase and in every development initiative.** We do it even if the output simply describes what you are doing and there are no particular security risks involved.

If we have a long list of threats to address, **we use simple risk frameworks** to keep us on the right path. We use them as a tool but not as a formal score. There is no need for scoring if all threats are to be addressed or if none of the threats is relevant.

**Development teams drive at least the first iteration of the threat model**, which will get reviews and contributions from the Security Team. This can happen async or during one-hour meetings, depending on the complexity of the solution.

From the outputs of threat modelling, **Development teams and Security teams redesign,  build mitigations to the threats and create tests.** Mitigation strategies can include design changes, new features, and detection and recovery capabilities. **The threat model is also used to develop and fine-tune automated testing** to ensure threats are adequately covered. Everyone’s input is relevant.

**We focus on changes but keep track of previous models.** Why? It allows us to keep improving our overall security while continuing to learn.

The bumpy ride has proved invaluable. I am sure the way I describe how we do threat modelling today will change in the future. As systems change, teams change, and needs change, we adapt and change processes. But the crux of it remains unchanged: **create a secure by design approach where you focus on the problems you need to solve before you create them.**



## References

Shostack, A. (2014). _Threat Modeling: Designing for Security_. Wiley.

Images in this post were generated by AI. Click on the images for more information.