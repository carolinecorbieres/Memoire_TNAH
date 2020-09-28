# Mémoire de stage du master "Technologies numériques appliquées à l'histoire"

## Du catalogue au fichier TEI : Création d’un workflow pour encoder automatiquement en XML-TEI des catalogues d’exposition

Ce mémoire a été réalisé dans le cadre d'un stage pour le projet Artl@s de mai à octobre 2020, dans le cadre du Master "Technologies numériques appliquées à l'histoire" de l'École des chartes. L'enjeu de ce stage était de s'appuyer sur le travail de Lucie Rondeau du Noyer pour proposer à l'équipe d'Artl@s un _workflow_ permettant d'encoder automatiquement des catalogues d'exposition des XIXe et XXe siècles afin de verser les données récupérées dans la base de données BasArt. 

Le mémoire revient sur certains aspects techniques du stage, notamment ceux liés à l'intégration des fichiers ALTO dans la chaîne de traitement, ainsi que sur les étapes de la création du _workflow_ et les enjeux liés à son accessibilité.

Le dépôt contient également les livrables techniques que j'ai réalisé lors de mon stage. Vous trouverez dans les dossiers suivants :
  - [1_Reflexions_encodage_catalogues](https://github.com/carolinecorbieres/Memoire_TNAH/tree/master/1_Reflexions_encodage_catalogues) regroupe les réflexions menées sur la modélisation de l'encodage des catalogues d'exposition et des sources catalographiques. Ce dossier est divisé en deux sous-dossiers:
    - **1_Cataloguesexposition** contient une page de catalogue d'exposition et un document XML dans lequel est encodé une entrée du catalogue. Ce document a été présenté à Béatrice Joyeux-Prunel afin de faire valider la structure de l'encodage des catalogues d'exposition. Les commentaires présents dans le documents décrivent les balises utilisées et celles qui peuvent être ajoutées. 
    - **2_GROBID_Cat** contient deux pages de catalogues (un catalogue de vente de manuscrits `1857_02_05_JA1` et un catalogue d'exposition `Cat-Rouen-1860`) et deux documents XML dans lesquels sont encodées des entrées de catalogues selon le modèle proposé par Laurent Romary. Ces documents sont également accompagnés d'une ODD rédigée par Laurent Romary qui permet de valider l'enchaînement de balises que nous avons proposé pour encoder des sources catalographiques.  
  - [2_Worflow](https://github.com/carolinecorbieres/Memoire_TNAH/tree/master/2_Workflow) regroupe toutes les étapes du _workflow_, rédigées en anglais, réalisé pendant ce stage. L'étape 0 (`0_Headers`) a été conçue et rédigée par Auriane Quoix, elle permet de récupérer les métadonnées d'un catalogue regroupées dans un fichier CSV et de les insérer dans le header d'un fichier XML. Les six étapes suivantes ont été l'objet de mon stage:
    - **1_ImportCatalogues** comprend un tutoriel expliquant comment récupérer une version numérique du catalogue d'exposition. Si celui-ci est disponible sur une API IIIF, il est possible d'utiliser le script `import_iiif.py` pour le télécharger. 
    - **2_OCR** est composé d'un tutoriel expliquant les différentes étapes relatives l'OCRisation du document ainsi que de deux dossiers dans lesquels se trouvent des scripts écrits par Ljudmila Petkovic. Le premier sert à évaluer la bonne formation des balises dans la transcription du catalogue et pointe les erreurs à corriger manuellement dans le logiciel d'OCR. Le second script corrige automatiquement les autres erreurs de balisage et transforme les fichiers ALTO en sortie de Transkribus en fichiers ALTO lisibles par _GROBID-dictionaries_.
    - **3_ALTOtoPDF** contient un tutoriel détaillant toutes les étapes pour transformer un fichier ALTO en PDF en passant par XSL-FO et une feuille de style XSL permettant d'obtenir un fichier FO à partir d'un fichier ALTO.
    - **4_GROBID** comprend deux tutoriels, un premier qui permet de lancer _GROBID-dictionaries_ afin d'encoder un catalogue et un second qui explique comment entraîner un modèle dans _GROBID-dictionaries_. Ce dossier possède également quatre modèles, dont trois entraînés à partir d'un même jeu de données (`trainingData_INDEPENDANTS`) mais sur des fichiers différents (PDF avec information typographique `PDF-TYPO`, PDF sans information typographique `PDF-ST` et ALTO `ALTO`). Les résultats de chacun de ces modèles ont permis d'évaluer leur efficacité. 
    - **5_ImproveGROBIDoutput** est composé d'un tutoriel expliquant comment appliquer les scénarii de transformation au fichier XML encodé par _GROBID-dictionaries_ afin d'obtenir un fichier XML-TEI conforme à l'ODD. S'y trouvent aussi deux sous-dossiers comprenant les deux ODD validant chaque étape de transformation, dont l'ODD finale qui a été rédigée avec Auriane Quoix, et les feuilles de style XSL. 
    - **6_TEItoCSV** contient un tutoriel expliquant comment transformer le fichier XML-TEI en CSV et la feuille de style XSL qui permet de le faire. 
    
  À ces 6 dossiers s'ajoutent un projet Oxygen `.xpr` qui permet d'accéder à l'ensemble du dossier dans l'éditeur XML ainsi que les `requirements` à télécharger pour que le _worfkow_ fonctionne. 
  - [3_Catalogues_encodes](https://github.com/carolinecorbieres/Memoire_TNAH/tree/master/3_Catalogues_encodes) regroupe deux sous-dossiers dans lesquels se trouvent quelques catalogues dans les formats XML-TEI et CSV. La série des catalogues de la Société des artistes indépendant sera entièrement encodée au cours du mois d'octobre. 
