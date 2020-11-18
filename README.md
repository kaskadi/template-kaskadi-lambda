![](https://img.shields.io/github/package-json/v/kaskadi/template-kaskadi-lambda)
![](https://img.shields.io/badge/code--style-standard-blue)
![](https://img.shields.io/github/license/kaskadi/template-kaskadi-lambda?color=blue)

**GitHub Actions workflows status**

[![Deploy status](https://img.shields.io/github/workflow/status/kaskadi/template-kaskadi-lambda/deploy?label=deployed&logo=Amazon%20AWS)](https://github.com/kaskadi/template-kaskadi-lambda/actions?query=workflow%3Adeploy)
[![Build status](https://img.shields.io/github/workflow/status/kaskadi/template-kaskadi-lambda/build?label=build&logo=mocha)](https://github.com/kaskadi/template-kaskadi-lambda/actions?query=workflow%3Abuild)
[![Syntax check status](https://img.shields.io/github/workflow/status/kaskadi/template-kaskadi-lambda/syntax-check?label=syntax-check&logo=serverless)](https://github.com/kaskadi/template-kaskadi-lambda/actions?query=workflow%3Asyntax-check)
[![Docs generation status](https://img.shields.io/github/workflow/status/kaskadi/template-kaskadi-lambda/generate-docs?label=docs&logo=read-the-docs)](https://github.com/kaskadi/template-kaskadi-lambda/actions?query=workflow%3Agenerate-docs)

**CodeClimate**

[![](https://img.shields.io/codeclimate/maintainability/kaskadi/template-kaskadi-lambda?label=maintainability&logo=Code%20Climate)](https://codeclimate.com/github/kaskadi/template-kaskadi-lambda)
[![](https://img.shields.io/codeclimate/tech-debt/kaskadi/template-kaskadi-lambda?label=technical%20debt&logo=Code%20Climate)](https://codeclimate.com/github/kaskadi/template-kaskadi-lambda)
[![](https://img.shields.io/codeclimate/coverage/kaskadi/template-kaskadi-lambda?label=test%20coverage&logo=Code%20Climate)](https://codeclimate.com/github/kaskadi/template-kaskadi-lambda)

<!-- You can add badges inside of this section if you'd like -->

****

# Repository initialization

When creating a repository from this template, an `init` workflow (see [here](./.github/workflows/init.yml)) will run. This workflow uses [`kaskadi-cli`](https://www.npmjs.com/package/kaskadi-cli) in order to properly initialize your repository by:
- updating the names refering to the template in relevant files (for example `package.json`, `package-lock.json`, etc.) and renaming some files if need be
- automatically adding your repository to _Code Climate_

# Testing

`mocha`, `chai`, `nyc` & `standard` are available as dev dependencies.

A `build` workflow (see [here](./.github/workflows/build.yml)) is running on `pull request` and will execute your test suite before allowing you to merge your PR. It also has a `coverage` job already prepared that you can comment out as soon as your testing is in place and your `REPORTER_ID` is in the repository secrets. This is the ID on _Code Climate_ used for uploading code coverage reports.

Beside running your unit tests, this workflow also runs a static code analysis to find any vulnerability in your code. If a vulnerability is found, the workflow will directly fail and a notification will appear in the `Security` tab of your repository.

Along `build`, a `syntax-check` workflow will also run to check your `serverless.yml` file syntax.

****

# Documentation

This repository comes with a `generate-docs` workflow that generates documentation automatically for you by reading your main `serverless.yml` configuration file and extracting meta data of all lambda functions you defined. See [here](https://github.com/kaskadi/action-generate-docs) and [there](./serverless.yml) for more information.

Before generating the documentation, the workflow will check for syntax error in your `serverless.yml` file.

If you would like to see the workflow configuration, head [here](./.github/workflows/generate-docs.yml).

You can configure the template used to generate the action documentation [here](./docs/template.md).

****

# Deploying

Deploying to AWS is done automatically via a `deploy` workflow (see [here](./.github/workflows/deploy.yml)). This workflow will run on `push`. Before publishing it:
1. performs a static code analysis of the layer to detect any vulnerabilities. If a vulnerability is found, the workflow will directly fail. A notification will also appear in the `Security` tab of your repository.
2. checks the syntax of `serverless.yml` for any errors
3. run any tests you may have set up with `npm test`

**You'll have to switch the command from `--version` to `deploy -v` in the [workflow configuration file](./.github/workflows/deploy.yml) to actually deploy!**

**Warning: you may need to manually deploy the first time via `Serverless` CLI locally.**

****

<!-- automatically generated documentation will be placed in here -->
# Resources documentation

The following lambda functions are defined in this repository:
- [template-kaskadi-lambda](#template-kaskadi-lambda)

The following layers are defined in this repository:
- [template-kaskadi-lambda-layer](#template-kaskadi-lambda-layer)

## template-kaskadi-lambda <a name="template-kaskadi-lambda"></a>

|           Name          | Sources                      | Timeout |                 Handler                 | Layers                                                                            |
| :---------------------: | :--------------------------- | :-----: | :-------------------------------------: | :-------------------------------------------------------------------------------- |
| template-kaskadi-lambda | <ul><li>HTTP (GET)</li></ul> | default | [handler](./template-kaskadi-lambda.js) | <ul><li>[template-kaskadi-lambda-layer](#template-kaskadi-lambda-layer)</li></ul> |

See [configuration file](./serverless.yml) for more details.

## template-kaskadi-lambda-layer <a name="template-kaskadi-lambda-layer"></a>

### Description

Layer for template-kaskadi-lambda

### Dependencies

- `template-kaskadi-lambda-utils` (local utility)

See [configuration file](./serverless.yml) for more details.

# Stack tags

You can use any tags (and their respective values) visible below to find ressources related to this stack on AWS. See [here](https://docs.amazonaws.cn/en_us/AWSCloudFormation/latest/UserGuide/aws-properties-resource-tags.html) for more details.

| Tag          | Value                   |
| :----------- | :---------------------- |
| app          | your-app-name           |
| service      | template-kaskadi-lambda |
| logical-unit | api-logical-unit        |
| type         | s3, sns, etc.           |
<!-- automatically generated documentation will be placed in here -->

<!-- You can customize this template as you'd like! -->
