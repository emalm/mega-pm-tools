# mega-pm-tools

Here are some scripts and README's to automate and simplify the work of a Cloud Foundry/the MEGA team PM.  For extra ease of use, install `direnv` (see `ws-setup.md`) and add an `.envrc` file to this directory with the approriate environment variables exported.

## Mailing List Tracker Issue

If an email from the cf-dev or cf-bosh mailing list appears in your inbox and you think it's relevant to your team, copy the email subject (e.g. \[cf-dev\] I can haz cloud?) and then paste it and pipe it to the `ml-issue` script:

```
pbpaste | ./ml-issue
```

You will need to have the following environment variables exported:
- `TRACKER_API_TOKEN`
- `MEGA_PROJECT_ID`
- `MEGA_PM_ID`

## Release Candidate SHA of cf-release for Cloud Ops

If the previous Cloud Ops deployment of cf-release was, say, 213, then you can use the `prod-gist` script to generate a Gist with a release candidate SHA from the `release-candidate` branch, as well as a diff of all the job spec and manifest template changes.  The script will also comment on Cloud Ops' deploy checklist with a link to the Gist, along with some other data and @-mentions of other PMs involved:

```
./prod-gist 213
```

You will need to have the following environment variable exported:
- `GH_ACCESS_TOKEN`

## Release Notes Tracker Story

When Cloud Ops creates a Github release on cf-release, a Concourse job can automatically create a Tracker story in the MEGA backlog assigned to the PM to write release notes.  `rel-notes.yml` provides a task configuration which consumes the cf-release Github release resource and creates the Tracker story.

## PM Workstation Setup

`ws-setup.md` has everything you need to know to set up your machine.  Don't bother with chef, sprout, etc.
