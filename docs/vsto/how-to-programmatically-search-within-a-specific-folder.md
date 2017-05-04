---
title: "Comment&#160;: rechercher dans un dossier sp&#233;cifique par programmation | Microsoft Docs"
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
  - "dossiers Outlook (développement Office dans Visual Studio), rechercher"
ms.assetid: 8f2cdc8b-f757-412c-aa2b-ebd5bc52f697
caps.latest.revision: 30
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 29
---
# Comment&#160;: rechercher dans un dossier sp&#233;cifique par programmation
  Cet exemple de code utilise les méthodes `Find` et `FindNext` pour rechercher un texte dans le champ d'objet des courriers électroniques présents dans la **Boîte de réception**.  Cette méthode utilise un filtre de chaîne pour vérifier la présence éventuelle de la lettre T en tant que lettre initiale du texte `Subject`.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## Exemple  
 [!code-csharp[Trin_OL_SearchFolder#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_OL_SearchFolder/CS/thisaddin.cs#1)]  
  
## Voir aussi  
 [Utilisation des dossiers](../vsto/working-with-folders.md)   
 [Vue d'ensemble du modèle d'objet Outlook](../vsto/outlook-object-model-overview.md)   
 [Comment : récupérer un dossier par nom par programmation](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)  
  
  