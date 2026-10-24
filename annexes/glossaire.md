# Glossaire

> **Annexe - Glossaire des termes EBIOS Risk Manager**  
> Dossier parent : [`README.md`](../README.md) · Fiche associée : [`references.md`](./references.md)

---

## 1. Objet

Ce glossaire recense les termes utilisés dans l'analyse EBIOS Risk Manager de la plateforme cloud ERP/CRM de Rhénalis SAS. Il est destiné à faciliter la lecture du dossier de synthèse, du classeur et des fiches d'atelier. Les termes sont classés par ordre alphabétique, avec leur définition, leur usage dans l'étude et, le cas échéant, les codes correspondants.

---

## 2. Termes méthodologiques

### 2.1 Concepts EBIOS RM

| Terme | Définition | Usage dans l'étude |
|---|---|---|
| **Atelier** | Étape de la méthode EBIOS RM. Cinq ateliers structurent l'analyse : cadrage et socle (A1), sources de risque (A2), scénarios stratégiques (A3), scénarios opérationnels (A4), traitement du risque (A5). | Cinq ateliers, cinq fiches de synthèse, une feuille par atelier dans le classeur. |
| **Bien support (BS)** | Composant technique, humain, physique ou organisationnel qui porte une ou plusieurs valeurs métier. | Annuaire, base de données, sauvegardes, postes de travail, messagerie, personnel, etc. |
| **Chemin d'attaque** | Enchaînement d'actions permettant à une source de risque d'atteindre un objectif visé, en traversant ou non une partie prenante. | Cinq chemins stratégiques (SS1 à SS5) et cinq chemins opérationnels (SO1 à SO5). |
| **Couple SR/OV** | Association d'une source de risque et d'un objectif visé. Évalué en croisant motivation et ressources. | Huit couples évalués, trois retenus : SR1/OV1, SR2/OV2, SR3/OV3. |
| **Écosystème** | Ensemble des parties prenantes qui interagissent avec l'objet étudié : prestataires, fournisseurs, partenaires, clients. | Neuf parties prenantes cotées, une en zone danger, deux en zone contrôle, six en veille. |
| **Événement redouté (ER)** | Ce que l'on cherche à éviter pour une valeur métier donnée. Coté en gravité et rattaché aux besoins D-I-C-T. | Sept ER identifiés, un seul coté G4 (ER6), trois cotés G3 (ER1, ER3, ER5). |
| **Gravité (G)** | Impact métier d'un événement redouté. Échelle à quatre niveaux : G1 (mineure) à G4 (critique). | ER6 coté G4 ; ER1, ER3, ER5 cotés G3 ; ER2, ER4, ER7 cotés G2. |
| **Objectif visé (OV)** | Ce qu'une source de risque cherche à obtenir. | Huit OV identifiés, trois retenus : OV1 (rançon), OV2 (fraude), OV3 (export fichier clients). |
| **Partie prenante (PP)** | Acteur de l'écosystème qui interagit avec l'objet étudié. Cotée sur dépendance, pénétration, maturité et confiance. | Neuf PP cotées, indice de menace calculé, zones danger/contrôle/veille. |
| **Périmètre** | Ensemble des éléments inclus dans l'étude, et exclusions explicites. | ERP/CRM, postes, serveurs, base de données, annuaire, sauvegardes, infogérance. Hors périmètre : paie, site vitrine, équipements d'entrepôt. |
| **Risque (R)** | Agrégation d'une source de risque, d'un objectif visé, d'un ER, d'un SS et d'un SO. Coté en gravité et vraisemblance. | Cinq risques identifiés : R1 et R3 élevés, R2, R4 et R5 modérés. |
| **Scénario opérationnel (SO)** | Description concrète des actions de l'attaquant, structurée en quatre phases : Connaître, Rentrer, Trouver, Exploiter. | Cinq SO (SO1 à SO5), un par scénario stratégique. |
| **Scénario stratégique (SS)** | Chemin d'attaque de haut niveau, de la source de risque à l'événement redouté, en passant ou non par une partie prenante. | Cinq SS (SS1 à SS5), cotés en gravité. |
| **Socle de sécurité** | État réel des mesures de sécurité en place, et écarts par rapport aux référentiels. | Treize écarts identifiés (GAP01 à GAP13), tous fondés sur des hypothèses ou des informations manquantes. |
| **Source de risque (SR)** | Acteur ou catégorie d'acteurs susceptible de porter atteinte aux valeurs métier. | Huit SR identifiées, trois retenues : SR1 (rançongiciel), SR2 (fraude), SR3 (menace interne). |
| **Valeur métier (VM)** | Processus ou information à laquelle l'organisation accorde de la valeur. | Cinq VM : VM1 (commandes), VM2 (fichier clients), VM3 (facturation), VM4 (comptabilité), VM5 (stocks). |
| **Vraisemblance (V)** | Probabilité qu'un scénario opérationnel aboutisse, en supposant que la source de risque passe à l'acte. Échelle à quatre niveaux : V1 à V4. | SO1, SO3, SO4, SO5 cotés V3 ; SO2 coté V2. |

