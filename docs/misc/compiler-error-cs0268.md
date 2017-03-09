---
title: "Erreur du compilateur CS0268 | Microsoft Docs"
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
  - "CS0268"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0268"
ms.assetid: a4faca71-8b4a-4f22-a89e-59d92ced48cb
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0268
Le type importé 'type' n’est pas valide. Il contient une dépendance de classe de base circulaire.  
  
 Cette erreur se produit quand un type importé à l’aide d’un autre langage possède une dépendance de classe de base circulaire. Ce type ne peut pas être utilisé dans un programme C\#. Pour résoudre ce problème, vérifiez les types qui ont été importés à l’aide d’autres langages et qui se trouvent dans les assemblys et les modules référencés.