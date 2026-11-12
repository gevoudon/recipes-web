# Recipe publishing

Verified 2026-11-12: public repository gevoudon/recipes-web, default branch main,
GitHub connection reports push permission; main is unprotected and no rulesets exist.
CNAME is recipes.chuckminster.de. Existing dynamic `pages build and deployment`
runs deploy main successfully. No custom workflow or shared template exists.
Exact Pages settings could not be read through the connector (endpoint unsupported);
public API returned 404. Do not change Pages configuration.

## Repeatable workflow

1. Inspect latest main, repository instructions and rules before editing.
2. Search all recipe names, source URLs and slugs to avoid duplicates.
3. Extract only reliable source data. Preserve ranges and unspecified quantities.
   Omit unknown recipeYield/prepTime/cookTime/totalTime. Explain missing data visibly.
4. Use one directory per recipe, with index.html and a web-optimized JPEG or WebP.
   Follow the simple semantic HTML and styling of existing recipe pages.
5. Generate a matching food photograph without text or extra ingredients; label
   it as AI-generated on the page. Keep the image on the same public domain.
6. Include schema.org Recipe JSON-LD: name, description, absolute image URL,
   recipeIngredient text list, ordered HowToStep objects, source in isBasedOn
   and citation. Add quantities, durations and yield only if known.
7. Parse JSON-LD, compare visible ingredients and steps, verify image bytes,
   dimensions and URL. Existing historical recipes currently lack image fields;
   do not overwrite them without authorization.
8. Publish only new files in one small commit using Git blobs/tree/commit and a
   non-forced main ref update with expected head SHA. Preserve the full base tree.
9. Check the Pages run for this exact commit; then GET page and image without
   authentication. Compare public JSON-LD and image bytes with local outputs.
10. Report actual import success only after an authorized Mealie test import.
    Otherwise state technical checks passed, actual Mealie import unconfirmed.

## Connections and setup

No additional GitHub setup was required for the first test. The built-in image
 generator was available. To enable real end-to-end import tests, a reachable
Mealie instance and authorized API/session access are still needed. Never store
credentials in this repository. Instructions here document an agent workflow;
they are not a separately installed or scheduled autonomous agent.
