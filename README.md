# LAB-6-Analyse-statique-d-un-APK-avec-MobSF-dans-la-VM-Mobexler

# Task 1 — Préparation de l'environnement d'analyse

1. En premier, on va démarrer la VM Mobexler sur VMWare, et se connecter:

<img width="1920" height="932" alt="image" src="https://github.com/user-attachments/assets/9594648c-d2f6-4c9f-b52b-9c5f96595758" />

2. Ensuite, dans le terminale on va créer un dossier de travail dédié à cette analyse:

<img width="732" height="173" alt="image" src="https://github.com/user-attachments/assets/8b8c23e2-cb0b-49aa-a0f9-3a8d3c061ce2" />

3. Copier l'APK (DivaApplication.apk) à analyser dans ce dossier de travail:

  Étape 1 — Activer le dossier partagé dans VMware
  
  1. Éteins la VM 
  
  2. Clique droit sur la VM → Settings
  
  3. Va dans Options → Shared Folders
  
  4. Sélectionne Always enabled
  
  5. Clique sur Add → navigue vers le dossier de ton PC contenant l'APK
  
  6. Donne-lui un nom simple (diva-apk-file)
  
  7. Clique OK → Save

<img width="882" height="632" alt="image" src="https://github.com/user-attachments/assets/589fef4d-7a43-4e24-a4fc-f3b4f460bed4" />


  Étape 2 — Redémarre et accède au dossier dans la VM
  
  1. Démarre la VM, ouvre un terminal et vérifie que le dossier est bien monté avec la commande : ls /mnt/hgfs/
  
  On devrait voir le dossier partagé (diva-apk-file)
  
  Étape 3 — Copier l'APK dans ton dossier de travail

<img width="851" height="217" alt="image" src="https://github.com/user-attachments/assets/70aad6d9-65c2-45c1-97cb-3948339b1141" />

4. Vérification de l'intégrité de l'APK :

En premier, on va calculer et noter le hash SHA-256 de l'APK, puis noter la taille du fichier :
 
<img width="851" height="187" alt="image" src="https://github.com/user-attachments/assets/b0cfb99d-9c38-4a53-99d8-da8a2bf3be36" />

5. Documentation de l'environnement d'analyse par la création d'un fichier de traçabilité :

<img width="922" height="401" alt="image" src="https://github.com/user-attachments/assets/bc597cd8-53ab-4741-bfa8-179fb4e8b550" />

# Task 2 — Lancement de MobSF
 
Étape 1: Lancement de MobSF depuis le menu d'applications:

Version de MobSF: v4.0.6

<img width="1597" height="862" alt="image" src="https://github.com/user-attachments/assets/51758da0-da9a-4047-ae74-fff41f0a23a4" />

Étape 2: On va vérifier que l'interface web est accessible, en accédant à l'URL : http://127.0.0.1:8000 via le navigateur Firefox:

<img width="1917" height="827" alt="image" src="https://github.com/user-attachments/assets/42c3eaa7-a465-410c-83f7-dbf0db4a58ed" />

La page d'accueil MobSF s'affiche correctement:

<img width="1917" height="867" alt="image" src="https://github.com/user-attachments/assets/b39d04f5-ab2a-4d57-8037-20e2d9bd0c8d" />

Puis, on va noter la version de MobSF affichée en bas de page dans le fichier de traçabilité, par la commande suivante :

echo "MobSF version : 4.06 " >> ~/apk_analysis/$(date +%Y-%m-%d)/analyse_info.txt

<img width="1042" height="227" alt="image" src="https://github.com/user-attachments/assets/a6e9dd97-b115-40b2-983a-d35e24cb9243" />

# Task 3 — Import et analyse de l'APK:

1. Importer l'APK dans MobSF pour analyse

2. Dans l'interface web MobSF, cliquer sur le bouton "Upload & Analyze"

3. Cliquer sur "Choisir un fichier" et naviguer jusqu'au dossier de travail

4. Sélectionner l'APK à analyser (DivaApplication.apk)

5. Cliquer sur "Analyze" pour lancer l'analyse

