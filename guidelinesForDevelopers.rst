=========================
Guidelines for developers
=========================

These actions will improve traceability: making sure that the plan in the tracker is kept up-to-date with changes in the code, and that it is possible to easily see which code changes relate to which parts of the project plan.

---------------------
Commit code regularly
---------------------

* Rather make many small commits than one large commit.

---------------------
Commit comment refers to tracker item
---------------------

* All commit comments must refer to the tracker item that the work relates to by including the phrase "Tracker item ####", (where ####) is the tracker item number. If there isn't a relevant tracker item, then first create one.

---------------------
Update tracker item after committing code**
---------------------

* For most commits, explain how the commit affects the status of the tracker item (usually this is just a brief progress update). This must include a reference to the commit id, using the syntax "revision o####", where #### is the commit id, e.g. "revision o672". The tracker is set-up to create a hyper-link to the SVN viewer.
* Note: If the code commit is trivial, and really does not affect the status of the tracker item or represent progress worth mentioning, then there is no need to update the corresponding tracker item, but still check to see if a status update is needed, e.g. for cases where many small changes achieve a larger goal.

---------------------
Automated tests
---------------------

* Code commits must either include code for automated tests, or already be tested by existing automated tests. Ensure that new automated tests are added to the BuildBot script, and check the next day that they ran and passed.

---------------------
Keep an eye on changes and test results
---------------------

* Developers need to subscribe to the mailing list for automated notifications so that they are notified of new code commits by others as well as of BuildBot testing results.

---------------------
Review others' code`
---------------------

* Please take the time to review code that others have committed. If you have done even just a partial review, please add a comment to the tracker item for the code commit stating at least that a partial review was done. Preferably add further comments based on the review.

---------------------
Continuous improvement
---------------------

* Be on the lookout for ways to do things better. If you see a way of improving aspects of these practices, or anything about the way we work, talk about it and let's make it happen. Rather than defending the way things are done, let's all be open to suggestions on how our code or our project practices can be improved.

---------------------
Validation steps
---------------------

Ensure that the following validation etc. has been done for each solution type:

1. Solve on a 2D rectangular grid (commit as part of automated tests).

2. Compare against analytic solution (commit as part of automated tests).

3. Test convergence (document in tracker).

4. Solve in 3D (commit as part of automated tests).

5. Solve on complex geometry (commit as part of automated tests, i.e. commit result as "expected answer", automatic test compares result to "expected answer", so that any changes can be investigated).

6. Scalably parallelise (include a parallel test in automated testing).

7. Works with different interpolation schemes.

8. Works with different element types.

9. Document:

   a. the theory
   
   b. the implementation
   
   c. the examples

(commit documentation to version control system. Check the next day that automated builder generated the documentation).
