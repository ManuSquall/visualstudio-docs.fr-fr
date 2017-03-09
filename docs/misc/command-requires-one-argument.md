---
title: "Command requires one argument. | Microsoft Docs"
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
  - "vs.message.VS_E_INCORRECTPARAMCOUNT1"
  - "vs.message.0x800A00C3"
ms.assetid: b4d98e6d-6970-42fb-b1de-43f2e952fb9d
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Command requires one argument.
Cette erreur se produit généralement lorsqu'une quantité d'informations insuffisante a été spécifiée pour une commande ou qu'une combinaison incorrecte d'arguments a été utilisée.  
  
 Par exemple, si la syntaxe `alias` `/delete sample1 sample2` a été utilisée pour la commande `alias`, cette erreur se produira car alias `/delete` n'accepte qu'un seul nom d'alias et non deux.  Les noms d'alias ne contiennent pas d'espaces afin que la zone de texte **Rechercher\/Commande** ainsi que la fenêtre **Commande** interprètent `sample1 sample2` comme deux noms d'alias différents.  
  
### Pour corriger cette erreur  
  
1.  Vérifiez dans la documentation la syntaxe à respecter pour la commande et recommencez.  
  
## Voir aussi  
 [Commandes Visual Studio](../ide/reference/visual-studio-commands.md)