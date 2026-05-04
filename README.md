# CPAN Metadata v3 Specification

Status: **EXPERIMENTAL**

## Background

Version 2 of the [CPAN Meta Spec](https://metacpan.org/release/RJBS/CPAN-Meta-2.150013/view/lib/CPAN/Meta/Spec.pm) (CPAN distribution metadata specification) is does not allow the addition of new data, except using fields prefixed by "x_".

However, there is a need to include additional metadata about:

- external dependencies (e.g. services, libraries, files, or environment variables)
- embedded external libraries (e.g. zlib or bootstrap)
- licensing
- vulnerability reporting
- parent-child relationships (e.g. forked project)
- fixed vulnerabilities in this fork or in embedded libraries
- code and documentation generated through automation or using LLMs
- how and where to report security vulnerabilities
- project funding and sponsorship
- how the project is supported by maintainers beyond issue trackers
- enumeration of community health documents (e.g. security policy, governance, AI policy, code of conduct)

This is too much information to embed in existing `META.json` files, and
some of this metadata exists in alternative formats, for example:

- SBOM files
- Attestations
- VEX files
- Common Lifecycle Enumeration (CLE)
- Project Description (DOAP) file [1]
- OSSF Security Insights File [2]
- REUSE [3]

## Purpose

Note that most of this data is not necessary for installing CPAN modules. It exists mainly for documentation and auditing.
It will allow optional and enhanced tools to meet the needs of downstream distributors and users of CPAN modules:

- installation and configuration of external dependencies
- enumeration of all external and embedded dependencies for security auditing and regulatory compliance
- enumeration of all licenses for legal compliance
- generating SBOMs for an application using its dependencies
- auditing software for security vulnerabilities
- displaying the external documentation for a module that might not normally be installed, such as the security or governance policy

## Specification

Most of this data would reside in a [metadata directory](metadata-directory.md).

The files in the metadata directory would have [well-known and reserved](well-known-names.md)

Note that additionals to the standards can be made by adding a new file or directory to the metadata directory.

There may also be [external metadata archives](external-metadata-archive.md) for existing distributions that do not have this metadata.

## Tooling

Tooling will be needed to minimise the workload for project maintainers.

The tools will be experimental.

Because there are many different kinds of metadata,
we expect a CPAN Meta v3 system to support plugins for different kinds of meadata.

Modules should be configurable, testable and installable without any tools that support this specification.
However, metadata may be useful for tools that understand them, for example, to ensure external dependencies are met.

## References

[1] https://maastrichtu-ids.github.io/doap-workshop/

[2] https://github.com/ossf/security-insights

[3]  https://reuse.software/spec-3.3/