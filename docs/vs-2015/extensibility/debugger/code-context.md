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
ms.openlocfilehash: 0fedbb786c7282af213b5e5d5b80c06cb2f08159
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58953492"
---
# <a name="code-context"></a>Contexte de code
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Dans [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] débogage, un **contexte de code**:  
  
-   Fournit une abstraction d’une position dans le code comme connu du moteur de débogage (dé). Pour la plupart des architectures d’exécution dès aujourd'hui, un contexte de code peut être considéré comme une adresse dans le flux d’instructions d’un programme. Pour les langues non traditionnel, où code ne peut pas être représenté par des instructions, un contexte de code peut être représenté par d’autres moyens.  
  
-   Décrit la position actuelle dans le flux d’exécution du programme en cours de débogage.  
  
-   Existe uniquement lorsqu’un programme s’est arrêté à un point d’arrêt.  
  
-   A un contexte de document associé.  
  
-   Est implémentée par un [IDebugCodeContext2](../../extensibility/debugger/reference/idebugcodecontext2.md) interface.  
  
## <a name="see-also"></a>Voir aussi  
 [Contexte de document](../../extensibility/debugger/document-context.md)   
 [Contextes du débogueur](../../extensibility/debugger/debugger-contexts.md)
