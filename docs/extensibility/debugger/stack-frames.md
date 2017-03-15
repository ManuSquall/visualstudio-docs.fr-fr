---
title: "Frames de pile | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "frames de pile, le débogage"
  - "débogage (débogage SDK), des frames de pile"
  - "frames de pile"
ms.assetid: b5e439d4-1e9d-4e13-9cad-bb8b136d4ca8
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# Frames de pile
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Quant à l'architecture du débogueur, **un frame de pile**:  
  
-   est une abstraction d'une pile qui fournit le contexte d'exécution d'un thread.  Un thread s'exécute toujours d'une fonction.  Un frame de pile contient les variables locales de la fonction, et les arguments à celui\-ci.  Pour déboguer avec Visual Studio, le langage ou l'environnement en cours de débogage doit prendre en charge des frames de pile.  
  
-   Peut identifier et se décrire, et peut retourner le thread associé.  Un frame de pile peut également retourner le contexte de code qui représente le pointeur d'instruction actuel, ainsi que les contextes associés de la documentation et d'évaluation de l'expression.  
  
-   Possède des propriétés qui décrivent le nom, le type, et la valeur des variables locales et d'arguments, et qui apparaissent dans plusieurs fenêtres de débogage de l'IDE.  
  
-   Est représenté par une interface d' [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md) , généralement créée par un moteur de débogage \(DE\) ou un ordinateur virtuel devant être d'exécuter un thread.  
  
## Voir aussi  
 [Contextes de débogueur](../../extensibility/debugger/debugger-contexts.md)   
 [Concepts du débogueur](../../extensibility/debugger/debugger-concepts.md)   
 [Moteur de débogage](../../extensibility/debugger/debug-engine.md)   
 [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md)