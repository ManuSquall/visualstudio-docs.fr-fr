---
title: "Comment&#160;: ajouter et supprimer des d&#233;pendances de fonctionnalit&#233;s | Microsoft Docs"
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
  - "MICROSOFT.VISUALSTUDIO.SHAREPOINT.DESIGNERS.CUSTOMDEPENDENCYWINDOW"
  - "VS.SHAREPOINTTOOLS.RAD.FEATUREDESIGNERDEPENDENCY"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "développement SharePoint dans Visual Studio, fonctionnalités"
ms.assetid: 2b34c8d9-c975-4fe9-b8e0-52db4a6014ea
caps.latest.revision: 13
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 13
---
# Comment&#160;: ajouter et supprimer des d&#233;pendances de fonctionnalit&#233;s
  Votre fonctionnalité SharePoint peut dépendre d'autres fonctionnalités en matière de fonctionnalités ou de données.  Dans ces cas, vous pouvez marquer ces fonctionnalités comme dépendances pour votre fonctionnalité.  Le serveur SharePoint pourra ainsi s'assurer que les fonctionnalités dépendantes sont activées avant votre fonctionnalité.  
  
## Ajout de dépendances  
 Vous pouvez ajouter d'autres fonctionnalités dans votre solution sous forme de dépendances.  Vous aurez ainsi la garantie que les fonctionnalités obligatoires sont installées et activées avant que votre fonctionnalité soit installée.  
  
#### Pour ajouter une dépendance à une fonctionnalité dans la solution  
  
1.  Ouvrez le concepteur de composant, développez le nœud **Dépendances d'activation de composants**, puis choisissez le bouton **Ajouter**.  
  
2.  Dans la boîte de dialogue **Ajouter des dépendances d'activation de composant**, sélectionnez la bouton d'option **Ajouter une dépendance aux composants dans la solution**, choisissez le titre du composant à ajouter en tant que dépendance, puis cliquez sur le bouton **Ajouter**.  
  
     Ajoutez plusieurs composants en choisissant plusieurs titres tout en appuyant sur la touche Ctrl.  
  
## Ajout de dépendances personnalisées  
 Vous pouvez ajouter des fonctionnalités déjà déployées sur un serveur SharePoint en tant que dépendance.  Le processus d'activation SharePoint pourra ainsi s'assurer que toutes les fonctionnalités dépendantes sont activées avant que votre fonctionnalité soit installée.  
  
#### Pour ajouter une dépendance par l'ID de Fonctionnalité  
  
1.  Ouvrez le concepteur de composant, développez le nœud **Dépendances d'activation de composants**, puis choisissez le bouton **Ajouter**.  
  
2.  Dans la boîte de dialogue **Ajouter des dépendances d'activation de composant**, sélectionnez le bouton d'option **Ajouter une dépendance personnalisée**.  
  
3.  Dans la zone de texte **ID de composant**, entrez le GUID du composant que vous souhaitez marquer comme une dépendance d'activation, et cliquez sur le bouton **Ajouter**.  
  
## Modification de dépendances personnalisées  
 Vous pouvez modifier des dépendances personnalisées que vous avez ajoutées précédemment.  En revanche, les fonctionnalités dépendantes faisant partie de votre solution peuvent uniquement être supprimées, mais pas modifiées.  
  
#### Pour modifier une dépendance d'une fonctionnalité dans la solution  
  
1.  Ouvrez le concepteur de composant, puis développez le nœud **Dépendances d'activation de composant**.  
  
2.  Sélectionnez le nom du composant à modifier, puis cliquez sur le bouton **Modifier**.  
  
3.  Dans la boîte de dialogue **Modifier la dépendance d'activation de composant personnalisé**, remplacez le titre, l'ID du composant ou la description, puis cliquez sur le bouton **Envoyer**.  
  
## Suppression de dépendances  
  
#### Pour retirer la dépendance d'une fonctionnalité dans la solution  
  
1.  Dans le concepteur de composant, développez le nœud **Dépendances d'activation de composant**, sélectionnez le nom du composant à supprimer, puis cliquez sur le bouton **Supprimer**.  
  
## Voir aussi  
 [Création de fonctionnalités SharePoint](../sharepoint/creating-sharepoint-features.md)   
 [Comment : personnaliser une fonctionnalité SharePoint](../sharepoint/how-to-customize-a-sharepoint-feature.md)   
 [Comment : ajouter et supprimer des éléments dans des fonctionnalités SharePoint](../sharepoint/how-to-add-and-remove-items-to-sharepoint-features.md)  
  
  