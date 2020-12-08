# Jenkins Job Builder - examples

> Work in Progress!

[Jenkins Job Builder][jjb-docs] is program than can generate Jenkins _Jobs_ and
_Views_ from YAML Template. First commit comes from [Monty Taylor][monty-wiki]
who helped to create [OpenStack][openstack]. Full source code is available on
[Jenkins Job Builder repository - OpenDev][jjb-git].

How it works:

* it reads YAML template
* it generate XML job definition - here it ends in `test` mode
* it will call Jenkins API and create/update job on Target
  Jenkins - in `update` mode

## Setup

* Tested host OS: `Debian 10`
* Tested Jenkins: `2.257`

Requirements:

* you must have installed, configured and running _Jenkins CI_ somewhere
* you need to generate API Token on Jenkins UI for user with enough privileges.

To install _Jenkins Job Builder_ on Debian 10 do this:

```bash
sudo apt-get install python3-jenkins-job-builder \
   jenkins-job-builder-doc jenkins-job-builder yamllint git
```

Now copy initial configuration example to its target directory:

```bash
mkdir -p ~/.config/jenkins_jobs/
cp /usr/share/doc/jenkins-job-builder/examples/jenkins_jobs.ini-sample \
   ~/.config/jenkins_jobs/jenkins_jobs.ini
  507  vim ~/.config/jenkins_jobs/jenkins_jobs.ini
```

Now you need to edit in `~/.config/jenkins_jobs/jenkins_jobs.ini` at least
these entries under `[jenkins]` section:

* `user=` - your Jenkins User
* `password=` - your Jenkins **API Token**
* `url=` - your Jenkins base URL

And finally (and obviously) checkout this project:

```bash
mkdir -p ~/projects
cd ~/projects
git clone https://github.com/hpaluch/jenkins-job-builder-examples.git
cd jenkins-job-builder-examples
```

## Deploying first example

Optional: Test your YAML file with `yamllint`:

```bash
yamllint hello-jjb.yaml
```

NOTE: Some errors seem to be a bit ridiculous for me (for example
treating empty line at the end of file as error).

At first run with argument `test` - it will parse YAML and dump job XML
definition on standard output:

```bash
jenkins-jobs test hello-jjb.yaml
```

To really create and/or update this job on target Jenkins, use command:

```bash
jenkins-jobs update hello-jjb.yaml
```

Now you can login to your Jenkins - there should be job called `hello-jjb` and you
can run it.

> NOTE: The `hello-jjb.yaml` job expects that your Jenkins Node is Running on
> Unix (including Linux)

TODO: How to remove comment in Job description

[jjb-docs]: https://jenkins-job-builder.readthedocs.io/en/latest/
[jjb-git]: https://opendev.org/jjb/jenkins-job-builder
[monty-wiki]: https://en.wikipedia.org/wiki/Monty_Taylor#OpenStack
[openstack]: https://www.openstack.org/
