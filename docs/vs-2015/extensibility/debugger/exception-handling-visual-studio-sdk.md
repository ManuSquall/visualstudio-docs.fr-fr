---
title: Gestion des exceptions (kit de développement logiciel Visual Studio) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], exception handling
ms.assetid: 7279dc16-db14-482c-86b8-7b3da5a581d2
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 38e646f032a12de48bbfb55b089462c7f8a4dd26
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68152790"
---
# <a name="exception-handling-visual-studio-sdk"></a>Gestion des exceptions (SDK Visual Studio)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Les éléments suivants décrivent le processus qui se produit lorsque des exceptions sont levées.  
  
## <a name="exception-handling-process"></a>Processus de gestion des exceptions  
  
1. Quand une exception est levée pour la première fois, mais avant qu’elle ne soit gérée par le gestionnaire d’exceptions dans le programme en cours de débogage, le moteur DE débogage (DE) envoie un [IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md) vers le gestionnaire de débogage de session (SDM) comme événement d’arrêt. `IDebugExceptionEvent2`Est envoyé si seuls les paramètres de l’exception (spécifiés dans la boîte de dialogue exceptions dans le package de débogage) spécifient que l’utilisateur souhaite s’arrêter sur les notifications d’exceptions de première chance.  
  
2. Le SDM appelle [IDebugExceptionEvent2 :: GetException](../../extensibility/debugger/reference/idebugexceptionevent2-getexception.md) pour récupérer la propriété de l’exception.  
  
3. Le package de débogage appelle [IDebugExceptionEvent2 :: CanPassToDebuggee](../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md) pour déterminer les options à présenter à l’utilisateur.  
  
4. Le package de débogage demande à l’utilisateur comment gérer l’exception en ouvrant une boîte de dialogue d’exception de première chance.  
  
5. Si l’utilisateur choisit de continuer, le SDM appelle [IDebugExceptionEvent2 :: CanPassToDebuggee](../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md).  
  
    - Si la méthode retourne S_OK, appelle [IDebugExceptionEvent2 ::P asstodebuggee](../../extensibility/debugger/reference/idebugexceptionevent2-passtodebuggee.md).  
  
         - ou -  
  
         Si la méthode retourne S_FALSE, le programme en cours de débogage reçoit une seconde chance de gérer l’exception.  
  
6. Si le programme en cours de débogage n’a pas de gestionnaire pour une exception de deuxième chance, le DE envoie un `IDebugExceptionEvent2` au SDM en tant que **EVENT_SYNC_STOP**.  
  
7. Le package de débogage demande à l’utilisateur comment gérer l’exception en ouvrant une boîte de dialogue d’exception de première chance.  
  
8. Le package de débogage appelle [IDebugExceptionEvent2 :: CanPassToDebuggee](../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md) pour déterminer les options à présenter à l’utilisateur.  
  
9. Le package de débogage demande à l’utilisateur comment gérer l’exception en ouvrant une boîte de dialogue d’exception de deuxième chance.  
  
10. Si la méthode retourne S_OK, appelle `IDebugExceptionEvent2::PassToDebuggee` .  
  
## <a name="see-also"></a>Voir aussi  
 [Événements d’appel du débogueur](../../extensibility/debugger/calling-debugger-events.md)
