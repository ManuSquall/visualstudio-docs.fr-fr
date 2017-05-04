---
title: "Comment&#160;: ajouter une entit&#233; &#224; un mod&#232;le | Microsoft Docs"
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
  - "EntityTool"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "BDC (développement SharePoint dans Visual Studio), ajouter une entité"
  - "BDC (développement SharePoint dans Visual Studio), entité"
  - "service de connectivité de données métiers (développement SharePoint dans Visual Studio), ajouter une entité"
  - "service de connectivité de données métiers (développement SharePoint dans Visual Studio), entité"
ms.assetid: 139a6639-dabe-4e14-bb64-e5f4efb6f2fb
caps.latest.revision: 23
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 22
---
# Comment&#160;: ajouter une entit&#233; &#224; un mod&#232;le
  Pour créer une entité, ajouter un contrôle de l'entité de la **Boîte à outils** Visual Studio sur le concepteur de connectivité de données métiers \(BDC, Business Data Connectivity\).  
  
### Pour ajouter une entité au modèle  
  
1.  Créez un projet BDC ou ouvrez un projet BDC existant.  Pour plus d'informations, consultez [Création d'un modèle de connectivité de données métiers](../sharepoint/creating-a-business-data-connectivity-model.md).  
  
2.  Dans la **Boîte à outils**, à partir du groupe **BusinessDataCatalog**, ajouter un contôle de l' **Entité** sur le concepteur.  
  
     La nouvelle entité s'affiche dans le concepteur.  Visual Studio ajoute un élément `<Entity>` au code XML du fichier du modèle BDC de votre projet.  Pour plus d'informations sur les attributs d'un élément d'entité, consultez [Entité](http://go.microsoft.com/fwlink/?LinkId=169296).  
  
3.  Dans le Concepteur, ouvrez le menu contextuel de l'entité, choisissez **ajouter**, puis choisissez **Identificateur**.  
  
     Un nouvel identificateur s'affiche sur l'entité.  
  
    > [!NOTE]  
    >  Vous pouvez modifier le nom de l'entité et l'identificateur dans la fenêtre **Propriétés**.  
  
4.  Définissez les champs de l'entité dans une classe.  Vous pouvez ajouter une nouvelle classe au projet ou utiliser une classe existante créée à partir d'autres outils, tels que le Concepteur Objet\/Relationnel \(Concepteur O\/R\).  L'exemple suivant illustre une classe d'entité nommée Contact.  
  
     [!code-csharp[SP_BDC_Entity_Data_Class#1](../snippets/csharp/VS_Snippets_OfficeSP/sp_bdc_entity_data_class/cs/bdcmodel1/contact.cs#1)]
     [!code-vb[SP_BDC_Entity_Data_Class#1](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_bdc_entity_data_class/vb/bdcmodel1/contact.vb#1)]  
  
## Voir aussi  
 [Comment : ajouter une méthode de création](../sharepoint/how-to-add-a-creator-method.md)   
 [Comment : ajouter une méthode de suppression](../sharepoint/how-to-add-a-deleter-method.md)   
 [Comment : ajouter une méthode de mise à jour](../sharepoint/how-to-add-an-updater-method.md)   
 [Comment : ajouter une méthode de recherche](../sharepoint/how-to-add-a-finder-method.md)   
 [Comment : ajouter une méthode de recherche spécifique](../sharepoint/how-to-add-a-specific-finder-method.md)  
  
  