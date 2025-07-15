# Release Notes Guidelines

A developer writing release notes needs to describe the change in terms of the enhanced experience to the end-user, such as changes to the documentation or APIs.

## Tenant Release Notes

It is a Developer Studio **requirement** for all tenants to document onboarding and ongoing changes to the content. This document describes:

- Github structure for release notes
- Location of release notes in document tree
- Release notes sections

**GitHub structure** for release notes is `tenant-name/docs/release-notes/2022.md`.
Developer Studio began mandating the specific location in order to make it uniform across all tenants and to index release notes in the future.

- For example, the Developer Studio release notes are located at: `developer-studio-support/docs/release-notes/2022.md`

**The left navigation** structure for tenant documents is defined by _tenant-name/config/document-explorer-definition.yaml_ file.

- For example, the Developer Studio document tree should be located at: `developer-studio-support/config/document-explorer-definition.yaml`

The requirement is to have Release notes section at the top level/tier of the document tree.

- sections:
  - title: Getting Started
    link: docs/getting-started.md
  - title: Release notes
    sections:
    - title: 2022
      link: docs/release-notes/2022.md

When creating release notes please include the following information:

- Title of the document, the header (H1), is always _Release Notes_
- Publication date, in H3 format: Month date, year
- Version of openAPI document, plain text
- Recommended sections, in H4

**Release notes sections** are described in [release notes template](?path=docs/getting-started/release-notes-template.md).

- _What's new_, in terms of additions to the documentation and endpoints.
- _Enhancements_, are changes to the existng documentation and endpoints.
- _Fixed_, is a list of mishaps that were patched or corrected with a work-arround.
- _Know Issues_, is a list of persistent issue(s) that's known and not fixed.
- _Deprecated_, is a document, an endpoint, or a payload field, regarded as obsolete and best avoided.

It is a requirement to have published release notes in order for a Tenant to be promoted to higher environments:

- Stage
- Production

Any changes to the content after the initial release should go into release notes under _the change date_ at the top of the file. So that the newer changes will be at the top of the document, followed by the older changes, with the oldest changes at the bottom of the document.

We propose to have one Release notes document for an entire year with the latest changes up on top.
