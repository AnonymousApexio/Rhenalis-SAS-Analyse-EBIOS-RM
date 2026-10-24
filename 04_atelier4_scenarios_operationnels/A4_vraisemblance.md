# A4 - Cotation de la vraisemblance

> **Atelier 4 - Étape 4.2 : Cotation de la vraisemblance**  
> Feuille du classeur : `Atelier 4 - SO` (colonne B) + `Métriques` (échelles)  
> Dossier parent : [`README.md`](../README.md) · Fiche amont : [`A4_scenarios_operationnels.md`](./A4_scenarios_operationnels.md) · Fiche aval : [`05_atelier5_traitement/A5_synthese_risques.md`](../05_atelier5_traitement/A5_synthese_risques.md)

---

## 1. Identification

| Champ | Valeur |
|---|---|
| **Objet de l'étude** | Plateforme cloud hébergeant l'ERP et le CRM de Rhénalis SAS |
| **Atelier** | Atelier 4 - Scénarios opérationnels |
| **Étape** | 4.2 - Cotation de la vraisemblance des scénarios opérationnels |
| **Livrable** | Vraisemblance V1 à V4 pour chacun des cinq scénarios, avec méthode et justification |
| **Statuts** | `[F]` fait établi · `[H]` hypothèse · `[M]` information manquante |

> **Rappel méthodologique** - La **vraisemblance** exprime la probabilité qu'un scénario opérationnel aboutisse, **en supposant que la source de risque passe à l'acte**. Elle se cote sur une échelle à quatre niveaux (V1 à V4) et conditionne, avec la gravité, le niveau de risque de l'atelier 5. Trois méthodes sont possibles : **expresse**, **standard** et **avancée**.

---

## 2. Méthode retenue

### 2.1 Choix de la méthode

| Méthode | Principe | Adaptée à… | Retenue ? |
|---|---|---|:-:|
| **Expresse** | Cotation directe de chaque scénario, en s'appuyant sur les écarts du socle (atelier 1) et sur le niveau de menace des parties prenantes (atelier 3) | Un premier exercice, un périmètre restreint, des scénarios peu nombreux | ✅ **OUI** |
| **Standard** | Cotation **action par action** dans le graphe d'attaque, puis agrégation sur le chemin le plus probable | Des scénarios longs, des chaînes de plusieurs étapes, une analyse fine | ❌ Non |
| **Avancée** | Analyse probabiliste sur des données historiques ou des modèles de menace quantifiés | Des organisations disposant de données de télémétrie et de modèles de menace | ❌ Non |

**Justification du choix** : le TP est un **premier exercice**, avec cinq scénarios et une dizaine d'écarts de sécurité. La méthode **expresse** est celle que recommande le guide du TP pour ce type d'exercice. Elle est cohérente avec le volume de données disponibles, qui ne permettrait pas une cotation action par action faute d'historique et de télémétrie.

### 2.2 Principe de la méthode expresse

La vraisemblance est cotée **directement**, scénario par scénario, en s'appuyant sur :

