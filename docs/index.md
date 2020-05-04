# Publish a Helm chart using GitHub pages

## Publish a website using GitHub pages

There are three options to publish a website using GitHub pages:

Using GitHub pages, you publish a Jekill generated web page from the markdown files on your repository.

You have three options:

* Expose your main **master** branch
* Expose another designated branch
* Expose content from a **docs** directory on your repository (you can't choose a different directory name or path)

The last option is best for keeping some content accesible from the main repository URL, and at the same time make clear where additional files are.

## URL and domain

The URL will be in the form of:
* \<github_username\>.github.io/\<repo_name\>

If your repository name is <github_username>.github.io, the URL will be:
* \<github_username\>.github.io

On repository settings you can:

* Enforce HTTPS the public URLs with a certificate issued by github.com
* Add your own custom domain
* Choose a template for pages generated from markdown to HTML and CSS by Jekyll

## Website content

You can use your own HTML and CSS files, or markdown files using on the templates.

If you want to use markdown, the default file that will be shown on each directory has to be named **index.md**

You can also choose an image that will be used when sharing the site in social media posts.

## Chart structure

To store charts, you have to package them and move to a subdirectory of your public website one, for example, **charts**.
Inside that folder we will place charts and a index.yaml file to address them, as we will explain:

```
helm package falco
mv falco-1.1.6.tgz docs/charts
helm repo index docs/charts --url https://<github_username>.github.io/<repo_name>/charts
```

To use in this repo:
```
helm repo index docs/charts --url https://vicenteherrera.github.io/my-falco-chart/charts
```

## How to test

Visit:
* [https://vicenteherrera.github.io/my-falco-chart](https://vicenteherrera.github.io/my-falco-chart)

You should see the content from:
* [https://github.com/vicenteherrera/my-falco-chart/docs/index.md](https://github.com/vicenteherrera/my-falco-chart/docs/index.md)

If you visit:
* [https://vicenteherrera.github.io/my-falco-chart/charts/index.yaml](https://vicenteherrera.github.io/my-falco-chart/charts/index.yaml)

You should see the contents of _index.yaml_ file:
* [https://github.com/vicenteherrera/my-falco-chart/docs/charts/index.yaml](https://github.com/vicenteherrera/my-falco-chart/docs/charts/index.yaml)

You can add this repository to deploy charts from it

```
helm repo add my-repo https://vicenteherrera.github.io/my-falco-chart/charts
helm repo update
helm search repo my-repo
```

## References

References:
* [https://helm.sh/docs/topics/chart_repository](Helm chart on GitHub pages)
* [https://pages.github.com](GitHub pages)
* [https://github.com/int128/helm-github-pages](CircleCI to generate Helm chart on GitHub pages)
* [https://medium.com/@stefanprodan/automate-helm-chart-repository-publishing-with-github-actions-and-pages-8a374ce24cf4](GitHub action to generate Helm chart on GitHub Pages)