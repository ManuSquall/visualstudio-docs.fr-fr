---
title: "Erreur du compilateur CS1541 | Microsoft Docs"
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
  - "CS1541"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1541"
ms.assetid: db3350fe-6432-4617-8b4a-64bc6cdf83f8
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS1541
Option de référence non valide : 'symbole' \-\- ne peut pas faire référence à des répertoires  
  
 Le compilateur a détecté une tentative de spécification d’un répertoire au lieu d’un fichier. Par exemple, quand vous utilisez l’option du compilateur [\/reference](/dotnet/csharp/language-reference/compiler-options/reference-compiler-option), vous devez spécifier un fichier. Vous ne pouvez pas spécifier un répertoire.  
  
 Par exemple, si vous passez `/reference:c:\` au compilateur, l’erreur CS1541 est générée.