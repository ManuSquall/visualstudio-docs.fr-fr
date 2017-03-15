---
title: "Erreur du compilateur CS0041 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0041"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0041"
ms.assetid: 80dbfe00-8cdb-4275-9574-8a215c7139d6
caps.latest.revision: 16
caps.handback.revision: 16
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0041
Le nom complet de 'type' est trop long pour les informations de débogage. Compilez sans l'option '\/debug'.  
  
 Cette erreur peut se produire quand vous utilisez l’option de compilateur [\/debug](/dotnet/csharp/language-reference/compiler-options/debug-compiler-option). Si vous rencontrez cette erreur, essayez de supprimer les fichiers PDB du répertoire bin, puis de relancer la compilation. Si vous rencontrez toujours cette erreur, vous devrez peut\-être réparer ou réinstaller [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].