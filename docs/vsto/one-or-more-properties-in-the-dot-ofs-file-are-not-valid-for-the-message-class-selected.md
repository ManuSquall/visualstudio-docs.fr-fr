---
title: "Au moins une propri&#233;t&#233; du fichier&#160;.ofs n&#39;est pas valide pour la classe de message s&#233;lectionn&#233;e | Microsoft Docs"
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
  - "VSTO.NewFormRegionWizard.OFSPropertyError"
dev_langs: 
  - "VB"
  - "CSharp"
ms.assetid: ca9e2ec1-df96-45ca-9611-cec47edfe1e4
caps.latest.revision: 8
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 7
---
# Au moins une propri&#233;t&#233; du fichier&#160;.ofs n&#39;est pas valide pour la classe de message s&#233;lectionn&#233;e
  Cette erreur s’affiche quand vous importez une zone de formulaire conçue dans Outlook, mais qu’un ou plusieurs champs de la zone de formulaire ne sont pas compatibles avec les classes de message que vous sélectionnez à la dernière page de l’Assistant **Nouvelle zone de formulaire**.  
  
 Par exemple, vous pouvez sélectionner **Tâche \(IPM.Task\)** à la dernière page de l’Assistant **Nouvelle zone de formulaire**. Si la zone de formulaire contient un champ **Adresse professionnelle**, vous recevez cette erreur, car une tâche n’a pas d’adresse d’entreprise. Par conséquent, le champ **Adresse professionnelle** n’est pas compatible avec la classe de message IPM.Task.  
  
### Pour corriger cette erreur  
  
-   À la dernière page de l’Assistant **Nouvelle zone de formulaire**, sélectionnez une classe de message qui soit compatible avec les champs de la zone de formulaire.  
  
-   Dans le Concepteur de formulaires d’Outlook, supprimez les champs qui ne sont pas compatibles avec les classes de message que vous prévoyez de sélectionner à la dernière page de l’Assistant **Nouvelle zone de formulaire**.  
  
## Voir aussi  
 [Procédure pas à pas : importation d'une zone de formulaire conçue dans Outlook](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)  
  
  