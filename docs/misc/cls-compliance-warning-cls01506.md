---
title: "Avertissement de conformit&#233; CLS CLS01506 | Microsoft Docs"
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
  - "CLS01506"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS01506"
ms.assetid: 030f1b81-1159-4057-9fee-8721a419a5d6
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# Avertissement de conformit&#233; CLS CLS01506
La contrainte varargs ne fait pas partie de la spécification CLS  
  
 La contrainte varargs ne fait pas partie de la spécification CLS \(Common Language Specification\).  La seule convention d’appel prise en charge par la spécification CLS est la convention d’appel managée standard.  
  
 Pour plus d’informations sur la vérification de conformité CLS, consultez les [assemblys conformes CLS](http://msdn.microsoft.com/fr-fr/3320b57e-ea55-4697-a17d-f509a36a3c93).  
  
 La déclaration de fonction suivante \(en langage d’assembly MSIL\) montre ce qui peut provoquer l’avertissement CLS01506 :  
  
```  
.method public instance vararg void  Method1() cil managed  
```  
  
 En supprimant le mot clé **vararg**, vous pouvez résoudre cet avertissement :  
  
```  
.method public instance void  Method1() cil managed  
```