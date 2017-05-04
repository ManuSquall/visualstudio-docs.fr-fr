---
title: "Comment&#160;: ajouter une m&#233;thode de suppression | Microsoft Docs"
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
  - "BDC (développement SharePoint dans Visual Studio), programme de suppression"
  - "BDC (développement SharePoint dans Visual Studio), supprimer des données"
  - "BDC (développement SharePoint dans Visual Studio), supprimer des instances d'entité"
  - "BDC (développement SharePoint dans Visual Studio), supprimer des données"
  - "service de connectivité de données métiers (développement SharePoint dans Visual Studio), programme de suppression"
  - "service de connectivité de données métiers (développement SharePoint dans Visual Studio), supprimer des données"
  - "service de connectivité de données métiers (développement SharePoint dans Visual Studio), supprimer des instances d'entité"
  - "service de connectivité de données métiers (développement SharePoint dans Visual Studio), supprimer des données"
ms.assetid: 3362eaf4-5dc7-4450-9009-b296308ae61f
caps.latest.revision: 21
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 21
---
# Comment&#160;: ajouter une m&#233;thode de suppression
  Vous pouvez permettre à un utilisateur final de supprimer un enregistrement de données dans une liste externe sur un site SharePoint en ajoutant une méthode de *suppression* au modèle.  Pour plus d'informations, consultez [Conception d'un modèle de connectivité de données métiers](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
### Pour créer une méthode de suppression  
  
1.  Dans le concepteur BDC, sélectionnez une entité.  
  
2.  Dans la barre de menus, cliquez sur **Affichage**, **Autres fenêtres**, **Détails de la méthode BDC**.  
  
     La fenêtre **Détails de méthode BDC** s'ouvre.  Pour plus d'informations sur cette fenêtre, consultez [Vue d'ensemble des outils de conception du modèle BDC](../sharepoint/bdc-model-design-tools-overview.md).  
  
3.  Dans la liste **Ajouter une méthode**, choisissez **Créez une méthode Deleter**.  
  
     Visual Studio ajoute les éléments suivants au modèle.  Ces éléments apparaissent dans la fenêtre **Détails de méthode BDC**.  
  
    -   Méthode nommée **Delete**.  
  
    -   Paramètre d'entrée pour la méthode  
  
    -   Descripteur de type du paramètre  
  
    -   Instance de méthode pour la méthode  
  
     Pour plus d'informations, consultez [Conception d'un modèle de connectivité de données métiers](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
4.  Dans l'**Explorateur de solutions**, ouvrez le menu raccourci du fichier de code de service qui a été généré pour l'entité, puis cliquez sur **Afficher le code**.  
  
     Le fichier de code de service de l'entité s'ouvre dans l'éditeur de code.  Pour plus d'informations sur le fichier de code de service de l'entité, consultez [Création d'un modèle de connectivité de données métiers](../sharepoint/creating-a-business-data-connectivity-model.md).  
  
5.  Ajoutez du code à la méthode de suppression pour supprimer un enregistrement.  L'exemple suivant supprime une ligne d'une commande client dans l'exemple de base de données AdventureWorks pour SQL Server.  
  
    > [!NOTE]  
    >  Dans cet exemple, la méthode utilise deux paramètres d'entrée.  
  
    > [!NOTE]  
    >  Remplacez la valeur du champ `ServerName` par le nom de votre serveur.  
  
     [!code-csharp[SP_BDC#6](../snippets/csharp/VS_Snippets_OfficeSP/sp_bdc/CS/bdcmodel1/salesorderdetailservice.cs#6)]
     [!code-vb[SP_BDC#6](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_bdc/VB/bdcmodel1/salesorderdetailservice.vb#6)]  
  
## Voir aussi  
 [Conception d'un modèle de connectivité de données métiers](../sharepoint/designing-a-business-data-connectivity-model.md)   
 [Comment : ajouter une méthode de recherche](../sharepoint/how-to-add-a-finder-method.md)   
 [Comment : ajouter une méthode de recherche spécifique](../sharepoint/how-to-add-a-specific-finder-method.md)   
 [Comment : ajouter une méthode de création](../sharepoint/how-to-add-a-creator-method.md)   
 [Comment : ajouter une méthode de mise à jour](../sharepoint/how-to-add-an-updater-method.md)   
 [Vue d'ensemble des outils de conception du modèle BDC](../sharepoint/bdc-model-design-tools-overview.md)   
 [Comment : ajouter un paramètre à une méthode](../sharepoint/how-to-add-a-parameter-to-a-method.md)   
 [Comment : définir une instance de méthode](../sharepoint/how-to-define-a-method-instance.md)  
  
  