---
title: "Test de zone 6: supprimer | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "contrôle de code source (Visual Studio SDK), la suppression d'éléments"
  - "contrôle plug-ins de source, la suppression d'éléments"
ms.assetid: 6f2e872c-5ba2-4303-9f50-a90cef9a6225
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# Test de zone 6: supprimer
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Cette zone de test du plug\-in du contrôle de code source couvre les actions de suppression.  
  
 le contrôle de code source répond aux actions de suppression dans **Explorateur de solutions**.  
  
 Voici une liste d'éléments qui peuvent être supprimés :  
  
-   Fichiers  
  
-   Dossiers  
  
-   Projet  
  
 Selon le type de projet, vous pourriez l'option à **Supprimer** le projet \(feuilles les fichiers sur le disque\) ou **Delete** le projet \(supprime les fichiers sur le disque\).  L'un ou l'autre d'action supprime le projet ou un élément d' **Explorateur de solutions**.  
  
## Comportement attendu  
 Le comportement attendu pour les cas de test dans la zone de texte de suppression est :  
  
-   L'élément dernier n'est plus visible dans **Explorateur de solutions**.  
  
-   Le parent du projet ou de l'élément supprimé est extrait en fonction de les besoins \(comportant éventuellement une invite.\)  
  
-   Après avoir supprimé vérifié ou l'élément ajouté, il n'apparaît pas dans la fenêtre d' **Archivages en attente** .  
  
-   L'élément existe toujours dans la mémoire étant de contrôle de code source, même après la suppression, et doit être manuellement vidé.  
  
|Action|Étapes de test|résultats attendus à vérifier|  
|------------|--------------------|-----------------------------------|  
|supprimez un projet client|1.  créez un projet client.<br />2.  Ajouter la solution au contrôle de code source.<br />3.  Supprimez la totalité du projet de la solution|Comportement attendu par courantes.|  
|supprimez un fichier vide|1.  créez un projet client.<br />2.  ajoutez un fichier à octet zéro au projet.<br />3.  Ajouter la solution au contrôle de code source.<br />4.  sélectionnez le fichier, supprimez\-le.|Comportement attendu par courantes.|  
|supprimez un dossier avec un fichier|1.  créez la solution unique de projet.<br />2.  ajoutez un dossier.<br />3.  ajoutez un fichier au dossier.<br />4.  Ajouter la solution au contrôle de code source.<br />5.  Contrôle le projet pour éviter des invites.<br />6.  supprimez le dossier.|Comportement attendu par courantes.|  
|supprimez un projet Web de système de fichiers|1.  créez un projet Web de système de fichiers \(utilisez le bouton Parcourir pour spécifier un chemin d'accès UNC\).<br />2.  Ajouter la solution au contrôle de code source.<br />3.  Supprimez la totalité du projet de la solution.<br />4.  Répétez les étapes 1 à 3 pour un projet Web local \(les chemins différents d'exercices à travers le code mais a la même interface externe et comportement\).|Comportement attendu par courantes.|  
|supprimez un fichier d'un projet Web de système de fichiers|1.  créez un projet Web de système de fichiers.<br />2.  Ajouter la solution au contrôle de code source.<br />3.  supprimez un fichier du projet.<br />4.  Répétez les étapes 1 à 3 pour un projet Web local \(les chemins différents d'exercices à travers le code mais a la même interface externe et comportement\).|Comportement attendu par courantes.|  
  
## Voir aussi  
 [Guide d'évaluation pour les Plug\-ins de contrôle de code Source](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)