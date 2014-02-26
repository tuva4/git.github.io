---
layout: default
title: SoC 2014 Applicant Microprojects
---

## Introduction

It is strongly recommended that students who want to apply to the Git
project for the Summer of Code 2014 submit a small code-related patch
to the Git project as part of their application.  Think of these
microprojects as the "Hello, world" of getting involved with the Git
project; the coding aspect of the change can be almost trivial, but to
make the change the student has to become familiar with many of the
practical aspects of working on the Git project:

* Downloading the source code: clone the repository using the
  [Git via Git](http://git-scm.com/downloads) instructions and read
  the `README` file.

* Build the source code: this is described in the file `INSTALL`.

* Glance over our coding guidelines in the file
  `Documentation/CodingGuidelines`.  We take things like proper code
  formatting very seriously.

* Read about the process for submitting patches to Git: this is
  described in `Documentation/SubmittingPatches`.

* **Making the actual change.**  (Funny, this is the only part they
  teach you about in college.)

* Run the test suite: this is described in the file `t/README`.  (If
  you have added new functionality, you should also add tests, but
  most microprojects will not add new functionality.)

* Commit your change.  Surprise: we use Git for that, so you will need
  to gain at least
  [a basic familiarity](http://git-scm.com/documentation) with using
  Git.  Make sure to write a good commit message that explains the
  reason for the change and any ramifications.  Remember to make sure
  that you agree with our "Developer's Certificate of Origin" (whose
  text is contained in `Documentation/SubmittingPatches`), and to
  signify your agreement by adding a `Signed-off-by` line.

* Submit your change to the Git mailing list.  For this step you
  probably want to use the commands `git format-patch` and `git
  send-email`.

* Expect feedback, criticism, suggestions, etc. from the mailing list.

  *Respond to it!* and follow up with improved versions of your
  change.  Even for a trivial patch you shouldn't be surprised if it
  takes two or more iterations before your patch is accepted.  *This
  is the best part of participating in the Git community; it is your
  chance to get personalized instruction from very experienced peers!*

The coding part of the microproject should be very small (say, 10-30
minutes).  We don't require that your patch be accepted into master by
the time of your formal application; we mostly want to see that you
have a basic level of competence and especially the ability to
interact with the other Git developers.

When you submit your patch, please mention that you plan to apply for
the GSoC.  This will ensure that we take special care not to overlook
your application among the large pile of others.

## Ideas for microprojects

The following are just ideas.  Any small code-related change would be
suitable.  Just remember to keep the change small!  It is much better
for you to finish a small but complete change than to try something
too ambitious and not get it done.

1.  Rewrite `git-compat-util.h:skip_prefix()` as a loop, so that it
    doesn't have to scan through the `prefix` string twice.

2.  Change `branch.c:install_branch_config()` to use `skip_prefix()`.

3.  In `branch.c:setup_tracking()`, figure out where the magic number
    `1024 - 7 - 7 - 1` comes from.  (Looking through the commit
    history might help.)  If the check involving the number is still
    necessary, document where the number comes from.  If the check is
    no longer necessary, explain why and delete the check.

4.  Rewrite `bulk-checkin.c:finish_bulk_checkin()` to use a `strbuf`
    for handling `packname`, and explain why this is useful.  Also
    check if the first argument of
    `pack-write.c:finish_tmp_packfile()` can be made const.

5.  Change `bundle.c:add_to_ref_list()` to use `hashcpy()`.  See if
    you can find other places where `hashcpy()` should be used instead
    of `memcpy()`.

6.  Change `bundle.c:add_to_ref_list()` to use `ALLOC_GROW()`.