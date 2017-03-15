---
title: "Configuration name is not valid. | Microsoft Docs"
ms.custom: ""
ms.date: "11/24/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.message.VS_E_INVALID_CFG_NAME"
  - "vs.message.0x800A00B7"
ms.assetid: aa439582-0863-41d3-825c-7c45b1773cde
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Configuration name is not valid.
Cette erreur se produit généralement lorsque le nom spécifié pour la configuration de build comprend des caractères non conformes, tels que \<, \>, &#124; et \*.  
  
### Pour corriger cette erreur  
  
1.  Vérifiez que le nom de la configuration n'utilise pas les caractères suivants : \<, \>, \*, &#124;, :, \\, \/, &, %, ", ., \#, ?, espace de début ou de fin.  En outre, le nom de la configuration ne doit pas contenir de noms réservés à Windows ou à MS\-DOS, comme « nul », « aux », « con », « com\# », « lpt\# », etc.  
  
2.  Entrez à nouveau le nom.  
  
## Voir aussi  
 [Génération d'applications dans Visual Studio](../ide/compiling-and-building-in-visual-studio.md)