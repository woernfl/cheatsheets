# Jenkins

## Global variables

To list global variable add `pipeline-syntax/globals` after your Jenkins URL in a browser, like that `$JENKINS_URL/pipeline-syntax/globals`

`env.$ENV_VAR` Get or set the value of a environment variable

`params.$PARAM_NAME` Get or set the value of a parametre

`currentBuild.result` Get or set the final status of a job. Typically SUCCESS, UNSTABLE, or FAILURE (may be null for an ongoing build)

## Environment variables

To list environment variable add `env-vars.html` after your Jenkins URL in a browser, like that `$JENKINS_URL/env-vars.html`

`BUILD_NUMBER` The current build number, such as "153"

`BUILD_TAG` String of "jenkins-${JOB_NAME}-${BUILD_NUMBER}". All forward slashes ("/") in the JOB_NAME are replaced with dashes ("-").

`BUILD_URL` Full URL of this build, like http://server:port/jenkins/job/foo/15/ (Jenkins URL must be set)

`BRANCH_NAME` For a multibranch project, this will be set to the name of the branch being built.

`GIT_BRANCH` The remote branch name, if any.

`GIT_COMMIT` The commit hash being checked out.

`GIT_PREVIOUS_COMMIT` The hash of the commit last built on this branch, if any.

`GIT_PREVIOUS_SUCCESSFUL_COMMIT` The hash of the commit last successfully built on this branch, if any.

`JOB_BASE_NAME` Short Name of the project of this build stripping off folder paths, such as "foo" for "bar/foo".

`JOB_NAME` Name of the project of this build, such as "foo" or "foo/bar".

`JOB_URL` Full URL of this job, like http://server:port/jenkins/job/foo/ (Jenkins URL must be set)

`WORKSPACE` The absolute path of the directory assigned to the build as a workspace.
