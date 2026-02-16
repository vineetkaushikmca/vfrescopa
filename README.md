# Frescopa Site Project
Based on the boilerplate for AEM Authoring with Edge Delivery Services projects that integrate with Adobe Commerce.

## Environments
- Live: https://frescopa.coffee/

## Content Setup
See <https://github.com/markszulc/frescopa-with-edge-delivery-services>

## Code Setup

See also [Developer Tutorial](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/edge-delivery/wysiwyg-authoring/edge-dev-getting-started)

1. Fork this repository
2. Add the [AEM Code Sync GitHub App](https://github.com/apps/aem-code-sync) to the repository, so your code changes get synced with EDS.
4. Update the mountpoint in `fstab.yaml`
5. Update the path mappings in `paths.json`

## Refreshing content source after changing fstab

If you change `fstab.yaml` (e.g. to a new AEM author) but [Admin API status](https://admin.hlx.page/status/vineetkaushikmca/vfrescopa/main/?editUrl=auto) still shows the old `sourceLocation`, the content bus is using cached metadata. Force a refresh so it re-reads from the new source:

1. **Using Sidekick**: Open the preview or live page, open Sidekick, and click **Update** (or **Preview** on the source) so the content is re-fetched from the new mountpoint.
2. **Using Admin API** (requires auth):  
   `POST https://admin.hlx.page/preview/vineetkaushikmca/vfrescopa/main/`  
   with your auth cookie or token to update the root path from the current fstab.

After a successful update, the status response should show the new `sourceLocation` and the Sidekick Edit button should work (or use the edit URL from `tools/sidekick/config.json`).