### 2.2 Besoins de sécurité D-I-C-T

| Terme | Définition | Niveaux |
|---|---|---|
| **Disponibilité (D)** | Capacité du bien à être accessible quand on en a besoin. | D1 à D4. D3 : indisponibilité max d'une journée. |
| **Intégrité (I)** | Capacité du bien à ne pas être altéré de manière non détectée. | I1 à I4. I4 : intégrité garantie. |
| **Confidentialité (C)** | Capacité du bien à n'être accessible qu'aux personnes autorisées. | C1 à C4. C4 : accès interdit pour tous. |
| **Traçabilité (T)** | Capacité à retrouver l'historique des actions sur le bien. | T1 à T4. T4 : traçabilité légale ou réglementaire. |

---

## 3. Termes de cotation

### 3.1 Échelles du classeur

| Terme | Définition | Niveaux |
|---|---|---|
| **Dépendance** | Importance de la relation entre l'organisation et la partie prenante. | 1 (non nécessaire) à 4 (indispensable et unique). |
| **Pénétration** | Niveau d'accès de la partie prenante au système d'information. | 1 (accès utilisateur) à 4 (accès administrateur infrastructure). |
| **Maturité SSI** | Niveau de maîtrise de la sécurité par la partie prenante. | 1 (ponctuel) à 4 (proactif). |
| **Confiance** | Niveau de confiance dans les intentions de la partie prenante. | 1 (non évaluables) à 4 (pleinement compatibles). |
| **Motivation** | Intensité de l'intérêt d'une source de risque à atteindre son objectif. | + (faible), ++ (moyenne), +++ (forte). |
| **Ressources** | Moyens dont dispose une source de risque. | + (faibles), ++ (moyens), +++ (élevés). |
| **Pertinence** | Résultat du croisement motivation × ressources. | Faible, Moyenne, Élevée. |

### 3.2 Indice de menace des parties prenantes

| Terme | Formule / définition |
|---|---|
| **Exposition** | `Dépendance × Pénétration` |
| **Niveau SSI** | `Maturité × Confiance` |
| **Indice de menace** | `Exposition ÷ Niveau SSI` |
| **Zone danger** | Indice ≥ 3,00. Partie prenante critique, à traiter en priorité. |
| **Zone contrôle** | 0,90 ≤ indice < 3,00. Partie prenante à surveiller. |
| **Zone veille** | Indice < 0,90. Partie prenante à suivre périodiquement. |
| **Hors périmètre** | Partie prenante non retenue dans l'analyse. |

### 3.3 Niveaux de risque

| Terme | Définition | Valeur |
|---|---|---|
| **Élevé** | Risque inacceptable en l'état. | 4 |
| **Modéré** | Risque à traiter et à accepter explicitement. | 3 |
| **Significatif** | Risque tolérable sous surveillance. | 2 |
| **Faible** | Risque acceptable. | 1 |

> ⚠️ **Attention** : sur l'échelle du classeur, **« Significatif » (2) est plus bas que « Modéré » (3)**. Un risque qui passe de « Modéré » à « Significatif » s'améliore.

---

## 4. Termes du plan de traitement

### 4.1 Groupes de la défense en profondeur

| Terme | Définition | Actions dans l'étude |
|---|---|---|
| **Gouvernance** | Politiques, contrats, organisation, sensibilisation. | M01, M02, M03, M04, M05, M10. |
| **Protection** | Mesures préventives techniques : MFA, bastion, droits, correctifs. | M06, M07, M08, M09, M11, M18, M19. |
| **Défense** | Détection et réponse : EDR, supervision, alerte. | M12, M13, M14. |
| **Résilience** | Sauvegarde, continuité, transfert. | M15, M16, M17. |

### 4.2 Priorités

