---
"geonovum-sbom": minor
---

`sbom.yml` werkt nu ook in repositories waar een workflow de release aanmaakt.

Maakt een workflow de GitHub-release aan met `github.token` (bijvoorbeeld met `gh release create` of changesets), dan start het release-event geen andere workflows en draaide `sbom.yml` nooit, zonder foutmelding.

- `sbom.yml` heeft een `workflow_call`-trigger met de invoer `tag`. De workflow die de release maakt, roept hem aan als extra job; het voorbeeld staat bovenin het sjabloon. De SBOM beschrijft de code van die tag.
- `scan_repo.js` meldt onder "Releases" welke workflow de release maakt en met welk token. De vorm van de bestaande uitvoer verandert niet; in de JSON-uitvoer komt `releaseWorkflows` erbij.
- SKILL.md legt in stap 8 uit wanneer de aanroep nodig is.
