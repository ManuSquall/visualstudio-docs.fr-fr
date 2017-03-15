---
title: "Avertissement de conformit&#233; CLS CLS02409 | Microsoft Docs"
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
  - "CLS02409"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS02409"
ms.assetid: 71d566ce-59c2-4d3d-97ff-72f4e9bd21ee
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# Avertissement de conformit&#233; CLS CLS02409
Les méthodes qui implémentent les méthodes getter et setter d’une propriété devront être marquées SpecialName dans les métadonnées  
  
 Les méthodes qui implémentent les méthodes getter et setter d’une propriété devront être marquées **specialname** dans les métadonnées.  
  
 Pour plus d’informations sur la vérification de conformité CLS, consultez [Assemblys conformes à CLS](http://msdn.microsoft.com/fr-fr/3320b57e-ea55-4697-a17d-f509a36a3c93).  
  
 La déclaration de fonction suivante \(en langage d’assembly MSIL\) illustre ce qui peut provoquer l’avertissement CLS02409 :  
  
```  
.method public instance int32 get_MyProperty() cil managed  
```  
  
 En ajoutant le mot clé **specialname**, vous pouvez résoudre cet avertissement :  
  
```  
.method public specialname instance int32 get_MyProperty() cil managed  
```