| Terme | Définition | Nombre |
|---|---|---|
| **P1** | Action urgente, à lancer immédiatement. | 9 actions. |
| **P2** | Action importante, à lancer dans l'année. | 7 actions. |
| **P3** | Action complémentaire, à étudier. | 3 actions. |

### 4.3 Autres termes du PTR

| Terme | Définition |
|---|---|
| **Plan de traitement du risque (PTR)** | Ensemble des mesures retenues pour réduire les risques identifiés. Dix-neuf actions, réparties en quatre groupes. |
| **Propriétaire** | Personne nommée responsable de la mise en œuvre d'une action du PTR. |
| **Indicateur de réalisation** | Mesure vérifiable permettant de savoir si une action a été réalisée. |
| **SMART** | Spécifique, Mesurable, Atteignable, Réalisable, Temporel. Critère de qualité d'une action du PTR. |
| **Risque résiduel** | Niveau de risque qui subsiste après mise en œuvre du PTR. |
| **Acceptation** | Décision de la direction de reconnaître un risque résiduel comme tolérable, sous conditions. |
| **Réduction** | Stratégie de traitement qui vise à diminuer la gravité ou la vraisemblance d'un risque. |
| **Transfert** | Stratégie de traitement qui vise à faire porter le risque financier par un tiers (cyber-assurance). |
| **Évitement** | Stratégie de traitement qui vise à supprimer l'activité à l'origine du risque. Non retenue dans l'étude, car la plateforme ERP/CRM est indispensable. |

---

## 5. Méthodes de cotation de la vraisemblance

| Terme | Définition |
|---|---|
| **Méthode expresse** | Cotation directe de chaque scénario, en s'appuyant sur les écarts du socle et le niveau de menace des parties prenantes. **Retenue dans l'étude.** |
| **Méthode standard** | Cotation action par action dans le graphe d'attaque, puis agrégation sur le chemin le plus probable. Non retenue : volume de données insuffisant. |
| **Méthode avancée** | Analyse probabiliste sur des données historiques ou des modèles quantifiés. Non retenue : pas de télémétrie disponible. |
| **Correction pour chaînes longues** | Diminution d'un niveau de vraisemblance pour les chaînes d'environ 10 étapes en série. Non appliquée : les scénarios comportent 4 étapes. |

---

## 6. Termes techniques et de sécurité

| Terme | Définition | Usage dans l'étude |
|---|---|---|
| **AD / LDAP** | Annuaire d'entreprise (Active Directory / Lightweight Directory Access Protocol). | Bien support transverse, cible des scénarios SS1 et SS3. |
| **Bastion d'administration** | Point d'accès unique et contrôlé pour les actions d'administration. | Mesure M07. |
| **CNIL** | Commission nationale de l'informatique et des libertés. | Autorité de contrôle RGPD, destinataire des notifications de violation. |
| **CRM** | Customer Relationship Management. Logiciel de gestion de la relation client. | Bien support de VM2. |
| **DPO** | Data Protection Officer (délégué à la protection des données). | Non désigné chez Rhénalis (hypothèse H16). |
| **EDR** | Endpoint Detection and Response. Solution de détection et réponse sur les postes et serveurs. | Mesure M12. |
| **ERP** | Enterprise Resource Planning. Logiciel de gestion intégré. | Bien support de VM1, VM3, VM4, VM5. |
| **IaaS** | Infrastructure as a Service. | Hébergeur des serveurs d'application. |
| **MFA** | Multi-Factor Authentication. Authentification multifacteur. | Mesure M06. |
| **PDP** | Plateforme de dématérialisation des factures. | Partie prenante PP7. |
| **PCA / PRA** | Plan de continuité d'activité / Plan de reprise d'activité. | Mesure M16. |
| **PSSI** | Politique de sécurité du système d'information. | Mesure M02. |
| **Ransomware / rançongiciel** | Logiciel malveillant qui chiffre les données et exige une rançon. | Menace principale, SR1. |
| **RGPD** | Règlement général sur la protection des données (UE 2016/679). | Référentiel réglementaire, GAP09. |
| **SecNumCloud** | Qualification ANSSI des fournisseurs cloud. | À vérifier pour l'hébergeur (H14). |
| **SIEM** | Security Information and Event Management. | Non déployé chez Rhénalis (hypothèse H11). |
| **SOC** | Security Operations Center. | Supervision externalisée envisagée (M13). |
| **SaaS** | Software as a Service. | Messagerie en ligne. |
| **VPN** | Virtual Private Network. | Liaisons site à site et nomades, accès d'administration de l'infogérant. |

