# A2 - Couples sources de risque / objectifs visés

> **Atelier 2 - Étape 2.1 : Sources de risque et objectifs visés**  
> Feuille du classeur : `Atelier 2 - SROV`  
> Dossier parent : [`README.md`](../README.md) · Fiche amont : [`01_atelier1_cadrage_socle/A1_socle_securite_gaps.md`](../01_atelier1_cadrage_socle/A1_socle_securite_gaps.md)

---

## 1. Identification

| Champ | Valeur |
|---|---|
| **Objet de l'étude** | Plateforme cloud hébergeant l'ERP et le CRM de Rhénalis SAS |
| **Atelier** | Atelier 2 - Sources de risque |
| **Étape** | 2.1 - Identification, cotation et sélection des couples SR/OV |
| **Livrable** | Tableau des 8 couples évalués, dont 3 retenus et 5 exclus, avec justifications |
| **Statuts** | `[F]` fait établi · `[H]` hypothèse · `[M]` information manquante |

> **Rappel méthodologique** - Une **source de risque (SR)** est un acteur ou une catégorie d'acteurs susceptible de porter atteinte aux valeurs métier. Un **objectif visé (OV)** décrit ce que cette source cherche à obtenir. Le couple **SR/OV** est évalué en croisant la **motivation** et les **ressources** de la source de risque ; la **pertinence** qui en résulte sert à décider si le couple est retenu pour la suite de l'analyse.

---

## 2. Échelles de cotation

### 2.1 Motivation et ressources

| Niveau | Motivation | Ressources |
|:-:|---|---|
| **+** | Motivation faible | Ressources faibles |
| **++** | Motivation moyenne | Ressources moyennes |
| **+++** | Motivation forte | Ressources élevées |

### 2.2 Grille de pertinence (feuille `Métriques`)

| Ressources \ Motivation | **+** | **++** | **+++** |
|:-:|:-:|:-:|:-:|
| **+++** | Moyenne | Élevée | Élevée |
| **++** | Faible | Moyenne | Élevée |
| **+** | Faible | Faible | Moyenne |

> La pertinence n'est pas le seul critère de sélection : un couple peut être **écarté par décision du groupe** malgré une pertinence moyenne, notamment lorsque la motivation réelle est jugée nulle (cas de SR5).

---

## 3. Tableau des couples SR/OV évalués

| Code | Source de risque | Objectif visé | Motivation | Ressources | Pertinence | Priorité | Retenu | Justification / motif d'exclusion |
|---|---|---|:-:|:-:|:-:|:-:|:-:|---|
| **SR1/OV1** | Organisation criminelle (rançongiciel) | **OV1** - Gain financier : chiffrer l'ERP/CRM et les sauvegardes puis exiger une rançon, avec exfiltration préalable des données pour double extorsion. ER visés : ERP indisponible (G3), perte des données (G4), vol du fichier clients (G3). | +++ | ++ | **Élevée** | 1 | **OUI** | Menace la plus structurante : motivation financière forte, ressources moyennes, impact potentiellement critique. Couvre trois ER et trois chemins stratégiques (SS1, SS2, SS3). |
| **SR2/OV2** | Organisation criminelle (fraude financière) | **OV2** - Gain financier : détourner les paiements clients par fraude au RIB, après compromission d'une messagerie ou d'un compte ERP. ER visé : fraude au RIB (G3). | +++ | + | **Moyenne** | 2 | **OUI** | Fraude peu coûteuse pour l'attaquant, impact financier direct. Retenu pour couvrir la fraude au RIB (SS4), même si les ressources nécessaires sont plus faibles que pour un rançongiciel. |
| **SR3/OV3** | Collaborateur malveillant (commercial sur le départ) | **OV3** - Lucratif / avantage personnel : emporter le fichier clients et les tarifs négociés chez un concurrent ou pour une future activité. ER visé : vol du fichier clients (G3). | ++ | ++ | **Moyenne** | 2 | **OUI** | Menace interne crédible : accès légitime au CRM, droits d'export trop larges. Retenu pour couvrir la fuite du fichier clients (SS5). |
| **SR4/OV4** | Concurrent | **OV4** - Espionnage : obtenir le fichier clients et la politique tarifaire de Rhénalis. | ++ | + | **Faible** | 0 | **NON** | Concurrents régionaux de taille comparable, sans capacité offensive et exposés à un risque pénal. Le scénario réaliste passe par un salarié débauché : il est couvert par **SR3/OV3**. |
| **SR5/OV5** | Organisation étatique | **OV5** - Espionnage ou prépositionnement stratégique. | + | +++ | **Moyenne** | 0 | **NON** | Pertinence théorique moyenne (ressources maximales) mais **motivation nulle** : Rhénalis n'a ni activité stratégique, ni données sensibles pour un État, ni client sensible. Exclu par décision du groupe, au-delà du seul résultat de la grille. |
| **SR6/OV6** | Activiste | **OV6** - Idéologique : nuire à l'image de l'entreprise ou perturber son activité. | + | ++ | **Faible** | 0 | **NON** | Aucune activité controversée (distribution de matériel électrique). Pas de motivation identifiée. |
| **SR7/OV7** | Amateur (script-kiddie) | **OV7** - Défi / amusement : perturber un service exposé sur Internet. | + | + | **Faible** | 0 | **NON** | Plateforme ERP/CRM non exposée publiquement (accès par VPN), site vitrine hors périmètre. Menace couverte par le socle de sécurité (atelier 1 - GAP). |
| **SR8/OV8** | Collaborateur mécontent (licencié) | **OV8** - Vengeance : saboter les données ou l'ERP. | ++ | + | **Faible** | 0 | **NON** | Droits utilisateurs limités, pas d'accès administrateur. Risque traité par le socle : retrait des accès au départ, sauvegardes. |

