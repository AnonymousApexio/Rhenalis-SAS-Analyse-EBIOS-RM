# A1 - Socle de sécurité et écarts de conformité

> **Atelier 1 - Étape 1.4 : Socle de sécurité**
> Feuille du classeur : `Atelier 1 - GAP`  
> Dossier parent : [`README.md`](../README.md) · Fiche amont : [`A1_evenements_redoutes.md`](./A1_evenements_redoutes.md) · Fiche aval: [`A2_couples_SR_OV.md`](../02_atelier2_sources_risque/A2_couples_SR_OV.md)

---

## 1. Identification

| Champ | Valeur |
|---|---|
| **Objet de l'étude** | Plateforme cloud hébergeant l'ERP et le CRM de Rhénalis SAS *(cas fictif)* |
| **Atelier** | Atelier 1 - Cadrage et socle de sécurité |
| **Étape** | 1.4 - État du socle de sécurité et écarts de conformité |
| **Livrable** | Tableau des écarts, rattachés aux référentiels, aux ER et aux risques |
| **Statuts** | `[F]` fait établi · `[H]` hypothèse · `[M]` information manquante |

> **Rappel méthodologique** - Le **socle de sécurité** décrit l'état réel des mesures de sécurité en place, et non l'état souhaité. Les écarts constatés alimentent directement la **cotation de vraisemblance** de l'atelier 4 et le **plan de traitement du risque** de l'atelier 5.  
> **Important** : dans ce cas fictif, **aucun écart n'est un fait établi**. Tous reposent sur des hypothèses `[H]` ou des informations manquantes `[M]`, à vérifier lors d'une mission réelle.

---

## 2. Référentiels utilisés

| Référentiel | Type | Usage dans l'étude |
|---|---|---|
| **Guide d'hygiène informatique ANSSI (42 mesures)** | Bonnes pratiques | Mesures techniques et organisationnelles de base |
| **RGPD (règlement UE 2016/679)** | Réglementation | Protection des données personnelles du CRM |
| **Code de commerce et Livre des procédures fiscales** | Réglementation | Conservation légale des pièces comptables pendant 10 ans |
| **Contrat d'infogérance InfoGest Services** | Contrat | Exigences de sécurité vis-à-vis du prestataire |
| **Contrat d'hébergement IaaS** | Contrat | Qualification et garanties de l'hébergeur |
| **Contrôle interne (procédures financières)** | Procédure interne | Vérification des changements de RIB |

---

## 3. Tableau des écarts de conformité

> Les codes `GAP01` à `GAP13` sont ajoutés pour la traçabilité documentaire ; le classeur ne comporte pas de codification propre dans la feuille `Atelier 1 - GAP`.

