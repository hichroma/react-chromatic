# 0.8.4 - 2017-06-07

* Fix an issue for stories that use `navigator.mimeTypes`

# 0.8.3 - 2017-04-26

* Fix a bug where sometimes the package did not detect the checked out branch.

# 0.8.2 - 2017-04-18

* Better support for rebasing branches - we now always treat the last build on this branch as a baseline, even if strictly it is not a git ancestor of the current commit. This helps deal with the situation where you rebase a branch off master, and still want to use the previously approved snapshots.

* Improved support for CI systems, especially _Netlify_ and _Travis PR builds_. Travis PR builds are a special case, read more about how to handle them in Chromatic here: https://docs.chromaticqa.com/setup_ci#travis

# 0.8.1 - 2017-03-28

* Fix a small bug in the git algorithm for old Chromatic projects.

# 0.8.0 - 2017-03-28

* Reworked the git baseline detection algorithm to use a different technique that should be more reliable across many different modes of usage.

* Gather stories from Storybook 3.4 without requiring direct installation.

* Added `--auto-accept-changes` to avoid approvals on certain branches

* Added `--only` flag to run a single story

# 0.7.11 - 2017-03-15

* Handle the case where the last few Chromatic builds were run against commits which are no longer in the repository (due to rebasing or squashing). This could cause the tool to crash or fail to find a baseline for a build.

* Add a `--url` argument to allow running tests against arbitrary running apps.

# 0.7.10 - 2017-02-22

* Small API change for querying build change counts.

# 0.7.9 - 2017-01-23

* Our test script now warns you if your storybook logs any errors. This can sometimes help reveal subtle problems that are caused by the script evaluating your storybook in JSDOM. If you have legitimate things logged to `console.error` this may cause noise---you should probably get rid of them.

# 0.7.8 - 2017-01-18

* We no longer write your app code to your `package.json` by default; instead we prefer you pass it via the `CHROMATIC_APP_CODE` environment variable. (You can still optionally use `--app-code=xyz` if you are comfortable with the security of your `package.json`).

* We now show the final part of your Story's kind as the component name in the Chromatic UI. So "Webapp/UserList" will appear in Chromatic as "UserList".

# 0.7.7 - 2017-12-21

* This version sends us a little more information about the environment the package runs in -- is it CI? which package version?

# 0.7.6 - 2017-12-19

* Fix an issue where we did not pass the context to stories in the right format.

# 0.7.5 - 2017-12-19

* We detect a running process on your app's port and don't try and start the app if so. Pass `--do-not-start` if you've already started the app.

# 0.7.3 - 2017-12-09

* We now upload your application bundle to our tunnel server directly from the package.
  This means that on slower uplinks, we no need to set arbitrary timeouts in our server process; instead we simply will not start your Chromatic build until we've verified the bundle has uploaded successfully.
