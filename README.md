# Google Cloud docs for DevDocs

[Google Cloud's guides](https://docs.cloud.google.com/docs) for a set of popular products, as a
DevDocs doc pack: searchable and readable offline, and scraped again every week. Each product is
its own doc, so you can turn on only the ones you use.

| Product | Pages from |
| --- | --- |
| Cloud Run | docs.cloud.google.com/run/docs |
| Cloud Storage | …/storage/docs |
| Compute Engine | …/compute/docs |
| Google Kubernetes Engine (GKE) | …/kubernetes-engine/docs |
| BigQuery | …/bigquery/docs |
| Pub/Sub | …/pubsub/docs |
| Cloud SQL | …/sql/docs |
| Firestore | …/firestore/native/docs |
| Identity and Access Management (IAM) | …/iam/docs |
| Gemini Enterprise Agent Platform (formerly Vertex AI) | …/gemini-enterprise-agent-platform |
| Google Cloud SDK (the `gcloud` CLI) | …/sdk/docs |

The whole site has some 60,000 guide pages, far too many for one pack, so only these products
are scraped. To add one, add a line to `PRODUCTS` in the DevDocs fork's
`lib/docs/scrapers/google_cloud.rb`: the product's name as its pages' breadcrumbs write it, and
its folder in the address. API and client library references, code sample pages and release
notes are left out.

**To add it:** in DevDocs (the [doc packs version](https://github.com/buggypather/devdocs/tree/main-custom-docs)),
open **Preferences → Doc packs**, paste `https://github.com/buggypather/devdocs-pack-google-cloud/tree/pack`,
and click **Add**. Then tick the products you want under **Google Cloud** in the list on the
left and click **Apply**.

## How it's made

A GitHub Actions workflow (`.github/workflows/scrape.yml`) checks out the DevDocs fork, runs its
Google Cloud scraper and publishes the result to the `pack` branch. The scraper reads at most
four pages a second, to go easy on the site, so a run takes a while. To scrape now, open the
**Actions** tab, choose **Scrape docs** and click **Run workflow**.

## Licence

The documentation is © Google LLC. Its text is licensed under the
[Creative Commons Attribution 4.0 License](https://creativecommons.org/licenses/by/4.0/) and its
code samples under the [Apache License 2.0](https://www.apache.org/licenses/LICENSE-2.0); each page
in the pack credits Google and links to its original. This repository's own files are under the
MIT licence.
