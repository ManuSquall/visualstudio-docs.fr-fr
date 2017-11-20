---
title: Contexte de code | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: debugging [Debugging SDK], contexts
ms.assetid: 65e4d37a-086b-426e-9394-a3534967fd59
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 92d6ed317bcf6ceead42db850ee61969409eb136
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
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