---
title: Frames de pile | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- stack frames, debugging
- debugging [Debugging SDK], stack frames
- stack frames
ms.assetid: b5e439d4-1e9d-4e13-9cad-bb8b136d4ca8
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: feb2bc9d87486b6f83cf4b19ecec24c8c03edee5
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31127997"
---
# <a name="stack-frames"></a>Frames de pile
En termes de l’architecture du débogueur, une **frame de pile**:  
  
-   Est une abstraction d’une pile qui fournit le contexte d’exécution d’un thread. Un thread s’exécute toujours dans une fonction. Un frame de pile conserve les variables locales de la fonction et les arguments. Pour déboguer avec Visual Studio, la langue ou l’environnement en cours de débogage doit prendre en charge les frames de pile.  
  
-   Peut identifier et décrire lui-même et peut retourner le thread associé. Un frame de pile peut également retourner le contexte de code qui représente le pointeur d’instruction en cours, ainsi que la documentation associée et les contextes d’évaluation d’expression.  
  
-   Possède des propriétés qui décrivent le nom, le type et la valeur des variables locales et les arguments et qui figurent dans les différentes fenêtres de débogage IDE.  
  
-   Est représenté par un [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md) interface, généralement créé par un moteur de débogage (DE) ou un ordinateur virtuel en raison de l’exécution d’un thread.  
  
## <a name="see-also"></a>Voir aussi  
 [Contextes de débogueur](../../extensibility/debugger/debugger-contexts.md)   
 [Concepts du débogueur](../../extensibility/debugger/debugger-concepts.md)   
 [Moteur de débogage](../../extensibility/debugger/debug-engine.md)   
 [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md)