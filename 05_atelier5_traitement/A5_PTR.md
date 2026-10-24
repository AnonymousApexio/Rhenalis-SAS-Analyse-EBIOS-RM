# A5 - Plan de traitement du risque (PTR)

> **Atelier 5 - Étape 5.2 : Plan de traitement du risque**  
> Feuille du classeur : `PTR` (+ `Atelier 5 - Risques`)  
> Dossier parent : [`README.md`](../README.md) · Fiche amont : [`A5_synthese_risques.md`](./A5_synthese_risques.md) · Fiches associées : [`A5_risques_residuels.md`](./A5_risques_residuels.md), [`A5_cadre_suivi.md`](./A5_cadre_suivi.md)

---

## 1. Identification

| Champ | Valeur |
|---|---|
| **Objet de l'étude** | Plateforme cloud hébergeant l'ERP et le CRM de Rhénalis SAS |
| **Atelier** | Atelier 5 - Traitement du risque |
| **Étape** | 5.2 - Plan de traitement du risque (PTR) |
| **Livrable** | 19 actions réparties en 4 groupes, avec propriétaire, complexité, délai, échéance, coût et indicateur de réalisation |
| **Statuts** | `[F]` fait établi · `[H]` hypothèse · `[M]` information manquante |

> **Rappel méthodologique** - Le **plan de traitement du risque (PTR)** décrit les mesures retenues pour réduire les risques identifiés. Chaque action doit être **SMART** : **S**pécifique, **M**esurable, **A**tteignable, **R**éaliste, **T**emporelle. Elle porte un **propriétaire nommé**, une **complexité**, un **délai**, une **échéance**, un **coût estimé** et un **indicateur de réalisation**. Les actions sont réparties dans les **quatre groupes de la défense en profondeur** : Gouvernance, Protection, Défense, Résilience.

---

## 2. Principes du PTR

### 2.1 Les quatre groupes de la défense en profondeur

| Groupe | Objet | Nombre d'actions |
|:-:|---|:-:|
| **Gouvernance** | Politiques, contrats, organisation, sensibilisation | **6** |
| **Protection** | Mesures préventives techniques : MFA, bastion, droits, correctifs | **7** |
| **Défense** | Détection et réponse : EDR, supervision, alerte | **3** |
| **Résilience** | Sauvegarde, continuité, transfert | **3** |
| **Total** | | **19** |

### 2.2 Priorités

| Priorité | Définition | Nombre d'actions |
|:-:|---|:-:|
| **P1** | Action urgente, à lancer immédiatement | **9** |
| **P2** | Action importante, à lancer dans l'année | **7** |
| **P3** | Action complémentaire, à étudier | **3** |

### 2.3 Complexité

| Niveau | Signification |
|:-:|---|
| **Faible** | Action organisationnelle ou paramétrage simple, sans dépendance technique |
| **Moyenne** | Déploiement technique ou négociation contractuelle |
| **Élevée** | Projet structurant, dépendant d'un tiers ou de plusieurs services |

---

## 3. Gouvernance - 6 actions

| N° | Mesure | Risques traités | Propriétaire | Complexité | Délai | Échéance | Coût estimé `[H]` | Indicateur de réalisation | Priorité | Statut |
|:-:|---|:-:|---|:-:|:-:|:-:|:-:|---|:-:|:-:|
| **M10** | Courrier aux grands comptes : Rhénalis ne change jamais de RIB par e-mail ; en cas de doute, rappeler le numéro habituel | R4 | Thomas Weber (DAF) | Faible | 1 mois | 30/11/2026 | 0 € | % des grands comptes informés (cible 100 %) | **P1** | À lancer |
| **M01** | Avenant sécurité au contrat d'infogérance : MFA, comptes nominatifs, journalisation, correctifs des serveurs sous 30 jours, notification d'incident sous 24 h, droit d'audit annuel | R1 | Thomas Weber (DAF) | Moyenne | 3 mois | 31/01/2027 | 2 k€ (juridique) | Avenant signé | **P1** | À lancer |
| **M05** | Sensibilisation des salariés à l'hameçonnage et campagne d'exercice semestrielle | R3, R4 | Sophie Haas (resp. informatique) | Faible | 3 mois | 31/01/2027 | 3 k€/an | Taux de clic aux exercices < 10 % | **P1** | À lancer |
| **M02** | Rédiger une PSSI simplifiée et désigner formellement un référent sécurité | Tous | Claire Muller (DG) | Moyenne | 6 mois | 30/04/2027 | Interne (~15 j) | PSSI validée en comité de direction | **P2** | À lancer |
| **M03** | Mise à jour du registre RGPD et procédure de notification à la CNIL sous 72 h | R5 | Thomas Weber (DAF) | Faible | 3 mois | 31/01/2027 | 0 € | Registre à jour, procédure validée | **P2** | À lancer |
| **M04** | Vérifier la qualification de l'hébergeur IaaS et les clauses de sécurité du contrat d'hébergement | R1 | Thomas Weber (DAF) | Faible | 2 mois | 31/12/2026 | 0 € | Rapport de vérification remis | **P2** | À lancer |

