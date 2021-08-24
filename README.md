![Envoy Logo](https://github.com/envoyproxy/artwork/blob/main/PNG/Envoy_Logo_Final_PANTONE.png)
[Cloud-native high-performance edge/middle/service proxy](https://www.envoyproxy.io/)

Envoy is hosted by the [Cloud Native Computing Foundation](https://cncf.io) (CNCF). If you are a
company that wants to help shape the evolution of technologies that are container-packaged,
dynamically-scheduled and microservices-oriented, consider joining the CNCF. For details about who's
involved and how Envoy plays a role, read the CNCF
[announcement](https://www.cncf.io/blog/2017/09/13/cncf-hosts-envoy/).

# Ambassador Envoy

This repository tracks the patched version of Envoy maintained by
Ambassador Labs for use in Ambassador Edge Stack / Emissary Ingress
(née Ambassador API Gateway) (collectively: "Edgissary").

Because this repository tracks a set of patches that are added to
upstream Envoy, branches often get rebased.  Here is a list of the
refs that you will find in this repository, and what your expectations
around them should be.

 - branch: `readme`: This branch, which exists to document conventions
   for Git refs in the repository (and to have a HEAD branch that
   won't cause Dependabot to spam us).
 - branches: `rebase/*`: The `rebase/` prefix indicates that these
   branches periodically get rebased, either on to newer upstream
   commits or to clean up the commit history.  You shouldn't be
   surprised if these refs get forced updates.
 - branch: `rebase/main`: The primary branch that development happens
   on.  New features or fixes are usually PRed in to this branch.
 - tags: Tags are immutable and should never change.
 - tags: `vX.Y.Z`: Upstream Envoy tags
 - tags: `ambassador-X.Y.Z`: The particular version of Envoy that was
   included in a given version of Edgissary.  A new tag is not created
   for each new Edgissary release; only when Edgissary changes Envoy
   versions.  For instance, there is an `ambassador-1.12.0` tag and an
   `ambassador-1.12.3` tag; it may be assumed that Edgissary 1.12.1
   and 1.12.2 used the Envoy pointed to by the `ambassador-1.12.0`
   tag.
 - tags: `ambassador-X.Y.Z-rebase`: The same content as the
   `ambassador-X.Y.Z` tag, but rebased to have a cleaner history.
   This is most frequently used after releasing a security update that
   had been under embargo; the `ambassador-X.Y.Z` tag will have the
   security fixes applied from the patches that are emailed out to the
   Envoy distributors mailing list, and the `ambassador-X.Y.Z-rebase`
   tag will have that rebased on to the commits that were pushed to
   the upstream [`envoy.git`](https://github.com/envoyproxy/envoy).
   Other times, it may simply be to clean up the history in
   preparation to update to a newer version of Envoy.
 - tags: `datawire-vX.Y.Z-N-gHASH`: Pins a commit that was used at
   some point by
   [`ambassador.git`](https://github.com/datawire/ambassador) but
   perhaps did not end up in an actual release.
