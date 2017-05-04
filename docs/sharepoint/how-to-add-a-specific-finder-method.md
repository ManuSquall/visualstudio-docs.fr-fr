---
title: "Comment&#160;: ajouter une m&#233;thode de recherche sp&#233;cifique | Microsoft Docs"
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
  - "BDC (développement SharePoint dans Visual Studio), obtenir une entité"
  - "BDC (développement SharePoint dans Visual Studio), retourner une entité"
  - "BDC (développement SharePoint dans Visual Studio), recherche spécifique"
  - "service de connectivité de données métiers (développement SharePoint dans Visual Studio), obtenir une entité"
  - "service de connectivité de données métiers (développement SharePoint dans Visual Studio), retourner une entité"
  - "service de connectivité de données métiers (développement SharePoint dans Visual Studio), recherche spécifique"
ms.assetid: 7bbc5986-2828-4755-96fa-9f1dc0f8dc75
caps.latest.revision: 30
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 29
---
# Comment&#160;: ajouter une m&#233;thode de recherche sp&#233;cifique
  Vous pouvez retourner une seule instance d'entité en créant une méthode de *recherche spécifique*.  Le service de connectivité de données métiers \(BDC, Business Data Connectivity\) exécute la méthode de recherche spécifique lorsqu'un utilisateur sélectionne une entité dans un composant WebPart de données métiers ou une liste externe.  Pour plus d'informations, consultez [Conception d'un modèle de connectivité de données métiers](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
### Pour créer une méthode de recherche spécifique  
  
1.  Dans le concepteur BDC, sélectionnez une entité.  
  
     Pour plus d'informations sur l'ajout d'une entité au concepteur BDC dans Visual Studio, consultez [Comment : ajouter une entité à un modèle](../sharepoint/how-to-add-an-entity-to-a-model.md).  
  
2.  Dans la barre de menus, cliquez sur **Affichage**, **Autres fenêtres**, **Détails de la méthode BDC**.  
  
     La fenêtre **Détails de méthode BDC** s'ouvre.  Pour plus d'informations sur cette fenêtre, consultez [Vue d'ensemble des outils de conception du modèle BDC](../sharepoint/bdc-model-design-tools-overview.md).  
  
3.  Dans la liste **Ajouter une méthode**, choisissez **Créer une méthode de recherche spécifique**.  
  
     Visual Studio ajoute les éléments suivants au modèle.  Ces éléments apparaissent dans la fenêtre **Détails de méthode BDC**.  
  
    -   Méthode  
  
    -   Paramètre d'entrée pour la méthode  
  
    -   Paramètre de retour pour la méthode  
  
    -   Descripteur de type pour chaque paramètre  
  
    -   Instance de méthode pour la méthode  
  
     Pour plus d'informations, consultez [Conception d'un modèle de connectivité de données métiers](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
4.  Ouvrez la fenêtre **Propriétés** de Visual Studio.  
  
5.  Configurez le descripteur de type du paramètre de retour en tant que descripteur de type entité.  Pour obtenir des informations sur la création d'un descripteur de type entité, consultez [How to: Define the Type Descriptor of a Parameter](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md).  
  
    > [!NOTE]  
    >  Vous n'avez pas à effectuer cette étape si vous avez ajouté une méthode de recherche à l'entité.  Visual Studio utilise le descripteur de type que vous avez défini dans la méthode de recherche.  
  
    > [!NOTE]  
    >  Si le champ d'identificateur du type d'entité représente un champ d'une table de base de données générée automatiquement, affectez à la propriété **Lecture seule** du champ d'identificateur la valeur **True**.  
  
6.  Dans la fenêtre **Détails de méthode**, sélectionnez l'instance de méthode de la méthode.  
  
7.  Dans **Fenêtre Propriétés**, affectez le nom du paramètre de retour de la méthode à la propriété **Nom du paramètre de retour**.  Pour plus d'informations sur les propriétés d'une instance de méthode, consultez [MethodInstance](http://go.microsoft.com/fwlink/?LinkID=169282).  
  
8.  Dans l'**Explorateur de solutions**, ouvrez le menu raccourci du fichier de code de service qui a été généré pour l'entité, puis cliquez sur **Afficher le code**.  
  
     Le fichier de code de service de l'entité s'ouvre dans l'éditeur de code.  Pour plus d'informations sur le fichier de code de service de l'entité, consultez [Création d'un modèle de connectivité de données métiers](../sharepoint/creating-a-business-data-connectivity-model.md).  
  
9. Ajoutez du code à la méthode de recherche spécifique.  Ce code exécute les tâches suivantes :  
  
    -   Il récupère un enregistrement à partir d'une source de données.  
  
    -   Il retourne une entité au service BDC.  
  
     L'exemple suivant retourne un contact à partir de l'exemple de base de données AdventureWorks pour SQL Server.  
  
    > [!NOTE]  
    >  Remplacez la valeur du champ `ServerName` par le nom de votre serveur.  
  
     [!code-csharp[SP_BDC#3](../snippets/csharp/VS_Snippets_OfficeSP/sp_bdc/CS/bdcmodel1/contactservice.cs#3)]
     [!code-vb[SP_BDC#3](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_bdc/VB/bdcmodel1/contactservice.vb#3)]  
  
## Voir aussi  
 [Conception d'un modèle de connectivité de données métiers](../sharepoint/designing-a-business-data-connectivity-model.md)   
 [Comment : ajouter une méthode de recherche](../sharepoint/how-to-add-a-finder-method.md)   
 [Comment : ajouter une méthode de création](../sharepoint/how-to-add-a-creator-method.md)   
 [Comment : ajouter une méthode de suppression](../sharepoint/how-to-add-a-deleter-method.md)   
 [Comment : ajouter une méthode de mise à jour](../sharepoint/how-to-add-an-updater-method.md)   
 [Vue d'ensemble des outils de conception du modèle BDC](../sharepoint/bdc-model-design-tools-overview.md)   
 [Comment : ajouter un paramètre à une méthode](../sharepoint/how-to-add-a-parameter-to-a-method.md)   
 [Comment : définir une instance de méthode](../sharepoint/how-to-define-a-method-instance.md)  
  
  