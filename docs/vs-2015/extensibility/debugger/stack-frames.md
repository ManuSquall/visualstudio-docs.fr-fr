---
title: Frames de pile | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- stack frames, debugging
- debugging [Debugging SDK], stack frames
- stack frames
ms.assetid: b5e439d4-1e9d-4e13-9cad-bb8b136d4ca8
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 301a782ebf0eda9b1e97c9f0f09c10a0985de4c2
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49271594"
---
# <a name="stack-frames"></a>Frames de pile
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

En termes d’architecture du débogueur, une **frame de pile**:  
  
-   Est une abstraction d’une pile qui fournit le contexte d’exécution d’un thread. Un thread s’exécute toujours dans une fonction. Un frame de pile conserve les variables locales de la fonction et les arguments. Pour déboguer avec Visual Studio, la langue ou l’environnement en cours de débogage doit prendre en charge les frames de pile.  
  
-   Peut identifier et décrire lui-même et peut retourner le thread associé. Un frame de pile peut également retourner le contexte de code qui représente le pointeur d’instruction en cours, ainsi que la documentation associée et des contextes d’évaluation d’expression.  
  
-   A des propriétés qui décrivent le nom, le type et la valeur des variables locales et des arguments, et qui figurent dans les différentes fenêtres de débogage d’IDE.  
  
-   Est représenté par un [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md) interface, généralement créé par un moteur de débogage (dé) ou d’une machine virtuelle en raison de l’exécution d’un thread.  
  
## <a name="see-also"></a>Voir aussi  
 [Contextes du débogueur](../../extensibility/debugger/debugger-contexts.md)   
 [Concepts du débogueur](../../extensibility/debugger/debugger-concepts.md)   
 [Moteur de débogage](../../extensibility/debugger/debug-engine.md)   
 [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md)

