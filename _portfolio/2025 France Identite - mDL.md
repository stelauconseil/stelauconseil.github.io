---
title: ISO 18013-5 mDL mDoc SDK
subtitle: SDK Android de lecteur de proximité ISO 18013-5 (BLE) et vérifieur en mode web
image: assets/img/portfolio/verify-with-stelau.jpg
alt: SDK Android lecteur ISO 18013-5 BLE et vérifieur web mDL/mDoc

caption:
  title: France Identité
  subtitle: Développement d'un SDK Android de lecteur ISO 18013-5 (BLE) et d'un vérifieur en mode web
  thumbnail: assets/img/portfolio/verify-with-stelau-thumbnail.jpg
---

## 1. Présentation du projet et des enjeux

Dans le cadre de France Identité, nous avons conçu et réalisé deux composants complémentaires autour de l’écosystème mDL/mDoc (ISO/IEC 18013-5) :

- Un **SDK Android de lecteur de proximité** implémentant la norme **ISO/IEC 18013-5** sur le transport **Bluetooth Low Energy (BLE)** pour l’obtention de Digital Credentials depuis un portefeuille mDL/mDoc.
- Un **vérifieur en mode web** permettant d’effectuer la vérification et la divulgation sélective des attributs depuis un navigateur moderne.

### Objectifs principaux

- Offrir un **SDK simple à intégrer** pour réaliser l’engagement de périphérique, établir la session sécurisée et **récupérer les attributs mDL/mDoc** en proximité via BLE.
- Assurer la **divulgation sélective** et le contrôle des autorisations de lecture conformément à la norme.
- Proposer un **vérifieur web** prêt à l’emploi pour des scénarios de contrôle sur poste fixe ou mobile, sans installation native.

---

## 2. Défis techniques et réglementaires

### a) Techniques

- Implémentation complète du **Device Engagement** et de la session **BLE** (découverte, appairage applicatif, négociation des paramètres, reprise/réessai).
- Mise en œuvre des briques **CBOR/COSE**, **ECDH** et chiffrement de session conformément à ISO/IEC 18013-5.
- Gestion des **Reader Auth Keys** et de la chaîne d’autorisation lecteur pour l’accès à certains attributs (lecture conditionnelle).
- Conception d’API Android **stables et idiomatiques** (Kotlin/Java), gestion de cycle de vie, cancellation, timeouts et résilience radio.
- Pour le **vérifieur web** : utilisation des capacités navigateur (ex. Web Bluetooth lorsque disponible) et mise en place de mécanismes de **handover** et de consentement adaptés à l’UX.

### b) Réglementaires et interopérabilité

- Respect des principes de **minimisation** et **confidentialité** par conception : clés éphémères, non‑traçabilité, divulgation sélective.
- Alignement avec l’écosystème mDL/mDoc et préparation à l’**interopérabilité** (tests croisés, jeux de données de référence, scénarios offline/online).

---

## 3. Solution mise en œuvre

### a) SDK Android lecteur ISO/IEC 18013-5 (BLE)

Fonctionnalités clés :

- APIs haut niveau pour initialiser une **session de proximité BLE**, demander un **ensemble d’attributs** (namespaces mDL/mDoc) et récupérer la réponse signée.
- Support de la **divulgation sélective** et des **autorisations lecteur** (présentation de certificats lecteur lorsque requis).
- Gestion des erreurs et de la **qualité radio** : timeouts, backoff, reconnexions, métriques.
- Observabilité (journaux d’audit applicatifs), hooks d’UI pour le **consentement utilisateur** et la gestion des refus.

### b) Vérifieur en mode web

- Application web (PWA) offrant un **flux de vérification** depuis le navigateur : sélection des attributs requis, consentement, puis récupération des **Digital Credentials** depuis le portefeuille en proximité.
- Utilisation des capacités **Web Bluetooth** lorsque supportées par le navigateur/appareil, avec fallback de handover selon le contexte d’exploitation.
- Interface opérateur simple : profils de vérification réutilisables, export de preuves, journaux d’usage.

<p align="center">
  <a class="btn btn-primary btn-xl" href="https://mdoc-web-verifier.stelau.com/" target="_blank" rel="noopener noreferrer">
    Essayer le vérifieur web
  </a>
  <span class="text-muted" style="display:block;margin-top:8px;font-size:9px">
    Ouvre une nouvelle fenêtre – compatible navigateurs supportant Web Bluetooth
  </span>
</p>

### c) Sécurité et performance

- Chiffrement bout‑en‑bout de la session, **clés éphémères** et messages signés (COSE) conformément à la norme.
- **Minimisation des données** échangées et protection contre la corrélation.
- Optimisations côté BLE et sérialisation CBOR pour réduire la **latence de lecture** en conditions réelles.

---

## 4. Résultats obtenus

- Un **SDK Android prêt à l’intégration**, documenté, avec exemples et scénarios de test représentatifs.
- Un **vérifieur web opérationnel**, adapté aux démos, pilotes et déploiements contrôlés sur postes compatibles.
- Validation d’**interopérabilité** sur des jeux de données mDL/mDoc courants et robustesse mesurée sur des environnements radio variés.

---

## 5. Perspectives et évolutions

- Extension multi‑transports (ex. Wi‑Fi Aware) et portage iOS côté lecteur.
- Enrichissement des profils de vérification et intégration dans des parcours **EUDI**.
- Durcissement continu (tests de non‑régression, fuzzing CBOR/COSE) et amélioration de la **télémétrie**.

{:.list-inline}

- Date: 2025
- Client: Agence France Titres
- Categorie: Développement SDK et vérifieur mDL/mDoc
