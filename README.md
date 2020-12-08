# Jenkins Job Builder - examples

> Work in Progress!

[Jenkins Job Builder][jjb-docs] is program than can generate Jenkins _Jobs_ and _Views_ from
YAML Template. It has origin from OpenStack community. Full source
code is available on [Jenkins Job Builder repository][jjb-git].

How it works:

* it reads YAML template
* it generate XML job definition - here it ends in `test` mode
* it will call Jenkins API and create/update job on Target Jenkins

# Setup

Tested host OS: `Debian 10`

Requirements:
- you must have installed, configured and running _Jenkins CI_ somewhere
- you need to generate API Token on Jenkins UI for user with enough privileges.

To install _Jenkins Job Builder_ on Debian 10 do this:

```bash
sudo apt-get install python3-jenkins-job-builder \
   jenkins-job-builder-doc jenkins-job-builder
```

TODO ...


[jjb-docs]: https://jenkins-job-builder.readthedocs.io/en/latest/
[jjb-git]: https://opendev.org/jjb/jenkins-job-builder