> **Lecture Gouvernance** : trois actions P1, dont deux à coût nul (M10, M04). L'avenant au contrat d'infogérance (M01) est l'action structurante : il conditionne la capacité de Rhénalis à imposer des mesures à l'infogérant.

---

## 4. Protection - 7 actions

| N° | Mesure | Risques traités | Propriétaire | Complexité | Délai | Échéance | Coût estimé `[H]` | Indicateur de réalisation | Priorité | Statut |
|:-:|---|:-:|---|:-:|:-:|:-:|:-:|---|:-:|:-:|
| **M06** | Authentification multifacteur sur tous les accès distants (administration, VPN nomades), sur la console d'administration IaaS et sur la messagerie | R1, R3, R4 | Sophie Haas (resp. informatique) | Moyenne | 2 mois | 31/12/2026 | 4 k€/an | % de comptes protégés par MFA (cible 100 %) | **P1** | À lancer |
| **M07** | Bastion d'administration avec comptes nominatifs et enregistrement des sessions ; suppression du compte admin partagé | R1, R2 | Sophie Haas (pilotage) / InfoGest | Élevée | 6 mois | 30/04/2027 | 15 k€ + 5 k€/an | Aucun compte admin partagé actif | **P1** | À lancer |
| **M09** | Restreindre l'export du CRM à la direction commerciale, revue trimestrielle des droits, blocage des supports USB sur les portables | R5 | Julien Roth (dir. commercial) | Faible | 2 mois | 31/12/2026 | 1 k€ | Revue des droits faite chaque trimestre | **P1** | À lancer |
| **M18** | Double validation par le DAF de toute modification de RIB dans l'ERP (clients et fournisseurs), avec traçabilité | R4 | Thomas Weber (DAF) | Faible | 1 mois | 30/11/2026 | 0 € | 100 % des RIB modifiés validés par le DAF | **P1** | À lancer |
| **M08** | Télémaintenance de l'éditeur ouverte uniquement à la demande, via le bastion, après validation interne | R2 | Sophie Haas (resp. informatique) | Faible | 7 mois | 31/05/2027 | 0 € | 100 % des sessions validées et enregistrées | **P2** | À lancer |
| **M11** | Durcissement de l'annuaire : séparation des comptes d'administration, mots de passe admin uniques | R1, R3 | InfoGest (pilotage Sophie Haas) | Élevée | 9 mois | 31/07/2027 | 8 k€ | Audit annuaire sans écart critique | **P2** | À lancer |
| **M19** | Vérifier chaque mois l'application des correctifs sur les postes (export de la console de mise à jour) | R3 | Sophie Haas (resp. informatique) | Faible | 2 mois | 31/12/2026 | 0 € | % de postes à jour depuis moins de 30 jours (cible ≥ 95 %) | **P2** | À lancer |

> **Lecture Protection** : quatre actions P1, dont deux à coût nul (M18, M09 partiellement). La MFA (M06) et le bastion (M07) sont les mesures les plus structurantes : elles réduisent directement R1 et R3.

---

## 5. Défense - 3 actions

| N° | Mesure | Risques traités | Propriétaire | Complexité | Délai | Échéance | Coût estimé `[H]` | Indicateur de réalisation | Priorité | Statut |
|:-:|---|:-:|---|:-:|:-:|:-:|:-:|---|:-:|:-:|
| **M12** | Déployer une solution de détection et réponse (EDR) sur les postes et les serveurs | R3 | Sophie Haas (resp. informatique) | Moyenne | 4 mois | 28/02/2027 | 8 k€/an | % du parc couvert (cible 100 %) | **P1** | À lancer |
| **M13** | Journalisation centralisée et supervision externalisée (SOC managé) des accès d'administration et de l'annuaire | R1, R3 | Sophie Haas (resp. informatique) | Élevée | 9 mois | 31/07/2027 | 20 k€/an | Délai de détection d'un accès admin anormal < 24 h | **P2** | À lancer |
| **M14** | Alerte automatique sur les exports volumineux du CRM | R5 | Sophie Haas (resp. informatique) | Moyenne | 6 mois | 30/04/2027 | 2 k€ | Alerte testée et opérationnelle | **P3** | À lancer |

> **Lecture Défense** : une seule action P1 (M12, EDR), qui cible R3. La supervision (M13) est P2 : elle est structurante mais plus lourde. L'alerte sur les exports (M14) est P3 : elle complète M09.

---

## 6. Résilience - 3 actions