6. Une barre de progression s'affiche pendant l'analyse

7. Noter l'heure de début d'analyse dans le fichier de traçabilité :

<img width="1916" height="801" alt="image" src="https://github.com/user-attachments/assets/dfd410bf-740b-4877-af2e-84e5ef0cb474" />

<img width="841" height="220" alt="image" src="https://github.com/user-attachments/assets/6fff8613-9739-4dc7-a7f5-5769d6812942" />

Après que l'analyse est terminé, le score de sécurité global attribué par MobSF est: 36/100.

<img width="1913" height="827" alt="image" src="https://github.com/user-attachments/assets/9f5802fa-a40e-40ab-b4ca-88a858896424" />


<img width="627" height="438" alt="image" src="https://github.com/user-attachments/assets/24b8df4b-0840-4223-9c9d-14a4924d4301" />


Puis, on va noter l'heure de fin d'analyse et le score de sécurité dans le fichier de traçabilité: 

<img width="843" height="311" alt="image" src="https://github.com/user-attachments/assets/50e0e141-08dc-4894-876c-1e9777c16b77" />

Application permission:

<img width="1656" height="435" alt="image" src="https://github.com/user-attachments/assets/0a198bc3-e641-4273-9c50-4f15467d2f21" />

Certificate analysis:

<img width="1651" height="545" alt="image" src="https://github.com/user-attachments/assets/00b11691-91b3-43df-ade7-c7f1217ff5a9" />

Manifest analysis:

<img width="1697" height="561" alt="image" src="https://github.com/user-attachments/assets/f98bc576-df51-455c-89fc-282d9621875b" />

Code analysis:

<img width="1712" height="581" alt="image" src="https://github.com/user-attachments/assets/d3c16c09-dd6f-45bd-aa6f-8a2f95587af6" />

# Task 4 — Analyse du manifeste et des permissions

Étape 1 — Noter les infos de base (App Information)

D'après  la section "App Information" du rapport :

<img width="841" height="302" alt="image" src="https://github.com/user-attachments/assets/5f39c29d-6edd-4894-8fab-1436f64a5a20" />

Étape 2 — Créer le fichier des permissions

<img width="942" height="382" alt="image" src="https://github.com/user-attachments/assets/38c95876-c2d1-460e-b339-b0f3f284a03f" />

Étape 3 — Créer le fichier des composants exportés

<img width="1322" height="346" alt="image" src="https://github.com/user-attachments/assets/7208b962-40b2-4215-8a0c-3e35b981d8bc" />


Étape 4 — Analyse des risques 

🔴 Critique — android:debuggable=true

Un attaquant peut attacher un debugger, lire la mémoire et extraire des données sensibles.

🔴 Critique — minSdk=15 (Android 4.0)

L'app tourne sur des OS très anciens sans patches de sécurité Google.

🟡 Warning — android:allowBackup=true

N'importe qui avec un PC et le débogage USB activé peut copier toutes les données de l'app via adb backup.

🟡 Warning — Composants non protégés

Les activités APICredsActivity et APICreds2Activity sont accessibles par n'importe quelle autre app — risque de vol de credentials API.

🟡 Warning — ContentProvider exporté

NotesProvider est accessible à toutes les apps sans permission — fuite de données possible.

# Task 5 — Analyse de la configuration réseau: N'est pas disponible.

# Task 6 — Analyse du code et des ressources 

<img width="1568" height="605" alt="image" src="https://github.com/user-attachments/assets/bd5a98af-6b63-447e-8ced-ccc0226504e8" />

Étape 1 — Créer le fichier des vulnérabilités

<img width="1215" height="761" alt="image" src="https://github.com/user-attachments/assets/a358772d-caa6-410b-a495-5a6414b75e60" />

Étape 2 — Créer le fichier des ressources sensibles

<img width="1205" height="348" alt="image" src="https://github.com/user-attachments/assets/5fe7d75e-2283-432f-a426-f3415b4ca406" />

Étape 3 — Vérification finale

<img width="897" height="206" alt="image" src="https://github.com/user-attachments/assets/897ef9a9-21d4-4808-afd0-ada1e29d3eaf" />

