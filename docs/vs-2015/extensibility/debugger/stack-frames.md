---
title: Frames de pile | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- stack frames, debugging
- debugging [Debugging SDK], stack frames
- stack frames
ms.assetid: b5e439d4-1e9d-4e13-9cad-bb8b136d4ca8
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d3050e89db2f5cbb138f3d358b10c7cd936c560e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62423385"
---
# <a name="stack-frames"></a>Frames de pile
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

En termes d’architecture du débogueur, un **Frame de pile**:  
  
- Est une abstraction d’une pile qui fournit le contexte d’exécution d’un thread. Un thread s’exécute toujours dans une fonction. Un frame de pile contient les variables locales de la fonction, ainsi que les arguments de celui-ci. Pour déboguer avec Visual Studio, le langage ou l’environnement en cours de débogage doit prendre en charge les frames de pile.  
  
- Peut à la fois identifier et décrire lui-même, et peut retourner le thread associé. Un frame de pile peut également retourner le contexte de code qui représente le pointeur d’instruction en cours, ainsi que la documentation associée et les contextes d’évaluation des expressions.  
  
- A des propriétés qui décrivent le nom, le type et la valeur des variables locales et des arguments, et qui s’affichent dans différentes fenêtres de débogage IDE.  
  
- Est représenté par une interface [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md) , généralement créée par un moteur de débogage (de) ou un ordinateur virtuel suite à l’exécution d’un thread.  
  
## <a name="see-also"></a>Voir aussi  
 [Contextes du débogueur](../../extensibility/debugger/debugger-contexts.md)   
 [Concepts du débogueur](../../extensibility/debugger/debugger-concepts.md)   
 [Moteur de débogage](../../extensibility/debugger/debug-engine.md)   
 [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md)
