---
title: "Vue d&#39;ensemble des outils de conception du mod&#232;le BDC | Microsoft Docs"
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
  - "VS.SharePointTools.BDC.Method_Details"
  - "VS.SharePointTools.BDC.Explorer"
  - "VS.SharePointTools.BDC.Diagram"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "BDC (développement SharePoint dans Visual Studio), explorateur BDC"
  - "BDC (développement SharePoint dans Visual Studio), concepteur"
  - "BDC (développement SharePoint dans Visual Studio), détails de méthode"
  - "BDC (développement SharePoint dans Visual Studio), Visual Tools"
  - "service de connectivité de données métiers (développement SharePoint dans Visual Studio), explorateur BDC"
  - "service de connectivité de données métiers (développement SharePoint dans Visual Studio), concepteur"
  - "service de connectivité de données métiers (développement SharePoint dans Visual Studio), détails de méthode"
  - "service de connectivité de données métiers (développement SharePoint dans Visual Studio), Visual Tools"
ms.assetid: dbd7b746-9e93-4ed4-a546-4a6f17a4725f
caps.latest.revision: 16
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 15
---
# Vue d&#39;ensemble des outils de conception du mod&#232;le BDC
  Vous pouvez concevoir un modèle de connectivité de données métiers \(BDC, Business Data Connectivity\) à l'aide du concepteur BDC, de la fenêtre **Détails de méthode BDC** et de l'**Explorateur BDC**.  
  
 L'**Explorateur BDC** vous permet de parcourir le modèle, de rechercher le modèle et de définir des descripteurs de type.  
  
## Concepteur BDC  
 Le concepteur BDC vous permet de définir les entités de votre modèle et de réorganiser visuellement leurs relations les unes avec les autres.  Vous pouvez utiliser le concepteur BDC pour effectuer les tâches suivantes :  
  
-   ajouter des entités au modèle ;  
  
-   supprimer des entités du modèle ;  
  
-   définir des relations entre les entités.  
  
 Pour ouvrir le BDC Designer, double\-cliquez sur le fichier de modèle de votre projet, ou ouvrez le menu contextuel du fichier de modèle et choisissez **Ouvrir**.  Ajoutez une entité au modèle en faisant glisser ou en copiant une **Entité** de la **Boîte à outils** sur le concepteur.  Pour créer une association entre deux entités, cliquez sur la contrôle**Association** dans la **Boîte à outils**, puis cliquez sur la première entité et sur la deuxième entité.  
  
## Fenêtre Détails de méthode BDC  
 Utilisez la fenêtre **Détails de méthode BDC** pour définir les paramètres, les instances et les descripteurs de filtre d'une méthode.  
  
 Vous pouvez générer rapidement des méthodes de recherche, de recherche spécifique, de création, de mise à jour et de suppression dans la fenêtre **Détails de méthode BDC**.  Lorsque vous générez ces méthodes, Visual Studio ajoute des métadonnées, telles que des paramètres, des instances et des descripteurs de type, à la méthode.  Vous pouvez modifier ces métadonnées de manière à les adapter à votre scénario spécifique.  
  
 Pour ouvrir la fenêtre **Détails de méthode BDC**, dans la barre de menu cliquez sur **Affichage**, puis sur **Autres fenêtres** et sur **Détails de méthode BDC**.  
  
 Pour afficher les méthodes dans la fenêtre **Détails de méthode BDC**, sélectionnez l'entité dans le concepteur BDC.  Les méthodes de l'entité sélectionnée s'affichent dans la fenêtre **Détails de méthode BDC**.  Si vous ne sélectionnez pas d'entité dans le concepteur BDC, la fenêtre **Détails de méthode BDC** n'affiche aucune information.  
  
 Développez ou réduisez des nœuds dans la fenêtre **Détails de méthode BDC** pour définir des paramètres, des instances et des descripteurs de filtre.  Vous pouvez utiliser l'**Explorateur BDC** pour définir des descripteurs de type.  
  
## Explorateur BDC  
 L'**Explorateur BDC** affiche les éléments qui composent le modèle.  Pour ouvrir l'**Explorateur BDC**, dans la barre de menus, cliquez sur **Affichage**, **Autres fenêtres**, **Explorateur BDC**.  Pour parcourir le modèle, développez des nœuds dans l'**Explorateur BDC**.  Chaque nœud représente un élément dans le code XML du fichier de modèle.  
  
 Lorsque vous sélectionnez des nœuds dans l'**Explorateur BDC**, les propriétés de chaque noeud choisi s'affichent dans la fenêtre **Propriétés**.  Ces propriétés correspondent pour la plupart aux attributs qui se trouvent dans le fichier de modèle.  Vous pouvez rechercher le modèle à l'aide de la zone de recherche située en haut de l'**Explorateur BDC**.  
  
> [!NOTE]  
>  L'**Explorateur BDC** n'affiche pas les identificateurs, les propriétés personnalisées, les chaînes localisées, les groupes d'association, les actions, les descripteurs de filtre, les listes de contrôle d'action ni les valeurs de paramètre par défaut.  
  
### Définition de descripteurs de type  
 Vous pouvez utiliser l'**Explorateur BDC** pour définir des descripteurs de type.  L'Explorateur BDC vous permet de définir un descripteur de type, puis de le réutiliser ailleurs dans votre modèle.  Pour ce faire, copiez un descripteur de type et collez\-le dans tout autre paramètre ou descripteur de type.  
  
> [!NOTE]  
>  Les modifications apportées à un descripteur de type d'origine n'affectent pas les copies de ce descripteur de type.  
  
 Pour plus d'informations, consultez [How to: Define the Type Descriptor of a Parameter](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md).  
  
## Voir aussi  
 [Comment : créer un modèle BDC](../sharepoint/how-to-create-a-bdc-model.md)   
 [Comment : ajouter une entité à un modèle](../sharepoint/how-to-add-an-entity-to-a-model.md)   
 [Comment : ajouter une méthode de recherche](../sharepoint/how-to-add-a-finder-method.md)   
 [Comment : ajouter une méthode de recherche spécifique](../sharepoint/how-to-add-a-specific-finder-method.md)   
 [Comment : ajouter une méthode de création](../sharepoint/how-to-add-a-creator-method.md)   
 [Comment : ajouter une méthode de suppression](../sharepoint/how-to-add-a-deleter-method.md)   
 [Comment : ajouter une méthode de mise à jour](../sharepoint/how-to-add-an-updater-method.md)   
 [Création d'une association entre des entités](../sharepoint/creating-an-association-between-entities.md)   
 [Procédure pas à pas : création d'une liste externe dans SharePoint à l'aide de données métiers](../sharepoint/walkthrough-creating-an-external-list-in-sharepoint-by-using-business-data.md)   
 [Intégration de données métiers dans SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)   
 [Création d'un modèle de connectivité de données métiers](../sharepoint/creating-a-business-data-connectivity-model.md)   
 [Conception d'un modèle de connectivité de données métiers](../sharepoint/designing-a-business-data-connectivity-model.md)  
  
  