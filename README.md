# ReversingLabs rl-secure GitLab CI Configuration Examples

This repository contains a working example of GitLab workflow to illustrate scanning with the [ReversingLabs Spectra Assure CLI](https://docs.secure.software/cli/).

ReversingLabs Spectra Assure CLI is capable of scanning [nearly any type](https://docs.secure.software/concepts/language-coverage) of software artifact or package that results from a build.

In this example, we're using the source code and Maven build instructions for the Struts2 showcase web app, which came with [Apache Struts v2.5.28](https://archive.apache.org/dist/struts/2.5.28/).

This example relies on the [ReversingLabs GitLab CI integration](https://github.com/reversinglabs/rl-scanner-gitlab-include) and includes it as a remote configuration file.

The following example is provided in this directory:

- **.gitlab-ci.yml**

This example requires that you create the `RLSECURE_ENCODED_LICENSE` and `RLSECURE_SITE_KEY` secrets to store your ReversingLabs [license and site key](https://docs.secure.software/cli/deployment/rl-deploy-quick-start#prepare-the-license-and-site-key).
You can define these secrets via your GitLab repository `Settings -> CI/CD -> Variables`.


## .gitlab-ci.yml

This pipeline configuration file produces the build artifact and scans it using the [ReversingLabs rl-scanner Docker image](https://hub.docker.com/r/reversinglabs/rl-scanner).

In order to be shared between jobs, this build artifact needs to be uploaded directly to the job.

After the file is scanned, analysis reports are saved as pipeline artifacts to the `$REPORT_PATH` directory provided by user as a variable.
