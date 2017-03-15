---
title: "Erreur du compilateur&#160;CS1727 | Microsoft Docs"
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
  - "CS1727"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1727"
ms.assetid: 66478a58-e0f6-4886-b940-5473ad485a01
caps.latest.revision: 5
caps.handback.revision: 5
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur&#160;CS1727
Impossible d’envoyer automatiquement le rapport d’erreur sans autorisation. Visitez '' pour autoriser l’envoi du rapports d’erreur.  
  
 Le site web indiqué dans le texte d’erreur explique comment activer les rapports d’erreurs automatiques pour les outils en ligne de commande [!INCLUDE[vsprvslong](../code-quality/includes/vsprvslong_md.md)].  
  
## Exemple  
 L’exemple suivant génère l’erreur CS1727.  
  
```  
// CS1727.cs // compile with: /errorreport:send // CS1727 expected class Test { static void Main(){} }  
```  
  
## Voir aussi  
 [\/errorreport \(Set Error Reporting Behavior\)](/dotnet/csharp/language-reference/compiler-options/errorreport-compiler-option)