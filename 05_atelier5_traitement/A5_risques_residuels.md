# A5 - Risques résiduels

> **Atelier 5 - Étape 5.3 : Risques résiduels**  
> Feuille du classeur : `Risques résiduels` (+ `PTR`, `Atelier 5 - Risques`)  
> Dossier parent : [`README.md`](../README.md) · Fiche amont : [`A5_PTR.md`](./A5_PTR.md) · Fiches associées : [`A5_synthese_risques.md`](./A5_synthese_risques.md), [`A5_cadre_suivi.md`](./A5_cadre_suivi.md)

---

## 1. Identification

| Champ | Valeur |
|---|---|
| **Objet de l'étude** | Plateforme cloud hébergeant l'ERP et le CRM de Rhénalis SAS |
| **Atelier** | Atelier 5 - Traitement du risque |
| **Étape** | 5.3 - Estimation des risques résiduels et décision |
| **Livrable** | Niveaux de risque résiduel après mise en œuvre du PTR, avec décision proposée à la direction |
| **Statuts** | `[F]` fait établi · `[H]` hypothèse · `[M]` information manquante |

> **Rappel méthodologique** - Le **risque résiduel** est le niveau de risque qui subsiste **après** mise en œuvre des mesures du plan de traitement. Il est estimé en supposant les mesures **réalisées et efficaces**, ce qui reste une **hypothèse de travail** tant que le PTR n'est pas effectivement déployé. La direction doit ensuite **accepter explicitement** les risques résiduels, ou décider de mesures complémentaires.

---

## 2. Échelles et matrice (rappel)

### 2.1 Échelle de niveau de risque (feuille `Métriques`)

> **Ordre de lecture** : du plus haut au plus bas, **Élevé (4) > Modéré (3) > Significatif (2) > Faible (1)**.

| Niveau | Valeur | Signification |
|:-:|:-:|---|
| 🔴 **Élevé** | 4 | Risque inacceptable en l'état |
| 🟡 **Modéré** | 3 | Risque à traiter et à accepter explicitement |
| 🟢 **Significatif** | 2 | Risque tolérable sous surveillance |
| ⚪ **Faible** | 1 | Risque acceptable |

> ⚠️ **Attention** : sur cette échelle, **« Significatif » (2) est plus bas que « Modéré » (3)**. Un risque qui passe de « Modéré » à « Significatif » **s'améliore**.

### 2.2 Matrice gravité × vraisemblance

| Gravité \ Vraisemblance | **V1** | **V2** | **V3** | **V4** |
|:-:|:-:|:-:|:-:|:-:|
| **G4** | Modéré | Élevé | Élevé | Élevé |
| **G3** | Significatif | Modéré | Élevé | Élevé |
| **G2** | Faible | Significatif | Modéré | Modéré |
| **G1** | Faible | Faible | Significatif | Significatif |

---

## 3. Tableau des risques résiduels

| Risque | Gravité initiale | Vraisemblance initiale | Niveau initial | Mesures appliquées | Gravité résiduelle | Vraisemblance résiduelle | Niveau résiduel | Décision |
|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|---|
| **R1** | G4 | V3 | 🔴 **Élevé** | M01, M04, M06, M07, M11, M13, M15, M16, M17 | **G3** | **V2** | 🟡 **Modéré** | Acceptation proposée à la direction, suivi trimestriel |
| **R2** | G3 | V2 | 🟡 **Modéré** | M07, M08, M15, M16 | **G3** | **V1** | 🟢 **Significatif** | Acceptation proposée à la direction |
| **R3** | G4 | V3 | 🔴 **Élevé** | M05, M06, M11, M12, M13, M15, M16, M19 | **G3** | **V2** | 🟡 **Modéré** | Acceptation proposée à la direction, suivi trimestriel |
| **R4** | G3 | V3 | 🟡 **Modéré** | M05, M06, M10, M17, M18 | **G3** | **V2** | 🟡 **Modéré** | Acceptation proposée à la direction, suivi trimestriel |
| **R5** | G3 | V3 | 🟡 **Modéré** | M03, M09, M14 | **G3** | **V2** | 🟡 **Modéré** | Acceptation proposée à la direction, suivi trimestriel |

