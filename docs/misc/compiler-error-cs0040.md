---
title: "Erreur du compilateur CS0040 | Microsoft Docs"
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
  - "CS0040"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0040"
ms.assetid: 6a600166-0335-4b6d-b050-6821b4624c96
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0040
Erreur inattendue lors de la création du fichier des informations de débogage \- 'reason'  
  
 Cette erreur peut se produire lorsque vous utilisez l’option de compilateur [\/debug](/dotnet/csharp/language-reference/compiler-options/debug-compiler-option). Elle indique que le compilateur n’a pas pu écrire dans le fichier .pdb. Pour résoudre cette erreur, vous pouvez réinstaller Visual Studio, vous assurant que le compilateur dispose d’un accès en écriture sur un fichier ou un répertoire ou ne pas compiler avec\/debug.