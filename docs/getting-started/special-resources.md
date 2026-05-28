# Special Resources

There are various special resources that can be defined by the tenant under `config/tenant.json` to be displayed on Developer Studio.

![special files](assets/images/resourcesFilePath.png)
  
## Getting started

The tenant is expected to provide a custom markdown file with introduction and general getting started instructions and information. This file should be set at `getStartedFilePath` such as `"getStartedFilePath": "docs/getting-started.mdx"`

## Resources

By default, Developer Studio generates zip files for all openapi specs and the generated postman collection from these specs. This is what we display in the default Resources file.

![Default resources](assets/images/default-resources.png)

We recommend that the tenant create their own markdown file with downloadable resources in their own `docs/resources/resources.md`. They can then set this in `config/tenant.json` such as `"resourcesFilePath": "docs/resources/resources.md"`.

The tenant can then include various images, code blocks, and links (including links for downloading various assets that they have generated and uploaded to Github).

For reference, here are some useful link syntaxes:

- Basic download link: `[File name](download/assets/files/downloadable.zip)`
- [Gated content](docs/configurations/how-to-use-gated-content.md) link: `[File name]D(locked_file.zip)`
- Images: `![Image alt text](assets/images/image.png)`