> Les valeurs entre parenthèses renvoient aux codes de la feuille `Risques résiduels`. Les niveaux résiduels sont calculés par la matrice de la feuille `Métriques`.

---

## 4. Analyse des risques résiduels

### 4.1 R1 - Perte définitive des données via l'infogérant

| Élément | Valeur |
|---|---|
| **Niveau initial** | 🔴 Élevé (G4 × V3) |
| **Mesures** | M01, M04, M06, M07, M11, M13, M15, M16, M17 |
| **Niveau résiduel** | 🟡 **Modéré** (G3 × V2) |
| **Décision** | Acceptation proposée, suivi trimestriel |

**Pourquoi la gravité passe de G4 à G3** : la mesure **M15** (sauvegarde immuable externalisée et testée trimestriellement) rend la **perte définitive des données non atteignable**. Même si l'attaquant chiffre l'ERP/CRM, une copie immuable existe chez un tiers distinct de l'infogérant, et elle est testée. Il reste l'**indisponibilité de l'ERP** et l'**exfiltration de données** (double extorsion), d'où le maintien en G3.

**Pourquoi la vraisemblance passe de V3 à V2** : l'avenant sécurité (M01) impose MFA, comptes nominatifs et journalisation à l'infogérant ; le bastion (M07) supprime le compte partagé et enregistre les sessions ; la MFA (M06) et le durcissement de l'annuaire (M11) rendent la compromission plus difficile ; la supervision (M13) réduit le temps d'impunité. Ces mesures **réduisent** la vraisemblance sans la supprimer : l'infogérant reste un tiers critique, et son avenant doit être accepté puis appliqué.

> **Point de vigilance** : la baisse de gravité dépend **entièrement** de M15. Si M15 n'est pas déployée, R1 reste en G4 et donc en **Élevé** (G4 × V2). C'est la mesure la plus structurante du PTR.

---

### 4.2 R2 - ERP indisponible via l'éditeur

| Élément | Valeur |
|---|---|
| **Niveau initial** | 🟡 Modéré (G3 × V2) |
| **Mesures** | M07, M08, M15, M16 |
| **Niveau résiduel** | 🟢 **Significatif** (G3 × V1) |
| **Décision** | Acceptation proposée |

**Pourquoi la gravité reste G3** : l'indisponibilité de l'ERP au-delà d'une semaine reste une atteinte grave, même avec une sauvegarde immuable. La restauration prend du temps, et M15 ne réduit pas la durée de reconstruction du serveur.

**Pourquoi la vraisemblance passe de V2 à V1** : la télémaintenance de l'éditeur est encadrée par M08 (ouverture à la demande, via le bastion, après validation interne), le bastion (M07) réduit les accès permanents, et la sauvegarde immuable (M15) raccourcit la restauration. **Seul risque à passer en V1**, car le tiers traversé (l'éditeur) est déjà le plus mature et le moins pénétrant des tiers critiques.

> **Lecture** : R2 est le seul risque dont le niveau résiduel **descend d'une catégorie** (Modéré → Significatif). C'est cohérent avec sa cotation initiale déjà plus basse (V2) et avec la maturité de l'éditeur.

---

### 4.3 R3 - Perte définitive des données via un salarié

| Élément | Valeur |
|---|---|
| **Niveau initial** | 🔴 Élevé (G4 × V3) |
| **Mesures** | M05, M06, M11, M12, M13, M15, M16, M19 |
| **Niveau résiduel** | 🟡 **Modéré** (G3 × V2) |
| **Décision** | Acceptation proposée, suivi trimestriel |

