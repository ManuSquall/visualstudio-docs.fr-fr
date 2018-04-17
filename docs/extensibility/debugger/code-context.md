---
title: Contexte de code | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], contexts
ms.assetid: 65e4d37a-086b-426e-9394-a3534967fd59
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 9a84596246ae930cdffc0265f2f2e09652661819
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="code-context"></a>Contexte de code
Dans [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] débogage, un **contexte de code**:  
  
-   Fournit une abstraction d’une position dans le code comme connu du moteur de débogage (DE). Pour la plupart des architectures d’exécution aujourd'hui, un contexte de code peut être considéré comme une adresse dans le flux d’instructions d’un programme. Pour les langues non traditionnel, où code ne peut pas être représenté par des instructions, un contexte de code peut-être être représenté par d’autres moyens.  
  
-   Décrit la position actuelle dans le flux d’exécution du programme en cours de débogage.  
  
-   Existe uniquement lorsqu’un programme s’est arrêté à un point d’arrêt.  
  
-   A un contexte de document associé.  
  
-   Est implémentée par un [IDebugCodeContext2](../../extensibility/debugger/reference/idebugcodecontext2.md) interface.  
  
## <a name="see-also"></a>Voir aussi  
 [Contexte de document](../../extensibility/debugger/document-context.md)   
 [Contextes du débogueur](../../extensibility/debugger/debugger-contexts.md)