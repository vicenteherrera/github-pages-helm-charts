# Publish a Helm Chart using GitHub pages

## Publish a website using GitHub pages

There are three options to publish a website using GitHub pages:

Using GitHub pages, you publish a Jekill generated web page from the markdown files on your repository.

You have three options:

* Expose your main **master** branch
* Expose another designated branch
* Expose content from a **docs** folder on your repository (you can't choose another different folder)

The last option is best for keeping some content accesible from the main repository URL, and at the same time make clear where additional files are.

## URL and domain

The URL will be in the form of:
* <github_username>.github.io/<repo_name>

If your repository name is <github_username>.github.io, the URL will be:
* <github_username>.github.io/<repo_name>

HTTPS can be enforced for those URLs with a certificate issued by github.com

You can also use your own custom domain.
