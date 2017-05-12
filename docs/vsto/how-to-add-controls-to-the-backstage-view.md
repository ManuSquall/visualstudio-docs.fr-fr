---
title: "Comment&#160;: ajouter des contr&#244;les au mode Backstage"
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
helpviewer_keywords: 
  - "contrôles, ruban"
  - "ruban personnalisé, menus"
  - "personnaliser le ruban, menus"
  - "menus, personnaliser"
  - "Microsoft Office (bouton)"
  - "Microsoft Office (menu)"
  - "Office (bouton)"
  - "ruban, personnaliser"
  - "ruban, menus"
ms.assetid: 4fda1278-9aea-4d54-928a-269a81584494
caps.latest.revision: 30
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 29
---
# Comment&#160;: ajouter des contr&#244;les au mode Backstage
  Vous pouvez utiliser le concepteur de ruban pour ajouter des contrôles au menu qui s'ouvre lorsque vous cliquez sur **Fichier** tableau.  lorsque vous exécutez l'application, les contrôles que vous ajoutez à l'onglet **Fichier** apparaissent un groupe nommé **Compléments**.  
  
 Vous ne pouvez pas positionner des contrôles avant ou après les contrôles prédéfinis à l'aide de le concepteur de ruban de Visual Studio.  Un contrôle intégré est un contrôle qui figure déjà en mode Backstage.  Si vous souhaitez positionner des contrôles avant ou après les contrôles prédéfinis, vous devez utiliser un élément XML Ruban.  Pour plus d'informations sur **Ruban \(XML\)**, consultez [Élément XML Ribbon](../vsto/ribbon-xml.md).  Pour plus d'informations sur la personnalisation du mode Backstage, consultez [Introduction au mode Backstage Office 2010 pour les développeurs \(page éventuellement en anglais\)](http://go.microsoft.com/fwlink/?LinkId=182189) et [Personnalisation du mode Backstage Office 2010 pour les développeurs \(page éventuellement en anglais\)](http://go.microsoft.com/fwlink/?LinkId=182188).  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
### Pour ajouter des contrôles au mode Backstage  
  
1.  Ouvrez l'élément Ruban en mode Design.  
  
     Pour plus d'informations sur l'ajout d'un élément **Ruban \(Concepteur visuel\)** à votre projet, consultez [Comment : démarrer avec la personnalisation du ruban](../vsto/how-to-get-started-customizing-the-ribbon.md).  
  
2.  Dans le concepteur de ruban, cliquez sur **Fichier** tableau.  
  
     Un Concepteur de menus s'affiche.  Cette aire de conception ne contient pas de contrôles.  
  
3.  Depuis l'onglet **Contrôles de ruban Office** de la **Boîte à outils**, faites glisser l'un des contrôles suivants vers le Concepteur de menus :  
  
    -   Button  
  
    -   CheckBox  
  
    -   Gallery  
  
    -   Menu  
  
    -   Separator  
  
    -   SplitButton  
  
    -   ToggleButton  
  
4.  Faites glisser les contrôles jusqu'à leur nouvelle position dans le menu.  
  
## Voir aussi  
 [Vue d'ensemble du ruban](../vsto/ribbon-overview.md)   
 [Concepteur de ruban](../vsto/ribbon-designer.md)   
 [Élément XML Ribbon](../vsto/ribbon-xml.md)   
 [Comment : démarrer avec la personnalisation du ruban](../vsto/how-to-get-started-customizing-the-ribbon.md)   
 [Procédure pas à pas : création d'un onglet personnalisé à l'aide du Concepteur de ruban](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)  
  
  