Points importants :
🔴 Le plus critique : android:debuggable=true + BuildConfig.java confirment que c'est un build de debug en production — double confirmation.

🟡 Pattern récurrent : Les activités InsecureDataStorage (2, 3, 4) montrent que DIVA est intentionnellement vulnérable 

sur le thème du stockage non sécurisé — c'est une app d'entraînement !

# Task 7 — Corrélation avec OWASP MASVS 

Étape 1 — Créer le fichier de corrélation MASVS

Accés à la documentation MASVS : https://mas.owasp.org/MASVS/

<img width="1920" height="982" alt="image" src="https://github.com/user-attachments/assets/acea7e3b-c8bd-4515-a7e7-9e8283e61177" />

Étape 1 — Créer le fichier de corrélation MASVS

Vulnérabilité 1 — SQL Injection
Vulnérabilité 2 — Stockage externe non sécurisé
Vulnérabilité 3 — Fichier temporaire sensible
Vulnérabilité 4 — Debug activé en production
Vulnérabilité 5 — Logs sensibles

<img width="1395" height="762" alt="image" src="https://github.com/user-attachments/assets/1cb49232-c5ba-428e-bfff-8c71fbe4efee" />

Étape 2 — Ajouter les tests MASTG complémentaires

<img width="1410" height="240" alt="image" src="https://github.com/user-attachments/assets/10f6ca14-a9a4-4a83-a34b-a7158bbac38d" />

Étape 3 — Vérifier le fichier complet

<img width="1116" height="536" alt="image" src="https://github.com/user-attachments/assets/ab0c8c4c-80f5-4257-a40c-5af57d0e0bd3" />

<img width="1102" height="338" alt="image" src="https://github.com/user-attachments/assets/0631cea9-fe49-47a8-9c40-a117712b42ec" />

# Task 8 — Exportation et analyse du rapport complet

Étape 1 — Exporter le rapport PDF depuis MobSF:

<img width="1912" height="822" alt="image" src="https://github.com/user-attachments/assets/0fd19acc-7caf-41d3-9788-8b8a36b40597" />

Téléchargement du rapport dans le dossier de travail et renommage du fichier avec un nom explicite :

<img width="942" height="201" alt="image" src="https://github.com/user-attachments/assets/26788d6e-6f30-4c7b-89ea-3c1180a75764" />

Étape 2 — Créer le fichier Top Vulnérabilités

<img width="1103" height="430" alt="image" src="https://github.com/user-attachments/assets/30f30737-ab05-4cd9-9a72-9a62a3d51af1" />

Étape 3 — Ajouter les faux positifs potentiels

<img width="1082" height="297" alt="image" src="https://github.com/user-attachments/assets/265fae47-53ac-49a7-a9bc-71afcd1d0407" />

Étape 4 — Vérification finale de tous les fichiers

<img width="936" height="491" alt="image" src="https://github.com/user-attachments/assets/1c28766e-06db-4416-b6b9-12a9c96e42d1" />

# Task 9 — Rédaction du mini-rapport d'audit

Étape 1 — Créer le fichier 

<img width="703" height="107" alt="image" src="https://github.com/user-attachments/assets/b5055a9e-6ff2-4cb3-9493-be27c692ae20" />


<img width="1905" height="848" alt="image" src="https://github.com/user-attachments/assets/b6fd73df-7e6c-4896-a129-4e5c3a3bb1be" />


Étape 2 — Finaliser la traçabilité

<img width="900" height="335" alt="image" src="https://github.com/user-attachments/assets/f5e252b2-d613-49ed-94e1-b4ccc6db0051" />

Structure du rapport: 

<img width="910" height="841" alt="image" src="https://github.com/user-attachments/assets/bdc35205-c4cd-44c2-8606-fc9eb550c251" />

<img width="911" height="815" alt="image" src="https://github.com/user-attachments/assets/69429c49-6a13-46b5-b2ea-37daaf5596d9" />

<img width="940" height="671" alt="image" src="https://github.com/user-attachments/assets/3571cde5-7c63-4343-b00c-5602ad14f4ae" />






































