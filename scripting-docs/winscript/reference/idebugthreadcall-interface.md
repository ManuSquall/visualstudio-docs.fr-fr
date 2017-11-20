---
title: IDebugThreadCall (Interface) | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: IDebugThreadCall interface
ms.assetid: 9a9a9892-f310-4ef3-8db2-4f868be52d7e
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8b2b1b500aec08520166d9092edfa6a58c1df0fa
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="idebugthreadcall-interface"></a>IDebugThreadCall, interface
Le `IDebugThreadCall` interface est généralement implémentée par un composant qui effectue des appels inter-threads avec le `IDebugThread` le marshaling d’implémentation fournie par le Gestionnaire de processus de débogage (PDM).  
  
 Les appels PDM le `IDebugThreadCall` interface dans le thread souhaité et le `IDebugThreadCall` interface distribue l’appel à l’implémentation de votre choix. Le `IDebugThreadCall` interface convertit les informations de paramètre passées dans les paramètres vers le haut approprié.  
  
 Le `IDebugThreadCall` interface est un objet libre de threads.  
  
## <a name="methods"></a>Méthodes  
 Outre les méthodes héritées de `IUnknown`, le `IDebugThreadCall` interface expose les méthodes suivantes.  
  
|Méthode|Description|  
|------------|-----------------|  
|[IDebugThreadCall::ThreadCallHandler](../../winscript/reference/idebugthreadcall-threadcallhandler.md)|Gère les appels à exécuter du code dans un autre thread.|