| Code | Référentiel | Type | État d'application | Écart constaté | Justification / statut | Hypothèses | ER / risques concernés |
|---|---|---|---|---|---|---|---|
| **GAP01** | Guide d'hygiène ANSSI (42 mesures) | Bonnes pratiques | Partiellement appliqué | Pas d'authentification multifacteur sur les accès distants d'administration (VPN de l'infogérant) ni sur la messagerie | Configuration historique de l'infogérant, jamais remise en cause ; aucune exigence MFA dans le contrat. `[H]` | H04 | ER1, ER6 ; R1, R3, R4 |
| **GAP02** | Guide d'hygiène ANSSI (42 mesures) | Bonnes pratiques | Partiellement appliqué | Compte administrateur de domaine partagé entre les techniciens de l'infogérant, non nominatif | Facilité d'exploitation pour l'infogérant ; empêche toute traçabilité des actions d'administration. `[H]` | H05 | ER1, ER6 ; R1, R3 |
| **GAP03** | Guide d'hygiène ANSSI (42 mesures) | Bonnes pratiques | Partiellement appliqué | Aucun test de restauration documenté ; pas de copie hors ligne ou immuable | Fréquence quotidienne à confirmer (H06) ; aucun compte rendu de test (H07 `[M]`) ; copie sur la même infrastructure (H08). Coût d'une copie externalisée jamais budgété. | H06, H07, H08 | ER6 ; R1, R2, R3 |
| **GAP04** | Guide d'hygiène ANSSI (42 mesures) | Bonnes pratiques | Partiellement appliqué | Pas de solution de détection sur les postes (EDR), antivirus classique uniquement | Budget sécurité limité, pas de personnel pour exploiter les alertes. `[H]` | H09 | ER6 ; R3 |
| **GAP05** | Guide d'hygiène ANSSI (42 mesures) | Bonnes pratiques | Non appliqué | Pas de journalisation centralisée ni de supervision de sécurité | Aucun SIEM ni SOC ; journaux conservés localement sur chaque serveur. `[H]` | H11 | ER1, ER6 ; R1, R3 |
| **GAP06** | Guide d'hygiène ANSSI (42 mesures) | Bonnes pratiques | À vérifier | Application des correctifs sur les postes déclarée mensuelle, sans preuve | Déclaration à recueillir auprès du responsable informatique (H10) : à confirmer par un export de la console de mise à jour. Correctifs des serveurs : responsabilité de l'infogérant, non documentée. | H10 | ER6 ; R3 |
| **GAP07** | Guide d'hygiène ANSSI (42 mesures) | Bonnes pratiques | Non appliqué | Pas de politique de sécurité (PSSI) ni de plan de continuité et de reprise (PCA/PRA) | Pas de RSSI dédié, sujet jamais porté par la direction. `[H]` | H12 | Tous les ER ; R1 à R5 |
| **GAP08** | Guide d'hygiène ANSSI (42 mesures) | Bonnes pratiques | Partiellement appliqué | Droits d'accès au CRM trop larges : tous les commerciaux peuvent exporter l'ensemble du fichier clients ; aucun contrôle des exports ni des supports USB | Paramétrage par défaut du CRM, pas de revue périodique des droits. `[H]` | H19, H21 | ER3 ; R5 |
| **GAP09** | RGPD (règlement UE 2016/679) | Réglementation | Partiellement appliqué | Registre des traitements incomplet pour le CRM ; pas de procédure de notification de violation à la CNIL sous 72 h | Pas de DPO désigné, sujet traité ponctuellement par le DAF. `[H]` | H16 | ER3 ; R5 |
| **GAP10** | Code de commerce et Livre des procédures fiscales | Réglementation | Appliqué sous réserve | La conservation légale repose sur des sauvegardes sans test de restauration documenté | Conformité théorique, non démontrée tant qu'aucun test de restauration n'est réalisé (H07). | H07 | ER6 ; R1, R3 |
| **GAP11** | Contrat d'infogérance InfoGest Services | Contrat | Partiellement appliqué | Aucune clause de sécurité : ni exigences techniques, ni droit d'audit, ni délai de notification d'incident | Contrat ancien centré sur la disponibilité ; jamais renégocié. `[H]` | H13 | ER1, ER6 ; R1 |
| **GAP12** | Contrat d'hébergement IaaS | Contrat | À vérifier | Niveau de qualification ou de certification de l'hébergeur inconnu (SecNumCloud ou autre) | Information manquante : à vérifier dans le contrat et les annexes de sécurité. `[M]` | H14 | ER6 ; R1 |
| **GAP13** | Contrôle interne (procédures financières) | Procédure interne | Non appliqué | Aucune procédure de vérification des changements de RIB (ni contre-appel, ni double validation) ; clients jamais informés du risque de fraude | Changements de RIB traités sur simple courriel. `[H]` | H20 | ER5 ; R4 |

---

## 4. Analyse du socle de sécurité

### 4.1 Répartition par état d'application

| État d'application | Nombre d'écarts | Codes | Poids |
|:-:|:-:|:-:|:-:|
| **Partiellement appliqué** | 7 | GAP01, GAP02, GAP03, GAP04, GAP08, GAP09, GAP11 | 54 % |
| **Non appliqué** | 3 | GAP05, GAP07, GAP13 | 23 % |
| **À vérifier** | 2 | GAP06, GAP12 | 15 % |
| **Appliqué sous réserve** | 1 | GAP10 | 8 % |
| **Total** | **13** | - | **100 %** |

### 4.2 Répartition par référentiel

| Référentiel | Nombre d'écarts | Codes |
|:-:|:-:|:-:|
| Guide d'hygiène ANSSI (42 mesures) | 8 | GAP01 à GAP08 |
| RGPD | 1 | GAP09 |
| Code de commerce / procédures fiscales | 1 | GAP10 |
| Contrat d'infogérance | 1 | GAP11 |
| Contrat d'hébergement IaaS | 1 | GAP12 |
| Procédure interne | 1 | GAP13 |

> **Lecture** : les écarts sont concentrés sur le guide d'hygiène ANSSI, ce qui est cohérent avec une PME dont la sécurité est portée par une seule personne et un infogérant. Les écarts contractuels (GAP11, GAP12) sont particulièrement structurants, car ils conditionnent la capacité de Rhénalis à exiger des mesures de son prestataire.

---

## 5. Écarts critiques et rattachement aux risques

