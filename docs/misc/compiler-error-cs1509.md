---
title: "Erreur du compilateur CS1509 | Microsoft Docs"
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
  - "CS1509"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1509"
ms.assetid: 51a475c3-f085-49cb-89b0-c6582b68653f
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS1509
Le fichier référencé 'fichier' n’est pas un assembly ; utilisez plutôt l’option '\/addmodule'  
  
 Un fichier de sortie \(fichier de sortie 1\), généré dans une compilation qui utilisait [\/target:module](../Topic/-target:module%20\(C%23%20Compiler%20Options\).md) \(sans manifeste d’assembly\), a été spécifié dans [\/reference](/dotnet/csharp/language-reference/compiler-options/reference-compiler-option). Ainsi, au lieu d’ajouter un assembly à l’assembly du programme actuel, les informations de métadonnées contenues dans le fichier de sortie 1 sont ajoutées à l’assembly du programme actuel.