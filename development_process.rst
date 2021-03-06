==================================
OpenCMISS-Iron Development Process
==================================

This page details the development process that should be followed for OpenCMISS-Iron.

----------------
Before you begin
----------------

Before you begin you should:

- Familiarise yourself with the latest coding style (see \ref code_style)

- Study the git workflow (see http://sourceforge.net/apps/mediawiki/opencmiss/index.php?title=Git_Workflow)

- todo: In the setup document add info about creating a post-commit hook.

-------------------
Development Process
-------------------

The development process that should be followed is:

1. Discuss your problem and proposal either at the OpenCMISS-Iron meeting or on the mailing list. 

2. Create a tracker item for your work.

3. Create a git branch for your work and check it out.

4. Commit and push your changes often to your repository with appropriate commit messages (including the tracker number with a “tracker item” before the number so that the post-commit hook will add a link to the tracker). Commit small and often!

5. Write a test example if possible or practicable.

------------------
Committing Process
------------------

The committing process that should be followed is:

1. The commit message format should be summary, blank line, tracker item number, blank line, more detail.

2. Update the tracker often so as to reflect the progress and problems faced. Make the tracker tell the story of the change! Some of this will be done by the post-commit hook but add extra comments if required.

3. Run tests on your changes and run all the examples on buildbot to make sure that they all pass. Include a buildbot link to the build in the tracker. 

4. Make sure all compiler warnings are addressed.

5. When you are ready to have your code merged back into the trunk create a “pull request” for your changes. The tracker item should be changed to “resolved/fixed”.

6. Approach or nominate people to review your changes and place this information in the tracker. 

--------------
Review Process
--------------

The review process that should be followed is:
1. Once you have accepted the role of reviewer change the tracker to assign it to yourself.

2. Go through the code and make comments on the GitHub pull request on any required changes and corrections and/or questions about the code. 

3. You should review coding style, code clarity, existence of tests, implementation method, documentation, OpenCMISS-Iron notes. 

4. During the review the commit messages should state what has changed and be independent of the review comments. 

5. The reviewer should ensure that the examples run using the buildbot sandbox.

6. When the review has finished and the code is ready to be pulled into the main repository the reviewer should add a comment to this effect in GitHub and the tracker. The code reviewer should change the tracker status to “verified/fixed”.

7. Once the tracker item has been changed to verified/fixed and the repository manager is happy with the process they will pull the code into the repository and changed the tracker item to “closed/fixed”.	

---------------------
Collaboration Process
---------------------

The collaboration process that should be followed is:

1. The collaboration process should be very similar to the commit process above (with the exception of changing the tracker status).

2. If developers are working particularly close on an item git and GitHub allow for other modes of collaboration. A few of these include:

  -  Set up each of your collaborators' repositories as a remote and then merge their changes into your repository.
  
  -  Give collaborators access to your repository so that they can push changes directly.