| N° | Mesure | Risques traités | Propriétaire | Complexité | Délai | Échéance | Coût estimé `[H]` | Indicateur de réalisation | Priorité | Statut |
|:-:|---|:-:|---|:-:|:-:|:-:|:-:|---|:-:|:-:|
| **M15** | Sauvegarde immuable externalisée chez un tiers distinct de l'infogérant, test de restauration trimestriel | R1, R2, R3 | Sophie Haas (resp. informatique) | Moyenne | 3 mois | 31/01/2027 | 6 k€/an | Test de restauration réussi chaque trimestre | **P1** | À lancer |
| **M16** | Plan de continuité et de reprise de l'ERP (mode dégradé documenté) et exercice de crise annuel | R1, R2, R3 | Claire Muller (DG) | Élevée | 12 mois | 31/10/2027 | 5 k€ | Exercice de crise réalisé, reprise < 48 h | **P2** | À lancer |
| **M17** | Étudier une cyber-assurance pour transférer le risque financier résiduel | R1, R4 | Thomas Weber (DAF) | Faible | 6 mois | 30/04/2027 | 5 à 10 k€/an | Décision de la direction | **P3** | À lancer |

> **Lecture Résilience** : M15 est **la mesure clé** du PTR. Elle fait passer la gravité de R1 et R3 de G4 à G3, car la perte définitive des données n'est plus atteignable. C'est la seule mesure qui agit sur la **gravité** et non seulement sur la vraisemblance.

---

## 7. Synthèse du PTR

### 7.1 Répartition par groupe et par priorité

| Groupe | P1 | P2 | P3 | Total |
|:-:|:-:|:-:|:-:|:-:|
| **Gouvernance** | 3 (M01, M05, M10) | 3 (M02, M03, M04) | 0 | **6** |
| **Protection** | 4 (M06, M07, M09, M18) | 3 (M08, M11, M19) | 0 | **7** |
| **Défense** | 1 (M12) | 1 (M13) | 1 (M14) | **3** |
| **Résilience** | 1 (M15) | 1 (M16) | 1 (M17) | **3** |
| **Total** | **9** | **7** | **3** | **19** |

### 7.2 Les neuf actions prioritaires (P1)

| N° | Action | Propriétaire | Échéance | Coût `[H]` |
|:-:|---|---|:-:|:-:|
| **M10** | Courrier aux grands comptes sur le RIB | Thomas Weber (DAF) | 30/11/2026 | 0 € |
| **M18** | Double validation des RIB | Thomas Weber (DAF) | 30/11/2026 | 0 € |
| **M06** | MFA sur tous les accès distants et la messagerie | Sophie Haas | 31/12/2026 | 4 k€/an |
| **M09** | Restriction des exports CRM, blocage USB | Julien Roth | 31/12/2026 | 1 k€ |
| **M01** | Avenant sécurité au contrat d'infogérance | Thomas Weber (DAF) | 31/01/2027 | 2 k€ |
| **M15** | Sauvegarde immuable externalisée et testée | Sophie Haas | 31/01/2027 | 6 k€/an |
| **M05** | Sensibilisation à l'hameçonnage | Sophie Haas | 31/01/2027 | 3 k€/an |
| **M12** | EDR sur les postes et serveurs | Sophie Haas | 28/02/2027 | 8 k€/an |
| **M07** | Bastion d'administration, comptes nominatifs | Sophie Haas / InfoGest | 30/04/2027 | 15 k€ + 5 k€/an |

**Regroupement par risque cible** :