> **Priorité 0** = couple non retenu pour la suite de l'analyse. Les priorités 1 et 2 distinguent les couples retenus : SR1/OV1 est prioritaire, SR2/OV2 et SR3/OV3 viennent ensuite.

---

## 4. Analyse de la sélection

### 4.1 Les trois couples retenus

| Couple | Pourquoi il est retenu | Scénarios stratégiques associés | Risques finaux |
|---|---|---|---|
| **SR1/OV1** | Motivation financière forte, ressources moyennes, pertinence élevée. Il permet de couvrir les trois ER les plus graves : indisponibilité de l'ERP, perte définitive des données et vol du fichier clients. | SS1, SS2, SS3 | R1, R2, R3 |
| **SR2/OV2** | Fraude au RIB peu coûteuse, impact financier direct et crédible pour une PME. Pertinence moyenne mais scénario concret. | SS4 | R4 |
| **SR3/OV3** | Menace interne crédible : le commercial dispose déjà des droits nécessaires. Pertinence moyenne. | SS5 | R5 |

> Les trois couples retenus couvrent **trois profils de menace distincts** : le crime organisé à but lucratif, la fraude financière et la menace interne. Cette diversité est recherchée : elle évite de ne traiter qu'une seule famille d'attaquants.

### 4.2 Ce que les exclusions ne signifient pas

Les couples exclus ne sont pas nécessairement impossibles. Ils sont **écartés pour cette analyse** car :

- soit un autre couple couvre déjà le scénario réaliste (**SR4** couvert par SR3/OV3) ;
- soit la motivation est jugée insuffisante (**SR5**, **SR6**) ;
- soit la menace est traitée par le socle de sécurité (**SR7**, **SR8**).

> **SR5** illustre un cas particulier : la grille calcule une pertinence moyenne du fait de ressources maximales, mais la motivation est nulle. Le groupe a donc exclu le couple par décision motivée, au-delà du seul résultat de la grille. Ce point doit être explicité en soutenance.

---

## 5. Rattachement aux scénarios stratégiques

| Couple SR/OV | Scénario(s) stratégique(s) | ER visé(s) | Risque(s) final(aux) |
|---|---|---|---|
| **SR1/OV1** | SS1 - via l'infogérant | ER1, ER6, ER3 | R1, R3 |
| **SR1/OV1** | SS2 - via l'éditeur de l'ERP | ER1 | R2 |
| **SR1/OV1** | SS3 - via hameçonnage d'un salarié | ER1, ER6 | R3 |
| **SR2/OV2** | SS4 - fraude au RIB | ER5 | R4 |
| **SR3/OV3** | SS5 - export du fichier clients | ER3 | R5 |

> Un même couple SR/OV peut donner lieu à **plusieurs scénarios stratégiques** lorsque les chemins d'attaque diffèrent (c'est le cas de SR1/OV1 avec SS1, SS2 et SS3).

---

## 6. Correspondance avec le classeur EBIOS RM

| Élément de cette fiche | Feuille du classeur | Colonnes |
|---|---|---|
| Codes SR1 à SR8 | `Atelier 2 - SROV` | Colonne A (Sources de risque) |
| Objectifs visés OV1 à OV8 | `Atelier 2 - SROV` | Colonne B |
| Motivation | `Atelier 2 - SROV` | Colonne C |
| Ressources | `Atelier 2 - SROV` | Colonne D |
| Pertinence du couple SR/OV | `Atelier 2 - SROV` | Colonne E |
| Priorité | `Atelier 2 - SROV` | Colonne F |
| Retenu (OUI/NON) | `Atelier 2 - SROV` | Colonne G |
| Justification de l'exclusion | `Atelier 2 - SROV` | Colonne H |
| Grille de pertinence | `Métriques` | Bloc « Pertinence / Motivation / Ressources » |

---

## 7. Checklist de validation

- [x] Les **8 couples SR/OV** de la feuille `Atelier 2 - SROV` sont repris.
- [x] Chaque couple est coté en **motivation** et en **ressources** selon les échelles du classeur.
- [x] La **pertinence** est cohérente avec la grille de la feuille `Métriques`.
- [x] Les **3 couples retenus** sont clairement identifiés : SR1/OV1, SR2/OV2, SR3/OV3.
- [x] Les **5 couples exclus** sont justifiés individuellement.
- [x] Le cas **SR5** est explicité : pertinence moyenne mais motivation nulle, exclusion par décision du groupe.
- [x] Les couples retenus sont rattachés aux **scénarios stratégiques** et aux **risques finaux**.
- [x] La distinction entre **pertinence calculée** et **décision de sélection** est rappelée.
- [x] Le tableau est **cohérent avec la feuille `Atelier 2 - SROV`** du classeur.

---

## 8. Références

- ANSSI - *EBIOS Risk Manager*, fiche méthode « Sources de risque et objectifs visés » (atelier 2).
- Classeur modèle `EBIOS_RM_Ateliers_modele.xlsx` - feuilles `Atelier 2 - SROV`, `Métriques`.
- Dossier de synthèse - § 4 « Atelier 2 - Sources de risque et objectifs visés » et § 4.1 « Justification des exclusions » (pages 8-9).
- Fiche amont : [`01_atelier1_cadrage_socle/A1_socle_securite_gaps.md`](../01_atelier1_cadrage_socle/A1_socle_securite_gaps.md).
- Fiche aval : [`03_atelier3_scenarios_strategiques/A3_scenarios_strategiques.md`](../03_atelier3_scenarios_strategiques/A3_scenarios_strategiques.md).