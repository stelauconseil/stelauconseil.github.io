---
title: idFod
subtitle: Développement d'une solution de signature électronique permettant l'accès aux empreintes digitales contenues dans les passeports électroniques et les CNIe
image: assets/img/portfolio/idfod-thumbnail.png
alt:

caption:
  title: idFod
  subtitle: Développement d'une solution de signature électronique permettant l'accès aux empreintes digitales contenues dans les passeports électroniques et les CNIe
  thumbnail: assets/img/portfolio/idfod-thumbnail.png
---

## 1. Présentation du projet et des enjeux

Le client, Eviden et l'**Agence Nationale des Titres Sécurisés (ANTS)**, ont fait appel à notre expertise pour développer une solution innovante permettant de :

- **Signer le challenge d'accès** envoyé par un titre de voyage (asseport électronique, carte d'identité et titre de séjour) pour autoriser l’accès au **Data Group 3 (DG3)**, qui contient les images des empreintes digitales.
- **Exposer des webservices SOAP** facilitant :
  - La récupération de la chaîne des certificats de confiance.
  - La signature du challenge envoyé par le titre de voyage.
- Fournir une **interface utilisateur moderne** pour la gestion et l’administration.
- **S’interfacer avec les PKI** capables d’émettre des certificats électroniques au format **Card Verifiable Certificate (CVC)** et des **HSM** garantissant la génération sécurisée de bi-clés et la signature des challenges.

---

## 2. Défis techniques et réglementaires

### a) Techniques

- Garantir la compatibilité des webservices avec les dispositifs de remise déjà déployés en mairie, prefecture, consulats et les dispositifs de contrôle en zone aéroportuaire pour gérer la chaîne des certificats et le processus de signature.
- Garantir la **compatibilité avec les PKI** et les spécifications CVC, essentielles pour les passeports électroniques et les titres de voyage.
- Assurer une interopérabilité avec des **HSM certifiés** pour la gestion des clés cryptographiques.
- Mettre en place une interface utilisateur intuitive et performante pour les administrateurs.

### b) Réglementaires

- Respecter les exigences des standards internationaux tels que [ICAO 9303](https://www.icao.int/publications/pages/publication.aspx?docnum=9303) et [TR-03110](https://www.bsi.bund.de/EN/Themen/Unternehmen-und-Organisationen/Standards-und-Zertifizierung/Technische-Richtlinien/TR-nach-Thema-sortiert/tr03110/TR-03110_node.html) pour les titres de voyage.
- Aligner la solution sur les cadres réglementaires européens et nationaux, notamment **eIDAS** et **RGS**.

---

## 3. Solution mise en œuvre

### a) Architecture technique

1. **Exposition de webservices SOAP sécurisés** :

   - Développement de services permettant de :
     - **Récupérer la chaîne des certificats de confiance** nécessaires pour valider les échanges.
     - **Demander la signature du challenge** transmis par le passeport électronique.
   - Mise en œuvre de mécanismes de chiffrement avancés pour sécuriser les communications (TLS 1.3).

2. **Intégration avec des PKI et HSM** :

   - Connexion aux **PKI** pour l’émission de certificats au format CVC, utilisés dans les tites de voyage.
   - Utilisation d’**HSM certifiés** pour :
     - Générer des paires de clés asymétriques.
     - Réaliser les signatures des challenges.

3. **Interface utilisateur moderne pour l’administration** :
   - Développement d’une interface intuitive et ergonomique pour :
     - Gérer les certificats et les clés cryptographiques.
     - Suivre les logs et surveiller l’état des services.
   - Conception en utilisant le framework React pour garantir performance et accessibilité.

---

## 4. Résultats obtenus

- Déploiement d’une solution complète permettant :
  - Une gestion sécurisée et conforme des challenges d’accès au DG3 des titres de voyage.
  - Une intégration fluide avec les infrastructures de confiance (PKI et HSM).
- **Conformité totale avec les standards ICAO, eIDAS et RGS**.
- Adoption par l’ANTS grâce à des performances largement améliorées et une interface utilisateur moderne et intuitive

---

En collaborant avec l’ANTS, nous avons mis en œuvre une solution pionnière, sécurisée et évolutive, qui répond parfaitement aux enjeux réglementaires et techniques des passeports électroniques et des cartes d'identité électronique.

{:.list-inline}

- Date: Septembre 2024
- Client: Eviden
- Categorie: Développement sécurisé
