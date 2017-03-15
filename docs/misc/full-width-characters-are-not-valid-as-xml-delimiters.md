---
title: "Les caract&#232;res &#224; pleine chasse ne sont pas valides en tant que d&#233;limiteurs XML | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc31197"
  - "bc31197"
helpviewer_keywords: 
  - "BC31197"
ms.assetid: f5d724f8-545b-4cf8-9606-12c63814c6e8
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Les caract&#232;res &#224; pleine chasse ne sont pas valides en tant que d&#233;limiteurs XML
Vous avez défini un littéral XML qui comprend un caractère à pleine chasse comme délimiteur. Les caractères à pleine chasse sont également appelés caractères larges ou multioctets.  
  
 **ID d’erreur :** BC31197  
  
### Pour corriger cette erreur  
  
-   Supprimez le caractère à pleine chasse de la définition du littéral XML et remplacez\-le par un caractère de délimiteur ANSI valide. Les caractères délimiteurs valides sont les suivants : `<`, `>`, `=`, `:`, `/`.  
  
## Voir aussi  
 [XML Literals](/dotnet/visual-basic/language-reference/xml-literals/index)   
 [Encodage de caractères dans le .NET Framework](../Topic/Character%20Encoding%20in%20the%20.NET%20Framework.md)   
 [XML](/dotnet/visual-basic/programming-guide/language-features/xml/index)