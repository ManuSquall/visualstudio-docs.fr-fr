---
title: "Erreur du compilateur CS0468 | Microsoft Docs"
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
  - "CS0468"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0468"
ms.assetid: 1ec4f8af-0b32-4ea9-8bc0-bb9e52b9457b
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0468
Ambiguïté entre le type 'type1' et le type 'type2'  
  
 Cette erreur est générée quand il existe deux types dans l’assembly compilé qui portent le même nom qualifié complet. Cela peut se produire si les deux se trouvent dans des modules ajoutés ou si l’un se trouve dans un module ajouté et l’autre dans la source.