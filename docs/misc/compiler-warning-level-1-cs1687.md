---
title: "Avertissement du compilateur (niveau&#160;1) CS1687 | Microsoft Docs"
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
  - "CS1687"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1687"
ms.assetid: f65d184f-fa1d-45d7-be7d-f439f67bace4
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Avertissement du compilateur (niveau&#160;1) CS1687
Le fichier source a dépassé la limite de 16 707 565 lignes pouvant être représentées dans le PDB ; les informations de débogage seront incorrectes  
  
 Le PDB et le débogueur ont des limitations relatives à la taille de fichier. Si le fichier source est trop volumineux, le débogueur ne se comportera pas correctement au\-delà de cette limite. L’utilisateur doit soit ne pas émettre d’informations de débogage pour ce fichier en utilisant éventuellement `#line hidden`, soit trouver un moyen de réduire la taille du fichier, par exemple en le fractionnant en plusieurs fichiers. Vous pouvez utiliser le mot clé `partial` pour fractionner une grande classe.