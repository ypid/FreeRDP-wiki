The following guidelines and rules should be used for releases.

# Versioning

Freerdp uses a x.y.z[-rcx] versioning scheme where
* x is the major version - this will be incremented when major steps are made or after architectural changes
* y defines the API version - this will be incremented when the public API is changed and not backwards compatible anymore.
* z patch version - incremented after bug fixes - no changes to the public API.

For release canidates the suffix -rc with an number will be used to indicate that this is not the final release.

## Tags
Tags should be in the format of the version string described above (x.y.z[-rc]) . Like 1.0.1-rc1, 1.2.2


# Branches

The main git repository on github should consist of the following branches:
* **master** - development branch - used from developers - should build all the time but might be "broken"
* **stable-x.y** - stable versions. Created from master before a new release is initiated (~ every 4 months). **No new features** are added and the API must not change for a version after the first release. The stable branch is to stabelize a version and for fix bugs. The latest stable branch should be used from **end users and distributions**. After a new stable branch was created only important bug fixes are made to older stable branches. A old stable branch is kept around as long as required.

Other branches should be kept in the developer repositories.

# Bug fixes

Issues found in the latest stable branch should be fixed in master and picked/merged to the stable branch afterwards.
Critical issues found in master should also be merged/picked to the latest stable branch.
If cherry-picking is used the -x parameter must be used in order to record the source commit of the pick.

When possible a test case should be added for an issue in order to make regression tests for new releases.

# Release procedure

Each release follows the following procedure:

* If it's a new major release create a stable-x.y branch
* Create a release canidate (rc)
* A release candidate must pass all available tests
* A release candidate should be tested agains a predefined test matrix (e.g. win7, win8, nla/rdp/tls..) - tbd

## Creating the release
* Create a (signed) tag for the release
* Create tarball/packages/...
* Write an announcement/blog post/...