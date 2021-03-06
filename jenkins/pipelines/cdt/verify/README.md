## Eclipse CDT Plug-in Gerrit Verify Pipelines

This directory contains the the Gerrit Verify Pipelines used by the CDT Plug-ins.

The Verify Pipelines are configured on the CDT CI instance on: https://ci.eclipse.org/cdt/view/Gerrit/

## CDT Verify Code Cleanliness

[cdt-verify-code-cleanliness-pipeline](cdt-verify-code-cleanliness-pipeline.Jenkinsfile) runs a series of checks on the code base to ensure that the code base to ensure that various rules (such as formatting, whitespace and version number bumping) are respected in the gerrit patch. See the [script](https://git.eclipse.org/c/cdt/org.eclipse.cdt.git/tree/releng/scripts/check_code_cleanliness.sh) for details.

## CDT Verify Test jobs

The collection of CDT Verify Test jobs run `mvn verify` across the CDT plug-ins. There are multiple jobs to split up the number of tests to turn around the whole gerrit verify faster.

 * [cdt-verify-test-cdt-ui-only-pipeline](cdt-verify-test-cdt-ui-only-pipeline.Jenkinsfile) runs the org.eclipse.cdt.ui tests only and CDT standalone debugger build.
 * [cdt-verify-test-dsf-gdb-only-pipeline](cdt-verify-test-dsf-gdb-only-pipeline.Jenkinsfile) runs all the CDT DSF GDB tests
 * [cdt-verify-test-cdt-other-pipeline](cdt-verify-test-cdt-other-pipeline.Jenkinsfile) runs all the tests not covered by the above jobs. This job also archives a P2 repository to make it easier and quicker to test the gerrit change

## CDT Combined Pipeline

The [cdt-verify-combined-pipeline](cdt-verify-combined-pipeline.Jenkinsfile) job is an experiment in progress to combine all the jobs into one pipeline to have good parallelization without having to redo all the steps.
