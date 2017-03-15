---
title: "Erreur du compilateur CS1022 | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS1022"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1022"
ms.assetid: 76b9f32b-2ebf-471d-a635-852daf8877d7
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS1022
Définition de type ou d’espace de noms, ou fin de fichier attendue  
  
 Un fichier de code source n’a pas de paire d’accolades correspondante.  
  
 L’exemple suivant génère l’avertissement CS1022 :  
  
```  
// CS1022.cs namespace x { } }   // CS1022  
```