| Écart critique | Pourquoi il est critique | ER visé | Risque(s) | Mesures PTR associées |
|---|---|---|---|---|
| **GAP03** - sauvegardes non testées, pas de copie hors ligne | Il conditionne le seul ER coté **G4** : la perte définitive des données comptables. Sans test de restauration, la conformité légale de conservation n'est pas démontrée. | ER6 | R1, R3 | M15, M16 |
| **GAP01** - absence de MFA | Facilite la compromission de l'infogérant et des messageries ; cité comme facteur favorisant de SO1 et SO4. | ER6, ER5 | R1, R3, R4 | M06, M01 |
| **GAP02** - compte administrateur partagé | Supprime la traçabilité des actions d'administration et facilite le mouvement latéral. | ER6 | R1, R3 | M07, M11, M01 |
| **GAP08** - droits CRM trop larges, exports non contrôlés | Permet à un commercial d'emporter le fichier clients avec ses droits légitimes. | ER3 | R5 | M09, M14 |
| **GAP13** - aucune vérification des changements de RIB | Laisse la fraude au RIB se produire sans contrôle interne détectable. | ER5 | R4 | M10, M18 |
| **GAP11** - contrat d'infogérance sans clause de sécurité | Empêche d'imposer MFA, comptes nominatifs, journalisation et notification d'incident à l'infogérant. | ER1, ER6 | R1 | M01 |

> **Point de vigilance** : **H07** `[M]` (aucun compte rendu de test de restauration) et **H14** `[M]` (qualification de l'hébergeur inconnue) bloquent une conclusion ferme sur R1. La cotation de R1 dépend directement de la vérification de GAP03 et GAP12.

---

## 6. Rattachement aux scénarios et au plan de traitement

| Scénario stratégique | Écarts du socle qui le favorisent | Mesures de traitement |
|---|---|---|
| **SS1** - rançongiciel via l'infogérant | GAP01, GAP02, GAP03, GAP05, GAP11 | M01, M06, M07, M11, M13, M15 |
| **SS2** - rançongiciel via l'éditeur | GAP03, GAP05, GAP07 | M07, M08, M15, M16 |
| **SS3** - rançongiciel via hameçonnage d'un salarié | GAP01, GAP03, GAP04, GAP05, GAP06, GAP07 | M05, M06, M11, M12, M13, M15, M16, M19 |
| **SS4** - fraude au RIB | GAP01, GAP13 | M05, M06, M10, M17, M18 |
| **SS5** - export du fichier clients | GAP08, GAP09 | M03, M09, M14 |

> Les écarts du socle ne sont pas des constats d'audit : ce sont des **hypothèses de travail**. Les vérifier — tests de restauration, configuration des accès distants, revue des droits du CRM — serait la première étape d'une mission réelle et pourrait modifier les vraisemblances de l'atelier 4.

---

## 7. Correspondance avec le classeur EBIOS RM

| Élément de cette fiche | Feuille du classeur | Colonnes |
|---|---|---|
| Référentiel | `Atelier 1 - GAP` | Colonne A (Type de référentiel) |
| Nom du référentiel | `Atelier 1 - GAP` | Colonne B |
| État d'application | `Atelier 1 - GAP` | Colonne C |
| Écart constaté | `Atelier 1 - GAP` | Colonne D |
| Justification de l'écart | `Atelier 1 - GAP` | Colonne E |
| Échelles D-I-C-T et gravité | `Métriques` | Bloc « Besoins de sécurité » et bloc « Gravité » |
| Risques et mesures | `Atelier 5 - Risques`, `PTR` | Colonnes Risque, Mesures |

---

## 8. Checklist de validation

- [x] Les **13 écarts** de la feuille `Atelier 1 - GAP` sont repris et codés `GAP01` à `GAP13`.
- [x] Chaque écart est rattaché à un **référentiel** et à un **type** (bonnes pratiques, réglementation, contrat, procédure interne).
- [x] Chaque écart est qualifié par un **état d'application** : partiellement appliqué, non appliqué, à vérifier, appliqué sous réserve.
- [x] Chaque écart est **justifié** par une hypothèse `[H]` ou une information manquante `[M]`.
- [x] Les écarts **critiques** sont identifiés et reliés aux ER, aux risques et aux mesures PTR.
- [x] Les dépendances aux informations manquantes **H07** et **H14** sont explicitées.
- [x] Le tableau est **cohérent avec la feuille `Atelier 1 - GAP`** du classeur.
- [x] La distinction entre **socle réel** et **socle souhaité** est rappelée.
- [x] Les écarts sont rattachés aux **scénarios stratégiques** et au **plan de traitement**.

---

## 9. Références

- ANSSI - *Guide d'hygiène informatique*, 42 mesures.
- ANSSI - *EBIOS Risk Manager*, fiche méthode « Socle de sécurité » (atelier 1).
- RGPD - règlement UE 2016/679.
- Code de commerce et Livre des procédures fiscales - conservation des pièces comptables.
- Classeur modèle `EBIOS_RM_Ateliers_modele.xlsx` - feuilles `Atelier 1 - GAP`, `Métriques`.
- Dossier de synthèse - § 3.3 « Socle de sécurité : écarts constatés » (page 7).
- Fiche amont : [`A1_evenements_redoutes.md`](./A1_evenements_redoutes.md).
- Fiche aval : [`02_atelier2_sources_risque/A2_couples_SR_OV.md`](../02_atelier2_sources_risque/A2_couples_SR_OV.md).