- **Pour R1** (perte définitive via l'infogérant) : M01 (avenant), M07 (bastion), M06 (MFA), M15 (sauvegarde immuable).
- **Pour R3** (perte définitive via un salarié) : M05 (sensibilisation), M12 (EDR), M06 (MFA), M15 (sauvegarde immuable).
- **Pour R4** (fraude au RIB) : M10 (courrier), M18 (double validation), M06 (MFA).
- **Pour R5** (export fichier clients) : M09 (restriction des exports).

> **Trois mesures rapides et presque sans coût** : M09, M10, M18. Elles peuvent être lancées immédiatement et réduisent R4 et R5 sans attendre les mesures plus lourdes.

### 7.3 Effet sur les risques

| Risque | Niveau initial | Mesures principales | Effet attendu | Niveau résiduel |
|:-:|:-:|---|---|:-:|
| **R1** | 🔴 Élevé | M01, M06, M07, M11, M13, M15, M16 | G4 → G3 (M15), V3 → V2 | 🟡 **Modéré** |
| **R2** | 🟡 Modéré | M07, M08, M15, M16 | V2 → V1 | 🟢 **Significatif** |
| **R3** | 🔴 Élevé | M05, M06, M11, M12, M13, M15, M16, M19 | G4 → G3 (M15), V3 → V2 | 🟡 **Modéré** |
| **R4** | 🟡 Modéré | M05, M06, M10, M17, M18 | V3 → V2 | 🟡 **Modéré** |
| **R5** | 🟡 Modéré | M03, M09, M14 | V3 → V2 | 🟡 **Modéré** |

### 7.4 Budget et décisions attendues

**Ordre de grandeur** `[H]` : environ **33 k€ d'investissement** et **51 à 56 k€ par an de fonctionnement**, soit environ **0,4 % du chiffre d'affaires supposé** (22 M€) la première année, puis **0,25 % par an**.

| Poste | Investissement | Fonctionnement annuel |
|---|:-:|:-:|
| Gouvernance | 2 k€ | 3 k€ |
| Protection | 24 k€ | 10 k€ |
| Défense | 2 k€ | 28 k€ |
| Résilience | 5 k€ | 11 à 16 k€ |
| **Total** | **~33 k€** | **~51 à 56 k€** |

**Décisions attendues de la direction** :

1. **Valider le plan de traitement du risque et son budget**.
2. **Mandater le DAF** pour renégocier le contrat d'infogérance (M01) avant fin janvier 2027.
3. **Désigner formellement un référent sécurité** et instaurer un comité sécurité trimestriel.
4. **Accepter explicitement les risques résiduels** : R1, R3, R4 et R5 restent modérés après traitement ; R2 devient significatif.

> **Point de vigilance** : les coûts sont des ordres de grandeur, destinés à permettre un arbitrage de la direction. Ils devraient être confirmés par devis avant engagement.

---

## 8. Correspondance avec le classeur EBIOS RM

| Élément de cette fiche | Feuille du classeur | Colonnes |
|---|---|---|
| Numéro d'action (M01 à M19) | `PTR` | Colonne A |
| Groupe (Gouvernance, Protection, Défense, Résilience) | `PTR` | Colonne B |
| Mesure | `PTR` | Colonne C |
| Risques traités | `PTR` | Colonne D |
| Propriétaire | `PTR` | Colonne E |
| Complexité | `PTR` | Colonne F |
| Délai (mois) | `PTR` | Colonne G |
| Échéance | `PTR` | Colonne H |
| Coût estimé | `PTR` | Colonne I |
| Indicateur de réalisation | `PTR` | Colonne J |
| Priorité | `PTR` | Colonne K |
| Statut | `PTR` | Colonne L |
| Risques résiduels | `Risques résiduels` | Colonnes A à I |

---

## 9. Checklist de validation

- [x] Les **19 actions** de la feuille `PTR` sont reprises et codées `M01` à `M19`.
- [x] Les actions sont réparties dans les **quatre groupes** de la défense en profondeur : Gouvernance (6), Protection (7), Défense (3), Résilience (3).
- [x] Chaque action porte un **propriétaire nommé** (et non une fonction seule).
- [x] Chaque action est **SMART** : spécifique, mesurable (indicateur), atteignable, réaliste, temporelle (échéance).
- [x] Les **priorités** sont cohérentes : 9 P1, 7 P2, 3 P3.
- [x] Les **coûts** sont estimés en ordre de grandeur `[H]`, avec la mention qu'ils doivent être confirmés par devis.
- [x] Les **mesures rapides et sans coût** sont identifiées (M09, M10, M18).
- [x] La mesure **M15** (sauvegarde immuable testée) est identifiée comme **mesure clé** : elle agit sur la gravité, pas seulement sur la vraisemblance.
- [x] Les **décisions attendues de la direction** sont explicitées.
- [x] Le **budget** est cohérent avec le dossier de synthèse (~33 k€ d'investissement, ~51 à 56 k€/an).
- [x] Le PTR est **cohérent avec la synthèse des risques** (`A5_synthese_risques.md`).
- [x] Le PTR est **cohérent avec les risques résiduels** (`A5_risques_residuels.md`).
- [x] Les actions sont **cohérentes avec les écarts du socle** (GAP) de l'atelier 1 et les mesures de l'atelier 3 (ECO).

---

## 10. Références

- ANSSI - *EBIOS Risk Manager*, fiche méthode « Plan de traitement du risque » (atelier 5).
- Classeur modèle `EBIOS_RM_Ateliers_modele.xlsx` - feuilles `PTR`, `Risques résiduels`, `Cadre de suivi`.
- Dossier de synthèse - § 7.2 « Plan de traitement du risque » (pages 16-18) et § 1.2 « Les neuf actions prioritaires (P1) » (page 3).
- Fiche amont : [`A5_synthese_risques.md`](./A5_synthese_risques.md).
- Fiches associées : [`A5_risques_residuels.md`](./A5_risques_residuels.md), [`A5_cadre_suivi.md`](./A5_cadre_suivi.md).