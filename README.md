# 🎓 FSAC Student Card Generator

**FSAC Student Card Generator** est une application développée en **Python avec Streamlit** pour faciliter la génération et l’impression des cartes étudiantes de la **Faculté des Sciences Aïn Chock (FSAC) – Université Hassan II de Casablanca**.

L’objectif du projet est d’automatiser le processus de création des cartes étudiantes : recherche depuis **Apogée**, récupération des informations et de la photo, génération du **recto/verso** et impression de la carte.

---

## 🎯 Objectif du projet

L’application permet de centraliser les différentes étapes nécessaires à la création d’une carte étudiante dans une seule interface simple.

Elle génère les cartes au format standard **CR80 – 85,60 × 53,98 mm**, avec une résolution de **300 DPI**.

---

## ✨ Fonctionnalités principales

🔎 Recherche d’un étudiant par **Code Apogée ou CIN**.

🗄️ Connexion directe à **Apogée / Oracle**.

👤 Récupération automatique des informations de l’étudiant.

📸 Recherche automatique de la photo de l’étudiant.

✏️ Possibilité de modifier manuellement les informations avant impression.

🎨 Génération automatique du **recto et du verso** de la carte.

🎓 Intégration de l’identité visuelle et du logo FSAC.

📱 Génération d’un **QR Code fonctionnel** vers le site officiel de la FSAC.

▥ Intégration d’un code-barres graphique sur le recto.

👁️ Prévisualisation du recto et du verso avant impression.

💾 Téléchargement du recto et du verso au format PNG.

🖨️ Détection automatique des imprimantes sous Windows.

🔄 Impression **recto + verso dans un seul travail d’impression**.

✅ Vérification de l’état de l’imprimante et de la disponibilité du duplex.

---

## 🪪 Informations présentes sur la carte

Le **recto** de la carte contient les principales informations de l’étudiant :

👤 Nom et prénom  
🎓 Filière / Étape  
🔢 Numéro étudiant / Code Apogée  
🆔 CNE  
🪪 CIN  
📸 Photo de l’étudiant  
🏛️ Logo FSAC  
▥ Code-barres graphique  

Le **verso** contient notamment le logo de la FSAC ainsi qu’un **QR Code permettant d’accéder directement au site officiel de la faculté**.

---

## 🗄️ Connexion Apogée / Oracle

L’application peut communiquer avec la base **Apogée** à travers Oracle afin de récupérer automatiquement les informations nécessaires à la génération de la carte.

La recherche peut être effectuée à partir du :

🔹 **Code Apogée**  
🔹 **CIN**

La connexion utilise la bibliothèque **python-oracledb** avec **Oracle Thick Mode**.

🔐 Pour des raisons de sécurité, le nom d’utilisateur et le mot de passe Oracle ne sont pas enregistrés directement dans le code. Ils sont renseignés depuis l’interface Streamlit.

---

## 📸 Gestion des photos

L’application recherche automatiquement la photo correspondant à l’étudiant dans le dossier configuré.

Le prototype utilise notamment :

`C:\myimage`

Si aucune photo n’est trouvée automatiquement, l’utilisateur peut également importer une photo manuellement.

📁 Formats supportés : **PNG, JPG, JPEG, BMP et WEBP**.

---

## 📱 QR Code

Le verso de la carte intègre un **QR Code fonctionnel**.

📲 Une fois scanné, il permet d’accéder directement au site officiel de la **FSAC**.

Le QR Code est généré automatiquement par l’application avec la bibliothèque Python **QRCode**.

---

## 🖨️ Impression recto-verso

L’application détecte les imprimantes disponibles sous **Windows** à travers plusieurs mécanismes :

🖨️ pywin32 / EnumPrinters  
🪟 Imprimante Windows par défaut  
⚡ PowerShell Get-Printer  
💻 WMIC  
🛠️ Sélection manuelle en cas de besoin  

Le **recto et le verso sont envoyés dans un seul travail d’impression**.

### ⚠️ Important

Pour bénéficier d’une véritable impression recto-verso automatique, l’imprimante doit disposer d’un **module duplex** et son pilote Windows doit être correctement configuré pour l’impression double face.

L’application est notamment adaptée à l’utilisation d’une **imprimante Evolis compatible duplex**.

---

## 🛠️ Technologies utilisées

🐍 **Python** — langage principal  
🌐 **Streamlit** — interface utilisateur  
🖼️ **Pillow** — génération et traitement des cartes  
📱 **QRCode** — génération du QR Code  
🗄️ **python-oracledb** — connexion Apogée / Oracle  
🪟 **pywin32** — communication avec les imprimantes Windows  
🔌 **Oracle Instant Client** — connexion Oracle Thick Mode  
⚡ **PowerShell / WMIC** — détection complémentaire des imprimantes  

---

## 📦 Installation

Installer tout d’abord les principales dépendances :

`pip install streamlit pillow qrcode[pil] pywin32`

Pour utiliser la connexion **Apogée / Oracle** :

`pip install oracledb`

---

## ▶️ Lancement

Pour démarrer l’application :

`streamlit run fsac_carte_etudiant_apogee_thick.py`

🌐 L’interface Streamlit sera ensuite accessible depuis le navigateur.

---

## 🚀 Utilisation

1️⃣ Configurer la connexion **Oracle / Apogée**.

2️⃣ Sélectionner le dossier contenant les photos des étudiants.

3️⃣ Saisir le **Code Apogée ou le CIN**.

4️⃣ 🔎 Lancer la recherche.

5️⃣ Vérifier les informations et la photo récupérées.

6️⃣ ✏️ Corriger les informations si nécessaire.

7️⃣ 👁️ Prévisualiser le recto et le verso.

8️⃣ 🖨️ Sélectionner l’imprimante.

9️⃣ ✅ Vérifier que l’imprimante et le duplex sont disponibles.

🔟 Lancer l’impression **recto-verso**.

---

## 🔐 Sécurité et confidentialité

⚠️ Ce projet peut manipuler des **données personnelles et administratives d’étudiants**.

Les éléments suivants ne doivent jamais être publiés dans un dépôt GitHub public :

🔑 mots de passe Oracle ;  
👤 identifiants Apogée ;  
🌐 paramètres sensibles de l’infrastructure interne ;  
🪪 CIN, CNE et Codes Apogée réels ;  
📸 photos réelles des étudiants.

Pour une démonstration publique du projet, il est recommandé d’utiliser uniquement des **données fictives**.

---

## 🚀 Évolutions futures

📚 Génération de cartes par lot.

🖨️ Historique des impressions.

👥 Authentification et gestion des utilisateurs.

🔐 Gestion des rôles et permissions.

📊 Tableau de bord d’administration.

📱 QR Code individuel pour chaque étudiant.

🎓 Amélioration de l’intégration avec Apogée.

🖨️ Amélioration de la compatibilité avec les imprimantes Evolis.

📦 Création d’une version Windows directement exécutable.

---

## 👨‍💻 Auteur

**Developed by Abdel-Hakmi Reda**

🎓 Faculté des Sciences Aïn Chock — **FSAC**  
🏛️ Université Hassan II de Casablanca

---

## ⚠️ Avertissement

Ce projet est développé dans un **contexte académique et institutionnel**.

L’utilisation des données étudiantes, des accès Apogée, du logo FSAC et des ressources institutionnelles doit respecter les règles de **sécurité, de confidentialité et les autorisations de l’établissement**.
