---
title: "Comment&#160;: ajouter une m&#233;thode de cr&#233;ation | Microsoft Docs"
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
  - "BDC (développement SharePoint dans Visual Studio), ajouter des entités"
  - "BDC (développement SharePoint dans Visual Studio), ajouter des instances d'entité"
  - "BDC (développement SharePoint dans Visual Studio), créateur"
  - "service de connectivité de données métiers (développement SharePoint dans Visual Studio), ajouter des entités"
  - "service de connectivité de données métiers (développement SharePoint dans Visual Studio), ajouter des instances d'entité"
  - "service de connectivité de données métiers (développement SharePoint dans Visual Studio), créateur"
ms.assetid: 52f0382f-10a0-4a51-83fe-6f22f4647df8
caps.latest.revision: 30
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 29
---
# Comment&#160;: ajouter une m&#233;thode de cr&#233;ation
  Une méthode de création ajoute de nouvelles données à la source de données d'une entité.  Le service de connectivité de données métiers \(BDC, Business Data Connectivity\) appelle cette méthode lorsque les utilisateurs choisissent le bouton **Nouvel élément** sur le ruban d'une liste basée sur le modèle.  Pour plus d'informations, consultez [Conception d'un modèle de connectivité de données métiers](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
### Pour ajouter une méthode de création  
  
1.  Dans le concepteur BDC, sélectionnez une entité.  
  
2.  Dans la barre de menus, cliquez sur **Affichage**, **Autres fenêtres**, **Détails de la méthode BDC**.  
  
     La fenêtre **Détails de méthode BDC** s'ouvre.  Pour plus d'informations sur cette fenêtre, consultez [Vue d'ensemble des outils de conception du modèle BDC](../sharepoint/bdc-model-design-tools-overview.md).  
  
3.  Dans la liste **Ajouter une méthode**, choisissez **Créer une méthode de créateur**.  
  
     Visual Studio ajoute les éléments suivants au modèle, et ces éléments apparaissent dans la fenêtre **Détails de méthode BDC**.  
  
    -   Méthode nommée **Create**  
  
    -   Paramètre d'entrée pour la méthode  
  
    -   Paramètre de retour pour la méthode  
  
    -   Type de descripteur des paramètres.  
  
    -   Instance de méthode pour la méthode  
  
     Pour plus d'informations, consultez [Conception d'un modèle de connectivité de données métiers](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
4.  Dans l'**Explorateur de solutions**, ouvrez le menu raccourci du fichier de code de service qui a été généré pour l'entité, puis cliquez sur **Afficher le code**.  
  
     Le fichier de code de service de l'entité s'ouvre dans l'éditeur de code.  Pour plus d'informations sur le fichier de code de service de l'entité, consultez [Création d'un modèle de connectivité de données métiers](../sharepoint/creating-a-business-data-connectivity-model.md).  
  
5.  Ajoutez du code à la méthode de création qui ajoute des données à la source de données.  L'exemple suivant ajoute un nouveau contact à l'exemple de base de données AdventureWorks pour SQL Server.  
  
    > [!NOTE]  
    >  Remplacez la valeur du champ `ServerName` par le nom de votre serveur.  
  
     [!code-csharp[SP_BDC#4](../snippets/csharp/VS_Snippets_OfficeSP/sp_bdc/CS/bdcmodel1/contactservice.cs#4)]
     [!code-vb[SP_BDC#4](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_bdc/VB/bdcmodel1/contactservice.vb#4)]  
  
## Voir aussi  
 [Conception d'un modèle de connectivité de données métiers](../sharepoint/designing-a-business-data-connectivity-model.md)   
 [Comment : ajouter une méthode de recherche](../sharepoint/how-to-add-a-finder-method.md)   
 [Comment : ajouter une méthode de recherche spécifique](../sharepoint/how-to-add-a-specific-finder-method.md)   
 [Comment : ajouter une méthode de suppression](../sharepoint/how-to-add-a-deleter-method.md)   
 [Comment : ajouter une méthode de mise à jour](../sharepoint/how-to-add-an-updater-method.md)   
 [Vue d'ensemble des outils de conception du modèle BDC](../sharepoint/bdc-model-design-tools-overview.md)   
 [Comment : ajouter un paramètre à une méthode](../sharepoint/how-to-add-a-parameter-to-a-method.md)   
 [Comment : définir une instance de méthode](../sharepoint/how-to-define-a-method-instance.md)  
  
  