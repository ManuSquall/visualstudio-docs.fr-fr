---
title: "Comment&#160;: cr&#233;er un mod&#232;le BDC | Microsoft Docs"
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
ms.assetid: e8b888d4-a531-4d13-9ebf-efbbd33eebc6
caps.latest.revision: 15
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 14
---
# Comment&#160;: cr&#233;er un mod&#232;le BDC
  Vous pouvez créer un modèle BDC \(Business Data Connectivity\) en utilisant le modèle pour ce type d'élément et en l'ajoutant à un projet SharePoint.  Pour plus d'informations, consultez [Création d'un modèle de connectivité de données métiers](../sharepoint/creating-a-business-data-connectivity-model.md).  Pour plus d'informations sur la conception du modèle, consultez [Conception d'un modèle de connectivité de données métiers](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
### Pour créer un projet BDC  
  
1.  Dans la barre de menus, sélectionnez **Fichier**, **Nouveau**, **Projet**.  
  
    > [!NOTE]  
    >  Si votre interface IDE est définie pour utiliser les paramètres de développement Visual Basic, choisissez **Fichier**, **Nouveau projet**.  
  
     La boîte de dialogue **Nouveau projet** s'affiche.  
  
2.  Sous **Visual Basic** ou **Visual C\#**, sélectionnez **Office\/SharePoint**, **Solutions SharePoint**.  
  
3.  Dans le volet **Modèles**, sélectionnez l'élément **SharePoint 2013 – Projet vide**, puis choisissez le bouton **OK**.  
  
     L'**Assistant Personnalisation de SharePoint** s'affiche.  
  
4.  Sur la page **Spécifier le site et le niveau de sécurité pour le débogage**, spécifiez l'URL d'un site SharePoint sur l'ordinateur local, sélectionnez la case d'option **Déploiement comme une solution de batterie**, puis choisissez le bouton **Terminer**.  
  
     Vous testerez le modèle sur le site SharePoint que vous avez spécifié.  
  
    > [!IMPORTANT]  
    >  Vous devez déployer le projet en tant que solution de batterie, car les modèles BDC prennent en charge uniquement les solutions de batterie.  
  
     Un projet SharePoint vide est créé.  
  
5.  Dans la barre de menus, choisissez **Projet**, **Ajouter un nouvel élément**.  
  
6.  Dans la boîte de dialogue **Ajouter un nouvel élément**, choisissez le nœud **Office\/SharePoint**.  
  
7.  Dans la liste de modèles SharePoint, sélectionnez **Modèle de connectivité de données métiers \(solution de batterie uniquement\)**.  
  
8.  Dans la zone **Nom**, indiquez un nom pour le modèle BDC, puis choisissez le bouton **Ajouter**.  
  
     Un élément **Modèle de connectivité de données métiers** est ajouté au projet.  Par défaut, le modèle s'affiche dans le concepteur BDC.  Pour plus d'informations, consultez [Création d'un modèle de connectivité de données métiers](../sharepoint/creating-a-business-data-connectivity-model.md).  
  
## Voir aussi  
 [Création d'un modèle de connectivité de données métiers](../sharepoint/creating-a-business-data-connectivity-model.md)   
 [Comment : ajouter un fichier de modèle BDC existant à un projet SharePoint](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md)   
 [Comment : utiliser un fichier de ressources pour spécifier des noms localisés, propriétés et autorisations](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)   
 [Comment : inclure un assembly personnalisé dans une fonctionnalité BDC](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md)   
 [Intégration de données métiers dans SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)  
  
  