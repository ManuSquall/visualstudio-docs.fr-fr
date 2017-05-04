---
title: "Comment&#160;: ajouter une m&#233;thode de recherche | Microsoft Docs"
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
  - "BDC (développement SharePoint dans Visual Studio), Finder (méthode)"
  - "BDC (développement SharePoint dans Visual Studio), obtenir des entités"
  - "BDC (développement SharePoint dans Visual Studio), retourner des entités"
  - "service de connectivité de données métiers (développement SharePoint dans Visual Studio), Finder (méthode)"
  - "service de connectivité de données métiers (développement SharePoint dans Visual Studio), obtenir des entités"
  - "service de connectivité de données métiers (développement SharePoint dans Visual Studio), retourner des entités"
ms.assetid: 5de2cae3-d1f7-4a68-aac0-458967aca692
caps.latest.revision: 25
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 25
---
# Comment&#160;: ajouter une m&#233;thode de recherche
  Pour permettre au service de connectivité de données métiers \(BDC, Business Data Connectivity\) d'afficher une liste d'entités dans une liste ou un composant webPart, vous devez créer une méthode de *recherche*.  Une méthode de recherche est une méthode spéciale qui retourne une collection d'instances d'entité.  Pour plus d'informations, consultez [Conception d'un modèle de connectivité de données métiers](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
### Pour créer une méthode de recherche  
  
1.  Dans le concepteur BDC, sélectionnez une entité.  
  
     Pour plus d'informations, consultez [Comment : ajouter une entité à un modèle](../sharepoint/how-to-add-an-entity-to-a-model.md).  
  
2.  Dans la barre de menus, cliquez sur **Affichage**, **Autres fenêtres**, **Détails de la méthode BDC**.  
  
     La fenêtre **Détails de méthode BDC** s'ouvre.  Pour plus d'informations sur la fenêtre **Détails de méthode BDC**, consultez [Vue d'ensemble des outils de conception du modèle BDC](../sharepoint/bdc-model-design-tools-overview.md).  
  
3.  Dans la liste **Ajouter une méthode**, choisissez **Créer une méthode de recherche**.  
  
     Visual Studio ajoute une méthode, un paramètre de retour et un descripteur de type.  
  
4.  Configurez le descripteur de type en tant que collection d'entités.  Pour plus d'informations sur la création d'un descripteur de type de collection d'entités, consultez [How to: Define the Type Descriptor of a Parameter](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md).  
  
    > [!NOTE]  
    >  Vous n'avez pas à effectuer cette étape si vous avez ajouté une méthode de recherche spécifique à l'entité.  Visual Studio utilise le descripteur de type que vous avez défini dans la méthode de recherche spécifique.  
  
5.  Dans l'**Explorateur de solutions**, ouvrez le menu raccourci du fichier de code de service qui a été généré pour l'entité, puis cliquez sur **Afficher le code**.  Pour plus d'informations sur le fichier de code de service, consultez [Création d'un modèle de connectivité de données métiers](../sharepoint/creating-a-business-data-connectivity-model.md).  
  
6.  Ajoutez du code à la méthode de recherche.  Ce code exécute les tâches suivantes :  
  
    -   Récupère des données dans une source de données.  
  
    -   Retourne une liste d'entités au service BDC.  
  
     L'exemple suivant retourne une collection d'entités `Contact` à partir des données de l'exemple de base de données AdventureWorks pour SQL Server.  
  
    > [!NOTE]  
    >  Remplacez la valeur du champ `ServerName` par le nom de votre serveur.  
  
     [!code-csharp[SP_BDC#2](../snippets/csharp/VS_Snippets_OfficeSP/sp_bdc/CS/bdcmodel1/contactservice.cs#2)]
     [!code-vb[SP_BDC#2](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_bdc/VB/bdcmodel1/contactservice.vb#2)]  
  
## Voir aussi  
 [Vue d'ensemble des outils de conception du modèle BDC](../sharepoint/bdc-model-design-tools-overview.md)   
 [Conception d'un modèle de connectivité de données métiers](../sharepoint/designing-a-business-data-connectivity-model.md)   
 [Comment : ajouter une méthode de recherche spécifique](../sharepoint/how-to-add-a-specific-finder-method.md)   
 [Comment : ajouter une méthode de création](../sharepoint/how-to-add-a-creator-method.md)   
 [Comment : ajouter une méthode de suppression](../sharepoint/how-to-add-a-deleter-method.md)   
 [Comment : ajouter une méthode de mise à jour](../sharepoint/how-to-add-an-updater-method.md)   
 [Comment : ajouter un paramètre à une méthode](../sharepoint/how-to-add-a-parameter-to-a-method.md)   
 [Comment : définir une instance de méthode](../sharepoint/how-to-define-a-method-instance.md)  
  
  