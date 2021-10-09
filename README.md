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

## Referencing other actions

### Customizing
1. Handling with Inputs and Outputs
Github example [available here...](https://docs.github.com/en/actions/learn-github-actions/finding-and-customizing-actions#using-inputs-and-outputs-with-an-action)
```yml
name: "Example"
description: "Receives file and generates output"
inputs:
  file-path: # id of input
    description: "Path to test script"
    required: true
    default: "test-file.js"
outputs:
  results-file: # id of output
    description: "Path to results file"
```

### Finding
1. **Using tags (versions):**
   1. Using that code, you are saying you want to use the version **v1.0.1** of the public action called **javascript-action**
      ```yml
        steps:
          - uses: actions/javascript-action@v1.0.1
      ```

1. **Using SHAs:**
   1. On this way, you are specifing which exacly version of the action you want to use, leaving no room for to any updates from those action.
      ```yml
        steps:
          - uses: actions/javascript-action@172239021f7ba04fe7327647b213799853a9eb89
      ```

1. **Using Branchs:**
   1. Specifies you want to use the code where is on branch _main_ from the action repository, but you was exposed to any changes the maintener do at his code.
      ```yml
        steps:
          - uses: actions/javascript-action@main
      ```

1. **Using actions at the same repository**
   1. Tree directory from this own project (until now):
   ```plaintext
   |-- Learning Github Actions (repository)
   |  |__ .github
   |     |__ actions
   |        |__ hello-world-action.yml
   |     |__ workflows
   |        |__ github-actions-demo.yml
   |        |__ learn-github-actions.yml
   |        |__ finding-customizing-actions.yml
   ```

   1. Follow the guides:
      1. `<repository-owner>/<repository-name>@<reference-you-wish>`; or
      1. `./<path-to-directory's-action>`
   1. How to:
    ```yml
      jobs:
        runs-on: ubuntu-latest
        steps:
          - uses: actions/checkout@v2 # This step checks out a copy of your repository.
          - uses: ./.github/actions/hello-world-action # This step references the directory that contains the action.
    ```

1. **Referencing a dockerhub container**
   1. Folow the guide: `docker://<docker-image>:<image-tag (version)>`
    ```yml
      jobs:
        my_first_job:
          steps:
            - name: My first step
              uses: docker://alpine:3.8
    ```

1. Look for more at [Fiding and customizing actions](https://docs.github.com/en/actions/learn-github-actions/finding-and-customizing-actions)
