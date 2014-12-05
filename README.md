Automated-CI-Service
====================

An series of tools to help facilitate automated continuous integration service

## Technologies
* git - Using [githooks](http://git-scm.com/book/en/v2/Customizing-Git-Git-Hooks) (see git-hooks folder),
we bind git events such as commit, push etc and create events such as validating code commit using LINT'ing
tools or firing off a curl request to the jenkins service to start a new job based on some parameters.

* jenkins - The [Jenkins-CI](http://jenkins-ci.org) service helps facilitate continuous integration by
working as the job manager for project test cases.

* docker - With the help of [docker.io](http://docker.io) containers we isolate and load custom testing
environments (determined by the project githooks & configuration parameters) for the target project.

* ansible - Using [ansible](http://ansible.com) (see ansible-toolkit folder) shipped with this project allows for easy
grouping & management using predefined templates for various services which helps ensure each docker
container can be syncronized and customized for various roles etc.

