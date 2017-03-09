---
title: "&#39;&lt;nom_param&#232;tre&gt;&#39; est d&#233;j&#224; d&#233;clar&#233; en tant que param&#232;tre de type de cette m&#233;thode | Microsoft Docs"
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
  - "bc32089"
  - "vbc32089"
helpviewer_keywords: 
  - "BC32089"
ms.assetid: 5e440b4b-f62b-4ff5-9148-2372d4752bf6
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;nom_param&#232;tre&gt;&#39; est d&#233;j&#224; d&#233;clar&#233; en tant que param&#232;tre de type de cette m&#233;thode
Une procédure générique définit un paramètre normal ou une variable locale avec le même nom qu’un paramètre de type.  
  
 Chaque paramètre d’une procédure, y compris chaque paramètre de type d’une procédure générique, doit avoir un nom différent de tous les autres paramètres. Les paramètres de procédure étant utilisés comme variables locales, toute variable locale déclarée dans la procédure doit également avoir un nom différent de tous les paramètres et paramètres de type.  
  
 **ID d’erreur :** BC32089  
  
### Pour corriger cette erreur  
  
-   Modifiez le nom du paramètre normal ou de la variable locale.  
  
## Voir aussi  
 [Generic Procedures in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-procedures)   
 [Parameter List](/dotnet/visual-basic/language-reference/statements/parameter-list)