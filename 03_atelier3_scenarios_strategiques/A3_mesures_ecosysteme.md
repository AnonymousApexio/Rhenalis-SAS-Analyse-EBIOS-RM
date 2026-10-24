# A3 - Mesures sur l'écosystème

> **Atelier 3 - Étape 3.3 : Mesures sur l'écosystème**  
> Feuille du classeur : `Atelier 3 - PP` (effets sur l'indice de menace) · Mesures reprises dans `PTR`  
> Dossier parent : [`README.md`](../README.md) · Fiche amont : [`A3_parties_prenantes.md`](./A3_parties_prenantes.md) · Fiches aval : [`A3_scenarios_strategiques.md`](./A3_scenarios_strategiques.md)

---

## 1. Identification

| Champ | Valeur |
|---|---|
| **Objet de l'étude** | Plateforme cloud hébergeant l'ERP et le CRM de Rhénalis SAS |
| **Atelier** | Atelier 3 - Scénarios stratégiques |
| **Étape** | 3.3 - Mesures de sécurité portant sur l'écosystème |
| **Livrable** | Tableau des mesures par partie prenante, avec effet attendu sur l'indice de menace |
| **Statuts** | `[F]` fait établi · `[H]` hypothèse · `[M]` information manquante |

> **Rappel méthodologique** - Les mesures de l'atelier 3 portent sur les **parties prenantes** de l'écosystème, et non sur les biens supports internes. Elles relèvent essentiellement de la **contractualisation** : on ne peut pas imposer une configuration technique à un tiers comme on le fait sur ses propres biens supports. Chaque mesure est rattachée à un **critère** de la cotation (maturité, confiance, pénétration) et à un **effet attendu** sur l'indice de menace. Les mesures qui en découlent sont reprises dans le **PTR** de l'atelier 5 sous les codes `M01`, `M04`, `M06`, `M07`, `M08`, `M10`, `M15`.

---

## 2. Principe directeur

Les mesures sur l'écosystème ne visent pas à **faire baisser l'indice de toutes les parties prenantes**. Elles visent à :

1. **Sortir de la zone danger** la partie prenante critique (**InfoGest Services**) en agissant sur sa **maturité** et sur sa **confiance** — c'est-à-dire sur le contrat —, ainsi que sur sa **pénétration** — c'est-à-dire sur les accès qu'on lui accorde ;
2. **Maintenir sous contrôle** les parties prenantes en zone contrôle (**hébergeur IaaS**, **éditeur de l'ERP**) par des mesures de **vérification** et de **surveillance** ;
3. **Réduire la vraisemblance des scénarios** qui passent par une partie prenante, sans nécessairement faire bouger son indice (cas des grands comptes dans SS4).

> **Point de vigilance** - Une mesure sur l'écosystème ne se substitue pas à une mesure sur les biens supports. L'avenant au contrat d'infogérance (**M01**) exige la MFA ; c'est la mesure **M06** qui la déploie techniquement. Les deux sont nécessaires.

---

## 3. Tableau des mesures sur l'écosystème

| Code | Partie prenante | Critère visé | Mesure | Effet attendu sur l'indice | Mesure(s) PTR associée(s) |
|:-:|---|---|---|---|---|
| **ECO1** | **PP1 - InfoGest Services** (infogérant) | **Maturité, confiance** | Avenant de sécurité au contrat d'infogérance : MFA, comptes nominatifs, journalisation, notification d'incident sous 24 h, correctifs des serveurs sous 30 jours, droit d'audit annuel | **4,00 → 1,78** : sortie de la zone danger | **M01** |
| **ECO2** | **PP1 - InfoGest Services** (infogérant) | **Pénétration** | Accès d'administration via un bastion, sessions enregistrées, suppression du compte administrateur partagé | Accès tracé et limité au nécessaire ; réduction de la pénétration de 4 à 3 | **M07**, **M11** |
| **ECO3** | **PP2 - Hébergeur IaaS** | **Maturité** | Vérifier la qualification de l'hébergeur (SecNumCloud ou autre) ; MFA sur la console d'administration ; sauvegarde immuable externalisée chez un tiers distinct de l'infogérant | **1,78 → 1,33** seulement si la qualification SecNumCloud est confirmée ; sinon **inchangé** | **M04**, **M06**, **M15** |
| **ECO4** | **PP3 - Éditeur de l'ERP** | **Confiance** | Clauses de sécurité au contrat de maintenance ; télémaintenance ouverte uniquement à la demande, via le bastion, après validation interne | **1,33 → 1,00** (confiance 3 → 4) : reste en zone contrôle, sous surveillance. La **pénétration reste à 3** : les droits d'administration sur le serveur demeurent | **M08** |
| **ECO5** | **PP6 - Grands comptes** | **Confiance** | Courrier aux grands comptes : Rhénalis ne change jamais de RIB par e-mail ; en cas de doute, rappeler le numéro habituel | **Indice inchangé**, mais **vraisemblance de SS4 réduite** | **M10** |

> **Lecture des effets** : une mesure peut réduire la vraisemblance d'un scénario **sans** faire baisser l'indice de menace de la partie prenante. C'est le cas d'ECO5 : les grands comptes restent en veille (indice 0,50), mais le courrier réduit la probabilité qu'ils paient une fausse facture.

---

## 4. Justification détaillée

### 4.1 ECO1 et ECO2 - InfoGest Services

**Problème** : InfoGest est seule en **zone danger** (indice 4,00). La relation est indispensable et non substituable à court terme, l'infogérant dispose de droits d'administration sur l'annuaire, les serveurs et les sauvegardes, mais sa sécurité est réactive et le contrat est dépourvu de clause de sécurité (H13).

**Deux leviers distincts** :

- **ECO1 agit sur la maturité et la confiance** par le contrat. En exigeant MFA, comptes nominatifs, journalisation, notification d'incident sous 24 h, correctifs sous 30 jours et droit d'audit, on relève la **maturité** de 2 à 3 et la **confiance** de 2 à 3. L'indice passe de **4,00 à 1,78** et sort de la zone danger.
- **ECO2 agit sur la pénétration** par l'architecture. En imposant un bastion avec sessions enregistrées et en supprimant le compte administrateur partagé, on réduit les accès permanents et non tracés. La **pénétration** passe de 4 à 3.

> Ces deux leviers sont **complémentaires** : sans ECO1, l'infogérant n'a aucune obligation contractuelle de déployer le bastion ; sans ECO2, l'avenant reste théorique.

**Limite** : ECO1 exige que l'infogérant accepte l'avenant. En cas de refus, la direction devra arbitrer entre renégocier, changer de prestataire ou accepter le risque résiduel.

### 4.2 ECO3 - Hébergeur IaaS

**Problème** : l'hébergeur est en zone contrôle (1,78), mais il contrôle l'hyperviseur et le stockage. Il porte un rôle dans SS1 : la console IaaS est utilisée pour supprimer les sauvegardes et instantanés.

**Effet conditionnel** : la baisse de l'indice à **1,33** ne se produit **que si** la qualification SecNumCloud est confirmée. Si l'hébergeur n'est pas qualifié, son indice reste à 1,78. Cette incertitude est liée à **H14** `[M]` : le niveau de qualification de l'hébergeur est inconnu.

> **Conséquence** : la vérification de la qualification (M04) est un **préalable** à toute conclusion sur l'hébergeur. C'est une mesure P2 dans le PTR, mais elle conditionne la lecture de SS1.

### 4.3 ECO4 - Éditeur de l'ERP

**Problème** : l'éditeur est en zone contrôle (1,33). Il dispose d'un accès administrateur au serveur d'application en télémaintenance (H17). Il porte SS2.

**Effet limité** : la mesure relève la **confiance** de 3 à 4, ce qui fait passer l'indice de **1,33 à 1,00**. Mais la **pénétration reste à 3** : les droits d'administration sur le serveur demeurent. L'éditeur reste donc en zone contrôle, sous surveillance.

> **Point de vigilance** : ECO4 ne supprime pas le risque de SS2. Elle le réduit en encadrant la télémaintenance, mais un éditeur compromis conserve ses droits. La mesure **M15** (sauvegarde immuable testée) est indispensable en complément.

### 4.4 ECO5 - Grands comptes

**Problème** : les grands comptes sont les **victimes** de la fraude au RIB (SS4), pas un intermédiaire. Ils restent en veille (indice 0,50).

**Effet** : l'indice ne bouge pas, mais le courrier **réduit la vraisemblance de SS4**. Les grands comptes informés de la procédure RIB de Rhénalis sont moins susceptibles de payer une fausse facture.

> **Lecture méthodologique** : c'est un cas où la mesure sur l'écosystème ne se traduit pas par une baisse d'indice, mais par une **baisse de vraisemblance** au niveau du scénario. Les deux effets sont distincts et doivent être expliqués séparément.

---

## 5. Effets attendus sur la cartographie

### 5.1 Avant mesures

| Zone | PP | Indice |
|:-:|---|:-:|
| 🔴 Danger | InfoGest | 4,00 |
| 🟠 Contrôle | Hébergeur | 1,78 |
| 🟠 Contrôle | Éditeur | 1,33 |
| 🟢 Veille | 6 PP | 0,19 à 0,67 |

### 5.2 Après mesures

| Zone | PP | Indice | Évolution |
|:-:|---|:-:|---|
| 🔴 Danger | *aucune* | - | **Sortie de la zone danger** |
| 🟠 Contrôle | InfoGest | **1,78** | **4,00 → 1,78** |
| 🟠 Contrôle | Hébergeur | **1,33** *(si SecNumCloud confirmé)* | 1,78 → 1,33, sinon 1,78 |
| 🟠 Contrôle | Éditeur | **1,00** | 1,33 → 1,00 |
| 🟢 Veille | 6 PP | 0,19 à 0,67 | Inchangé |

> Les cartographies avant et après mesures sont produites dans [`A3_parties_prenantes.md`](./A3_parties_prenantes.md) (§ 5.3) à partir de la feuille `Atelier 3 - Carto PP`.

---

## 6. Rattachement aux scénarios stratégiques

| Scénario | Mesure(s) sur l'écosystème | Effet sur la vraisemblance |
|---|---|---|
| **SS1** - rançongiciel via l'infogérant | ECO1, ECO2, ECO3 | Sortie de la zone danger pour InfoGest ; MFA et bastion ; sauvegarde immuable (M15) |
| **SS2** - rançongiciel via l'éditeur | ECO4 | Télémaintenance encadrée ; l'éditeur reste en zone contrôle |
| **SS4** - fraude au RIB | ECO5 | Vraisemblance réduite sans baisse d'indice |

> SS3 (hameçonnage d'un salarié) et SS5 (export du fichier clients) sont des scénarios **directs**, sans partie prenante intermédiaire. Ils ne donnent pas lieu à une mesure de l'atelier 3, mais à des mesures sur les biens supports (M05, M09, M12, M14).

---

## 7. Correspondance avec le classeur EBIOS RM

| Élément de cette fiche | Feuille du classeur | Colonnes |
|---|---|---|
| Partie prenante visée | `Atelier 3 - PP` | Colonne B |
| Critère visé | `Atelier 3 - PP` | Colonnes C à F (dépendance, pénétration, maturité, confiance) |
| Effet sur l'indice | `Atelier 3 - PP` | Colonne I (indice de menace) |
| Mesures associées | `PTR` | Colonne C (mesure), colonne B (groupe) |
| Propriétaire, délai, coût | `PTR` | Colonnes E à J |

> Les mesures ECO1 à ECO5 sont **reprises dans le PTR** sous les codes `M01`, `M04`, `M06`, `M07`, `M08`, `M10`, `M11`, `M15`. Le PTR ajoute le propriétaire, la complexité, le délai, l'échéance, le coût et l'indicateur de réalisation.

---

## 8. Checklist de validation

- [x] Chaque mesure est rattachée à une **partie prenante** identifiée dans `A3_parties_prenantes.md`.
- [x] Chaque mesure est rattachée à un **critère** de la cotation (maturité, confiance, pénétration).
- [x] L'**effet attendu** sur l'indice est explicité, y compris lorsque l'indice ne bouge pas (ECO5).
- [x] Les mesures **conditionnelles** sont signalées (ECO3 : SecNumCloud à confirmer ; ECO4 : pénétration inchangée).
- [x] Les mesures sont **rattachées aux scénarios stratégiques** qu'elles réduisent.
- [x] Les mesures sont **reprises dans le PTR** avec un code `Mxx` cohérent.
- [x] La distinction entre **mesure sur l'écosystème** et **mesure sur les biens supports** est rappelée.
- [x] Le rôle des **grands comptes comme victimes** dans SS4 est explicité.
- [x] Les **limites** sont signalées : refus possible de l'infogérant, incertitude sur la qualification de l'hébergeur.

---

## 9. Références

- ANSSI - *EBIOS Risk Manager*, fiche méthode « Mesures de sécurité sur l'écosystème » (atelier 3).
- Classeur modèle `EBIOS_RM_Ateliers_modele.xlsx` - feuilles `Atelier 3 - PP`, `Atelier 3 - Carto PP`, `PTR`.
- Dossier de synthèse - § 5.4 « Mesures sur l'écosystème » (page 12).
- Fiche amont : [`A3_parties_prenantes.md`](./A3_parties_prenantes.md).
- Fiche aval : [`A3_scenarios_strategiques.md`](./A3_scenarios_strategiques.md).