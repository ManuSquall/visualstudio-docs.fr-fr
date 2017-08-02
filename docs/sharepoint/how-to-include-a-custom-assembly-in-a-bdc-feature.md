---
title: "Comment&#160;: inclure un assembly personnalis&#233; dans une fonctionnalit&#233; BDC"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.SharePointTools.BDC.Add_Assemblies_Dialog"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "BDC (développement SharePoint dans Visual Studio), ajouter une référence"
  - "BDC (développement SharePoint dans Visual Studio), assembly personnalisé"
  - "service de connectivité de données métiers (développement SharePoint dans Visual Studio), ajouter une référence"
  - "service de connectivité de données métiers (développement SharePoint dans Visual Studio), assembly personnalisé"
ms.assetid: 2ddf44b9-5f51-4bca-b8bb-94c4bbd1c5f3
caps.latest.revision: 17
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 16
---
# Comment&#160;: inclure un assembly personnalis&#233; dans une fonctionnalit&#233; BDC
  Votre projet peut référencer des assemblys d'autres projets dans la même solution.  Toutefois, vous devez ajouter ces assemblys au fichier de fonctionnalités du projet à l'aide de la boîte de dialogue **Assigner des assemblys référencés à des LobSystems**.  
  
### Pour inclure un assembly personnalisé dans une fonctionnalité de connectivité de données métiers \(BDC, Business Data Connectivity\)  
  
1.  Dans l'**Explorateur de solutions**, choisissez le dossier qui contient le modèle BDC.  
  
2.  Dans le menu **Affichage**, cliquez sur **Fenêtre Propriétés**.  
  
3.  Dans la fenêtre **Propriétés**, sélectionnez la propriété **Assemblys**, puis choisissez le bouton de sélection \(![Bouton de sélection du concepteur ASP.NET mobile](~/docs/sharepoint/media/mwellipsis.gif "Bouton de sélection du concepteur ASP.NET mobile")\).  
  
     La boîte de dialogue **Assigner des assemblys référencés à des LobSystems** apparaît.  
  
4.  Dans la liste **Sélectionnez un assembly**, choisissez l'assembly personnalisé.  
  
    > [!NOTE]  
    >  Les assemblys s'affichent dans la boîte de dialogue **Assigner des assemblys référencés à des LobSystems** uniquement si vous avez ajouté une référence au projet qui contient l'assembly.  Pour plus d'informations, consultez [Comment : ajouter ou supprimer des références à l'aide de la boîte de dialogue Ajouter une référence](http://msdn.microsoft.com/fr-fr/3bd75d61-f00c-47c0-86a2-dd1f20e231c9).  
  
5.  Dans le groupe **Propriétés de la référence**, ouvrez sur la liste qui s'affiche pour la propriété **Portée de LobSystem**, puis choisissez le système LOB des méthodes qui utilisent l'assembly personnalisé, et ensuite choisissez le bouton **OK**.  
  
    > [!NOTE]  
    >  Pour déboguer le code dans l'assembly personnalisé, vous devez ajouter l'assembly au package de solution.  Pour plus d'informations, consultez [Comment : ajouter et supprimer des assemblys supplémentaires](../sharepoint/how-to-add-and-remove-additional-assemblies.md).  
  
## Voir aussi  
 [Comment : utiliser un fichier de ressources pour spécifier des noms localisés, propriétés et autorisations](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)   
 [Comment : ajouter un fichier de modèle BDC existant à un projet SharePoint](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md)   
 [Création d'un modèle de connectivité de données métiers](../sharepoint/creating-a-business-data-connectivity-model.md)   
 [Comment : créer un modèle BDC](../sharepoint/how-to-create-a-bdc-model.md)   
 [Intégration de données métiers dans SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)  
  
  