# github_actions : Repo with github-action's workflow files for practice purposes (Beginners)

## BASICS :

Github EVENTS (changes made in/to your repo) -> trigger workflow which consists of/executes jobs (which consists of steps) that runs on runners
Note: Job - run in parallel , Steps within a job -> run in sequence

TERMINOLOGIES: 

> Workflow: A workflow is a configurable automated process that you define in a YAML file. It includes one or more jobs that run on specific events or schedules in your GitHub repository.
> Workflow file: The YAML file that defines your workflow. It resides in the .github/workflows directory of your repository.
> Job: A job is a set of steps that execute on the same runner in parallel. Jobs within a workflow can be run sequentially or in parallel, depending on your configuration.
> Step: A step is an individual task in a job. Each step performs a specific action, such as running a script, checking out code, or deploying an application.
> Action: An action is a reusable unit of code that can be used in workflows. It encapsulates a specific task, making it easier to maintain and share common actions across repositories.
> Runner: A runner is a virtual machine or physical host where your jobs run. GitHub provides default runners, but you can also create and use self-hosted runners on your own infrastructure.
Github hosted runners : windows, ubuntu, macOS
> Event: An event is a specific activity that triggers a workflow. Examples include pushes to the repository, pull requests, or scheduled runs.
Examples :
- push event : when something is pushed to repo 
- pull_request
- pull_request_review: when review is submitted or dismissed
- issue : when an issue is opened/edited/assigned/closed/labeled
- issue_comment : when someone comments on an issue
- schedule event : runs workflows on schedule
- workflow_dispatch Event: Allows you to trigger a workflow manually using the GitHub API.
- create , delete : when repo/branch/tag is created/deleted
- deployment : when a deployment is created or updated. 

> Artifact: An artifact is a file or set of files produced during a workflow run that you want to persist or share with other jobs in the workflow.
> Environment: An environment is a named, configurable set of environment variables that you can use to define secrets, configuration values, or other data accessible during workflow runs.
> Secrets: Secrets are encrypted environment variables that you can store in your repository or organization settings. They are used to store sensitive information securely, such as API keys or credentials.


# GITHUB CLI : gh 

> Installation :  
macOS:  breq install gh 
Windows: winget install -id Github.cli 
> Login : gh auth login    //or use GITHUB_TOKEN

# GITHUB REST API : base url i.e. "https://api.github.com/" + path , methods : GET , POST, PATCH , PUT , DELETE
EX: 
curl -X GET \
  -H "Authorization: token YOUR_ACCESS_TOKEN" \
  -H "Accept: application/vnd.github.v3+json" \
  https://api.github.com/repos/username/repo

# COMMON API'S : 

> get repo details :   https://api.github.com/repos/username/repo
> get issues of a repo : https://api.github.com/repos/username/repo/issues
> create a new issue on a repo :
curl -X POST \
  -H "Authorization: token YOUR_ACCESS_TOKEN" \
  -H "Accept: application/vnd.github.v3+json" \
  -d '{"title":"New Issue","body":"This is a new issue created via API."}' \
  https://api.github.com/repos/username/repo/issues
> update an issue :
curl -X PATCH \
  -H "Authorization: token YOUR_ACCESS_TOKEN" \
  -H "Accept: application/vnd.github.v3+json" \
  -d '{"title":"Updated Issue","body":"This is an updated issue via API."}' \
  https://api.github.com/repos/username/repo/issues/1
> close an issue : 
curl -X PATCH \
  -H "Authorization: token YOUR_ACCESS_TOKEN" \
  -H "Accept: application/vnd.github.v3+json" \
  -d '{"state":"closed"}' \
  https://api.github.com/repos/username/repo/issues/1
> comment on an issue of a repo :
  -d '{"body":"This is a comment on the issue."}' \
  https://api.github.com/repos/username/repo/issues/1/comments
