## collectd+LLNW customizations

This repo is a sync fork from collectd upstream (see `master` info); LLNW custom
improvements and additions to the existing product are tracked in branches and
shall integrate with upstream.

##### protip to get all tag info from upstream to your local repo.

     git fetch upstream refs/tags/*:refs/tags/*

##### Upstream major version cherry-pick onto new branch

     git rebase --onto LLNW-API-2.2 a495dde~1 upstream/F-LLNW

(Note: helpful comparison: https://github.com/llnw/collectd/compare/collectd-5.4...LLNW-collectd-5.4)

## Repo structure

* Branches
   * `F-*` are feature and/or bug fix branches we maintain on top of upstream
     -STABLE
   * LLNW-collectd-5.4 is the current 5.4-STABLE branch with our patches applied

*  Tags
   *  refs from upstream repo ([compare/collectd-5.4.0...collectd-5.4.1](https://github.com/llnw/collectd/compare/collectd-5.4.0...collectd-5.4.1))
   *  LLNW specific tags are `<release>-llnw<increment from 1>` (e.g. `collectd-5.4.1+llnw1`)

##### master

This is a mirror of upstream master,
https://github.com/collectd/collectd latest (updated by [Jenkins](https://build.llnw.net/view/SysDev-Metrics/job/SysDev-Metrics-collectd_upsteam_sync/))

##### collectd-5.4

This is a mirror of upstream -STABLE for 5.4, and is also automatically syncd.
We develop patches against this pristine branch.

##### LLNW

This is the default branch, with a README.md to explain the repository
structure.

##### LLNW-collectd-5.4

This is the current -STABLE branch.  Patches should be developed against
vanilla collectd-5.4 branch and then merged here.

##### F-METRICS-379-libperl-5.4

* From:  https://github.com/collectd/collectd/pull/390
* Issue: https://github.com/llnw/collectd/issues/1

The perl embed config is supplying incorrect flags to the linker.
This patch is nearly correct and is needed for a successful build on Linux.

##### F-METRICS-383-tsdb-writer-5.4

* From: https://github.com/collectd/collectd/pull/247
* Issue: https://github.com/llnw/collectd/issues/2

Adds an OpenTSDB writer.  No additional dependencies.

##### F-METRICS-384-gstat-5.4

* From: https://github.com/collectd/collectd/pull/341
* Issue: https://github.com/llnw/collectd/issues/3

Adds a gstat plugin for FreeBSD.

##### F-METRICS-380-exec-as-root-5.4

* From: https://github.com/bpiraeus/collectd/commit/0ed4d1724b0d2cd94966e36e0417b14158462edf
* Issue: https://github.com/llnw/collectd/issues/4

Allow exec plugin to maintain root privileges.

##### F-METRICS-385-netstat-5.4

* From: https://github.com/collectd/collectd/pull/247
* Issue: https://github.com/llnw/collectd/issues/5

Adds a netstat plugin for FreeBSD and Linux.

**Warning, breaks build unless configured with --enable-ipv6**
