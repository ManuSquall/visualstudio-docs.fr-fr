---
title: "Avertissement de conformit&#233; CLS CLS02902 | Microsoft Docs"
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
  - "CLS02902"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS02902"
ms.assetid: 028c91fc-d3bb-4c97-92e6-159b5d663fc2
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# Avertissement de conformit&#233; CLS CLS02902
Les méthodes qui implémentent un événement doivent être marquées comme SpecialName dans les métadonnées  
  
 Une méthode qui implémente un événement n’a pas été marquée comme **specialname** dans les métadonnées.  
  
 Pour plus d’informations sur la vérification de conformité CLS, consultez les [assemblys conformes CLS](http://msdn.microsoft.com/fr-fr/3320b57e-ea55-4697-a17d-f509a36a3c93).  
  
 La déclaration de fonction suivante \(en langage d’assembly MSIL\) montre ce qui peut provoquer l’avertissement CLS02902 :  
  
```  
.method public instance void raise_MyEvent(object __unnamed000, class [mscorlib]System.EventArgs __unnamed001) cil managed { } // end of method One::raise_MyEvent  
```  
  
 En ajoutant le mot clé **specialname**, vous pouvez résoudre cet avertissement :  
  
```  
.method public specialname instance void raise_MyEvent(object __unnamed000, class [mscorlib]System.EventArgs __unnamed001) cil managed { } // end of method One::raise_MyEvent  
```