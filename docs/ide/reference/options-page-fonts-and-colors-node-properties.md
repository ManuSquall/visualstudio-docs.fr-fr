---
title: "Page Options, Polices et couleurs, propri&#233;t&#233;s de nœud | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Options d’outils (paramètres), propriétés de nœud Polices et couleurs"
  - "automation (Visual Studio), contrôle de la boîte de dialogue Options du menu Outils"
ms.assetid: 8e1ab784-5f85-4e2b-8ef9-e5d59ca4dbcb
caps.latest.revision: 8
caps.handback.revision: 8
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Page Options, Polices et couleurs, propri&#233;t&#233;s de nœud
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Ce document décrit les propriétés de police et de couleur pour une fenêtre Outil qui est inscrite pour apparaître sous **Polices et couleurs** dans la catégorie **Environnement** de la boîte de dialogue **Options**.  Ce procédé prend en charge la nature dynamique des groupes d'éléments qui autorisent la modification de la couleur, qui peut être modifiée si des VSPackages sont installés ou désinstallés.  
  
 La section suivante montre un exemple de type de fenêtres inscrites, ainsi que les propriétés disponibles pour chaque fenêtre.  
  
## Éditeur de texte ou Imprimante ou Boîtes de dialogue et Fenêtres Outil  
 `DTE.Properties("FontsAndColors", "TextEditor")`  
  
 ou  
  
 `DTE.Properties("FontsAndColors", "Printer")`  
  
 ou  
  
 `DTE.Properties("FontsAndColors", "Dialogs and Tool Windows")`  
  
|Nom de l'élément de propriété|Valeur|Description|  
|-----------------------------------|------------|-----------------|  
|FontFamily|Get\/Set \(String\)|Le nom de police à utiliser, tel que « Courier New ».|  
|FontCharacterSet|Get\/Set \(<xref:EnvDTE.vsFontCharSet>\)|Une valeur <xref:EnvDTE.vsFontCharSet>, qui spécifie le type du jeu de caractères à utiliser, tel que Hébreu ou Russe.|  
|FontSize|Get\/Set \(Short\)|La taille de police utiliser, en points.  Par exemple, 10 ou 12.|  
  
## Voir aussi  
 [Contrôle des paramètres de la boîte de dialogue Options](../Topic/Controlling%20Options%20Settings.md)   
 [Détermination des noms d'éléments de propriété dans les pages Options](../Topic/Determining%20the%20Names%20of%20Property%20Items%20on%20Options%20Pages.md)   
 [Page Options, Environnement, propriétés de nœud](../../ide/reference/options-page-environment-node-properties.md)   
 [Page Options, Éditeur de texte, propriétés de nœud](../../ide/reference/options-page-text-editor-node-properties.md)