---

## 7. Codes utilisés dans l'étude

| Préfixe | Signification | Nombre |
|---|---|:-:|
| **VM** | Valeur métier | 5 (VM1 à VM5) |
| **ER** | Événement redouté | 7 (ER1 à ER7) |
| **SR** | Source de risque | 8 (SR1 à SR8) |
| **OV** | Objectif visé | 8 (OV1 à OV8) |
| **PP** | Partie prenante | 9 (PP1 à PP9) |
| **SS** | Scénario stratégique | 5 (SS1 à SS5) |
| **SO** | Scénario opérationnel | 5 (SO1 à SO5) |
| **R** | Risque | 5 (R1 à R5) |
| **M** | Mesure du PTR | 19 (M01 à M19) |
| **GAP** | Écart de conformité | 13 (GAP01 à GAP13) |
| **ECO** | Mesure sur l'écosystème | 5 (ECO1 à ECO5) |
| **I** | Indicateur de suivi | 8 (I01 à I08) |
| **H** | Hypothèse | 23 (H01 à H23) |

---

## 8. Statuts des informations

| Statut | Signification | Convention |
|---|---|---|
| **`[F]`** | Fait établi. Information fournie par l'énoncé ou vérifiable. | Aucun `[F]` dans l'étude, hormis l'objet et les composants donnés par le sujet. |
| **`[D]`** | Déclaration. Information recueillie auprès d'un interlocuteur, non vérifiée. | Aucune `[D]` dans l'étude : le cas est fictif, aucune information n'a été recueillie. |
| **`[H]`** | Hypothèse. Information retenue par le groupe, à vérifier. | 21 hypothèses (H01 à H06, H08 à H13, H15 à H23). |
| **`[M]`** | Information manquante. Information non disponible, à obtenir. | 2 informations manquantes : H07 (test de restauration), H14 (qualification hébergeur). |

---

## 9. Correspondance avec le classeur

| Terme | Feuille(s) du classeur |
|---|---|
| Valeur métier, bien support | `Atelier 1 - Missions` |
| Événement redouté, gravité | `Atelier 1 - ER` |
| Socle de sécurité, écart | `Atelier 1 - GAP` |
| Source de risque, objectif visé | `Atelier 2 - SROV` |
| Partie prenante, indice de menace | `Atelier 3 - PP`, `Atelier 3 - Carto PP` |
| Scénario stratégique | `Atelier 3 - SS` |
| Scénario opérationnel, vraisemblance | `Atelier 4 - SO` |
| Risque, niveau | `Atelier 5 - Risques` |
| Mesure, propriétaire, priorité | `PTR` |
| Risque résiduel | `Risques résiduels` |
| Indicateur, cible | `Cadre de suivi` |
| Échelles, matrice | `Métriques` |

---

## 10. Checklist de validation

- [x] Les termes du **README** sont couverts : VM, BS, ER, SR, OV, PP, SS, SO, PTR.
- [x] Les termes des **échelles de cotation** sont définis : G, V, D-I-C-T, dépendance, pénétration, maturité, confiance, motivation, ressources, pertinence.
- [x] Les termes de l'**indice de menace** sont définis : exposition, niveau SSI, indice, zones.
- [x] Les termes du **PTR** sont définis : groupes, priorités, propriétaire, indicateur, SMART, risque résiduel, acceptation.
- [x] Les **méthodes de vraisemblance** sont définies : expresse, standard, avancée, correction pour chaînes longues.
- [x] Les **termes techniques** sont définis : AD/LDAP, bastion, EDR, ERP, CRM, MFA, PCA/PRA, PSSI, RGPD, SecNumCloud, SIEM, SOC, VPN.
- [x] Les **codes utilisés** dans l'étude sont listés avec leur nombre d'occurrences.
- [x] Les **statuts des informations** sont définis : `[F]`, `[D]`, `[H]`, `[M]`.
- [x] La **correspondance avec le classeur** est fournie.
- [x] Le glossaire est **cohérent avec les fiches d'atelier** et le dossier de synthèse.

---

## 11. Références

- ANSSI - *EBIOS Risk Manager*, guide méthodologique et fiches méthodes des ateliers 1 à 5 : `cyber.gouv.fr`.
- Classeur modèle `EBIOS_RM_Ateliers_modele.xlsx` - feuille `Métriques`.
- Dossier de synthèse - annexe A « Journal d'hypothèses » (pages 21-22).
- Fiche associée : [`references.md`](./references.md).
