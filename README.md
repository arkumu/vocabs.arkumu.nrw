# vocabs.arkumu.nrw

## Deutsch

Kontrollierte Vokabulare für https://arkumu.nrw

Im Rahmen einer Überarbeitung werden 2026 alle Vokabulare konsolidiert, logisch validiert und nach SKOS konvertiert. 

Die einzelnen Vokabulare können als .xlsx gepflegt und mit einer Anwendung wie https://xls2rdf.sparna.fr/web/convert nach .ttl konvertiert werden. Über dieses Repositorium werden sie auf https://skohub.io veröffentlicht, wo sie programmatisch verfügbar sind.

Hinweis: Die Aussage skos:exactMatch trifft nicht unbedingt immer zu. Bei einer redaktionellen Überarbeitung aller Einträge würde sich wahrscheinlich bei einzelnen zeigen, dass skos:closeMatch besser zutrifft.


## English

vocabularies for https://arkumu.nrw

As part of a restructuring process in 2026, all vocabularies will be consolidated, logically validated and converted to SKOS. 

Vocabularies can be maintained as .xlsx files and converted to .ttl using a tool such as https://xls2rdf.sparna.fr/web/convert. They are published via this repository at https://skohub.io, where they are available for automated use.

NB: The skos:exactMatch property does not necessarily always apply. During an editorial review of all entries, it would likely become apparent that skos:closeMatch is a better fitfor some.



---

</br></br></br>
README from the original repository https://github.com/skohub-io/skohub-vocabs. See also https://blog.skohub.io/2024-03-21-skohub-pages.


# SkoHub Pages

This is an example repository (formerly named `skohub-docker-vocabs`) to show how you can publish your SKOS vocabulary using GitHub infrastructure (Actions and Pages).

Every time a change is made to a vocabulary a GitHub-workflow-action is triggered to publish the most recent vocabulary to the `gh-pages`-branch, which is used by GitHub pages.
It spins up a Docker container made from [SkoHub Vocabs](https://github.com/hbz/skohub-vocabs).

## Usage

If you want to reuse this repo and have your vocabulary automatically pushed und published via GitHub-Pages, follow these steps (and note the [Troubleshooting section](#troubleshooting) below when things don't work as expected):

1. Fork this repo. **Uncheck the box to only fork the main branch**.
1. Go to "Actions" tab and if not already activated, activate GitHub Actions.
1. Go to "Settings", navigate to the "Pages" setting and select `gh-pages` as the branch your site is being built from. 
1. Go back to the main page of your repo and click the little gear icon in the top right of the "About" section. Check the box at "Use your GitHub Pages website".
1. Add a commit to the main branch and your vocabulary will be automatically published (sometimes it takes a little to see the changes, remember to do some hard refreshing).

Any issues? Please open up a issue [here](https://github.com/skohub-io/skohub-pages/issues)

## Custom Domain

If you want to host your vocabularies under your GitHub pages domain (so no W3 perma-id or purl.org redirect), you have to provide that domain in the [`config.yaml`](./config.yaml).

Example:

Your GitHub Pages domain is: `https://skohub-io.github.io/skohub-pages/`
Then provide `https://skohub-io.github.io/skohub-pages/` as `custom_domain` in your `config.yaml`.

The base of your concept scheme could then be something like: `https://skohub-io.github.io/skohub-pages/colours/`

Notice that this will apply to all your hosted vocabularies.

## Troubleshooting

### There is no `gh-pages` branch to select for GitHub Pages

You probably only forked the main branch.
You have two options:

- Delete the repo and fork it again, but make sure to uncheck the box to only fork the main branch
- Make sure the GitHub Action is activated ➡️ Go to "Actions" tab and activate it. After that commit changes to a vocabulary in the main branch. This should trigger the build and create a `gh-pages` branch.

### I push changes, but they seem to have no effect. My vocabulary stays the same

Maybe your GitHub Action is not activated yet.
Go to the "Actions" tab and activate GitHub Actions for your repository.

### During the build I get an error saying `The requested URL returned error: 403`

You maybe need to update permissions like described here: https://github.com/peaceiris/actions-gh-pages/issues/744
Go to `Settings` > `Actions` > `General` > `Workflow permissions` and toggle the Read and write permissions.

## CHANGELOG

09.02.2021:

- In an earlier version, there was the .env variable `PATH_PREFIX` set to point to the repository the vocabulary is hosted at. To align with rest of code, this was changed to `BASEURL`.
- The docker image now also support i18n