**Pourquoi la gravité passe de G4 à G3** : comme pour R1, la mesure **M15** rend la perte définitive des données non atteignable. Il reste l'indisponibilité de l'ERP et l'exfiltration de données.

**Pourquoi la vraisemblance passe de V3 à V2** : la sensibilisation (M05) réduit le taux de clic aux hameçonnages ; l'EDR (M12) détecte les prises de contrôle de poste ; la MFA (M06) et le durcissement de l'annuaire (M11) freinent l'élévation de privilèges ; la supervision (M13) réduit le temps d'impunité ; la vérification des correctifs (M19) ferme les vulnérabilités connues. Ces mesures **réduisent** la vraisemblance sans la supprimer : environ 75 utilisateurs restent exposés, et aucun EDR n'est infaillible.

> **Point de vigilance** : R3 est **le risque le plus difficile à faire baisser durablement**, car il dépend du comportement des utilisateurs. La sensibilisation (M05) et l'EDR (M12) sont des mesures **continues**, pas des projets ponctuels.

---

### 4.4 R4 - Fraude au RIB

| Élément | Valeur |
|---|---|
| **Niveau initial** | 🟡 Modéré (G3 × V3) |
| **Mesures** | M05, M06, M10, M17, M18 |
| **Niveau résiduel** | 🟡 **Modéré** (G3 × V2) |
| **Décision** | Acceptation proposée, suivi trimestriel |

**Pourquoi la gravité reste G3** : la fraude peut encore détourner plusieurs centaines de k€ avant détection, et les pertes restent souvent irrécupérables. **Aucune mesure ne supprime totalement la fraude**, car c'est le client qui effectue le paiement.

**Pourquoi la vraisemblance passe de V3 à V2** : le courrier aux grands comptes (M10) les informe que Rhénalis ne change jamais de RIB par e-mail ; la double validation des RIB (M18) empêche une modification frauduleuse dans l'ERP ; la MFA (M06) et la sensibilisation (M05) réduisent la compromission de la messagerie. **Ces mesures réduisent la fraude sans la supprimer** : le client peut encore être trompé par un courriel soigné, ou la fraude peut passer par un canal que Rhénalis ne contrôle pas.

> **Lecture** : R4 **reste modéré** après traitement. C'est le risque dont la réduction est la plus limitée, car la décision de payer appartient au client. La cyber-assurance (M17) est un **complément** pertinent pour transférer la part financière résiduelle.

---

### 4.5 R5 - Départ d'un commercial avec le fichier clients

| Élément | Valeur |
|---|---|
| **Niveau initial** | 🟡 Modéré (G3 × V3) |
| **Mesures** | M03, M09, M14 |
| **Niveau résiduel** | 🟡 **Modéré** (G3 × V2) |
| **Décision** | Acceptation proposée, suivi trimestriel |

**Pourquoi la gravité reste G3** : la divulgation du fichier clients reste une atteinte durable à la position commerciale et une violation RGPD, même si les exports sont restreints.

**Pourquoi la vraisemblance passe de V3 à V2** : la restriction des exports à la direction commerciale et le blocage des supports USB (M09) réduisent les possibilités d'export massif ; l'alerte sur les exports volumineux (M14) détecte les comportements anormaux ; la mise à jour du registre RGPD (M03) améliore la conformité. **Ces mesures réduisent la fraude sans la supprimer** : un commercial conserve un **accès légitime** au CRM, et il peut photographier l'écran ou copier des données à la main.

> **Lecture** : R5 **reste modéré** après traitement. C'est un risque de **menace interne** : la détection et la dissuasion progressent, mais un accès légitime ne peut pas être totalement neutralisé.

---

## 5. Synthèse des évolutions

### 5.1 Répartition avant / après

