---
title: "Erreur du compilateur&#160;CS1680 | Microsoft Docs"
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
  - "CS1680"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1680"
ms.assetid: 973da155-e6fa-4de8-94fd-7838f839a81f
caps.latest.revision: 11
caps.handback.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur&#160;CS1680
Option d’alias de référence non valide : 'alias\=' \-\- nom de fichier manquant.  
  
 Cette erreur se produit lorsque vous utilisez la fonctionnalité `alias` avec l’option de compilateur **\/reference** sans spécifier un nom de fichier valide.  
  
 L’exemple suivant génère l’erreur CS1680.  
  
```  
// CS1680.cs // compile with: /reference:alias= // CS1680 expected // To resolve, specify the name of a file with an assembly manifest class MyClass {}  
  
```