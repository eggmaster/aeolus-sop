# Contact Information

  ---------- -----------------------------
  Owner      Aeolus Team
  Contact:   \#aeolus or aeolus-devel@lists.fedorahosted.org
  Purpose    Release Engineering Process
  Related    N/A
  ---------- -----------------------------

# Description

This SOP focuses on the Aeolus / CloudForms development process. It
describes the schedule and process to make tags, create rpms, tarballs,
and update our upstream release documentation.

# Schedule

Each sprint will have several key days. Sprints begin and end on Thursdays and are three weeks in length (although the following calendar shows days falling in each of four weeks for readability, the Sprint is three weeks long).

-   Tail of Week 3

    -   Friday - All user stories proposed as github Issues
    -   Friday - Issue grooming in preparation for Monday Planning Poker
    -   Friday - All bugfix commits backported to EOS release branch, final release tag
    -   Friday - Release Documentation prepped and staged

-   Week 1

    -   Monday - Sprint planning meeting, Planning Poker, create new Sprint Milestone
    -   Monday - Release Docs reviewed/approved
    -   Monday - End of Sprint Release Announcement posted and emailed
    -   Monday - Previous Sprint demo recording made public
    -   Wednesday - Proposed test cases created for Issues in current Milestone
    -   Friday - User story backlog grooming and prioritization round one

-   Week 2

    -   Monday - Developers update status of open issues
    -   Tuesday - User story backlog grooming and triage
    -   Tuesday - All issues must have corresponding pull request
    -   Wednesday - Open issues must have a reviewer assigned
    -   Thursday - Close of business, End of Sprint tag created in github
    -   Thursday - From this point no new commits land on Sprint tag without manager approval
    -   Thursday - All open issues updated to reflect correct current state
    -   Thursday - Tagged repos handed off to QE for testing

-   Week 3

    -   Monday - QE Bug Scrub and prioritization
    -   Tuesday - Issue grooming, remove milestone on any issues that missed Tag cutoff
    -   Wednesday - All QE issues updated to reflect correct current state
    -   Wednesday - All bugfixes backported to EOS release branch
    -   Thursday - End of Sprint demo


-   Specific dates are on the [team
    calendar](https://aeolusproject.org/TBD)

It's critical to meet deliverables on these dates and not slip items. We
go from planning of new features to minor releases every three weeks and this pace requires a
significant amount of discipline. Also, it means we must keep a focus on
*simplicity*. If something can't be coded, tested and handle any
migrations within 2 weeks, we are probably taking on too much. Simple,
small, and extremely fast - that is our development model.

# Required Git Repos

Currently the four components owned directly by the Aeolus team are

 - conductor - https://github.com/aeolusproject/conductor
 - aeolus-configure - https://github.com/aeolusproject/aeolus-configure
 - aeolus-cli - https://github.com/aeolusproject/aeolus-cli
 - aeolus-image-rubygem - https://github.com/aeolusproject/aeolus-image-rubygem

Additionally, we depend directly on the alchemy ui project

 - ui-alchemy/alchemy - https://github.com/ui-alchemy/alchemy 

Deployment for development and testing are managed using the dev-tools project

 - aeolus-incubator/dev-tools - https://github.com/aeolus-incubator/dev-tools 

# Maintenance of RPM packaging artifacts

For each of the four main components (conductor, aeolus-configure, aeolus-cli, and aeolus-image-rubygem) care should be taken to maintain RPM specfiles, in particular the package dependencies (Requires, BuildRequires) must be updated when new dependencies are introduced to the codebase.

To facilitate packaging for RPM-based downstreams, each package should successfully build an RPM at the end of each Sprint. RPM packages can be created in a git checkout by issuing the following commands in each checkout's top directory:

 - 'make clean; make rpms' (conductor -- Note that converge-ui-devel is required, see following section 'Configuration of alchemy')
 - 'rake rpms' (aeolus-configure, aeolus-cli, aeolus-image-rubygem)

# Configuration of alchemy

Conductor has an RPM BuildRequires on the converge-ui-devel package. To build the converge-ui-devel RPM, check out alchemy (See previous section 'Required Git Repos') and run 'tito build --test --rpm' in the checkout.

# Use of dev-tools for QE testing purposes

As noted previously, the dev-tools scripts are our primary means of providing QE with a consistent, easy-to-configure, multi-distro installation method for testing.

 - aeolus-incubator/dev-tools - https://github.com/aeolus-incubator/dev-tools 

# Organization of Upstream Releases

WORK IN PROGRESS