| Niveau | Avant PTR | Après PTR | Évolution |
|:-:|:-:|:-:|:-:|
| 🔴 **Élevé** | **2** (R1, R3) | **0** | **-2** |
| 🟡 **Modéré** | **3** (R2, R4, R5) | **4** (R1, R3, R4, R5) | **+1** |
| 🟢 **Significatif** | **0** | **1** (R2) | **+1** |
| ⚪ **Faible** | **0** | **0** | 0 |

> **Lecture** : les **deux risques élevés sont éliminés** (R1 et R3 passent en Modéré), et R2 descend en Significatif. Aucun risque ne reste en Élevé. En revanche, **quatre risques restent en Modéré** : R1, R3, R4 et R5. C'est cohérent avec la nature des mesures : elles réduisent la vraisemblance, mais ne suppriment pas les scénarios.

### 5.2 Effet des mesures sur la gravité et la vraisemblance

| Risque | Gravité | Vraisemblance | Niveau |
|:-:|:-:|:-:|:-:|
| **R1** | **G4 → G3** (M15) | V3 → V2 | Élevé → Modéré |
| **R2** | G3 (inchangée) | **V2 → V1** | Modéré → Significatif |
| **R3** | **G4 → G3** (M15) | V3 → V2 | Élevé → Modéré |
| **R4** | G3 (inchangée) | V3 → V2 | Modéré (inchangé) |
| **R5** | G3 (inchangée) | V3 → V2 | Modéré (inchangé) |

**Deux enseignements** :

1. **La baisse de gravité ne concerne que R1 et R3**, et elle est **entièrement due à M15**. Aucune autre mesure n'agit sur la gravité : toutes les autres réduisent la vraisemblance.
2. **La baisse de vraisemblance concerne les cinq risques**, mais elle est **plus forte pour R2** (V2 → V1) que pour les autres (V3 → V2). Le tiers traversé par R2 est déjà le plus mature.

### 5.3 Ce que le PTR ne résout pas

| Limite | Risque concerné | Explication |
|---|:-:|---|
| Un commercial conserve un **accès légitime** au CRM | R5 | M09 et M14 détectent et restreignent, mais ne peuvent pas empêcher un accès légitime |
| Le **client** effectue le paiement | R4 | M10 et M18 informent et contrôlent, mais la décision de payer appartient au client |
| L'**exfiltration de données** reste possible | R1, R3 | M15 empêche la perte définitive, mais pas la copie des données avant chiffrement |
| L'**indisponibilité de l'ERP** reste possible | R1, R2, R3 | M16 (PCA/PRA) réduit la durée, mais ne supprime pas l'arrêt |
| Un **tiers critique** reste un tiers critique | R1, R2 | M01 et M08 encadrent, mais ne suppriment pas la dépendance |

> Ces limites doivent être **explicitées en soutenance** : un PTR ne supprime pas tous les risques, il les **réduit à un niveau accepté par la direction**.

---

## 6. Décision proposée à la direction

### 6.1 Les quatre décisions attendues

