---
title: "Erreur du compilateur CS1617 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS1617"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1617"
ms.assetid: fd3371ed-39eb-4d3d-b8f5-d96ac0c79398
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS1617
Option 'option' non valide pour \/langversion ; doit avoir la valeur ISO\-2, ISO\-2 ou Default  
  
 Cette erreur se produit si vous avez utilisé le paramètre de projet ou le commutateur de ligne de commande [\/langversion](/dotnet/csharp/language-reference/compiler-options/langversion-compiler-option) sans spécifier d’option de langue valide. Pour résoudre cette erreur, vérifiez la syntaxe de ligne de commande ou le paramètre de projet et remplacez\-le par l’une des options répertoriées.  
  
 Par exemple, si vous compilez avec `csc /langversion:ISO`, l’erreur CS1617 est générée.