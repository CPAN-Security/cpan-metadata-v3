# CPAN Metadata v3 Specification

Status: **EXPERIMENTAL**

## Background

Version 2 of the [CPAN Meta Spec])https://metacpan.org/release/RJBS/CPAN-Meta-2.150013/view/lib/CPAN/Meta/Spec.pm) (CPAN distribution metadata specification) is does not allow the addition of new data, except using fields prefixed by "x_".

However, there is a need to include additional metadata about:
- external dependencies (libraries, files, environment)
- embedded external libraries
- licensing
- vulnerability reporting
- fixed vulnerabilities
- parent-child relationships (e.g. forked project)
- code and documentation generated through automation or using LLMs
- enumeration of community health documents

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

The purpose of this specification is to allow optional and enhanced tools to meet the needs of downstream distributors and users of CPAN modules:
- installation and configuration of external dependencies
- enumeration of all external and embedded dependencies for security auditing and regulatory compliance
- enumeration of all licenses for legal compliance

## Specification

Most of this data would reside in a [metadata directory](metadata-directory.md).

The files in the metadata directory would have [well-known and reserved](well-known-names.md)

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