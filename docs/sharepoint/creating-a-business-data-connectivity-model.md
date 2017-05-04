---
title: "Cr&#233;ation d&#39;un mod&#232;le de connectivit&#233; de donn&#233;es m&#233;tiers | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "BDC (développement SharePoint dans Visual Studio), créer un modèle"
  - "service de connectivité de données métiers (développement SharePoint dans Visual Studio), créer un modèle"
  - "service de connectivité de données métiers (développement SharePoint dans Visual Studio), modèle"
  - "développement SharePoint dans Visual Studio, service de connectivité de données métiers"
ms.assetid: 19fd12d0-a51a-4da4-98ac-918542e84507
caps.latest.revision: 24
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 23
---
# Cr&#233;ation d&#39;un mod&#232;le de connectivit&#233; de donn&#233;es m&#233;tiers
  Vous pouvez créer un modèle de connectivité de données métiers \(BDC, Business Data Connectivity\) ou personnaliser un modèle BDC existant à l'aide de Visual Studio.  Chaque projet SharePoint ne peut contenir qu'un seul modèle.  Pour plus d'informations, consultez [Intégration de données métiers dans SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md).  
  
## Création d'un modèle  
 Pour créer un modèle, créez un projet **Modèle de connectivité de données métiers** ou ajoutez un élément **Modèle de connectivité de données métiers** à un **Projet SharePoint vide**.  
  
> [!NOTE]  
>  [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] doit être installé sur votre ordinateur.  
  
 Visual Studio ajoute un dossier au projet.  Ce dossier porte le nom que vous spécifiez pour l'élément **Modèle de connectivité de données métiers** dans la boîte de dialogue **Ajouter un nouvel élément**.  Si vous créez un projet **Modèle de connectivité de données métiers**, Visual Studio nomme le dossier **BdcModel1**.  
  
 Visual Studio ajoute les fichiers suivants au nouveau dossier :  
  
|Fichier|Description|  
|-------------|-----------------|  
|Fichier de définition du modèle|Contient du code XML qui définit les entités, les méthodes, les objets systèmes métiers, ainsi que d'autres métadonnées qui décrivent le modèle.<br /><br /> Vous pouvez modifier les métadonnées de ce fichier à l'aide du concepteur BDC, de l'**Explorateur BDC**, de la fenêtre **Détails de méthode BDC** et de la fenêtre **Propriétés**.|  
|Fichier de code de service de l'entité|Contient des méthodes qui récupèrent, mettent à jour et suppriment des instances de l'entité par défaut.|  
  
 Pour définir les propriétés d'une entité, vous pouvez modifier le fichier de code de l'entité.  Pour plus d'informations, consultez [Comment : ajouter une entité à un modèle](../sharepoint/how-to-add-an-entity-to-a-model.md).  
  
 Pour récupérer, mettre à jour et supprimer des instances d'une entité, vous pouvez ajouter du code au fichier de code de service de l'entité.  Pour plus d'informations, consultez [Conception d'un modèle de connectivité de données métiers](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
 Lorsque vous compilez le projet, Visual Studio crée un assembly.  Veillez à ne pas ajouter au projet d'autres éléments qui ajouteraient du code à l'assembly du projet \(par exemple, un élément **Flux de travail séquentiel** ou un élément **WebPart**\).  Le code de cet élément ne s'exécuterait pas lors du déploiement de la solution, car le package de solution ne copie pas l'assembly dans le Global Assembly Cache.  Le package de solution déploie l'assembly dans la base de données BDC uniquement dans SharePoint.  
  
> [!NOTE]  
>  Visual Studio copie l'assembly dans les deux emplacements de votre ordinateur local lorsque vous déboguez le projet.  
  
## Ajout d'un modèle existant  
 Vous pouvez importer un modèle créé avec d'autres outils, tels que SharePoint Designer.  Vous pouvez importer un modèle existant dans votre projet dans les cas suivants :  
  
-   Pour personnaliser un modèle qui est déjà déployé dans une batterie de serveurs SharePoint.  
  
-   Pour empaqueter et déployer un modèle existant dans plusieurs batteries de serveurs SharePoint.  
  
 Dans les deux cas, les systèmes métiers définis dans le modèle que vous importez ne sont pas modifiés et ils continueront à fonctionner comme prévu.  Pour ajouter un modèle existant à un projet SharePoint, utilisez la boîte de dialogue **Ajouter un élément existant** de Visual Studio.  Pour plus d'informations, consultez [Comment : ajouter un fichier de modèle BDC existant à un projet SharePoint](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md).  
  
 Vous pouvez ajouter un système LOB de type assembly .NET Framework au modèle importé en sélectionnant une option dans **Ajouter un LobSystem d'assembly .NET**.  Cela vous permet de personnaliser le code et d'utiliser un concepteur pour définir les métadonnées du modèle importé.  
  
## Rubriques connexes  
  
|Titre|Description|  
|-----------|-----------------|  
|[Comment : créer un modèle BDC](../sharepoint/how-to-create-a-bdc-model.md)|Vous indique comment créer un modèle BDC.|  
|[Comment : ajouter un fichier de modèle BDC existant à un projet SharePoint](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md)|Vous indique comment importer un modèle existant dans un projet SharePoint.|  
|[Comment : utiliser un fichier de ressources pour spécifier des noms localisés, propriétés et autorisations](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)|Décrit comment fournir des chaînes fusionnées avec les métadonnées du modèle lorsque le modèle est consommé par un composant WebPart ou une page Web.|  
|[Comment : inclure un assembly personnalisé dans une fonctionnalité BDC](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md)|Vous indique comment inclure un assembly personnalisé dans une fonctionnalité.|  
  
  