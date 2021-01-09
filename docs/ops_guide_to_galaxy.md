# ~~hitchhiker's~~ Ops guide to the galaxy

This document has the objective to address several questions that starts with "How do I ... ?"

# How do I know which version of a package is available in the Portage tree

We pin Portage versions by using packages that are shipping a version of it.
This guarantees that there are no moving parts, and we can in this way provide updates as part of a development lifecycle.

We have an automated bot that automatically opens PR to track new version of the available Portage version. The package is available here: https://github.com/mocaccinoOS/desktop/tree/master/packages/portage. You don't need to do it manually. Just wait for a PR from `MarvinHatesOceans` to pop-up, we will review it and merge it only when we decide (after proper QA) that a development lifecycle is over.

## So, how do I know which portage I can build things against?

At the moment is as easy as browsing the portage git and point it at the same commit of our package. 

For example:

`git.hash: "b0e157b071cb23b348acab3d596b49f66c244808"` in https://github.com/mocaccinoOS/desktop/blob/e9ae4aafead5a79d1d36630c932d907361d8c93c/packages/portage/definition.yaml#L6 tells you that we are pinning at commit `b0e157b071cb23b348acab3d596b49f66c244808` of portage tree. So you can e.g. point your browser at : https://github.com/gentoo/gentoo/tree/b0e157b071cb23b348acab3d596b49f66c244808

# How do I revbump a package? (and when it's actually needed?)

By convention, we have chosen to increment the version of a package after the `+`, following [semver](https://semver.org/) notation.

That means, if a package version is at `1.0.0`, it's revbump version would be `1.0.0+1`, and a subsequent one would be for example `1.0.0+2`.

## When I do need to bump a package?

Only when there is a new version available!

## When I do need to revbump a package?

A Package revbump is necessary when you apply changes to `build.yaml`, although, it's not always necessary, but just in few cases:

- When you change `steps` in the `build.yaml`
- When you change `prelude` in the `build.yaml`
- When you change `requires` in the `build.yaml`

## What about packages depending on it?

Always by convention, we have chosen to revbump __manually__ those. Luet does support tracking automatically new package versions, but we want to make this transparent in the Git repository, so reverting changes introduced by mistakes it's easier, and so we also rely on the caching mechanism of Luet.

If we don't revbump reverse dependencies our CI would skip such changes, because we enforced this by policy.

## How do I do that?

Until https://github.com/mocaccinoOS/desktop/issues/7 is delivered, it is a manual process.

# How do I add a useflag to a Portage package? 

# How do I try my changes?

# How do I update provides list, and what are they?

# How do I add a package?

# How do I know that a package belongs to a Layer?