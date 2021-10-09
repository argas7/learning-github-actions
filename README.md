# learning-github-actions
**A repository to record my studies about GitHub actions**

___
## Overview

1. We have a series of new names and concepts to know:
   1. **Event-driven:** it's mean that you can run many tasks as you wish after a determinate event;
   1. **Workflow:** basically a to-do list you have to guide every action you want run;
   1. **Jobs:** at line above I said a workflow has many actions, but the Github call it as _Jobs_ to be done, by default, multiple jobs inside a workflow run in parallel;
   1. **Steps:** every _job_ has many steps (shell commands) as we want to program. __In order__ this steps controlling how the _actions_ should run;
   1. **Actions:** are the smallest commands we can break this flow that, standalone or combined, builds an step;
   1. Of course it is the shortest resume I could do. An explication infinity better could be found here, at [Understanding Github Action](https://docs.github.com/en/actions/learn-github-actions/understanding-github-actions) article.
