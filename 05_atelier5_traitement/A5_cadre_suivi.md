# A5 - Cadre de suivi

> **Atelier 5 - Étape 5.4 : Cadre de suivi**  
> Feuille du classeur : `Cadre de suivi` (+ `PTR`, `Risques résiduels`)  
> Dossier parent : [`README.md`](../README.md) · Fiche amont : [`A5_risques_residuels.md`](./A5_risques_residuels.md) · Fiches associées : [`A5_synthese_risques.md`](./A5_synthese_risques.md), [`A5_PTR.md`](./A5_PTR.md)

---

## 1. Identification

| Champ | Valeur |
|---|---|
| **Objet de l'étude** | Plateforme cloud hébergeant l'ERP et le CRM de Rhénalis SAS |
| **Atelier** | Atelier 5 - Traitement du risque |
| **Étape** | 5.4 - Cadre de suivi du plan de traitement et des risques résiduels |
| **Livrable** | Indicateurs, cibles, fréquences, responsables ; gouvernance du suivi ; cycles de revue |
| **Statuts** | `[F]` fait établi · `[H]` hypothèse · `[M]` information manquante |

> **Rappel méthodologique** - Le **cadre de suivi** vérifie que le PTR est **réellement appliqué** et que les risques résiduels restent **sous contrôle**. Il définit des **indicateurs mesurables**, un **responsable nommé** pour chacun, une **fréquence de mesure** et une **cible**. Il définit aussi la **gouvernance** : qui pilote, à quelle fréquence, et selon quels cycles de revue.

---

## 2. Principes du cadre de suivi

### 2.1 Trois finalités

| Finalité | Question à laquelle le cadre répond |
|---|---|
| **Vérifier l'exécution** | Les actions du PTR sont-elles **réellement déployées** dans les délais ? |
| **Vérifier l'efficacité** | Les mesures **produisent-elles l'effet attendu** sur les risques résiduels ? |
| **Détecter les évolutions** | Le contexte (menace, écosystème, périmètre) a-t-il **changé** au point de revoir l'analyse ? |

### 2.2 Règles de construction

- **Un indicateur = une mesure liée** : chaque indicateur est rattaché à une action du PTR (colonne « Mesure liée »).
- **Une cible chiffrée** : l'indicateur doit être **mesurable**, avec une valeur cible explicite.
- **Un responsable nommé** : la responsabilité est portée par une **personne**, pas par un service ou une fonction seule.
- **Une fréquence de mesure** : mensuelle, trimestrielle, semestrielle ou annuelle.
- **Un circuit de décision** : ce qui se passe si la cible n'est pas atteinte.

---

## 3. Indicateurs de suivi

### 3.1 Tableau des indicateurs

| Code | Indicateur | Mesure liée | Cible | Fréquence | Responsable | Source de la donnée |
|:-:|---|:-:|:-:|:-:|---|---|
| **I01** | % de comptes à privilèges et d'accès distants protégés par MFA | **M06** | **100 %** | Mensuelle | Sophie Haas (resp. informatique) | Console d'administration MFA |
| **I02** | Tests de restauration réussis | **M15** | **4 par an** | Trimestrielle | Sophie Haas (resp. informatique) | Compte rendu de test de restauration |
| **I03** | Taux de clic aux exercices d'hameçonnage | **M05** | **< 10 %** | Semestrielle | Sophie Haas (resp. informatique) | Résultats de la campagne d'exercice |
| **I04** | Comptes administrateurs partagés encore actifs | **M07** | **0** | Mensuelle | InfoGest / Sophie Haas | Audit de l'annuaire |
| **I05** | Avancement du PTR (actions terminées / prévues) | **Toutes** | **100 % au 31/10/2027** | Trimestrielle | Claire Muller (DG) | Tableau de bord du PTR |
| **I06** | RIB modifiés dans l'ERP validés par le DAF | **M18** | **100 %** | Mensuelle | Thomas Weber (DAF) | Journal des modifications RIB |
| **I07** | Grands comptes informés de la procédure RIB | **M10** | **100 %** | Annuelle | Thomas Weber (DAF) | Liste des envois et accusés de réception |
| **I08** | Postes à jour des correctifs depuis moins de 30 jours | **M19** | **≥ 95 %** | Mensuelle | Sophie Haas (resp. informatique) | Console de gestion des mises à jour |

