# Publish a Helm chart using GitHub pages

This is a tutorial about how to publish your **Helm charts repository** using **GitHub pages**.

It is also a working example that you can test with Helm, or fork to create your own Helm charts repository using GitHub Pages.

## Publish a website using GitHub pages

Using GitHub pages, you publish a Jekyll generated web page from the markdown files on your repository.

Going into settings for the repo, you have three options:

* Expose your main **master** branch
* Expose another designated branch
* Expose content from a **docs** directory on your repository (you can't choose a different directory name or path)

The last option is best for keeping some content accesible from the main repository URL, and at the same time make clear where additional files are.

In this exaple we chose the first one, so when we update the root `readme.md`, the same file gets exposed to the website and the repository page on GitHub.

## URL and domain

The URL will be in the form of:
* **\<github_username\>.github.io/\<repo_name\>**

If your repository name is _\<github_username\>.github.io_, the URL will be:
* **\<github_username\>.github.io**

On repository settings, in adition to set up what to expose to the public web, you can:

* Choose an image that will be used when sharing the site in social media posts.
* Enforce HTTPS the public URLs with a certificate issued by github.com
* Add your own custom domain
* Choose a template for pages generated from markdown to HTML and CSS by Jekyll

## Website content

You can use your own HTML and CSS files, placing an `index.html` file on folders to be shown by default, or use markdown files that GitHub Jekyll enging transforms to HTML using templates.

If you want to use markdown, the default file that will be shown on each directory has to be named `index.md`, unless it's on the root directory, where `readme.md` will be also used.

When you apply or change a theme from settings, a `_config.yml` file will be commited to the exposed directory/branch, where you can set aditional settings for the Jekyll template (see references).

## How to create the Helm charts repo index

To store charts, you have to package them and move to a subdirectory of your public website one, for example, `packages`.

Inside that folder we will place packaged charts `tgz` format (don't do it yourself, use the Helm `package` command). 

We will create a `index.yaml` file to list the charts, as we explain in the following steps:

```bash
# Prepare your packaged chart
# "falco" package folder not included in this demo
helm package falco
mv falco-1.1.6.tgz docs/charts

#Update ndex.yml searching all subfolders for possible packaged charts
helm repo index docs/charts --url https://<github_username>.github.io/<repo_name>

```

How we used in this repo:
```bash
helm repo index docs/charts --url https://vicenteherrera.github.io/github-pages-helm-charts
```

## How to install Helm charts from this repo

Visit:
* [vicenteherrera.github.io/github-pages-helm-charts](https://vicenteherrera.github.io/github-pages-helm-charts)

You should see the content from:
* [github.com/vicenteherrera/github-pages-helm-charts/blob/master/readme.md](https://github.com/vicenteherrera/github-pages-helm-charts/blob/master/readme.md)

If you visit:
* [vicenteherrera.github.io/github-pages-helm-charts/index.yaml](https://vicenteherrera.github.io/github-pages-helm-charts/index.yaml)

You should see the contents of _index.yaml_ file:
* [github.com/vicenteherrera/github-pages-helm-charts/blob/master/index.yaml](https://github.com/vicenteherrera/github-pages-helm-charts/blob/master/index.yaml)

To add this repository to deploy charts from it:

```bash
helm repo add my-repo https://vicenteherrera.github.io/github-pages-helm-charts

helm repo update

helm search repo github-pages-helm-charts
```

## References

References:
* [Helm chart on GitHub pages](https://helm.sh/docs/topics/chart_repository)
* [GitHub pages](https://pages.github.com)
* [Jekyll themes for GitHub pages](https://help.github.com/en/github/working-with-github-pages/adding-a-theme-to-your-github-pages-site-with-the-theme-chooser)
* [Customizing Cayman Jekyll theme](https://github.com/pages-themes/cayman)
* [CircleCI to generate Helm chart on GitHub pages](https://github.com/int128/helm-github-pages)
* [GitHub action to generate Helm chart on GitHub Pages](https://medium.com/@stefanprodan/automate-helm-chart-repository-publishing-with-github-actions-and-pages-8a374ce24cf4)