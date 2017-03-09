---
title: "La d&#233;finition &#39;AddHandler&#39; est manquante pour l’&#233;v&#233;nement &#39;&lt;nom_&#233;v&#233;nement&gt;&#39; | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc31130"
  - "vbc31130"
helpviewer_keywords: 
  - "BC31130"
ms.assetid: cf6c7fd6-ce2e-4916-b427-2a4a63e7279d
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# La d&#233;finition &#39;AddHandler&#39; est manquante pour l’&#233;v&#233;nement &#39;&lt;nom_&#233;v&#233;nement&gt;&#39;
Si un événement est déclaré comme `Custom`, il doit fournir une procédure pour ajouter un gestionnaire d’événements.  
  
 **ID d’erreur :** BC31130  
  
### Pour corriger cette erreur  
  
1.  Placez une déclaration `AddHandler` entre l’instruction `Custom Event` et l’instruction `End Event`.  
  
2.  Vérifiez que les autres procédures de la déclaration event se terminent correctement.  
  
## Voir aussi  
 [AddHandler Statement](/dotnet/visual-basic/language-reference/statements/addhandler-statement)   
 [Event Statement](/dotnet/visual-basic/language-reference/statements/event-statement)