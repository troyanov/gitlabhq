# Contribute to GitLab

This guide details how to use issues and pull requests to improve GitLab.

-  [Closing policy for issues and pull requests](#closing-policy-for-issues-and-pull-requests)
-  [Issue tracker](#issue-tracker)
-  [Pull requests](#pull-requests)
-  [Contributing process](#contributing-process)

## Closing policy for issues and pull requests

GitLab is a popular open source project and the capacity to deal with issues and pull requests is limited. Out of respect for our volunteers, issues and pull requests not in line with the guidelines listed in this document may be closed without notice.

Please treat our volunteers with courtesy and respect, it will go a long way towards getting your issue resolved.

Issues and pull requests should be in English and contain appropriate language for audiences of all ages.

## Issue tracker

To get support for your particular problem please use the channels as detailed in [the getting help section of the readme](https://github.com/gitlabhq/gitlabhq#getting-help). Professional [support subscriptions](http://www.gitlab.com/subscription/) and [consulting services](http://www.gitlab.com/consultancy/) are available from [GitLab.com](http://www.gitlab.com/).

The [issue tracker](https://github.com/gitlabhq/gitlabhq/issues) is only for obvious bugs or misbehavior in the latest [stable or development release of GitLab](MAINTENANCE.md). When submitting an issue please conform to the issue submission guidelines listed below. Not all issues will be addressed and your issue is more likely to be addressed if you submit a pull request which partially or fully addresses the issue.

Do not use the issue tracker for feature requests. We have a specific [feedback and suggestions forum](http://feedback.gitlab.com) for this purpose.

Please send a pull request with a tested solution or a pull request with a failing test instead of opening an issue if you can. If you're unsure where to post, post to the [mailing list](https://groups.google.com/forum/#!forum/gitlabhq) or [Stack Overflow](http://stackoverflow.com/questions/tagged/gitlab) first. There are a lot of helpful GitLab users there who may be able to help you quickly. If your particular issue turns out to be a bug, it will find its way from there.

### Issue tracker guidelines

**[Search](https://github.com/gitlabhq/gitlabhq/search?q=&ref=cmdform&type=Issues)** for similar entries before submitting your own, there's a good chance somebody else had the same issue. Show your support with `:+1:` and/or join the discussion. Please submit issues in the following format (as the first post):

1. **Summary:** Summarize your issue in one sentence (what goes wrong, what did you expect to happen)
2. **Steps to reproduce:** How can we reproduce the issue, preferably on the [GitLab Vagrant virtual machine](https://github.com/gitlabhq/gitlab-vagrant-vm) (start with: `vagrant destroy && vagrant up && vagrant ssh`)
3. **Expected behavior:** Describe your issue in detail
4. **Observed behavior**
5. **Relevant logs and/or screenshots:** Please use code blocks (\`\`\`) to format console output, logs, and code as it's very hard to read otherwise.
6. **Output of checks**
    * Results of GitLab [Application Check](doc/install/installation.md#check-application-status) (`sudo -u git -H bundle exec rake gitlab:check RAILS_ENV=production`); we will only investigate if the tests are passing
    * Version of GitLab you are running; we will only investigate issues in the latest stable and development releases as per the [maintenance policy](MAINTENANCE.md)
    * Add the last commit sha1 of the GitLab version you used to replicate the issue (obtainable from the help page)
    * Describe your setup (use relevant parts from `sudo -u git -H bundle exec rake gitlab:env:info RAILS_ENV=production`)
7. **Possible fixes**: If you can, link to the line of code that might be responsible for the problem

## Pull requests

We welcome pull requests with fixes and improvements to GitLab code, tests, and/or documentation. The features we would really like a pull request for are listed with the [status 'accepting merge/pull requests' on our feedback forum](http://feedback.gitlab.com/forums/176466-general/status/796455) but other improvements are also welcome.

### Pull request guidelines

If you can, please submit a pull request with the fix or improvements including tests. If you don't know how to fix the issue but can write a test that exposes the issue we will accept that as well. In general bug fixes that include a regression test are merged quickly while new features without proper tests are least likely to receive timely feedback. The workflow to make a pull request is as follows:

1. Fork the project on GitHub
1. Create a feature branch
1. Write [tests](README.md#run-the-tests) and code
1. Add your changes to the [CHANGELOG](CHANGELOG)
1. If you have multiple commits please combine them into one commit by [squashing them](http://git-scm.com/book/en/Git-Tools-Rewriting-History#Squashing-Commits)
1. Push the commit to your fork
1. Submit a pull request
2. [Search for issues](https://github.com/gitlabhq/gitlabhq/search?q=&ref=cmdform&type=Issues) related to your pull request and mention them in the pull request description

We will accept pull requests if:

* The code has proper tests and all tests pass (or it is a test exposing a failure in existing code)
* It can be merged without problems (if not please use: `git rebase master`)
* It does not break any existing functionality
* It's quality code that conforms to the [Ruby](https://github.com/bbatsov/ruby-style-guide) and [Rails](https://github.com/bbatsov/rails-style-guide) style guides and best practices
* The description includes a motive for your change and the method you used to achieve it
* It is not a catch all pull request but rather fixes a specific issue or implements a specific feature
* It keeps the GitLab code base clean and well structured
* We think other users will benefit from the same functionality
* If it makes changes to the UI the pull request should include screenshots
* It is a single commit (please use `git rebase -i` to squash commits)

For examples of feedback on pull requests please look at already [closed pull requests](https://github.com/gitlabhq/gitlabhq/pulls?direction=desc&page=1&sort=created&state=closed).

## Contributing process

### Purpose of describing the contributing process

Below we describe the contributing process for two reasons. Contributors know what to expect from maintainers (initial, response within xx days, friendly treatment, etc). And maintainers know what to expect from contributors (use latest version, confirm the issue is addressed, friendly treatment, etc).

### How we handle issues

The priority should be mentioning people that can help and assigning workflow labels. Workflow labels are purposely not very detailed since that would be hard to keep updated as you would need to reevaluate them after every comment. We optionally use functional labels on demand when want to group related issues to get an overview (for example all issues related to RVM, to tackle them in one go) and to add details to the issue. 

If an issue is complex and needs the attention of a specific person, assignment is a good option but assigning issues might discourage other people from contributing to that issue. We need all the contributions we can get so this should never be discouraged. Also, an assigned person might not have time for a few weeks, so others should feel free to takeover. 

Priority (from high to low):

1. Mentioning people (very important)
2. Workflow labels
3. Functional labels (less important)
4. Assigning issues (optional)

### Workflow labels

- _Awaiting feedback_: Feedback pending from the reporter
- _Awaiting confirmation of fix_: The issue should already be solved in **master** (generally you can avoid this workflow item and just close the issue right away)
- _Attached PR_: There is a PR attached and the discussion should happen there
  - We need to let issues stay in sync with the PR's. We can do this with a "Closing #XXXX" or "Fixes #XXXX" comment in the PR. We can't close the issue when there is a pull request because sometimes a PR is not good and we just close the PR, then the issue must stay.
- _Awaiting developer action/feedback_: Issue needs to be fixed or clarified by a developer

### Functional labels

These labels describe what development specialities are involved such as: PostgreSQL, UX, LDAP.

### Label colors
- Light orange `#fef2c0`: workflow labels for issue team members (awaiting feedback, awaiting confirmation of fix)
- Bright orange `#eb6420`: workflow labels for core team members (attached PR, awaiting developer action/feedback)
- Light blue `#82C5FF`: functional labels
- Green labels `#009800`: issues that can generally be ignored. For example, issues given the following labels normally can be closed immediately (we do have some old ones open that Yves will handle):
  - Feature request (see copy & paste response: [Feature requests](#feature-requests))
  - Support (see copy & paste response: [Support requests and configuration questions](#support-requests-and-configuration-questions)

### Common actions

#### Issue team
- Sets up an email filter for comments from the core development team
- Looks for issues without workflow labels and triages issue
- Monitors pull requests
- Closes invalid issues and pull requests with a comment (duplicates, [feature requests](#feature-requests), [fixed in newer version](#issue-fixed-in-newer-version), [issue report for old version](#issue-report-for-old-version), not a problem in GitLab, etc.)
- Assigns appropriate [labels](#how-we-handle-issues)
- Asks for feedback from issue reporter/pull request initiator ([invalid issue reports](#improperly-formatted-issue), [format code](#code-format), etc.)
- Asks for feedback from the relevant developer(s) based on the [list of members and their specialities](http://gitlab.org/team/)
- Monitors all issues/pull requests for feedback (but especially ones commented on since automatically watching them):
- Assigns issues to developers if they indicate they are fixing it
- Assigns pull requests to developers if they indicate they will take care of merge
- Closes issues with no feedback from the reporter for two weeks
- Closes stale pull requests

#### Development team

- Sets up an email filter for mentions from the issue team (Yves, Ben, and Robert)  
- Responds to issues and pull requests the issue team mentions them in
- Monitors for new issues in _Awaiting developer action/feedback_ with no developer activity (once a week)
- Monitors for new pull requests (at least once a week)
- Manages their work queue by looking at issues and pull requests assigned to them
- Close fixed issues (via commit messages or manually)
- Codes [new features](http://feedback.gitlab.com/forums/176466-general/filters/top)!
- Response guidelines
- Be as kind as possible to people trying to contribute. Be aware that people can be a non-native or a native English speaker, they might not understand thing or they might be very sensitive to how your word things. Use emoji to express your feelings (hearth, star, smile, etc.). Some good tips about giving feedback to pull requests is in the [Thoughtbot code review guide](https://github.com/thoughtbot/guides/tree/master/code-review).

### Copy & paste responses

#### Improperly formatted issue

Thanks for the issue report. Please reformat your issue to conform to the issue tracker guidelines found in our \[contributing guidelines\]\(https://github.com/gitlabhq/gitlabhq/blob/master/CONTRIBUTING.md#issue-tracker-guidelines).

#### Feature requests

Thanks for your interest in GitLab. We don't use the GitHub issue tracker for feature requests. Please use http://feedback.gitlab.com/ for this purpose or create a pull request implementing this feature. Have a look at the \[contribution guidelines\]\(https://github.com/gitlabhq/gitlabhq/blob/master/CONTRIBUTING.md) for more information.

#### Issue report for old version

Thanks for the issue report but we only support issues for the latest stable version of GitLab. I'm closing this issue but if you still experience this problem in the latest stable version, please open a new issue (but also reference the old issue(s)). Make sure to also include the necessary debugging information conforming to the issue tracker guidelines found in our \[contributing guidelines\]\(https://github.com/gitlabhq/gitlabhq/blob/master/CONTRIBUTING.md#issue-tracker-guidelines).

#### Support requests and configuration questions

Thanks for your interest in GitLab. We don't use the GitHub issue tracker for support requests and configuration questions. Please use the \[support forum\]\(https://groups.google.com/forum/#!forum/gitlabhq), \[Stack Overflow\]\(http://stackoverflow.com/questions/tagged/gitlab), the unofficial #gitlab IRC channel on Freenode or the http://www.gitlab.com paid services for this purpose. Have a look at the \[contribution guidelines\]\(https://github.com/gitlabhq/gitlabhq/blob/master/CONTRIBUTING.md) for more information.

#### Code format

Please use ``` to format console output, logs, and code as it's very hard to read otherwise.

#### Issue fixed in newer version

Thanks for the issue report. This issue has already been fixed in newer versions of GitLab. Due to the size of this project and our limited resources we are only able to support the latest stable release as outlined in our \[contributing guidelines\]\(https://github.com/gitlabhq/gitlabhq/blob/master/CONTRIBUTING.md#issue-tracker). In order to get this bug fix and enjoy many new features please \[upgrade\]\(http://blog.gitlab.org/). If you still experience issues at that time please open a new issue following our issue tracker guidelines found in the \[contributing guidelines\]\(https://github.com/gitlabhq/gitlabhq/blob/master/CONTRIBUTING.md#issue-tracker-guidelines).

#### Improperly formatted pull request

Thanks for your interest in improving the GitLab codebase! Please resubmit your pull request following the \[contributing guidelines\]\(https://github.com/gitlabhq/gitlabhq/blob/master/CONTRIBUTING.md#pull-request-guidelines).

#### Inactivity close of an issue

It's been at least 2 weeks (and a new release) since we heard from you. I'm closing this issue but if you still experience this problem, please open a new issue (but also reference the old issue(s)). Make sure to also include the necessary debugging information conforming to the issue tracker guidelines found in our \[contributing guidelines\]\(https://github.com/gitlabhq/gitlabhq/blob/master/CONTRIBUTING.md#issue-tracker-guidelines).

#### Inactivity close of a pull request

This pull request has been closed because a request for more information has not been reacted to for more than 2 weeks. If you respond and conform to the pull request guidelines in our \[contributing guidelines\]\(https://github.com/gitlabhq/gitlabhq/blob/master/CONTRIBUTING.md#pull-requests) we will reopen this pull request.

#### Closing an issue

Avoid using this if possible, more details are better.

This issue has been closed because it doesn't conform to the guidelines, please see https://github.com/gitlabhq/gitlabhq/blob/master/CONTRIBUTING.md#closing-policy-for-issues-and-pull-requests for more information.

#### Closing a pull request

Avoid using this if possible, more details are better.

This pull request has been closed because it doesn't conform to the guidelines, please see https://github.com/gitlabhq/gitlabhq/blob/master/CONTRIBUTING.md#closing-policy-for-issues-and-pull-requests for more information.
