---
title: Boîte de dialogue du sélecteur d’URL (développement SharePoint dans Visual Studio) | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.VWD.URLPicker
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, URL picker
- SharePoint development in Visual Studio, designer
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: dbb0c682f478ca7a950cb4d5c1ef88eeee98731a
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2019
ms.locfileid: "54870751"
---
# <a name="url-picker-dialog-box-sharepoint-development-in-visual-studio"></a>Boîte dialogue Sélecteur d’URL (développement SharePoint dans Visual Studio)
  Dans la boîte de dialogue du sélecteur URL, vous pouvez choisir des fichiers tels que les fichiers de page maître ou des fichiers image qui se trouvent dans votre projet ou sur le serveur local qui exécute SharePoint.  
  
 Cette boîte de dialogue s’affiche lorsque vous avez la possibilité de choisir un fichier pour définir une propriété. Vous pouvez ouvrir cette boîte de dialogue en choisissant le bouton de sélection (![ellipse de concepteur ASP.NET Mobile](../sharepoint/media/mwellipsis.gif "ellipse de concepteur ASP.NET Mobile")) en regard de différentes propriétés dans le **propriétés** fenêtre. Le bouton de sélection apparaît également comme un IntelliSense invite lorsque vous assignez des valeurs à certains attributs dans le **Source** vue du concepteur.  
  
## <a name="uielement-list"></a>Liste UIElement
 **Dossiers du projet**  
 Affiche une liste des dossiers définis dans le projet ou sur le serveur local qui exécute SharePoint. Choisissez le bouton pour afficher les sous-dossiers.  
  
 Développez le **projet** nœud pour choisir des fichiers dans votre projet. Pour apparaître comme sélectionnables dans la boîte de dialogue, les fichiers de votre projet doivent respecter les critères suivants :  
  
- Le fichier doit figurer dans un dossier mappé.  
  
- Le fichier doit être ajouté au package de solution.  
  
- Le fichier ne peut pas se trouver dans un autre projet.  
  
  Si vous souhaitez faire référence aux fichiers qui ne répondent pas à ces critères, vous devez entrer le chemin d’accès du fichier manuellement.  
  
  Développez le **Server** nœud pour choisir les fichiers qui se trouvent sur le serveur local qui exécute SharePoint. Pour apparaître comme sélectionnables dans la boîte de dialogue, ces fichiers doivent respecter les critères suivants :  
  
- Le fichier doit se trouver dans un des dossiers mappés suivants : **Images**, **dispositions**, ou **ControlTemplates**.  
  
- Le fichier ne peut pas se trouver dans la base de données de contenu SharePoint.  
  
  Si vous souhaitez faire référence aux fichiers qui ne répondent pas à ces critères, vous devez entrer le chemin d’accès du fichier manuellement.  
  
  **Contenu du dossier**  
  Affiche la liste des fichiers du dossier sélectionné. Choisissez un fichier, puis le **OK** bouton pour fermer la boîte de dialogue et envoyer votre sélection au processus qui l’a appelée.  
  
  **Types de fichiers**  
  Vous permet de choisir parmi une liste de fichiers qui sont appropriés pour la tâche que vous effectuez.  
  
## <a name="see-also"></a>Voir aussi
 [Créer des pages d’application pour SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md)   
 [Créer des composants WebPart pour SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)   
 [Créer des contrôles réutilisables pour les composants WebPart ou les pages d’application](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)   
