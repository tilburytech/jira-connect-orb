# JIRA Connect orb  

A fork of the official Circle CI Jira Orb that works with CT build practices. As part of the "Where is my feature?" workstream we've forked this orb and customised it to either use our internal tooling or to use a file provided.

## Setup
This Orb uses the existing Atlassian Jira token that can be configured for CircleCI Projects and requires that [CircleCI for Jira](https://marketplace.atlassian.com/apps/1215946) be installed in the Jira instance.  Please see [CircleCI Jira integration docs](https://circleci.com/docs/2.0/jira-plugin/)

## Usage

In order to use this too commit and PR messages must contain JIRA keys i.e.

`git commit -m "Working on CC-21"`

Then in a build you need to include the notify step, the simplest form, which pulls tickets in the commit in the build and 
then regsiters a build in Jira is

```
- jira/notify
```

To send a deplotment to Jira using tickets found by another job use

```
- jira/notify:
    job_type: deployment
    environment: dev
    environment_type: development
    issue_keys_filename: /tmp/wismf/tickets.txt
```

### Example Build in Jira
![Jira developer panel with CircleCI build info](/assets/new_issue_view.png)

### Example Deployment in Jira

![Jira developer panel with CircleCI build info](/assets/deployment_support.png)