1. les **écarts du socle de sécurité** (GAP de l'atelier 1), qui augmentent la facilité d'exploitation ;
2. le **niveau de menace des parties prenantes** (indice de l'atelier 3), qui augmente la probabilité d'un passage par un tiers ;
3. le **niveau de maturité** du tiers traversé, qui peut réduire la vraisemblance (cas de SO2).

> **Point clé** : la méthode demande de coter **en supposant que la source de risque passe à l'acte**. Ce n'est pas la probabilité qu'un attaquant existe qui est cotée, mais la probabilité qu'il **réussisse** s'il agit. C'est pourquoi un scénario de menace interne (SO5) est coté V3 : une fois décidé, le commercial réussit presque à coup sûr.

### 2.3 Correction pour les chaînes longues

Le guide rappelle qu'une **chaîne d'attaque d'environ 10 étapes en série** doit voir sa vraisemblance **diminuée d'un niveau**, car la multiplication des étapes réduit la probabilité de succès.

**Application dans cette étude** : les cinq scénarios comportent **une action par phase**, soit **quatre étapes** au total. Aucune chaîne n'atteint le seuil d'environ 10 étapes. **Aucune correction n'est donc appliquée.** Ce point est consigné dans le journal de bord.

---

## 3. Échelle de vraisemblance (rappel - feuille `Métriques`)

| Niveau | Définition |
|:-:|---|
| **V1** | La source de risque a **très peu de chance** d'atteindre son objectif visé en empruntant un des modes opératoires |
| **V2** | La source de risque est **susceptible** d'atteindre son objectif visé en empruntant un des modes opératoires |
| **V3** | La source de risque va **probablement** atteindre son objectif visé en empruntant un des modes opératoires |
| **V4** | La source de risque va **certainement** atteindre son objectif visé en empruntant un des modes opératoires |

---

## 4. Tableau de cotation

| Code | Scénario | Vraisemblance | Facteurs favorisants | Facteurs limitants |
|:-:|---|:-:|---|---|
| **SO1** | Rançongiciel via l'infogérant | **V3** - Très vraisemblable | GAP01 (pas de MFA), GAP02 (compte partagé), GAP05 (pas de supervision), GAP11 (contrat sans clause de sécurité) ; InfoGest en **zone danger** (indice 4,00) ; accès permanent de l'infogérant | Confiance limitée dans l'infogérant (confiance 2) ; vérification de la qualification de l'hébergeur (M04) en cours |
| **SO2** | Rançongiciel via l'éditeur de l'ERP | **V2** - Vraisemblable | GAP03 (sauvegardes non testées), GAP05 (pas de supervision), GAP07 (pas de PCA/PRA) ; H17 (télémaintenance ouverte sans validation) | **Éditeur plus mature** (maturité 3 contre 2 pour l'infogérant) ; accès **à la demande** (H17) et non permanent ; éditeur en **zone contrôle** (indice 1,33) |
| **SO3** | Rançongiciel via hameçonnage d'un salarié | **V3** - Très vraisemblable | GAP01 (pas de MFA), GAP03 (sauvegardes non testées), GAP04 (pas d'EDR), GAP05 (pas de supervision), GAP06 (correctifs non vérifiés), GAP07 (pas de PCA/PRA) ; **~75 utilisateurs exposés** | Sensibilisation des salariés (M05, à déployer) ; EDR (M12, à déployer) |
| **SO4** | Fraude au RIB | **V3** - Très vraisemblable | GAP01 (pas de MFA sur la messagerie), GAP13 (aucune vérification des RIB, clients jamais informés) ; **hameçonnage réussi en 2025** (H15) | Courrier aux grands comptes (M10, à déployer) ; double validation des RIB (M18, à déployer) |
| **SO5** | Export du fichier clients par un commercial | **V3** - Très vraisemblable | GAP08 (droits d'export trop larges, exports et USB non contrôlés) | Restrictions des exports (M09) et alerte automatique (M14), à déployer |

> Les **facteurs limitants** sont des mesures **à déployer** : ils ne réduisent pas encore la vraisemblance initiale, mais la réduiront après mise en œuvre du PTR (cf. risques résiduels).

---

## 5. Justification détaillée

### 5.1 SO1 - V3

**Pourquoi V3 et non V2** : le scénario passe par un tiers en **zone danger** (InfoGest, indice 4,00). Cet indice traduit une relation indispensable et non substituable, des droits d'administration sur l'annuaire, les serveurs et les sauvegardes, une sécurité réactive et un contrat sans clause de sécurité. **Quatre écarts** du socle favorisent directement le scénario : pas de MFA (GAP01), compte partagé (GAP02), pas de supervision (GAP05), contrat sans clause (GAP11). Un attaquant qui compromet l'infogérant accède à la plateforme **sans rencontrer de barrière technique**.

**Pourquoi V3 et non V4** : les écarts sont des **hypothèses** `[H]`, non des faits établis. La cotation est donc **provisoire** : si les hypothèses sont confirmées, elle pourrait passer à V4 ; si elles sont infirmées (par exemple si l'infogérant a déployé la MFA depuis), elle pourrait redescendre à V2. Ce point doit être signalé en soutenance.

### 5.2 SO2 - V2

**Pourquoi V2 et non V3** : comme SO1, SO2 passe par un tiers, mais un tiers **mieux protégé** : l'éditeur a une **maturité de 3** (contre 2 pour l'infogérant) et n'accède au serveur **qu'à la demande** (H17), alors que l'infogérant dispose d'un **accès permanent**, sans MFA et avec un compte partagé (GAP01, GAP02). L'éditeur est en **zone contrôle** (indice 1,33) et non en zone danger. Le facteur limitant est donc structurel : l'attaquant doit d'abord compromettre un tiers plus mature, puis attendre l'ouverture de la télémaintenance.

**Pourquoi V2 et non V1** : les écarts GAP03 (sauvegardes non testées), GAP05 (pas de supervision) et GAP07 (pas de PCA/PRA) restent présents. Si l'éditeur est compromis, l'attaquant obtient un accès administrateur au serveur d'application, et la restauration est longue faute de test documenté.

### 5.3 SO3 - V3

**Pourquoi V3** : environ **75 utilisateurs** sont exposés (postes de l'ADV, portables des commerciaux, postes de la comptabilité). L'antivirus est seul, sans EDR (GAP04), la supervision est absente (GAP05), les sauvegardes ne sont pas copiées hors ligne (GAP03) et les correctifs ne sont pas vérifiés (GAP06). Un seul clic suffit : la barrière technique est faible, et l'élévation de privilèges jusqu'à administrateur du domaine est facilitée par l'absence de durcissement de l'annuaire.

**Pourquoi V3 et non V4** : la sensibilisation des salariés (M05) n'est **pas encore déployée**, mais une partie des utilisateurs peut adopter des réflexes ; l'EDR (M12) est absent. Comme pour SO1, la cotation est **provisoire** et dépend de la vérification des hypothèses H09, H10, H11.

### 5.4 SO4 - V3

**Pourquoi V3** : la messagerie est **sans MFA** (GAP01), les changements de RIB ne sont **pas vérifiés** (GAP13) et les clients ne sont **pas informés** du risque de fraude. Un **hameçonnage a déjà réussi en 2025** (H15), ce qui démontre que le vecteur est opérationnel. La fraude au RIB est peu coûteuse pour l'attaquant : quelques courriels suffisent.

**Pourquoi V3 et non V4** : le courrier aux grands comptes (M10) et la double validation des RIB (M18) sont **à déployer**, mais leur absence n'empêche pas la fraude ; en revanche, la vigilance naturelle de certains clients peut réduire la probabilité de paiement. La cotation reste V3, mais elle pourrait redescendre à V2 après déploiement de M10 et M18.

### 5.5 SO5 - V3

**Pourquoi V3** : le scénario ne nécessite **aucune effraction**. Le commercial utilise ses **droits légitimes** sur le CRM, avec des droits d'export trop larges (GAP08) et aucun contrôle des exports ni des supports USB. Une fois décidé, il réussit **presque à coup sûr**.

**Pourquoi V3 et non V4** : comme le veut la méthode, la cotation se fait **en supposant que la source de risque passe à l'acte**. Le commercial peut être dissuadé par la clause de confidentialité de son contrat, par le blocage des USB (M09, à déployer) ou par l'alerte sur les exports volumineux (M14, à déployer). Ces facteurs limitants justifient de ne pas coter V4, mais ils ne suffisent pas à faire descendre à V2 sans les mesures effectives.

---

## 6. Cohérence avec les autres ateliers

### 6.1 Cohérence avec les GAP de l'atelier 1

| GAP | SO concerné | Effet sur la vraisemblance |
|---|:-:|---|
| **GAP01** - pas de MFA | SO1, SO3, SO4 | Favorise la compromission initiale et la fraude |
| **GAP02** - compte admin partagé | SO1 | Favorise le mouvement latéral |
| **GAP03** - sauvegardes non testées | SO1, SO2, SO3 | Favorise l'atteinte de l'objectif (pas de restauration) |
| **GAP04** - pas d'EDR | SO3 | Favorise la prise de contrôle d'un poste |
| **GAP05** - pas de supervision | SO1, SO2, SO3 | Favorise l'impunité de l'attaquant |
| **GAP06** - correctifs non vérifiés | SO3 | Favorise l'exploitation d'une vulnérabilité |
| **GAP07** - pas de PCA/PRA | SO2, SO3 | Allonge la durée d'indisponibilité |
| **GAP08** - droits CRM trop larges | SO5 | Favorise l'export massif |
| **GAP11** - contrat sans clause | SO1 | Empêche d'imposer des mesures à l'infogérant |
| **GAP13** - pas de vérification des RIB | SO4 | Favorise la fraude |

### 6.2 Cohérence avec les parties prenantes de l'atelier 3

| Partie prenante | Zone | Indice | Scénario concerné | Effet sur la vraisemblance |
|---|:-:|:-:|:-:|---|
| **InfoGest Services** | Danger | 4,00 | SO1 | **Favorise** : tiers critique, sécurité réactive, contrat sans clause |
| **Éditeur de l'ERP** | Contrôle | 1,33 | SO2 | **Limite** : tiers plus mature, accès à la demande |
| **Hébergeur IaaS** | Contrôle | 1,78 | SO1 | **Favorise** : contrôle hyperviseur et stockage, qualification inconnue |
| **Grands comptes** | Veille | 0,50 | SO4 | **Victimes** : la mesure porte sur la confiance (M10) |

> La distinction SO1 (V3) / SO2 (V2) est **directement lisible** dans la cartographie : l'infogérant est en zone danger, l'éditeur en zone contrôle. C'est le principal facteur d'écart entre les deux scénarios.

### 6.3 Cohérence avec les risques de l'atelier 5

| Risque | Scénario | Gravité | Vraisemblance | Niveau initial |
|:-:|:-:|:-:|:-:|:-:|
| **R1** | SO1 | G4 | V3 | 🔴 Élevé |
| **R2** | SO2 | G3 | V2 | 🟡 Modéré |
| **R3** | SO3 | G4 | V3 | 🔴 Élevé |
| **R4** | SO4 | G3 | V3 | 🟡 Modéré |
| **R5** | SO5 | G3 | V3 | 🟡 Modéré |

> La matrice gravité × vraisemblance (feuille `Métriques`) donne le niveau de risque. R1 et R3 sont **élevés** ; R2, R4 et R5 sont **modérés**.

---

## 7. Limites et points de vigilance

### 7.1 Limites de la méthode expresse

- **Cotation globale par scénario** : elle ne permet pas de distinguer les étapes les plus critiques du graphe d'attaque. Une cotation **action par action** (méthode standard) donnerait un résultat plus fin, en particulier pour SO1 et SO3, qui comportent plusieurs étapes à risque.
- **Dépendance aux hypothèses** : les cotations reposent sur des écarts `[H]` non vérifiés. Si l'infogérant a déployé la MFA depuis, SO1 redescend à V2 ; si les sauvegardes sont en réalité immuables et testées, SO1 et SO3 redescendent à V2.
- **Pas de données historiques** : aucun incident n'est documenté pour Rhénalis. Seul H15 (hameçonnage réussi en 2025) apporte un élément factuel.

### 7.2 Points à vérifier avant toute conclusion ferme

| Hypothèse | Statut | Effet si infirmée |
|---|:-:|---|
| **H04** - pas de MFA | `[H]` | Si MFA déployée, SO1 et SO4 redescendent |
| **H07** - pas de test de restauration | `[M]` | Si test documenté, SO1 et SO3 redescendent |
| **H08** - sauvegardes sur la même infrastructure | `[H]` | Si copie hors ligne, SO1 et SO3 redescendent |
| **H09** - pas d'EDR | `[H]` | Si EDR déployé, SO3 redescend |
| **H11** - pas de supervision | `[H]` | Si SOC, SO1, SO2, SO3 redescendent |
| **H14** - qualification de l'hébergeur | `[M]` | Si non qualifié, SO1 reste V3 ; si qualifié, SO1 pourrait redescendre |
| **H19, H21** - droits CRM trop larges, USB non contrôlés | `[H]` | Si restrictions déployées, SO5 redescend |

> **Formule utile en soutenance** : « Faute d'information sur X, nous avons retenu l'hypothèse Y ; si elle se révèle fausse, la cotation du risque Rn passerait de A à B. »

### 7.3 Pas de correction pour chaînes longues

Les scénarios comportent **4 étapes** chacun, bien en dessous du seuil d'environ 10 étapes qui déclencherait une correction. **Aucune correction n'est appliquée.** Ce point est documenté dans le journal de bord.

---

## 8. Correspondance avec le classeur EBIOS RM

| Élément de cette fiche | Feuille du classeur | Colonnes |
|---|---|---|
| Codes SO1 à SO5 | `Atelier 4 - SO` | Colonne A |
| Vraisemblance globale | `Atelier 4 - SO` | Colonne B |
| Justification | `Atelier 4 - SO` | Colonne B (texte) |
| Échelle de vraisemblance | `Métriques` | Bloc « Vraisemblance » |
| Niveau de risque | `Métriques` | Bloc « Niveau de risque » |
| Risques finaux | `Atelier 5 - Risques` | Colonnes A à L |

---

## 9. Checklist de validation

- [x] La **méthode retenue** est explicitée : méthode **expresse**.
- [x] La **justification du choix** est argumentée (premier exercice, pas de données historiques).
- [x] Le **principe de cotation** est rappelé : cotation **en supposant que la source de risque passe à l'acte**.
- [x] La **correction pour chaînes longues** est traitée : aucune chaîne n'atteint le seuil, aucune correction appliquée.
- [x] Les **cinq scénarios** sont cotés : SO1 V3, SO2 V2, SO3 V3, SO4 V3, SO5 V3.
- [x] Chaque cotation est **justifiée** par les GAP, le niveau de menace des PP et les facteurs limitants.
- [x] Les **facteurs limitants** sont distingués des facteurs favorisants, et identifiés comme mesures **à déployer**.
- [x] La distinction **SO1 V3 / SO2 V2** est expliquée par la différence de maturité et d'accès entre l'infogérant et l'éditeur.
- [x] Le rôle des **grands comptes comme victimes** dans SO4 est rappelé.
- [x] La **cohérence** avec les ateliers 1, 3 et 5 est vérifiée.
- [x] Les **limites** de la méthode et les **hypothèses à vérifier** sont documentées.
- [x] Les cotations sont **cohérentes avec la feuille `Atelier 4 - SO`** du classeur.
- [x] Les niveaux de risque (élevé/modéré) sont **cohérents avec la matrice** de la feuille `Métriques`.

---

## 10. Références

- ANSSI - *EBIOS Risk Manager*, fiche méthode « Évaluer la vraisemblance des scénarios opérationnels » (atelier 4).
- Classeur modèle `EBIOS_RM_Ateliers_modele.xlsx` - feuilles `Atelier 4 - SO`, `Métriques`.
- Dossier de synthèse - § 6.3 « Cotation de la vraisemblance » (page 15).
- MITRE ATT&CK - cadre de référence pour les techniques d'attaque : `attack.mitre.org`.
- Fiche amont : [`A4_scenarios_operationnels.md`](./A4_scenarios_operationnels.md).
- Fiche aval : [`05_atelier5_traitement/A5_synthese_risques.md`](../05_atelier5_traitement/A5_synthese_risques.md).