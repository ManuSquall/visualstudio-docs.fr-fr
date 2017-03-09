---
title: "Erreur du compilateur CS1562 | Microsoft Docs"
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
  - "CS1562"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1562"
ms.assetid: fbadbcc6-9cf2-4af6-b372-fd4e4da4402e
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS1562
L'option \/out doit être spécifiée pour les sorties dépourvues de source  
  
 La compilation a réussi à créer un fichier de sortie, mais son nom n’a pas pu être déduit en raison de l’absence d’un fichier de code source en tant qu’entrée. Par exemple, vous essayez peut\-être de compiler un fichier contenant uniquement des métadonnées ou des ressources.  
  
 Utilisez l’option de compilateur [\/out](/dotnet/csharp/language-reference/compiler-options/out-compiler-option) pour spécifier le nom du fichier de sortie.