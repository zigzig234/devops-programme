# GitHub Actions Practice

## Prerequisites

- Organize your git repo to follow the guidelines provides in the presentation

```sh
├── .editorconfig
├── .github
│   └── workflows
│       └── ci-pipeline.yml
├── .gitignore
├── .markdownlint.json
├── .python-version
├── Dockerfile
├── LICENSE
├── README.md
├── ansible
│   ├── README.md
│   └── playbook.yml
├── app
│   ├── README.md
│   ├── app.py
│   ├── app_test.py
│   └── requirements.txt
└── requirements.txt
```

## Task description

Create a GitHub Actions pipeline that runs on commit to a feature branch (i.e. not `main`) and performs the following checks on our simple Flask app repository.

- Check `.editorconfig`
- Code Lint and style - use `pylint` and `black` to check for style/formatting/syntax errors
- Check makrdown files [markdownlint-cli](https://www.npmjs.com/package/cli-markdown)
- Code Unittest - there's a simple unit test next to our app called `app_test.py`. Make sure our unittest passes (`python -m unittest` executed in the app directory)
- Check for hardcoded secrets (`gitleaks`) - not just our app but the whole repository.
- SAST - SonarCloud; Review code smells and security issues
- SCA - Snyk; review security issues
- Build a Docker image. Use Git commit SHA as an Image tag.
- Scan the built image with `Trivy`
- Push the built image to your Docker HUB account
- (optional) Add CONTRIBUTORS guide. Follow [this](https://docs.github.com/en/communities/setting-up-your-project-for-healthy-contributions/setting-guidelines-for-repository-contributors) document from GitHUb.

:warning: Make sure that you run as many tests in parallel as you see fit

:warning: Make sure you don't push your image to Docker HUB if Critical vulnerabilities are found

:warning: Try and use ready-made GH Actions. Avoid shell-out if possible

:exclamation: At the end open a PR with your solution.

## Extra effort

- Create a pre-commit hook that safeguards for the following
  - hardcoded secrets (`gitleaks`)
  - yamllint
  - check-merge-conflict <https://github.com/pre-commit/pre-commit-hooks>
  - check-added-large-files <https://github.com/pre-commit/pre-commit-hooks>
- Setup docker-compose with build and run a container
- Try out GitHub Actions schedule trigger event - <https://docs.github.com/en/actions/using-workflows/events-that-trigger-workflows#schedule>
