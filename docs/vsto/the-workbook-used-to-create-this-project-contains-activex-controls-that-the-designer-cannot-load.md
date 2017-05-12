---
title: "Le classeur utilis&#233; pour cr&#233;er ce projet contient des contr&#244;les&#160;ActiveX que le concepteur ne peut pas charger | Microsoft Docs"
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
  - "VST.SelectDocWizard.ContainsActiveXControls"
dev_langs: 
  - "VB"
  - "CSharp"
ms.assetid: 91e9c6ee-7543-41e3-be0c-6c000cfd32d1
caps.latest.revision: 15
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 14
---
# Le classeur utilis&#233; pour cr&#233;er ce projet contient des contr&#244;les&#160;ActiveX que le concepteur ne peut pas charger
  Cette erreur apparaît quand vous ajoutez par programmation un contrôle à un document Word ou une feuille de calcul Excel, enregistrez le document ou le classeur, puis créez une solution au niveau du document basée sur le document ou le classeur.  
  
 Les informations qui décrivent le type managé du contrôle ne sont pas enregistrées avec le document ou le classeur.  Quand vous créez une solution basée sur ce document ou classeur, Visual Studio ne possède pas suffisamment d'informations pour charger le contrôle dans le concepteur d'éléments hôtes.  
  
### Pour corriger cette erreur  
  
1.  Ouvrez le document ou le classeur.  
  
2.  Supprimez les contrôles qui ont été ajoutés au moment de l'exécution.  Pour cela, sélectionnez\-les dans le document ou le classeur et appuyez sur la touche Suppr.  
  
3.  Créez une solution au niveau du document basée sur le document ou le classeur.  
  
## Voir aussi  
 [Comment : créer des projets Office dans Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Ajout de contrôles à des documents Office au moment de l'exécution](../vsto/adding-controls-to-office-documents-at-run-time.md)  
  
  