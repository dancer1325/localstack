<p align="center">
:zap: We are thrilled to announce the release of <a href="https://blog.localstack.cloud/localstack-release-v-3-8-0/">LocalStack 3.8</a> :zap:
</p>

<p align="center">
  <img src="https://raw.githubusercontent.com/localstack/localstack/master/docs/localstack-readme-banner.svg" alt="LocalStack - A fully functional local cloud stack">
</p>

<p align="center">
  <a href="https://circleci.com/gh/localstack/localstack"><img alt="CircleCI" src="https://img.shields.io/circleci/build/gh/localstack/localstack/master?logo=circleci"></a>
  <a href="https://coveralls.io/github/localstack/localstack?branch=master"><img alt="Coverage Status" src="https://coveralls.io/repos/github/localstack/localstack/badge.svg?branch=master"></a>
  <a href="https://pypi.org/project/localstack/"><img alt="PyPI Version" src="https://img.shields.io/pypi/v/localstack?color=blue"></a>
  <a href="https://hub.docker.com/r/localstack/localstack"><img alt="Docker Pulls" src="https://img.shields.io/docker/pulls/localstack/localstack"></a>
  <a href="https://pypi.org/project/localstack"><img alt="PyPi downloads" src="https://static.pepy.tech/badge/localstack"></a>
  <a href="#backers"><img alt="Backers on Open Collective" src="https://opencollective.com/localstack/backers/badge.svg"></a>
  <a href="#sponsors"><img alt="Sponsors on Open Collective" src="https://opencollective.com/localstack/sponsors/badge.svg"></a>
  <a href="https://img.shields.io/pypi/l/localstack.svg"><img alt="PyPI License" src="https://img.shields.io/pypi/l/localstack.svg"></a>
  <a href="https://github.com/psf/black"><img alt="Code style: black" src="https://img.shields.io/badge/code%20style-black-000000.svg"></a>
  <a href="https://github.com/astral-sh/ruff"><img alt="Ruff" src="https://img.shields.io/endpoint?url=https://raw.githubusercontent.com/astral-sh/ruff/main/assets/badge/v2.json"></a>
  <a href="https://twitter.com/localstack"><img alt="Twitter" src="https://img.shields.io/twitter/url/http/shields.io.svg?style=social"></a>
</p>

<p align="center">
  LocalStack is a cloud software development framework to develop and test your AWS applications locally.
</p>

<p align="center">
  <a href="#overview">Overview</a> •
  <a href="#install">Install</a> •
  <a href="#quickstart">Quickstart</a> •
  <a href="#running">Run</a> •
  <a href="#usage">Usage</a> •
  <a href="#releases">Releases</a> •
  <a href="#contributing">Contributing</a>
  <br/>
  <a href="https://docs.localstack.cloud" target="_blank">📖 Docs</a> •
  <a href="https://app.localstack.cloud" target="_blank">💻 Pro version</a> •
  <a href="https://docs.localstack.cloud/references/coverage/" target="_blank">☑️ LocalStack coverage</a>
</p>

---

# Overview

