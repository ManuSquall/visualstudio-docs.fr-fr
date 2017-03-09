---
title: "Alias definition is recursive. | Microsoft Docs"
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
  - "vs.message.0x800A00DA"
  - "vs.message.VS_E_RECURSIVEALIAS"
ms.assetid: e48a2908-9b94-4c6a-9807-beeeba71531c
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Alias definition is recursive.
Cette erreur se produit généralement lorsqu'un alias qui a été défini fait directement ou indirectement référence à lui\-même.  
  
### Pour corriger cette erreur  
  
1.  Modifiez la définition de l'alias et recommencez.  
  
     \- ou \-  
  
2.  Examinez la liste en cours des alias, ainsi que leurs définitions en entrant `>alias` dans la fenêtre **Commande** et recommencez.  
  
## Voir aussi  
 [Alias, commande](../ide/reference/alias-command.md)   
 [Alias de commandes Visual Studio](../ide/reference/visual-studio-command-aliases.md)