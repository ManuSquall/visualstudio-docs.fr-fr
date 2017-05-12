---
title: "Comment&#160;: cr&#233;er des gestionnaires d&#39;&#233;v&#233;nements dans les projets Office"
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
  - "gestionnaires d'événements (développement Office dans Visual Studio)"
  - "événements (développement Office dans Visual Studio)"
  - "Visual Basic (développement Office dans Visual Studio), gestionnaires d'événements"
  - "Visual C# (développement Office dans Visual Studio), gestionnaires d'événements"
ms.assetid: 2cfd6a45-4c25-4431-b4fc-e0f2c0a72e54
caps.latest.revision: 31
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 30
---
# Comment&#160;: cr&#233;er des gestionnaires d&#39;&#233;v&#233;nements dans les projets Office
  Il existe plusieurs façons de créer des gestionnaires d'événements en Visual Basic et C\#.  En mode Design, vous pouvez créer le gestionnaire d'événements par défaut pour les contrôles en double\-cliquant sur le contrôle ou utiliser le volet d'événements de la fenêtre **Propriétés** afin de créer des gestionnaires pour tout événement sur le contrôle.  Toutefois, si vous êtes en mode Code, vous ne souhaitez peut\-être pas basculer en mode Design pour créer un gestionnaire d'événements.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
### Pour créer un gestionnaire d'événements en Visual Basic  
  
1.  Dans la liste déroulante **Nom de la classe** située en haut de l'éditeur de code, sélectionnez l'objet pour lequel vous voulez créer un gestionnaire d'événements.  
  
    > [!NOTE]  
    >  Si vous souhaitez créer des gestionnaires d'événements pour `ThisDocument` ou `ThisWorkbook`, vous devez sélectionner **\(Événements ThisDocument\)** ou **\(Événements ThisWorkbook\)** dans la liste déroulante **Nom de la classe**.  
  
2.  Dans la liste déroulante **Nom de la méthode** située en haut de l'éditeur de code, sélectionnez l'événement.  
  
     Visual Studio crée le gestionnaire d'événements et déplace le point d'insertion jusqu'au nouveau gestionnaire d'événements.  Si le gestionnaire d'événements existe déjà, le point d'insertion se déplace jusqu'au gestionnaire d'événements existant.  
  
### Pour créer un gestionnaire d'événements en C\#  
  
1.  Créez le délégué d'événement dans l'événement **Startup** de la classe en tapant le nom d'événement qualifié suivi d'un espace, puis en tapant \+\=, non suivi d'un espace.  Par exemple :  
  
     `this.<object name>.<event name> +=`  
  
2.  À la fin de la ligne de code, appuyez deux fois sur la touche TAB.  
  
     Visual Studio complète automatiquement la ligne de code, crée le gestionnaire d'événements et déplace le point d'insertion jusqu'au nouveau gestionnaire d'événements.  
  
## Voir aussi  
 [Écriture de code dans les solutions Office](../vsto/writing-code-in-office-solutions.md)   
 [Procédure pas à pas : programmation d'événements d'un contrôle NamedRange](../vsto/walkthrough-programming-against-events-of-a-namedrange-control.md)   
 [Génération de solutions Office](../vsto/building-office-solutions.md)  
  
  