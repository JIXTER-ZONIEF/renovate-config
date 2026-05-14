# renovate-config

Configuration partagee Renovate pour tous les repos JIXTER-ZONIEF.

Chaque repo de l'organisation reference ce preset via `renovate.json` :

```json
{
  "$schema": "https://docs.renovatebot.com/renovate-schema.json",
  "extends": ["local>JIXTER-ZONIEF/renovate-config"]
}
```

## Ce que fait la config par defaut

- Scan hebdomadaire (lundi avant 6h, Europe/Paris)
- Auto-merge des minors/patches non-zero apres 3j de quarantaine
- Majors -> Dependency Dashboard (issue unique par repo, approbation manuelle)
- 0.x : minors traites comme breaking
- GitHub Actions, Docker digests, deps de test : auto-merge rapide
- Frameworks lourds (Spring, Firebase, Angular) : majors mensuels avec approbation
- Lockfile maintenance mensuel
- CVE : PR immediate avec auto-merge
- Limite : 5 PRs concurrentes / 2 PRs/heure

## Surcharger localement

Un repo peut surcharger en ajoutant ses propres `packageRules` apres l'extends :

```json
{
  "$schema": "https://docs.renovatebot.com/renovate-schema.json",
  "extends": ["local>JIXTER-ZONIEF/renovate-config"],
  "packageRules": [
    { "matchPackageNames": ["foo"], "enabled": false }
  ]
}
```
