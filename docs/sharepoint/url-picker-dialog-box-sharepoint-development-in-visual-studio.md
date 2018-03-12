---
title: "Boîte de dialogue Sélecteur d’URL (développement SharePoint dans Visual Studio) | Documents Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.SharePointTools.VWD.URLPicker
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, URL picker
- SharePoint development in Visual Studio, designer
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload:
- office
ms.openlocfilehash: 65851596d7a9df1ec7da9106891dff6471f1afb6
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/10/2018
---
# <a name="url-picker-dialog-box-sharepoint-development-in-visual-studio"></a>Boîte de dialogue du sélecteur d'URL (développement SharePoint dans Visual Studio)
  Dans la boîte de dialogue Sélecteur de URL, vous pouvez choisir des fichiers tels que les fichiers de page maître ou des fichiers image qui se trouvent dans votre projet ou sur le serveur local qui exécute SharePoint.  
  
 Cette boîte de dialogue s’affiche lorsque vous avez la possibilité de choisir un fichier pour définir une propriété. Vous pouvez ouvrir cette boîte de dialogue en cliquant sur le bouton de sélection (![ellipse de concepteur ASP.NET Mobile](../sharepoint/media/mwellipsis.gif "ellipse de concepteur ASP.NET Mobile")) en regard de différentes propriétés dans le **depropriétés** fenêtre. Le bouton de sélection apparaît également comme une IntelliSense invite lorsque vous assignez des valeurs à certains attributs dans le **Source** mode du concepteur.  
  
## <a name="uielement-list"></a>Liste des éléments d’interface  
 **Dossiers du projet**  
 Affiche la liste des dossiers définis dans le projet ou sur le serveur local qui exécute SharePoint. Choisissez le bouton pour afficher les sous-dossiers.  
  
 Développez le **projet** nœud à sélectionner les fichiers dans votre projet. Pour apparaître comme sélectionnables dans la boîte de dialogue, les fichiers de votre projet doivent respecter les critères suivants :  
  
-   Le fichier doit se trouver dans un dossier mappé.  
  
-   Le fichier doit être ajouté au package de solution.  
  
-   Le fichier ne peut pas se trouver dans un autre projet.  
  
 Si vous souhaitez faire référence aux fichiers qui ne répondent pas à ces critères, vous devez entrer le chemin d’accès du fichier manuellement.  
  
 Développez le **Server** nœud à sélectionner les fichiers qui sont trouvent sur le serveur local qui exécute SharePoint. Pour apparaître comme sélectionnables dans la boîte de dialogue, ces fichiers doivent respecter les critères suivants :  
  
-   Le fichier doit se trouver dans un des dossiers mappés suivants : **Images**, **dispositions**, ou **ControlTemplates**.  
  
-   Le fichier ne peut pas se trouver dans la base de données de contenu SharePoint.  
  
 Si vous souhaitez faire référence aux fichiers qui ne répondent pas à ces critères, vous devez entrer le chemin d’accès du fichier manuellement.  
  
 **Contenu du dossier**  
 Affiche la liste des fichiers du dossier sélectionné. Choisissez un fichier, puis le **OK** bouton pour fermer la boîte de dialogue et envoyer votre sélection au processus qui l’a appelée.  
  
 **Types de fichiers**  
 Vous permet de choisir parmi une liste de fichiers qui sont appropriés pour la tâche que vous effectuez.  
  
## <a name="see-also"></a>Voir aussi  
 [Création de Pages d’Application pour SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md)   
 [Création de composants WebPart pour SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)   
 [Création de contrôles réutilisables pour les composants WebPart ou les pages d’application](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)   
  
  