# Code examples — ArtisanFlow

> **Exemples illustratifs et simplifiés**, écrits pour cette vitrine. Ils illustrent les contrats techniques décrits, mais ne sont **pas des extraits certifiés du code privé** et ne démontrent pas le fonctionnement en production.

## Du texte vocal aux lignes de devis

Un modèle peut proposer des lignes, mais le serveur doit vérifier les quantités et résoudre les références dans un catalogue de confiance avant de calculer les montants.

```ts
type DraftLine = {
  referenceId: string;
  quantity: number;
};

type CatalogItem = {
  id: string;
  label: string;
  unitPriceCents: number;
};

function prepareQuote(
  suggestions: DraftLine[],
  catalog: Map<string, CatalogItem>
) {
  return suggestions.map(({ referenceId, quantity }) => {
    if (!Number.isFinite(quantity) || quantity <= 0 || quantity > 10_000) {
      throw new Error("Invalid quantity");
    }

    const item = catalog.get(referenceId);
    if (!item) throw new Error("Unknown catalog reference");

    const amountCents = Math.round(item.unitPriceCents * quantity);
    if (!Number.isSafeInteger(amountCents)) throw new Error("Amount overflow");

    return {
      referenceId: item.id,
      description: item.label,
      quantity,
      amountCents,
      requiresHumanApproval: true
    };
  });
}
```

**Point d'architecture :** le LLM ne décide ni du prix unitaire ni de la validité d'une référence. L'exemple ne couvre pas la TVA, les unités, les remises, les arrondis réglementaires, les autorisations ou la persistance.

**Pour une évaluation réelle :** démonstration de l'application, tests de correspondance catalogue et revue de code sous conditions adaptées.
