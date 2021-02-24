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

## Install Gitlab Runner on Windows 
1. Register your runner - run the commands below:
   ```
   C:\your\path\gitlab-runner.exe register --config C:\your\path\my-runner\config.toml --non-interactive --url YOUR-GITLAB-URL --registration-token YOUR-REGISTRATION-TOKEN --description my-runner
   ```
   This will do the following:
   1. Generate a Runner Token
   2. Generate a config.toml file based on the path
   3. Register your runner - your should see now in **project repository** -> Settings -> CI/CD -> Runners that there is a registered runner, but not yet running

2. Run your runner - run the commands below:
   ```
   C:\your\path\gitlab-runner.exe run --working-directory C:\your\path\my-runner\ --config  C:\your\path\my-runner\config.toml
   ```
   This will do the following:
   1. Run `my-runner`
   2. It is now ready to accept jobs

## Install Gitlab Runner on Windows that accepts bash commands





