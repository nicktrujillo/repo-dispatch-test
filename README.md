# repo-dispatch-test

## Old way

- grading.yml (Learners should not edit this)

  - on: repository_dispatch
  - steps
    - Looking Glass
      - catch the payload and respond accordingly

- use-secrets.yml (learner should edit this)
  - steps
    - Logic to validate
      - check the learner/read the secret/compare values
        - use a repo secret in a workflow (learner ask)
      - create the LG payload from the results of prev step
        - Send the payload using repo_dispatch (wrapper for POST) to grading.yml
        - as body to POST request

Bot -> Bot = infinite loop of bullshit (potential GH restrictions on this)

**Does not work**
worfklow1:

- on push

worfklow2

- on pull
  -step was to push

**results:**

CAN

- tigger workflow A from workflow B if we use repo dispatch
- must use PAT with repo scope

CANNOT

- use the GITHUB_TOKEN for the repo dispatch

POTENTIAL LAB

- Create repo scope PAT
- Set PAT as repo secret
- Use secret in workflow B