* [LocalStack](https://localstack.cloud)
  * == 👁️cloud service emulator (== runtime) / runs | 1! container 👁️ | your
    * laptop
    * CI environment
  * allows
    * running your AWS applications or Lambdas | your local machine -- WITHOUT connecting to a -- remote cloud provider
    * speed up and simplify the testing of complex
      * CDK applications
      * Terraform configurations
  * supports
    * growing number of AWS services 
      * [Full list of Feature Coverage](https://docs.localstack.cloud/user-guide/aws/feature-coverage/) 
      * _Example:_ AWS Lambda, S3, Dynamodb, Kinesis, SQS, SNS
    * if you are using [Pro version of LocalStack](https://localstack.cloud/pricing) -> additional APIs & advanced features
  * [User Guides](https://docs.localstack.cloud/user-guide/)

## Install

* install `awslocal` CLI 
  * == LocalStack AWS CLI
    * != AWS CLI (`aws`)
  * allows
    * interacting with local AWS services
  * [`awslocal` documentation](https://docs.localstack.cloud/user-guide/integrations/aws-cli/#localstack-aws-cli-awslocal)
* LocalStack CLI
  * quickest way to get started
  * allows
    * start & manage, the LocalStack Docker container -- through -- your CL
  * requirements
    * install [`docker` environment](https://docs.docker.com/get-docker/)

### Brew (macOS or Linux with Homebrew)

* [official LocalStack Brew Tap](https://github.com/localstack/homebrew-tap)
* `brew install localstack/tap/localstack-cli`

### Binary download (MacOS, Linux, Windows)

* download the pre-built LocalStack CLI binary
* steps
  * download the latest [localstack/localstack-cli releases](https://github.com/localstack/localstack-cli/releases/latest)
  * extract the downloaded archive | directory / -- included in -- your `PATH` variable
    * | MacOS/Linux -- `sudo tar xvzf ~/Downloads/localstack-cli-*-darwin-*-onefile.tar.gz -C /usr/local/bin` --

### PyPI (MacOS, Linux, Windows)

* LocalStack -- is developed via -- Python
* `python3 -m pip install localstack` or `pip install --user localstack`

## Quickstart

* `localstack start -d`
  * start LocalStack | Docker container
  * `docker ps`
    * check that a new Docker container is running

      ```bash
       % localstack start -d
    
           __                     _______ __             __
          / /   ____  _________ _/ / ___// /_____ ______/ /__
         / /   / __ \/ ___/ __ `/ /\__ \/ __/ __ `/ ___/ //_/
        / /___/ /_/ / /__/ /_/ / /___/ / /_/ /_/ / /__/ ,<
       /_____/\____/\___/\__,_/_//____/\__/\__,_/\___/_/|_|
    
       💻 LocalStack CLI 3.8.0
       👤 Profile: default
    
      [12:47:13] starting LocalStack in Docker mode 🐳                       localstack.py:494
                 preparing environment                                       bootstrap.py:1240
                 configuring container                                       bootstrap.py:1248
                 starting container                                          bootstrap.py:1258
      [12:47:15] detaching                                                   bootstrap.py:1262
      ```

* `localstack status services`
  * query the status of respective services | LocalStack

    ```bash
    % 
    ┏━━━━━━━━━━━━━━━━━━━━━━━━━━┳━━━━━━━━━━━━━┓
    ┃ Service                  ┃ Status      ┃
    ┡━━━━━━━━━━━━━━━━━━━━━━━━━━╇━━━━━━━━━━━━━┩
    │ acm                      │ ✔ available │
    │ apigateway               │ ✔ available │
    │ cloudformation           │ ✔ available │
    │ cloudwatch               │ ✔ available │
    │ config                   │ ✔ available │
    │ dynamodb                 │ ✔ available │
    ...
    ```

* `awslocal sqs create-queue --queue-name sample-queue`
  * use SQS | LocalStack

    ```shell
    % awslocal sqs create-queue --queue-name sample-queue
    {
        "QueueUrl": "http://sqs.us-east-1.localhost.localstack.cloud:4566/000000000000/sample-queue"
    }
    ```

## Running

* ways to run LocalStack
  * [LocalStack CLI](https://docs.localstack.cloud/getting-started/installation/#localstack-cli)
  * [Docker](https://docs.localstack.cloud/getting-started/installation/#docker)
  * [Docker Compose](https://docs.localstack.cloud/getting-started/installation/#docker-compose)
  * [Helm](https://docs.localstack.cloud/getting-started/installation/#helm)

## Usage

* check out our [documentation](https://docs.localstack.cloud)
  * [LocalStack Configuration](https://docs.localstack.cloud/references/configuration/)
  * [LocalStack in CI](https://docs.localstack.cloud/user-guide/ci/)
  * [LocalStack Integrations](https://docs.localstack.cloud/user-guide/integrations/)
  * [LocalStack Tools](https://docs.localstack.cloud/user-guide/tools/)
  * [Understanding LocalStack](https://docs.localstack.cloud/references/)
  * [Frequently Asked Questions](https://docs.localstack.cloud/getting-started/faq/)

* TODO:
To use LocalStack with a graphical user interface, you can use the following UI clients:

* [LocalStack Web Application](https://app.localstack.cloud)
* [LocalStack Desktop](https://docs.localstack.cloud/user-guide/tools/localstack-desktop/)
* [LocalStack Docker Extension](https://docs.localstack.cloud/user-guide/tools/localstack-docker-extension/)

## Releases

Please refer to [GitHub releases](https://github.com/localstack/localstack/releases) to see the complete list of changes for each release. For extended release notes, please refer to the [LocalStack Discuss](https://discuss.localstack.cloud/c/announcement/5).

## Contributing

If you are interested in contributing to LocalStack:

- Start by reading our [contributing guide](docs/CONTRIBUTING.md).
- Check out our [development environment setup guide](docs/development-environment-setup/README.md).
- Navigate our codebase and [open issues](https://github.com/localstack/localstack/issues).

We are thankful for all the contributions and feedback we receive.

## Get in touch

Get in touch with the LocalStack Team to
report 🐞 [issues](https://github.com/localstack/localstack/issues/new/choose),
upvote 👍 [feature requests](https://github.com/localstack/localstack/issues?q=is%3Aissue+is%3Aopen+sort%3Areactions-%2B1-desc+),
🙋🏽 ask [support questions](https://docs.localstack.cloud/getting-started/help-and-support/),
or 🗣️ discuss local cloud development:

- [LocalStack Slack Community](https://localstack.cloud/contact/)
- [LocalStack Discussion Page](https://discuss.localstack.cloud/)
- [LocalStack GitHub Issue tracker](https://github.com/localstack/localstack/issues)

### Contributors

We are thankful to all the people who have contributed to this project.

<a href="https://github.com/localstack/localstack/graphs/contributors"><img src="https://opencollective.com/localstack/contributors.svg?width=890" /></a>

### Backers

We are also grateful to all our backers who have donated to the project. You can become a backer on [Open Collective](https://opencollective.com/localstack#backer).

<a href="https://opencollective.com/localstack#backers" target="_blank"><img src="https://opencollective.com/localstack/backers.svg?width=890"></a>

### Sponsors

You can also support this project by becoming a sponsor on [Open Collective](https://opencollective.com/localstack#sponsor). Your logo will show up here along with a link to your website.

<a href="https://opencollective.com/localstack/sponsor/0/website" target="_blank"><img src="https://opencollective.com/localstack/sponsor/0/avatar.svg"></a>
<a href="https://opencollective.com/localstack/sponsor/1/website" target="_blank"><img src="https://opencollective.com/localstack/sponsor/1/avatar.svg"></a>
<a href="https://opencollective.com/localstack/sponsor/2/website" target="_blank"><img src="https://opencollective.com/localstack/sponsor/2/avatar.svg"></a>
<a href="https://opencollective.com/localstack/sponsor/3/website" target="_blank"><img src="https://opencollective.com/localstack/sponsor/3/avatar.svg"></a>
<a href="https://opencollective.com/localstack/sponsor/4/website" target="_blank"><img src="https://opencollective.com/localstack/sponsor/4/avatar.svg"></a>
<a href="https://opencollective.com/localstack/sponsor/5/website" target="_blank"><img src="https://opencollective.com/localstack/sponsor/5/avatar.svg"></a>
<a href="https://opencollective.com/localstack/sponsor/6/website" target="_blank"><img src="https://opencollective.com/localstack/sponsor/6/avatar.svg"></a>
<a href="https://opencollective.com/localstack/sponsor/7/website" target="_blank"><img src="https://opencollective.com/localstack/sponsor/7/avatar.svg"></a>
<a href="https://opencollective.com/localstack/sponsor/8/website" target="_blank"><img src="https://opencollective.com/localstack/sponsor/8/avatar.svg"></a>
<a href="https://opencollective.com/localstack/sponsor/9/website" target="_blank"><img src="https://opencollective.com/localstack/sponsor/9/avatar.svg"></a>

## License

Copyright (c) 2017-2024 LocalStack maintainers and contributors.

Copyright (c) 2016 Atlassian and others.

This version of LocalStack is released under the Apache License, Version 2.0 (see [LICENSE](LICENSE.txt)). By downloading and using this software you agree to the [End-User License Agreement (EULA)](docs/end_user_license_agreement).
