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

# Sprint Template

Overarching ideas:  

- Developers should work together to close out issues as soon as possible within the sprint rather than waiting until the last possible minute.  Think steady stream of patches.

- Quality checks should be part of accepting the pull request -- make sure you understand the test plan for your issues

- Build in time to plan for upcoming sprints

- Emphasize continuous integration testing

Sprint is 15 work days 

- Day 1 (Wed)
    - End of previous sprint Demo; New sprint start
- Day 2 (Thu)
    - Release doc review for previous sprint
- Day 3 (Fri)
    -  Release announcement for previous sprint sent<br>
    -  List of youtube demos (or playlist) from last sprint publicly available<br>
    -  List of test cases finalized
- Day 5 (Tue) 
- Day 6 (Wed)
    - Development checkpoint
- Day 7 (Thu)
- Day 8 (Fri)
- Day 9 (Mon)
    - Pull requests submitted; all pull requests must have an assignee
- Day 10 (Tue)
- Day 11 (Wed)
    - Sprint End Tags available for integration testing no later than 1800 EST
    - release branch is considered frozen -- anything picked to the release branch should require QE support + release manager approval
    - Start youtube demos
- Day 12 (Thu)
    - Backlog review, start creating new github issues for next sprint, identify high priority bugs to be fixed during next sprint and create github issues for those
- Day 13 (Fri)
    - finalized 'commit list' of bugs found within this sprint that should be addressed in the release branch.
- Day 14 (Mon)
    - Finalize Planning session agenda
- Day 15 (Tue)
    - All bugs from this sprint have been cherry picked to release branch, final release tag
    - Assemble all youtube demos for Sprint End Meeting
    - Next sprint planning meeting, planning Poker for next sprint


Specific dates are on the [team calendar](https://aeolusproject.org/TBD)

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
