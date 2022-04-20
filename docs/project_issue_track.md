# Project issue track

## About
[GitHub Action Reusable Workflow](https://docs.github.com/en/actions/using-workflows/reusing-workflows) for adding issues to a GitHub [Project Beta](https://docs.github.com/en/issues/trying-out-the-new-projects-experience/about-projects) Board.


## Usage
Obtain and declare the GitHub Project Beta Board ID as an input parameter called `project_number`.
![project-beta-id](images/project-beta-id.png)
`app_id` and `private_key` are [organization secrets](https://github.blog/changelog/2020-05-14-organization-secrets/) to authenticate the GitHub Action Workflow ([github-app-token](https://github.com/tibdex/github-app-token)). Both are available to all organization repositories.


Here is sample of [usage](https://github.com/commercetools/dummy-repo/blob/main/.github/workflows/main.yml):
```yml
# types of events we want to run the workflow
on:
  issues:
    types:
      - opened
      - reopened
      - transferred

jobs:
  project_issue_track:
    uses: commercetools/.github/.github/workflows/project_issue_track.yml@main
    with:
      project_number: 37
    secrets:
      app_id: ${{ secrets.CT_PROJECT_BETA_AUTOMATION_APP_ID }}
      private_key: ${{ secrets.CT_PROJECT_BETA_AUTOMATION_APP_PEM }}
```

