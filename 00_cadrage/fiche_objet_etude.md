# Fiche objet d'étude — Plateforme cloud ERP/CRM de Rhénalis SAS

> **Cadrage de l'étude EBIOS Risk Manager** - Atelier 1, étape 1.1  
> Feuille du classeur : `Organisation`

---

## 1. Identification du rendu

| Champ | Valeur |
|---|---|
| **Objet du TP** | Analyse de risques cyber d'une plateforme cloud ERP/CRM |
| **Méthode** | EBIOS Risk Manager v1.5 (ANSSI, mars 2024) - conforme ISO/IEC 27005:2022 |
| **Organisation étudiée** | Rhénalis SAS - PME de distribution B2B de matériel électrique |
| **Formation** | BUT 3 Réseaux & Télécommunications — parcours Cybersécurité |
| **Établissement** | UHA / IUT de Colmar |
| **Date de l'étude** | 21 octobre 2026 |
| **Livrables associés** | `EBIOS_RM_Ateliers_modele.xlsx` · [`dossier de synthèse`](../EBIOS_RM_Dossier_de_synthese.pdf) - support de restitution orale |

---

## 2. Objet de l'étude

L'étude porte sur la **capacité de Rhénalis SAS à vendre, livrer, facturer et tenir sa comptabilité** grâce à sa plateforme cloud hébergeant l'ERP et le CRM.

**Plateforme étudiée** [F] :
- Postes de travail (~75 postes, dont 12 portables nomades)
- Serveurs d'application ERP et CRM (IaaS)
- Base de données
- Annuaire (Active Directory)
- Sauvegardes
- Prestataire d'infogérance (InfoGest Services)

**Profil de l'organisation** [H] :
- ~90 salariés, 22 M€ de chiffre d'affaires
- Implantée à Colmar et Mulhouse
- Distribution B2B de matériel électrique à des professionnels

> **Statuts utilisés dans ce document** : `[F]` fait établi · `[D]` déclaration · `[H]` hypothèse · `[M]` information manquante. Le journal complet des 23 hypothèses figure en [annexe A du dossier de synthèse](../EBIOS_RM_Dossier_de_synthese.pdf).

---

## 3. Périmètre de l'étude

### 3.1 Dans le périmètre

| Élément | Justification |
|---|---|
| **ERP** (ventes, achats, stocks, facturation, comptabilité) | Cœur de l'activité métier (VM1, VM3, VM4, VM5) |
| **CRM** | Fichier clients et prospects (VM2) |
| **Messagerie SaaS** | Bien support de VM1 et VM3 : commandes et factures y transitent |
| **Serveurs d'application, base de données, annuaire, infrastructure IaaS** | Socle technique de l'ERP/CRM |
| **Sauvegardes** | Gérées par l'infogérant — critiques pour la résilience |
| **~75 postes** accédant à l'ERP/CRM, dont 12 portables nomades | Point d'entrée utilisateur (SO3, SO4, SO5) |
| **Accès VPN** du siège, VPN nomade et accès d'administration de l'infogérant | Chemin d'attaque privilégié (SO1) |

### 3.2 Hors périmètre

| Élément exclu | Raison |
|---|---|
| Infrastructure interne du fournisseur de messagerie | Relève du fournisseur — seul l'usage par Rhénalis est étudié |
| Hébergement physique des serveurs | Relève de l'hébergeur IaaS, traité comme **partie prenante** (atelier 3) |
| Paie et RH | Logiciel séparé, sans interface avec l'ERP [H] |
| Site web vitrine | Hébergé ailleurs, sans prise de commande en ligne [H] |
| Équipements d'entrepôt | Faible dépendance à la plateforme [H] |
| Téléphonie et sécurité physique des locaux | Hors objet d'étude |

---

## 4. Cadre temporel

| Élément | Valeur |
|---|---|
| **Date de l'étude** | Octobre 2026 |
| **Cycle stratégique** (ateliers 1, 2, 3, 5) | Révision tous les **3 ans**, ou en cas de changement majeur (nouvel ERP, changement d'infogérant ou d'hébergeur) |
| **Cycle opérationnel** (atelier 4 et suivi du plan) | Révision **annuelle**, ou après tout incident significatif |
| **Horizon du plan de traitement (PTR)** | **12 mois** |
| **Prochaine revue complète** | Octobre 2027 |

---

## 5. Participants et rôles

Matrice RACI issue de la feuille `Organisation` — **R** = réalise, **A** = approuve, **C** = consulté, **I** = informé.

![Matrice RACI EBIOS des participants](./Matrice%20RACI%20EBIOS%20des%20participants.png)


> ⚠️ **La direction et le métier sont indispensables à l'atelier 1** pour valider les enjeux.

---

## 6. Hypothèses structurantes du cadrage

Les hypothèses suivantes conditionnent directement l'objet et le périmètre de l'étude. Elles sont reprises intégralement dans le journal d'hypothèses (annexe A du dossier de synthèse).

| N° | Hypothèse | Impact sur le cadrage |
|---|---|---|
| **H01** | PME de 90 salariés, distribution B2B, 22 M€ de CA | Échelle de gravité (G3 ≈ 300 k€/semaine de CA) |
| **H02** | L'ERP est indispensable : sans lui, ni commande ni facturation | Justifie VM1 et VM3 comme valeurs métier critiques |
| **H03** | Le personnel peut tenir 1 journée en mode dégradé, pas davantage | Cote D3 pour VM1 |
| **H12** | Pas de PSSI formalisée ni de PCA/PRA | Maturité SSI faible, typique d'une PME |
| **H13** | Contrat d'infogérance sans clause de sécurité | InfoGest en zone danger (atelier 3) |

---

## 7. Correspondance avec le classeur

| Élément de cette fiche | Feuille du classeur |
|---|---|
| Objet de l'étude, participants, cadre temporel | [`Organisation`](../EBIOS_RM_Ateliers_modele.xlsx) |
| Échelles de gravité et de vraisemblance | [`Métriques`](../EBIOS_RM_Ateliers_modele.xlsx) |
| Détail des valeurs métier et biens supports | [`Atelier 1 - Missions`](../EBIOS_RM_Ateliers_modele.xlsx) |

---

## 8. Références

- ANSSI - *EBIOS Risk Manager*, guide et fiches méthodes des ateliers 1 à 5 : [cyber.gouv.fr](https://cyber.gouv.fr)
- Classeur modèle officiel `EBIOS_RM_Ateliers_modele.xlsx`
- MITRE ATT&CK - cadre de référence pour les scénarios opérationnels : [attack.mitre.org](https://attack.mitre.org)
- ISO/IEC 27005:2022 - management du risque lié à la sécurité de l'information