1. **Accepter explicitement les risques résiduels** : R1, R3, R4 et R5 restent **modérés** après traitement ; R2 devient **significatif**. Aucun risque ne reste en Élevé.
2. **Valider le plan de traitement du risque et son budget** (~33 k€ d'investissement, ~51 à 56 k€/an).
3. **Mandater le DAF** pour renégocier le contrat d'infogérance (M01) avant fin janvier 2027.
4. **Désigner formellement un référent sécurité** et instaurer un comité sécurité trimestriel.

### 6.2 Conditions de l'acceptation

L'acceptation des risques résiduels est **conditionnée** à :

- la **mise en œuvre effective de M15** (sauvegarde immuable testée), sans laquelle R1 et R3 restent en **Élevé** ;
- la **signature de l'avenant M01** avec l'infogérant, sans laquelle R1 reste en V3 ;
- le **déploiement de M06** (MFA), sans lequel R1, R3 et R4 restent en V3 ;
- la **mise en place du cadre de suivi** ([`A5_cadre_suivi.md`](./A5_cadre_suivi.md)) pour vérifier que les mesures sont réellement appliquées.

> **Formule utile en soutenance** : « Nous proposons à la direction d'accepter les risques résiduels R1, R3, R4 et R5 au niveau Modéré, et R2 au niveau Significatif, sous réserve que M15, M01 et M06 soient effectivement déployées et que le cadre de suivi soit opérationnel. »

### 6.3 Cas des risques non acceptés

Si la direction **refuse** d'accepter un risque résiduel, deux options sont possibles :

- **Renforcer le PTR** : ajouter une mesure complémentaire, par exemple une assurance plus couvrante (M17) ou une supervision 24/7 ;
- **Revoir le périmètre** : externaliser davantage, ou modifier l'architecture pour réduire la dépendance à un tiers.

> Ces options ne sont pas détaillées dans le PTR actuel : elles feraient l'objet d'une révision si la direction refusait l'acceptation.

---

## 7. Correspondance avec le classeur EBIOS RM

| Élément de cette fiche | Feuille du classeur | Colonnes |
|---|---|---|
| Risque | `Risques résiduels` | Colonne A |
| Gravité initiale | `Risques résiduels` | Colonne B |
| Vraisemblance initiale | `Risques résiduels` | Colonne C |
| Niveau initial | `Risques résiduels` | Colonne D |
| Mesures | `Risques résiduels` | Colonne E |
| Gravité résiduelle | `Risques résiduels` | Colonne F |
| Vraisemblance résiduelle | `Risques résiduels` | Colonne G |
| Niveau résiduel | `Risques résiduels` | Colonne H |
| Décision | `Risques résiduels` | Colonne I |
| Échelles et matrice | `Métriques` | Blocs « Gravité », « Vraisemblance », « Niveau de risque » |
| Mesures détaillées | `PTR` | Colonnes A à L |

---

## 8. Checklist de validation

- [x] Les **cinq risques résiduels** R1 à R5 de la feuille `Risques résiduels` sont repris.
- [x] Chaque risque porte sa **gravité initiale**, sa **vraisemblance initiale** et son **niveau initial**.
- [x] Chaque risque porte ses **mesures appliquées**, sa **gravité résiduelle**, sa **vraisemblance résiduelle** et son **niveau résiduel**.
- [x] Chaque risque porte une **décision** : acceptation proposée à la direction.
- [x] La **baisse de gravité de R1 et R3** est expliquée par M15 (sauvegarde immuable testée).
- [x] La **baisse de vraisemblance** est expliquée pour chaque risque par les mesures correspondantes.
- [x] Le cas **R2** (seul risque à passer en Significatif) est distingué.
- [x] Le cas **R4 et R5** (qui restent Modérés) est expliqué : le client paie, le commercial a un accès légitime.
- [x] Les **limites du PTR** sont explicitées : ce qu'il ne résout pas.
- [x] Les **conditions de l'acceptation** sont posées : M15, M01, M06, cadre de suivi.
- [x] Les **décisions attendues de la direction** sont explicitées.
- [x] Les niveaux résiduels sont **cohérents avec la matrice** de la feuille `Métriques`.
- [x] Le tableau est **cohérent avec la feuille `Risques résiduels`** du classeur.
- [x] Les risques résiduels sont **cohérents avec le PTR** (`A5_PTR.md`) et la synthèse (`A5_synthese_risques.md`).

---

## 9. Références

- ANSSI - *EBIOS Risk Manager*, fiche méthode « Risques résiduels » (atelier 5).
- Classeur modèle `EBIOS_RM_Ateliers_modele.xlsx` - feuilles `Risques résiduels`, `PTR`, `Métriques`.
- Dossier de synthèse - § 7.3 « Risques résiduels » (page 18).
- Fiche amont : [`A5_PTR.md`](./A5_PTR.md).
- Fiche associée : [`A5_synthese_risques.md`](./A5_synthese_risques.md), [`A5_cadre_suivi.md`](./A5_cadre_suivi.md).