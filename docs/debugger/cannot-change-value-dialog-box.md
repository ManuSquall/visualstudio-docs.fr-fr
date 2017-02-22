---
title: "Impossible de changer la valeur, bo&#238;te de dialogue | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.variables.failededit"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "Impossible de changer la valeur (boîte de dialogue)"
  - "variables (débogueur), modification"
ms.assetid: 19e930c2-5fbf-4c83-aae8-a1dc3f8fcae8
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# Impossible de changer la valeur, bo&#238;te de dialogue
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

## Erreur  
 `The value of this variable cannot be changed`  &#124; `The name` *name* `does not exist in the current context` &#124; *various other messages*  
  
 Cette boîte de message s'affiche lorsque vous essayez de remplacer le contenu d'une variable par une valeur non conforme dans une fenêtre du débogueur \(Automatique, Espion ou Variables locales\) ou dans la boîte de dialogue Espion express.  Par exemple, cette boîte de message s'affiche si vous essayez d'attribuer à la valeur d'une variable entière une chaîne de caractères.  
  
## Solution  
 Assurez\-vous que l'entrée que vous tapez dans la fenêtre du débogueur ou dans la boîte de dialogue Espion express représente une valeur conforme pour la variable que vous essayez de définir.  
  
## Voir aussi  
 [Expressions dans le débogueur](../debugger/expressions-in-the-debugger.md)