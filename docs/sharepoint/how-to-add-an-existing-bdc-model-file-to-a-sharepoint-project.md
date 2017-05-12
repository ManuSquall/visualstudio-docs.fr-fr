---
title: "Comment&#160;: ajouter un fichier de mod&#232;le BDC existant &#224; un projet SharePoint"
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
  - "VS.SharePointTools.BDC.ImportDialog"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "BDC (développement SharePoint dans Visual Studio), importer un modèle"
  - "BDC (développement SharePoint dans Visual Studio), supprimer un modèle"
  - "service de connectivité de données métiers (développement SharePoint dans Visual Studio), importer un modèle"
  - "service de connectivité de données métiers (développement SharePoint dans Visual Studio), réutiliser un modèle"
ms.assetid: e843738a-f936-4dcd-be35-249407573b74
caps.latest.revision: 16
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 15
---
# Comment&#160;: ajouter un fichier de mod&#232;le BDC existant &#224; un projet SharePoint
  Vous pouvez personnaliser, empaqueter, puis redéployer un modèle \(BDC\) de connectivité des données d'entreprise à l'aide de Visual Studio pour ajouter le fichier de modèle \(.bdcm\) à un projet de batterie de serveurs SharePoint.  Pour plus d'informations, consultez [Création d'un modèle de connectivité de données métiers](../sharepoint/creating-a-business-data-connectivity-model.md).  
  
### Pour ajouter un fichier de modèle BDC à un projet SharePoint  
  
1.  Dans l'**Explorateur de solutions**, sélectionnez le dossier pour un projet SharePoint.  
  
2.  Dans la barre de menus, choisissez **Projet**,  **Ajouter un élément existant**.  
  
3.  Dans la boîte de dialogue **Ajouter un élément existant**, recherchez le fichier de définition du modèle que vous souhaitez ajouter à votre projet, sélectionnez\-le, puis cliquez sur **Ajouter**.  
  
     Si le modèle ne définit pas de *système LOB de type assembly .NET*, la boîte de dialogue **Ajouter un LobSystem d'assembly .NET** s'affiche.  
  
4.  Si la boîte de dialogue apparaît, effectuez l'une des opérations suivantes :  
  
    -   Si vous souhaitez écrire un code personnalisé et utiliser un concepteur pour définir les métadonnées du modèle importé, cliquez sur le bouton **Oui**, nommez le système, puis cliquez sur le bouton **OK**.  
  
    -   Sinon, Choisissez le bouton **Non**, puis **OK**.  
  
     L'élément **Modèle de connectivité de données métiers** est ajouté au projet.  
  
## Voir aussi  
 [Création d'un modèle de connectivité de données métiers](../sharepoint/creating-a-business-data-connectivity-model.md)   
 [Comment : créer un modèle BDC](../sharepoint/how-to-create-a-bdc-model.md)   
 [Comment : utiliser un fichier de ressources pour spécifier des noms localisés, propriétés et autorisations](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)   
 [Comment : inclure un assembly personnalisé dans une fonctionnalité BDC](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md)   
 [Intégration de données métiers dans SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)  
  
  