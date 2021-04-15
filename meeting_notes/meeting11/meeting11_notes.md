---
title: Full Notes
parent: 11. Meeting, Apr 12 2021
grand_parent: Meeting Notes
has_children: false
nav_order: 1
---

# Eleventh Meeting: Monday APR 12 3:00 - 4:00pm UTC

## Welcome:
* Vanessa from Agoric

## Updates:
* Chain registry github:
	* Updated to latest sdk version
	* Testing a new version that can check chains periodically
	* Goes beyond seed nodes
	* Open questions: When shall chains be declared as "inactive", current suggestion 5 re-tries
* Update tutorial to verify IBC assets:
	* Necessary cosmjs code is present but released yet
	* Client sync status is currently difficult to determine, will probably not be fixed before the release of the tutorial
* Project Intros:
	* Nass working on a Navigator with a focus on DeFi:
		* Currently focusing on "single-hop" assets
		* Multi-hop assets need to be redeemed
		* Covering tx fees, for redeeming assets is currently an open issue leading to a sub-optimal UX, but there is hope for the next version