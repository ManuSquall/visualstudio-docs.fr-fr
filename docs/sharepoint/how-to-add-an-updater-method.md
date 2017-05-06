---
title: "Comment&#160;: ajouter une m&#233;thode de mise &#224; jour"
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
  - "BDC (développement SharePoint dans Visual Studio), programme de mise à jour"
  - "BDC (développement SharePoint dans Visual Studio), mise à jour de données"
  - "BDC (développement SharePoint dans Visual Studio), mettre à jour des instances d'entité"
  - "service de connectivité de données métiers (développement SharePoint dans Visual Studio), programme de mise à jour"
  - "service de connectivité de données métiers (développement SharePoint dans Visual Studio), mise à jour de données"
  - "service de connectivité de données métiers (développement SharePoint dans Visual Studio), mettre à jour des instances d'entité"
ms.assetid: c97e443c-58dc-4f8f-8cbd-0d52d8a6a06b
caps.latest.revision: 33
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 32
---
# Comment&#160;: ajouter une m&#233;thode de mise &#224; jour
  Vous pouvez permettre aux utilisateurs de mettre à jour des données métiers dans une liste externe SharePoint en créant une méthode de *mise à jour*.  Pour plus d'informations, consultez [Conception d'un modèle de connectivité de données métiers](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
### Pour créer une méthode de mise à jour  
  
1.  Dans le concepteur BDC, sélectionnez une entité.  
  
2.  Dans la barre de menus, cliquez sur **Affichage**, **Autres fenêtres**, **Détails de la méthode BDC**.  
  
     La fenêtre Détails de méthode BDC s'ouvre.  Pour plus d'informations sur cette fenêtre, consultez [Vue d'ensemble des outils de conception du modèle BDC](../sharepoint/bdc-model-design-tools-overview.md).  
  
3.  Dans la liste **Ajouter une méthode**, choisissez **Créer une méthode de mise à jour**.  
  
     Visual Studio ajoute les éléments suivants au modèle.  Ces éléments apparaissent dans la fenêtre Détails de méthode BDC.  
  
    -   Une méthode nommée **Mettre à jour**.  
  
    -   Paramètre d'entrée pour la méthode  
  
    -   Descripteur de type du paramètre  Par défaut, Visual Studio utilise le descripteur de type d'entité que vous avez défini pour la méthode de recherche \(par exemple : Contact\).  
  
    -   Instance de méthode pour la méthode  
  
     Pour plus d'informations, consultez [Conception d'un modèle de connectivité de données métiers](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
    > [!NOTE]  
    >  Si l'identificateur du type d'entité représente un champ d'une table de base de données qui n'est pas générée automatiquement, affectez la valeur **True** à la propriété **Champ de pré\-mise à jour**.  
  
4.  Dans l'**Explorateur de solutions**, ouvrez le menu raccourci du fichier de code de service qui a été généré pour l'entité, puis cliquez sur **Afficher le code**.  
  
     Le fichier de code de service de l'entité s'ouvre dans l'éditeur de code.  Pour plus d'informations sur ce fichier, consultez [Création d'un modèle de connectivité de données métiers](../sharepoint/creating-a-business-data-connectivity-model.md).  
  
5.  Ajoutez du code à la méthode Update pour mettre à jour les données.  L'exemple suivant met à jour les informations d'un contact dans l'exemple de base de données AdventureWorks pour SQL Server.  
  
    > [!NOTE]  
    >  Remplacez la valeur du champ `ServerName` par le nom de votre serveur.  
  
     [!code-csharp[SP_BDC#5](../snippets/csharp/VS_Snippets_OfficeSP/sp_bdc/CS/bdcmodel1/contactservice.cs#5)]
     [!code-vb[SP_BDC#5](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_bdc/VB/bdcmodel1/contactservice.vb#5)]  
  
## Voir aussi  
 [Conception d'un modèle de connectivité de données métiers](../sharepoint/designing-a-business-data-connectivity-model.md)   
 [Comment : ajouter une méthode de recherche](../sharepoint/how-to-add-a-finder-method.md)   
 [Comment : ajouter une méthode de recherche spécifique](../sharepoint/how-to-add-a-specific-finder-method.md)   
 [Comment : ajouter une méthode de création](../sharepoint/how-to-add-a-creator-method.md)   
 [How to: Add an Updater Method](../sharepoint/how-to-add-an-updater-method.md)   
 [Comment : ajouter une méthode de suppression](../sharepoint/how-to-add-a-deleter-method.md)   
 [Vue d'ensemble des outils de conception du modèle BDC](../sharepoint/bdc-model-design-tools-overview.md)   
 [Comment : ajouter un paramètre à une méthode](../sharepoint/how-to-add-a-parameter-to-a-method.md)   
 [Comment : définir une instance de méthode](../sharepoint/how-to-define-a-method-instance.md)  
  
  