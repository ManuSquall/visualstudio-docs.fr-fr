---
title: "Avertissement de conformit&#233; CLS CLS01501 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CLS01501"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS01501"
ms.assetid: 74361331-3773-48d5-8508-0113f5464a75
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# Avertissement de conformit&#233; CLS CLS01501
**La contrainte varargs ne fait pas partie de la spécification CLS**  
  
 La contrainte varargs ne fait pas partie du Common Language Subset \(CLS\).  La seule convention d’appel prise en charge par la spécification CLS est la convention d’appel managée standard.  
  
 Pour plus d’informations sur la vérification de conformité CLS, consultez [Assemblys conformes CLS](http://msdn.microsoft.com/fr-fr/3320b57e-ea55-4697-a17d-f509a36a3c93).  
  
 La déclaration de fonction suivante \(en langage d’assembly MSIL\) montre ce qui peut provoquer l’erreur CLS01501 :  
  
```  
.method public specialname rtspecialname instance vararg void  .ctor() cil managed  
```  
  
 Vous pouvez résoudre l’erreur CLS01501 au moyen d’un tableau de paramètres.  Pour plus d’informations, consultez [Variable Argument Lists \(...\) \(C\+\+\/CLI\)](/visual-cpp/windows/variable-argument-lists-dot-dot-dot-cpp-cli).