> Les indicateurs I01 à I08 sont ceux de la feuille `Cadre de suivi` du classeur. Aucun indicateur supplémentaire n'a été ajouté : le cadre doit rester **lisible et exploitable** par une PME.

### 3.2 Indicateurs par groupe du PTR

| Groupe | Indicateurs | Nombre |
|:-:|:-:|:-:|
| **Gouvernance** | I03 (sensibilisation M05), I05 (avancement PTR), I06 (RIB M18), I07 (courrier M10) | **4** |
| **Protection** | I01 (MFA M06), I04 (comptes partagés M07), I08 (correctifs M19) | **3** |
| **Défense** | *aucun indicateur dédié* | **0** |
| **Résilience** | I02 (tests de restauration M15) | **1** |
| **Total** | | **8** |

> **Point de vigilance** : les actions de **Défense** (M12 EDR, M13 supervision, M14 alerte exports) ne sont pas couvertes par un indicateur dédié dans le cadre actuel. C'est une **limite** : le cadre mesure l'exécution, mais pas directement l'efficacité de la détection. Une révision pourrait ajouter un indicateur de **délai de détection** (cf. § 3.3).

### 3.3 Indicateurs candidats pour une révision

| Indicateur candidat | Mesure liée | Cible proposée | Fréquence | Pourquoi il n'est pas dans le cadre initial |
|:-:|---|:-:|:-:|---|
| **Délai de détection d'un accès admin anormal** | M13 | **< 24 h** | Trimestrielle | Dépend du déploiement effectif du SOC managé (P2, 31/07/2027) |
| **% du parc couvert par l'EDR** | M12 | **100 %** | Trimestrielle | Dépend du déploiement effectif de l'EDR (P1, 28/02/2027) |
| **Nombre d'alertes d'export volumineux traitées** | M14 | **100 %** | Mensuelle | Dépend du déploiement de l'alerte (P3, 30/04/2027) |

> Ces indicateurs seront **ajoutés à la revue de octobre 2027**, une fois les mesures correspondantes déployées. Les intégrer dès maintenant créerait des indicateurs sans donnée disponible.

---

## 4. Gouvernance du suivi

### 4.1 Le comité sécurité trimestriel

| Élément | Valeur |
|---|---|
| **Fréquence** | Trimestrielle |
| **Participants** | Claire Muller (DG), Thomas Weber (DAF), Sophie Haas (resp. informatique), InfoGest Services |
| **Ordre du jour** | Avancement du PTR (I05), revue des indicateurs I01 à I08, décisions sur les écarts |
| **Livrable** | Compte rendu de comité, avec décisions et actions correctives |
| **Responsable** | Claire Muller (DG) |

> Le comité réunit **la direction et l'infogérant**. C'est le lieu où sont arbitrées les décisions qui engagent les deux parties : application de l'avenant M01, ouverture de la télémaintenance M08, suppression du compte partagé M07.

### 4.2 Le circuit de décision en cas d'écart

| Situation | Décision |
|---|---|
| **Indicateur en deçà de la cible** | Analyse de la cause, plan d'action correctif, suivi au comité suivant |
| **Indicateur en deçà de la cible pendant 2 comités consécutifs** | Escalade à la DG, révision de la mesure ou du PTR |
| **Indicateur en deçà de la cible pendant 3 comités consécutifs** | Révision du PTR, ou acceptation explicite d'un risque résiduel plus élevé |
| **Incident significatif** | Revue du cycle opérationnel (cf. § 5.2) |
| **Changement majeur de contexte** | Revue du cycle stratégique (cf. § 5.3) |

> Ce circuit évite que les indicateurs restent **sans effet** : un indicateur qui n'atteint pas sa cible déclenche une **décision**, pas seulement une observation.

---

## 5. Cycles de revue

### 5.1 Vue d'ensemble

| Cycle | Périmètre | Fréquence | Déclencheur |
|---|---|---|:-:|
| **Comité sécurité** | Avancement du PTR, indicateurs | Trimestrielle | Calendaire |
| **Cycle opérationnel** | Atelier 4 (scénarios opérationnels) et PTR | Annuelle | Calendaire, ou après tout incident significatif |
| **Cycle stratégique** | Ateliers 1, 2, 3 et 5 | Tous les 3 ans | Calendaire, ou en cas de changement majeur |
| **Revue complète** | Tous les ateliers | Tous les 3 ans | Calendaire |

