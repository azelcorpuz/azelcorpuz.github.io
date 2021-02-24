---
layout: post
title:  "Gitlab Runner on Windows"
date:   2021-02-24 11:07:00 +0800
categories: notes
---
## Prerequisites:
1. Gitlab runner binary file - [64 bit](https://gitlab-runner-downloads.s3.amazonaws.com/latest/binaries/gitlab-runner-windows-amd64.exe) [32 bit](https://gitlab-runner-downloads.s3.amazonaws.com/latest/binaries/gitlab-runner-windows-386.exe), rename it to gitlab-runner and put it to: `C:\your\path\`
2. Registration Token - this can be found when you go to your **project repository** -> Settings -> CI/CD -> Runners and you will see the **Registration Token** in **Set up a specific Runner manually** section 
3. Gitlab URL - your gitlab URL

## Gitlab Runner on Windows 
1. Register your runner - run the commands below:
   ```
   C:\your\path\gitlab-runner.exe register --config C:\your\path\my-runner\config.toml --non-interactive --executor shell --url YOUR-GITLAB-URL --registration-token YOUR-REGISTRATION-TOKEN --description my-runner
   ```
   This will do the following:
   1. Generate a Runner Token - the runner token is different from registration token as runner token is the one that will be used upon when running your runner
   2. Generate a config.toml file based on the path
   3. Register your runner - your should see now in **project repository** -> Settings -> CI/CD -> Runners that there is a registered runner, but not yet running

2. Run your runner - run the commands below:
   ```
   C:\your\path\gitlab-runner.exe run --working-directory C:\your\path\my-runner\ --config  C:\your\path\my-runner\config.toml
   ```
   This will do the following:
   1. Run `my-runner`
   2. It is now ready to accept jobs

Sample `.gitlab-ci.yml`
```
# This file is a template, and might need editing before it works on your project.
# Full project: https://gitlab.com/pages/plain-html
stages:
  - build
  
build_backend:
  stage: build
  script:
    - echo "hello world"
  only:
    - master
```

## Gitlab Runner on Windows that accepts bash commands
If you want to use bash commands for your scripts, its possible even if you are running windows - this is useful if you have multiple gitlab runners running in different platform but want to maintain the same `.gitlab-ci.yml`

Additional Prerequisites: `bash.exe` for windows - sometimes it is included with *git* - just make sure that `bash.exe` is a valid command by putting it in your %PATH%

1. Register your runner - do the same step as above
2. Modify the generated config:
   * change the `shell` to `bash`
   * update `builds_dir` and `cache_dir` - as the format for path is different between in linux and windows
   * your runners in `config.toml` shuold look like this:
```
[[runners]]
  name = "ut26vb-runner3"
  url = "YOUR_GITLAB_URL"
  token = "YOUR_RUNNER_TOKEN"
  executor = "shell"
  shell = "bash"
  builds_dir = "/C/your/path/my-runner/builds/"
  cache_dir = "/C/your/path/my-runner/cache/"
```
3. enter `bash` command line
4. Run your runner - run the commands below:
```
/C/your/path/gitlab-runner run --working-directory /C/your/path/my-runner --config /C/your/path/my-runner/config.toml
```
   This will do the following:
   1. Run `my-runner`
   2. It is now ready to accept jobs

Sample `.gitlab-ci.yml` with bash command
```
# This file is a template, and might need editing before it works on your project.
# Full project: https://gitlab.com/pages/plain-html
stages:
  - build
  
build_backend:
  stage: build
  script:
    - ls
  only:
    - master
```

## Install it as a Windows Service
1. It can be installed as a service by running the command:
```
/C/your/path/gitlab-runner install \
--working-directory /C/your/path/my-runner  \
--config /C/your/path/my-runner/config.toml \
--service 'SERVICE NAME' \
-u 'ADMIN_USERNAME' \
-p 'ADMIN_PASSWORD'
```

2. Run the service: 
```
/C/your/path/gitlab-runner start \
--service 'SERVICE NAME'
```
