---
title: "Test de zone 7: partage | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "contrôle de code source (Visual Studio SDK), partage des éléments"
  - "contrôle plug-ins de source, partager des éléments"
ms.assetid: 6ec4780a-bda4-4327-bb3e-c6c9e7eabf35
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# Test de zone 7: partage
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Cette zone de texte couvre les éléments de partage entre les emplacements via la commande de **partage** .  
  
 Une opération de hhare est la duplication passer des éléments de fichiers et dossiers entre deux emplacements ou plus dans une hiérarchie de fichiers du contrôle de code source.  La duplication ne se produit pas vraiment sur le serveur, mais l'utilisateur voit le même fichier dans des emplacements au moins deux spécifiés.  Chaque fois que des modifications sont apportées aux éléments partagés l'un des, ces modifications apparaissent dans tout l'autre des emplacements partagés.  
  
 Le partage dans des dossiers s'exécute si vous sélectionnez un dossier avec au moins un fichier sous contrôle de code source dans celui\-ci.  L'ordre de partage est désactivée dans les conditions suivantes :  
  
-   si le dossier sélectionné est un dossier vide.  
  
-   S'il existe un vrai dossier, mais de il ne contient aucun fichier du contrôle de code source.  
  
-   S'il existe un dossier virtuel, que les fichiers sous contrôle de code source se trouvent sur lui ou pas.  
  
-   S'il existe un projet Web de site distant.  
  
## menu Access de commande  
 Les chemins d'accès suivants de menu d'environnement de développement intégré \(IDE\) de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] sont utilisés dans des scénarios de test.  
  
 partage : **Fichier**\- \>**Contrôle de source de données**\- \>**partage**.  
  
## Comportement attendu  
  
-   Le fichier partagé apparaît à l'emplacement partagé.  
  
-   L'historique du magasin de version du contrôle de code source montre que les fichiers sont partagés.  
  
-   modifiant un fichier partagé modifie les deux emplacements du fichier.  
  
## Cas de test  
 Voici des scénarios de test spécifiques pour la zone de texte de partage.  
  
|Action|étapes de test|résultats attendus à vérifier|  
|------------|--------------------|-----------------------------------|  
|Partagez un fichier d'un projet chargé sous contrôle de code source vers un autre projet chargé|1.  Création d'un nouveau projet.<br />2.  ajoutez un deuxième projet à la solution.<br />3.  créez un fichier dans le deuxième projet avec un nom qui n'est pas dans le premier projet.<br />4.  Ajouter la solution au contrôle de code source.<br />5.  sélectionnez le premier projet.<br />6.  ouvrez la boîte de dialogue de **partage** \(**Fichier** \- \> **Contrôle de source de données** \- \> **partage**\).<br />7.  partagez le fichier du deuxième projet au premier projet.<br />8.  Acceptez **Extraire** si vous y êtes invité.|Comportement attendu par courantes.|  
|Partagez un fichier d'un projet à un autre|1.  Création d'un nouveau projet.<br />2.  Ajoutez \-la au contrôle de code source.<br />3.  fermez la solution.<br />4.  créez un deuxième projet \(la nouvelle solution.\)<br />5.  Ajouter la solution au contrôle de code source.<br />6.  sélectionnez le projet.<br />7.  ouvrez la boîte de dialogue de **partage** \(**Fichier** \- \> **Contrôle de source de données** \- \> **partage**\).<br />8.  Partagez un fichier projet précédemment ajouté au projet ouvert.<br />9. Acceptez **Extraire** si vous y êtes invité.|Comportement attendu par courantes.|  
|Partagez une partie de fichier pas du projet du contrôle de code source dans le projet actuellement chargé|1.  Création d'un nouveau projet.<br />2.  Ajouter la solution au contrôle de code source.<br />3.  Ajoutez un fichier au contrôle de code source qui ne fait pas partie du projet ou de la solution.<br />4.  sélectionnez le projet et ouvrez la boîte de dialogue de **partage** \(**Fichier** \- \> **Contrôle de source de données** \- \> **partage**\).<br />5.  Sélectionnez un fichier dans la boîte de dialogue de **partage** qui n'existe pas dans le projet ou la solution en cours et ne le partage pas.<br />6.  Acceptez **Extraire** si vous y êtes invité.|La mémoire étant de contrôle de code source a effectué une commande get, afin que le fichier est maintenant à l'emplacement local du projet.|  
|Fichiers partagés dans le même projet vers un dossier différent|1.  sélectionnez **Extraire automatiquement** dans **Outils** \- \> **Options** \- \> **Contrôle de source de données**.<br />2.  Créez un projet et ajoutez \-la au contrôle de code source.<br />3.  ajoutez un dossier au projet.<br />4.  ajoutez un fichier au dossier et signez le dossier.<br />5.  sélectionnez le dossier.<br />6.  ouvrez la boîte de dialogue de **partage** \(**Fichier** \- \> **Contrôle de source de données** \- \> **partage**\).<br />7.  Fichier partagé vers le dossier sélectionné.|Comportement attendu par courantes.<br /><br /> Le dossier doit être signé avec un fichier qui s'y trouvent avant son utilisation pour le partage.|  
|partagez un dossier dans le projet chargé \- récursif|1.  Création d'un nouveau projet.<br />2.  Ajouter la solution au contrôle de code source.<br />3.  sélectionnez le projet.<br />4.  ouvrez la boîte de dialogue de **partage** \(**Fichier** \- \> **Contrôle de source de données** \- \> **partage**\).<br />5.  sélectionnez un dossier.<br />6.  partagez le dossier de manière récursive dans le projet.|Comportement attendu par courantes.|  
|Partagez plusieurs fichiers d'un projet à un autre|1.  Créez un nouveau projet avec plusieurs fichiers qu'il contient.<br />2.  Ajouter la solution au contrôle de code source.<br />3.  fermez la solution.<br />4.  Créez un projet dans une solution.<br />5.  Ajouter la solution au contrôle de code source.<br />6.  sélectionnez le projet.<br />7.  ouvrez la boîte de dialogue de **partage** \(**Fichier** \- \> **Contrôle de source de données** \- \> **partage**\).<br />8.  Partagez plusieurs fichiers du projet créé précédemment au projet ouvert.|Comportement attendu par courantes.|  
  
## Voir aussi  
 [Guide d'évaluation pour les Plug\-ins de contrôle de code Source](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)