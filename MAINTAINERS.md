# Maintainers guide

Find information for maintaining the `ansible-community/ansible-docsite` repository as well as periodic updates for releases and other events.

## Updating the sitemap

A [sitemap](https://docs.readthedocs.com/platform/stable/reference/sitemaps.html) is a file that search engine crawlers use to index the documentation.
This repository includes a custom `sitemap.xml` that needs to be updated when:

- A new "latest" version of the Ansible community package is released.
- A new version of the Ansible community package documentation is added to Read The Docs.
- A new project is added to the Ansible namespace in Read The Docs.
- Substantial changes are made to the Ansible documentation that adds or removes multiple pages.

Read The Docs generates a sitemap named `sitemap.xml` that you cannot overwrite.
However you can overwrite the `robots.txt` file that Read The Docs generates and point to the url of a custom sitemap.
For this reason, the custom sitemap is named `ansible-sitemap.xml`.
The custom sitemap is additive to the Read The Docs sitemap and provides the full structure of all projects in the Ansible namespace in Read The Docs.

To generate the sitemap, do the following:

1. Install nodejs, if required, and the sitemap generator.
   ```bash
   sudo dnf install nodejs
   sudo npm install -g sitemap-generator-cli
   ```
1. Generate a sitemap named `ansible-sitemap.xml`.
   ```bash
   sitemap-generator -f ansible-sitemap.xml https://docs.ansible.com/
   ```
1. Commit the updates to `ansible-sitemap.xml` and open a pull request.

> The custom sitemap must be added to the Google Search Console as a one-time only configuration.
