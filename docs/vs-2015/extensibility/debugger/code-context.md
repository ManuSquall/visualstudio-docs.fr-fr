---
title: Contexte de code | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], contexts
ms.assetid: 65e4d37a-086b-426e-9394-a3534967fd59
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d59a4c79cb21386fa6f6e7031404aeb0b435b3b9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68197372"
---
# <a name="code-context"></a>Contexte de code
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Dans [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] le cadre du débogage, un **contexte de code**:  
  
- Fournit une abstraction d’une position dans le code telle que connue du moteur de débogage (DE). Pour la plupart des architectures Runtime actuelles, un contexte de code peut être considéré comme une adresse dans le flux d’instructions d’un programme. Pour les langages non traditionnels, où le code ne peut pas être représenté par des instructions, un contexte de code peut être représenté par d’autres moyens.  
  
- Décrit la position actuelle dans le flux d’exécution du programme en cours de débogage.  
  
- Existe uniquement lorsqu’un programme s’est arrêté à un point d’arrêt.  
  
- A un contexte de document associé.  
  
- Est implémenté par une interface [IDebugCodeContext2](../../extensibility/debugger/reference/idebugcodecontext2.md) .  
  
## <a name="see-also"></a>Voir aussi  
 [Contexte de document](../../extensibility/debugger/document-context.md)   
 [Contextes du débogueur](../../extensibility/debugger/debugger-contexts.md)
