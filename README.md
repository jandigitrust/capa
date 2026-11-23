# Capability Authority (CapA)

CapA is a domain authority for attested workloads. It evaluates whether a domain’s execution policy permits a workload to perform a particular operation and can issue a capability scoped to the subject, resource, and operation.

## How CapA makes a decision

CapA maintains the reference values and security context it uses to evaluate workloads. For a particular decision, it considers the applicable execution policy, the evidence about the workload’s state, and relevant information such as vulnerability advisories.

For example, a domain may permit an inference service to accept requests only while its loaded software meets the domain’s policy. A new advisory can change whether the service is eligible to accept requests even when its binaries and their measurements remain unchanged. The decision depends on whether the affected library build is loaded and what the policy requires.

## Working with MIRON

[MIRON](https://github.com/jandigitrust/miron) can reconstruct which library build is loaded in a particular service instance and identify the observations that support that conclusion. CapA can use that result to determine whether the advisory affects the service’s eligibility to accept new requests.

CapA can also supply MIRON with authenticated updates and delegate specific local responses. If domain policy calls for restricting new requests, MIRON can plan that response within its delegated authority. A gateway can apply the restriction. Subsequent observations establish whether it took effect.

## Scope of authority

A capability expresses permission within the issuing domain’s mandate. For example, a domain operator may authorize an inference service to run. If processing a particular dataset also requires the data owner’s permission, the owner or an authorized delegate must grant that permission separately.