### 5.2 Cycle opérationnel (annuel)

**Périmètre** : atelier 4 (scénarios opérationnels) et PTR.

**Fréquence** : **annuelle**, ou **après tout incident significatif**.

**Objet** :
- Vérifier que les **scénarios opérationnels** sont toujours pertinents (les techniques d'attaque évoluent) ;
- Vérifier que les **vraisemblances** sont toujours valides (les mesures déployées peuvent les réduire) ;
- Mettre à jour le **PTR** : actions terminées, actions reportées, nouvelles actions.

**Déclencheur d'incident significatif** :
- Un incident de sécurité avec impact opérationnel (indisponibilité > 1 jour, perte de données, fraude) ;
- Un incident chez un tiers critique (infogérant, hébergeur, éditeur) ;
- Une alerte de supervision non traitée.

### 5.3 Cycle stratégique (tous les 3 ans)

**Périmètre** : ateliers 1, 2, 3 et 5.

**Fréquence** : **tous les 3 ans**, ou en cas de **changement majeur**.

**Objet** :
- Réviser le **périmètre** (nouvelles valeurs métier, nouveaux biens supports) ;
- Réviser les **sources de risque** et les **parties prenantes** (nouveaux acteurs, nouvelles menaces) ;
- Réviser les **scénarios stratégiques** et les **risques** ;
- Réviser le **PTR** en conséquence.

**Changements majeurs déclencheurs** :
- Changement d'**ERP** ou de **CRM** ;
- Changement d'**infogérant** ou d'**hébergeur** ;
- Fusion, acquisition, ou changement significatif de l'activité ;
- Nouvelle réglementation impactante (par exemple, révision de la directive NIS 2).

### 5.4 Prochaine revue complète

**Date** : **octobre 2027**.

Cette date correspond à la fin du plan de traitement (échéance la plus lointaine : M16 au 31/10/2027). À cette date, le PTR doit être **intégralement déployé**, et une **revue complète** de l'analyse doit être conduite.

---

## 6. Tableau de bord du PTR

### 6.1 Vue trimestrielle

Le comité sécurité suit l'avancement du PTR selon le tableau suivant :

| Trimestre | Actions prévues | Actions terminées | % d'avancement | Écarts signalés | Décisions |
|:-:|:-:|:-:|:-:|---|---|
| **T4 2026** | M09, M10, M18, M06, M04, M19 | *à renseigner* | *à renseigner* | *à renseigner* | *à renseigner* |
| **T1 2027** | M01, M03, M05, M15 | *à renseigner* | *à renseigner* | *à renseigner* | *à renseigner* |
| **T2 2027** | M12, M08, M17 | *à renseigner* | *à renseigner* | *à renseigner* | *à renseigner* |
| **T3 2027** | M07, M11, M13, M14, M16 | *à renseigner* | *à renseigner* | *à renseigner* | *à renseigner* |
| **T4 2027** | M02, revue complète | *à renseigner* | *à renseigner* | *à renseigner* | *à renseigner* |

> Dans le cas éventuel ou ceci était un vrai suivi, ce tableau serait un **modèle** : il devrait être renseigné au fil des comités. Il n'est pas prérempli dans cette fiche, car l'analyse est conduite **avant** le déploiement du PTR.

### 6.2 Jalons critiques

| Jalon | Échéance | Mesure(s) | Conséquence si non tenu |
|---|:-:|:-:|---|
| **MFA déployée** | 31/12/2026 | M06 | R1, R3, R4 restent en V3 |
| **Avenant infogérance signé** | 31/01/2027 | M01 | R1 reste en V3 |
| **Sauvegarde immuable testée** | 31/01/2027 | M15 | R1 et R3 restent en **Élevé** |
| **Bastion d'administration opérationnel** | 30/04/2027 | M07 | R1 et R2 restent en V2 minimum |
| **Revue complète** | 31/10/2027 | Toutes | Le PTR doit être intégralement déployé |

> **Jalon le plus critique** : **M15** (31/01/2027). C'est la seule mesure qui fait passer R1 et R3 de G4 à G3. Si elle n'est pas tenue, les deux risques restent en **Élevé**, et l'acceptation proposée à la direction n'est plus valide.

---

## 7. Limites du cadre de suivi

| Limite | Explication | Conséquence |
|---|---|---|
| **Pas d'indicateur d'efficacité de la détection** | Les actions de Défense (M12, M13, M14) ne sont pas couvertes par un indicateur dédié | Le cadre mesure l'exécution, pas directement l'efficacité de la détection |
| **Pas d'indicateur de satisfaction client** | La fraude au RIB (R4) dépend du comportement des clients | Le cadre ne mesure pas si les clients appliquent la procédure RIB |
| **Pas d'indicateur de comportement interne** | L'export du fichier clients (R5) dépend du comportement des commerciaux | Le cadre mesure les restrictions, pas la dissuasion |
| **Indicateurs déclaratifs** | Plusieurs indicateurs reposent sur des données fournies par l'infogérant (I02, I04) | La fiabilité dépend de la transparence de l'infogérant |
| **Pas de mesure de la menace externe** | Le cadre ne suit pas l'évolution des sources de risque (SR1, SR2, SR3) | La revue du cycle stratégique (3 ans) est le seul mécanisme de mise à jour |

> Ces limites sont **assumées** : le cadre doit rester **exploitable** par une PME. Une organisation plus grande pourrait ajouter des indicateurs d'efficacité, au prix d'une charge de suivi plus lourde.

---

## 8. Correspondance avec le classeur EBIOS RM

| Élément de cette fiche | Feuille du classeur | Colonnes |
|---|---|---|
| Indicateur | `Cadre de suivi` | Colonne A |
| Mesure liée | `Cadre de suivi` | Colonne B |
| Cible | `Cadre de suivi` | Colonne C |
| Fréquence | `Cadre de suivi` | Colonne D |
| Responsable | `Cadre de suivi` | Colonne E |
| Gouvernance du suivi | `Cadre de suivi` | Bloc « Gouvernance du suivi » (lignes 11 à 15) |
| Actions du PTR | `PTR` | Colonnes A à L |
| Risques résiduels | `Risques résiduels` | Colonnes A à I |

---

## 9. Checklist de validation

- [x] Les **8 indicateurs** de la feuille `Cadre de suivi` sont repris et codés `I01` à `I08`.
- [x] Chaque indicateur est rattaché à une **mesure du PTR** (colonne « Mesure liée »).
- [x] Chaque indicateur a une **cible chiffrée**, une **fréquence** et un **responsable nommé**.
- [x] La **gouvernance** est définie : comité sécurité trimestriel, participants, ordre du jour.
- [x] Le **circuit de décision en cas d'écart** est explicité (escalade sur 2 puis 3 comités).
- [x] Les **cycles de revue** sont définis : comité trimestriel, cycle opérationnel annuel, cycle stratégique triennal.
- [x] La **prochaine revue complète** est fixée : octobre 2027.
- [x] Le **tableau de bord du PTR** est proposé, avec jalons critiques.
- [x] Le **jalon critique M15** (sauvegarde immuable testée) est identifié comme condition de l'acceptation des risques R1 et R3.
- [x] Les **limites** du cadre sont explicitées : pas d'indicateur d'efficacité de la détection, indicateurs déclaratifs, pas de mesure de la menace externe.
- [x] Le cadre est **cohérent avec le PTR** (`A5_PTR.md`) et les risques résiduels (`A5_risques_residuels.md`).
- [x] Le tableau est **cohérent avec la feuille `Cadre de suivi`** du classeur.

---

## 10. Références

- ANSSI - *EBIOS Risk Manager*, fiche méthode « Cadre de suivi » (atelier 5).
- Classeur modèle `EBIOS_RM_Ateliers_modele.xlsx` - feuilles `Cadre de suivi`, `PTR`, `Risques résiduels`.
- Dossier de synthèse - § 7.4 « Cadre de suivi » (page 19).
- Fiche amont : [`A5_risques_residuels.md`](./A5_risques_residuels.md).
- Fiches associées : [`A5_synthese_risques.md`](./A5_synthese_risques.md), [`A5_PTR.md`](./A5_PTR.md).