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
   jenkins-job-builder-doc jenkins-job-builder git
```

Now copy initial configuration example to its target directory:

```bash
mkdir -p ~/.config/jenkins_jobs/
cp /usr/share/doc/jenkins-job-builder/examples/jenkins_jobs.ini-sample \
   ~/.config/jenkins_jobs/jenkins_jobs.ini
  507  vim ~/.config/jenkins_jobs/jenkins_jobs.ini
```
Now you need to edit in `~/.config/jenkins_jobs/jenkins_jobs.ini` at least:
- `user=` - your Jenkins User
- `password=` - your Jenkins **API Token**
- `url=` - your Jenkins base URL

And finally (and obviously) checkout this project:

```bash
mkdir -p ~/projects
cd ~/projects
git clone https://github.com/hpaluch/jenkins-job-builder-examples.git
cd jenkins-job-builder-examples
```
## Deploying first example

TODO:

[jjb-docs]: https://jenkins-job-builder.readthedocs.io/en/latest/
[jjb-git]: https://opendev.org/jjb/jenkins-job-builder
