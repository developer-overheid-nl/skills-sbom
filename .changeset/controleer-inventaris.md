---
"geonovum-sbom": minor
---

De inventaris wordt nu tegen de repository gecontroleerd, zodat een verouderde `sbom-inventory.json` geen SBOM oplevert die geldig is maar niet klopt.

- `scan_repo.js --inventory <bestand> --check` eindigt met een fout als de inventaris een bestand van derden, een externe link of een lockfile-import mist, of een bestand noemt dat niet meer in de repository staat. De vergelijking met de inventaris geeft daarnaast waarschuwingen: een andere versie in kopregel, bestandsnaam of CDN-URL, `used` dat niet past bij wat de bestanden laadt, een ingebedde bibliotheek zonder `embeddedIn`, en een PHP-extensie of manifest zonder component.
- `build_sbom.js --strict` (versie 1.3.0) eindigt met een fout als de inventaris een bestand noemt dat niet te lezen is, of een `embeddedIn` die naar geen component wijst.
- Het sjabloon `sbom.yml` controleert de inventaris voordat het de SBOM maakt, en gebruikt `--strict`.
- Nieuw sjabloon `sbom-inventaris.yml`: dezelfde controle bij elke pull request en push naar de hoofdbranch, met alleen leesrechten.
