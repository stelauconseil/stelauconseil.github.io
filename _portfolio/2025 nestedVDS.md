---
title: Nested Visible Digital Seal (VDS) — TR‑23111
subtitle: Spécification inventée par Stelau pour l’attestation optique et la proximité mDL
image: assets/img/portfolio/france-identite-sncf-full.jpg
alt: Nested Visible Digital Seal TR‑23111

caption:
  title: France Identité
  subtitle: Invention et rédaction de la spécification TR‑23111 « Nested VDS »
  thumbnail: assets/img/portfolio/france-identite-sncf-thumbnail.jpg
---

## 1. Présentation du projet et des enjeux

Nous avons inventé et rédigé la spécification **TR‑23111 « Nested Visible Digital Seal (VDS) »**. Elle définit un mécanisme, au‑dessus d’**ISO 22376**, qui permet de présenter des **preuves optiques** compactes et vérifiables, et de les **imbriquer** pour renforcer la sécurité, la confidentialité et l’anti‑corrélation.

Principe clé :

- Un **Inner VDS** contient les données d’identité et la **clé publique de l’appareil** utilisateur, signé par l’Autorité Émettrice.
- Un **Outer VDS** encapsule l’Inner VDS (potentiellement **chiffré pour un ou plusieurs destinataires**) et est **signé par l’appareil** de l’utilisateur.

Enjeux adressés :

- Preuve **authentique et intégrité** via deux niveaux de signature (Autorité Émettrice et appareil).
- **Confidentialité** par chiffrement sélectif de l’Inner VDS pour des destinataires autorisés.
- **Interopérabilité** optique (QR/Datamatrix) et **proximité** via une extension **mDL ISO/IEC 18013‑5**.

---

## 2. Défis techniques et réglementaires

### a) Techniques

- Contrainte **taille/lecture optique** : encodage optimisé (ex. **Base45**), typage compact, timestamps.
- **Chiffrement par destinataire** de l’Inner VDS : génération d’une clé secrète K, **ECDHE éphémère** par destinataire pour chiffrer K.
- **Double signature** : ECDSA côté Autorité (Inner VDS), signature par l’appareil (Outer VDS).
- Indications d’implémentation : sérialisation binaire, gestion des **clés éphémères**, robustesse à l’imagerie QR et aux environnements contraints.

### b) Réglementaires

- Alignement sur **ISO 22376** (VDS) pour l’émission et la vérification optique.
- Extension **mDL (ISO/IEC 18013‑5)** : transport de l’artefact en proximité au sein du Device Engagement.
- Conception **privacy‑by‑design** : minimisation, non‑traçabilité, fenêtres temporelles courtes.

---

## 3. Approche et solution mise en œuvre

### a) Architecture imbriquée (Nested VDS)

- **Inner VDS**

  - Données d’identité (PID), **clé publique de l’appareil**.
  - Signature **Autorité Émettrice** (ECDSA).
  - En‑tête : la référence de certificat peut être positionnée à `000000000` pour indiquer que la **signature de l’Outer** provient de l’appareil, tandis que la **clé publique** de l’appareil est portée dans l’Inner VDS.

- **Outer VDS**
  - Contient l’**Inner VDS** (clair ou **chiffré**).
  - Porte la **clé publique éphémère** `ephPubKey` et, pour chaque destinataire, le **secret K chiffré**.
  - **Signature de l’appareil** assurant l’authenticité au moment de la présentation.

### b) Émission et présentation

1. **Émission** : l’appareil génère sa **paire de clés**, transmet sa **clé publique** à l’Autorité Émettrice qui produit et signe l’**Inner VDS**.
2. **Présentation** : l’appareil construit l’**Outer VDS**, optionnellement **chiffre** l’Inner pour les destinataires, puis **signe** l’Outer et **l’affiche** (optique) ou le transmet en **proximité**.

### c) Représentation

- **QR/Datamatrix** : encodage recommandé **Base45** pour compatibilité.
- **Extension mDL (ISO/IEC 18013‑5)** : insertion en **Device Engagement**, binaire, avec clé **−7** pour rester ignoré par les lecteurs legacy non compatibles.

---

## 4. Résultats obtenus

- Rédaction de la spécification **TR‑23111 v1.0 (05/01/2025)**.
- **Exemples de référence** fournis : manifestes Inner/Outer, trames hex, structures décodées.
- Gains **privacy** (anti‑corrélation par clés éphémères) et **interop** (optique + mDL proximité).
- Base solide pour **pilotes** et **démonstrateurs** autour de l’identité vérifiable.

---

## 5. Perspectives et évolutions

- Approfondissement des **profils d’usage** (présentation offline/online, parcours contrôle).
- Alignement avec **EUDI** et écosystèmes de wallets (interop de présentations).
- Optimisations **codage/lecture** et jeux de tests d’**interopérabilité** multi‑constructeurs.

{:.list-inline}

- Date: 2025
- Client: France Identité / Agence France Titres
- Categorie: Spécification technique & R&D
