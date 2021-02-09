---
title: Boîte de dialogue Sélecteur d’URL (développement SharePoint)
description: En savoir plus sur la boîte de dialogue Sélecteur d’URL, qui permet à un utilisateur de choisir des fichiers situés dans son projet ou sur le serveur local qui exécute SharePoint.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: d04857f0e61e5d9f293d73902cd090f718c65cd0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99892214"
---
# <a name="url-picker-dialog-box-sharepoint-development-in-visual-studio"></a>Boîte de dialogue Sélecteur d’URL (développement SharePoint dans Visual Studio)
  Dans la boîte de dialogue Sélecteur d’URL, vous pouvez choisir des fichiers tels que des fichiers de page maître ou des fichiers image qui se trouvent dans votre projet ou sur le serveur local qui exécute SharePoint.

 Cette boîte de dialogue apparaît lorsque vous avez la possibilité de choisir un fichier pour définir une propriété. Vous pouvez ouvrir cette boîte de dialogue en cliquant sur le bouton de sélection (![ellipse ASP.net Mobile designer](../sharepoint/media/mwellipsis.gif "Bouton de sélection du concepteur ASP.NET mobile")) en regard de différentes propriétés dans la fenêtre **Propriétés** . Le bouton de sélection apparaît également sous la forme d’une invite IntelliSense lorsque vous assignez des valeurs à certains attributs dans la vue **source** du concepteur.

## <a name="uielement-list"></a>Liste des éléments de l'interface utilisateur
 **Dossiers du projet** Affiche la liste des dossiers définis dans le projet ou sur le serveur local qui exécute SharePoint. Choisissez le bouton d’expansion pour afficher les sous-dossiers.

 Développez le nœud du **projet** pour choisir des fichiers dans votre projet. Pour qu’il apparaisse comme sélectionnable dans la boîte de dialogue, les fichiers de votre projet doivent répondre aux critères suivants :

- Le fichier doit être contenu dans un dossier mappé.

- Le fichier doit être ajouté au package de solution.

- Le fichier ne peut pas se trouver dans un autre projet.

  Si vous souhaitez référencer des fichiers qui ne répondent pas à ces critères, vous devez entrer manuellement le chemin d’accès au fichier.

  Développez le nœud du **serveur** pour choisir les fichiers qui se trouvent sur le serveur local qui exécute SharePoint. Pour qu’il apparaisse comme sélectionnable dans la boîte de dialogue, ces fichiers doivent répondre aux critères suivants :

- Le fichier doit se trouver dans l’un des dossiers mappés suivants : **images**, **dispositions** ou **ControlTemplate**.

- Le fichier est introuvable dans la base de données de contenu SharePoint.

  Si vous souhaitez référencer des fichiers qui ne répondent pas à ces critères, vous devez entrer manuellement le chemin d’accès au fichier.

  **Contenu du dossier** Affiche la liste des fichiers dans le dossier sélectionné. Choisissez un fichier, puis choisissez le bouton **OK** pour fermer la boîte de dialogue et envoyer votre sélection au processus qui l’a appelée.

  **Fichiers de type** Vous permet de choisir parmi une liste de fichiers qui conviennent à la tâche que vous effectuez.

## <a name="see-also"></a>Voir aussi
- [Créer des pages d’application pour SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md)
- [Créer des composants WebPart pour SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)
- [Créer des contrôles réutilisables pour les composants WebPart ou les pages d’application](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)
