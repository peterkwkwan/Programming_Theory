## 1) Focus on High-Leverage Activities
- Leverage = Impact / Time
  
![image](https://github.com/peterkwkwan/Programming_Theory/assets/37263010/2bd3718a-1539-4940-96f5-8cf22454cba3)

## 2) Optimize for Learning
- Adopt a Growth Mindset - avoid a Fixed Mindset
- Learning is like compound investing
- Seek out work environments conductive to Learning
  - Training
  - Pace
  - Openness
  - People / Talent
  - Autonomy

## 3) Prioritize Regularly
- Prioritize ideas based on estimated returns on investment
- Have a checklist of "to-do's"
  - checklists reduce errors in every field
- Focus on what directly produces *value*
![image](https://github.com/peterkwkwan/Programming_Theory/assets/37263010/8cf9dca5-1456-48b6-b0fb-02050ad05a86)
- Focus on the important and non-urgent
  - Quadrant 2 items provide significant value in the long term
  - Carve out time to invest in skill development
- Protect your Maker's schedule
  - getting into *flow* or *rhythm* takes around 10-15 minutes of uninterrupted concentration
  - preserve large chunks of your schedule into "focus blocks", reducing context-switches

## 4) Invest in iteration speed
- **Continuous deployment** when automated with QA testing is vital to velocity
  - CI allows for small, incremental changes rather than large, batched updates
  - Smaller iterations cause less overhead and context switching
  - Easier to debug changes as changes are minor and small
  - Avoid 'merge hell' that is associated with infrequent, large releases
 
- Move Fast to Learn Fast
  - the faster you iterate, the faster you learn what works and what doesn't work

- Invest in Time-Saving Tools
  - tools that save time will have a force-multiplier effect
  - empower you and your team to ship and deploy faster
 
- Master Your Programming Environment
  - Get proficient with your favorite text editor or IDE
  - Learn at least one productive, high-level programming language
  - Get familiar with UNIX (or Windows) shell commands
    - Learn basic commands like _grep_, _sort_, _uniq_, _wc_, _awk_, _sed_, _xargs_ and _find_
  - Automate your manual workflows
 

## 5) Measure What You Want to Improve
- Use Metrics to Drive Progress
  - If you can’t measure it, you can’t improve it
  - When visualized over time, good metrics help guard against future regressions
- Pick the Right Metric to Incentivize the Behavior You Want

## 6) Validate Your Ideas Early and Often
- Both external and internal feedback is vital
  - Iterate fast on an early PoC build and get feedback from stakeholders
  - Feedback helps the team prioritize which features are important
- You *can't* get everything right without validation from your end users
- The shorter the iteration cycles, the more quickly we can learn from our mistakes
  - The longer the cycles, the more likely the mistakes and errors will compound
- Fake validation (a button when clicked and just says "coming soon") is a highly effective way to gather feedback and data
- A/B is crucial to testing what works
  - use real data to validate what words/features catch on with users
 
- **Approach a problem iteratively to reduce wasted effort.**
- **Reduce the risk of large implementations by using small validations.**
- **Use A/B testing to continuously validate your product hypotheses.**

## 7) Improve Your Project Estimation Skills
- A study of over 50,000 software projects concluded that 44% of projects are delivered late, overbudget, or missing requirements; 24% fail to complete; and the average slipped project overruns its time budget by 79%

- How to give better estimates:
  - Decompose the project into granular tasks
  - Think of estimates as probability distributions, not best-case scenarios
  - Let the person doing the actual task make the estimate
  - Budget for the unknown
 
- Approach Rewrite Projects with Extreme Caution
  - Because we tend to be familiar with the original version, we typically underestimate rewrite projects more drastically than we would an undertaking in a new area
  - It is easy and tempting to bundle additional improvements into a rewrite. Why not refactor the code to reduce some technical debt, use a more performant algorithm, or redesign this subsystem while we’re rewriting the code?
  - When a rewrite is ongoing, any new features or improvements must either be added to the rewritten version (in which case they won’t launch until the rewrite completes) or they must be duplicated across the existing version and the new version (in order to get the feature or improvement out sooner). The cost of either option grows with the timeline of the project.

- Define measurable milestones.
  - Clear milestones can alert you as to whether you’re on track or falling behind. Use them as opportunities to revise your estimates.
 
- Do the riskiest tasks first.
  - Reduce variance in your estimates and risk in your project by exploring the unknown early on. Don’t give yourself the illusion of progress by focusing first on what’s easy to do.
 
## 8) Balance Quality with Pragmatism
- Software quality comes down to tradeoff between quality and development speed

- Benefits of code reviews
  - catching bugs or design flaws early
  - increasing accountability
  - positive modeling of best practices
  - knowledge sharing
  - increase long-term robustness
 
- Good abstraction qualities
  - easy to understand
  - easy to use
  - hard to misuse
  - easy to extend

- Establish a culture of code reviews
- Invest in good abstractions to solve difficult problems
- Scale code quality with automated testing
- Manage technical debt

## 9) Minimize Operational Burden
- When a team is small, minimizing features that tax resources is critical
- Recurring costs of operating a system or product require time and energy that could be spent on higher-leverage activities
- Avoid re-inventing the wheel and writing unnecessary custom software

- Embrace Operational Simplicity
  - Increased complexity introduces more potential single points of failure
  - New engineers face a steeper learning curve when learning and understanding the new systems
 
- Build Systems to Fail Fast
  - Crashing at startup time when encountering configuration errors
  - Bubbling up an error from an external service that you don’t know how to handle, rather than swallowing it
  - Alerting engineers about any invalid or inconsistent program state as early as possible
  - The more complex the system, the more time that fail-fast techniques can save

- Do the simple thing first
- Fail fast to pinpoint the source of errors
- Automate mechanics over decision-making
  - Aggressively automate manual tasks to save yourself time

