# Publish a Helm chart using GitHub pages

## Publish a website using GitHub pages

There are three options to publish a website using GitHub pages:

Using GitHub pages, you publish a Jekill generated web page from the markdown files on your repository.

You have three options:

* Expose your main **master** branch
* Expose another designated branch
* Expose content from a **docs** directory on your repository (you can't choose another different directory)

The last option is best for keeping some content accesible from the main repository URL, and at the same time make clear where additional files are.

## URL and domain

The URL will be in the form of:
* <github_username>.github.io/<repo_name>

If your repository name is <github_username>.github.io, the URL will be:
* <github_username>.github.io/<repo_name>

HTTPS can be enforced for those URLs with a certificate issued by github.com

You can also use your own custom domain.

## Website content

You can use your own HTML and CSS files, or markdown files using on the templates.

If you want to use markdown, the default file that will be shown on each directory has to be named **index.md**
On the repository settings you can choose the Jekill theme that will be used for automatically converting markdown to HTML and CSS.
You can also choose an image that will be used when sharing the site in social media posts.

## Chart structure

To store charts, you have to package them and move to a subdirectory of your public website one, for example, **charts**.
Inside that folder we will place charts and a index.yaml file to address them, as we will explain:

```
helm package falco
mv falco-1.1.6.tgz docs/charts
helm repo index docs/charts --url https://<github_username>.github.io/charts
```

## References

References:
* https://helm.sh/docs/topics/chart_repository/
* https://pages.github.com/