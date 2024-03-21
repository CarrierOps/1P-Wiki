# Development & Production Environments

Whenever working with code or data, we can assume that it will be used to build an application (in the case of code) or to power a report (in the case of data). While this sounds incredibly obvious, it also implies a very import issue: what happens if we accidentally create a bug in our code, what if we accidental transform our data in the wrong way? Well, then our app would break, our reports would either break or show completely inaccurate data - something we want to avoid at all costs.

This issue can easily be avoided by creating different environments; having a `development environment` (dev env) to use to develop, and another environment that is used for your app, reports, etc which we'll call the `production environment` (prod env). By separating our environments and having one dedicated to development, we can develop, fix bugs, test our code, re-develop reports with the peace of mind knowing that we won't break existing apps/reports. The dev env is essentially a sandbox where you can break as many things as you want, and the prod env is stable and ensures your app/reports are always working and accurate.

## How we do it

Our infrastructure is propped up by code (pipelines, utilities, etc), but ultimately, we are working with data and working to produce reports (slide decks, dashboards, etc). We apply this concept of having 2 environments (dev & prod) as much as possible and the way we split between dev & prod depends on the system, as we'll discuss in more details below.

### Code

All pipelines, utility scripts, or other things that are code-based are hosted on [GitHub](https://github.com/CarrierOps). We make use of [git branches](https://github.com/CarrierOps/1P-Wiki/blob/main/ByteSizedLearning/TinyTechTidbits/CodeMunchies/hello-github.md) to create a dev and a prod environment. Every pipeline, utility script, etc will have it's own repository, and each repository will have (at least) 2 branches - a dev branch and a main branch.

Development & bug fixing is done exclusively on the dev branch (or feature, hotfix, etc branches), **never on main**! When code is ready to be pushed into production, the user can open up a [pull request](https://github.com/CarrierOps/1P-Wiki/blob/main/ByteSizedLearning/TinyTechTidbits/CodeMunchies/hello-github.md) to request merging the changes into the main branch. When a pull request is accepted and merged into the main branch, a CD (continuous development) pipeline is kicked off to automatically re-deploy the code to which ever app/GCP service.

### Data

We duplicate our data across production and development to have 2 exact copies of it: one copy to power reports, dashboards, slide decks, and another copy used for developing. The 2 environments are split into separate datasets in [BigQuery](https://github.com/CarrierOps/1P-Wiki/blob/main/ByteSizedLearning/Description%20Of%20Services/BigQuery.md), where the development environment will have the same naming as the production environment with the "dev\_" prefix added.

To keep the dev & prod environments synced and up-to-date with each other (to make sure they have the same data), a script is run weekly. We treat the production data as the source of truth. Once a week, on weekends, a script running in [Elements](https://github.com/CarrierOps/1P-Wiki/blob/main/DocuMentor/platforms/Elements.md), will grab the last 2 quarters worth of data from the production environment and will overwrite all data in the development environment with the "source of truth" data. This set-up let's us tinker with data in dev as much as we want and ensures that the following week we will have access to clean, up to date data once again in dev to tinker with some more.

> **Note**
>
> We only split data between dev & prod in BigQuery (our data warehouse), **not** in GCS (our data lake).
