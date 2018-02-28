---
title: Exceptions (Visual Studio SDK) | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], exception handling
ms.assetid: 7279dc16-db14-482c-86b8-7b3da5a581d2
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 88a862c26dad97eecdb5f372f41a76d7886f32be
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="exception-handling-visual-studio-sdk"></a>Exceptions (Kit de développement logiciel Visual Studio)
La liste suivante décrit le processus qui se produit lorsque des exceptions sont levées.  
  
## <a name="exception-handling-process"></a>Processus de gestion des exceptions  
  
1.  Lorsqu’une exception est levée d’abord, mais avant qu’il est géré par le Gestionnaire d’exceptions dans le programme en cours de débogage, le moteur de débogage (DE) envoie une [IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md) pour le Gestionnaire de session de débogage (SDM) comme un événement d’arrêt. Le `IDebugExceptionEvent2` est envoyé si seuls les paramètres d’exception (spécifié dans la boîte de dialogue Exceptions dans le package de débogage) indiquent que l’utilisateur souhaite arrêter sur les notifications d’exceptions de première chance.  
  
2.  Les appels SDM [IDebugExceptionEvent2::GetException](../../extensibility/debugger/reference/idebugexceptionevent2-getexception.md) pour obtenir la propriété de l’exception.  
  
3.  Les appels de package de débogage [IDebugExceptionEvent2::CanPassToDebuggee](../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md) pour déterminer quelles options de présenter à l’utilisateur.  
  
4.  Le package de débogage demande à l’utilisateur comment gérer l’exception en ouvrant une boîte de dialogue Exceptions de première chance.  
  
5.  Si l’utilisateur choisit de continuer, le SDM appelle [IDebugExceptionEvent2::CanPassToDebuggee](../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md).  
  
    -   Si la méthode retourne S_OK, appelle [IDebugExceptionEvent2::PassToDebuggee](../../extensibility/debugger/reference/idebugexceptionevent2-passtodebuggee.md).  
  
         - ou -  
  
         Si la méthode retourne S_FALSE, le programme débogué est donné à une deuxième chance pour gérer l’exception.  
  
6.  Si le programme débogué n’a aucun gestionnaire pour une exception de deuxième chance, le D’envoie un `IDebugExceptionEvent2` pour le SDM comme **EVENT_SYNC_STOP**.  
  
7.  Le package de débogage demande à l’utilisateur comment gérer l’exception en ouvrant une boîte de dialogue Exceptions de première chance.  
  
8.  Les appels de package de débogage [IDebugExceptionEvent2::CanPassToDebuggee](../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md) pour déterminer quelles options de présenter à l’utilisateur.  
  
9. Le package de débogage demande à l’utilisateur comment gérer l’exception en ouvrant une boîte de dialogue d’exception de deuxième chance.  
  
10. Si la méthode retourne S_OK, appelle `IDebugExceptionEvent2::PassToDebuggee`.  
  
## <a name="see-also"></a>Voir aussi  
 [Événements d’appel du débogueur](../../extensibility/debugger/calling-debugger-events.md)