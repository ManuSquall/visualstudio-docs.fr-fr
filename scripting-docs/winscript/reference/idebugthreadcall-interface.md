---
title: Interface IDebugThreadCall | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugThreadCall interface
ms.assetid: 9a9a9892-f310-4ef3-8db2-4f868be52d7e
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a2167538f2251d961dfcad4a873658d9635a612e
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/16/2019
ms.locfileid: "54346265"
---
# <a name="idebugthreadcall-interface"></a>IDebugThreadCall, interface
Le `IDebugThreadCall` interface est généralement implémentée par un composant qui effectue des appels inter-threads avec le `IDebugThread` marshaling implémentation fournie par le Gestionnaire de débogage de processus (PDM).  
  
 Les appels PDM le `IDebugThreadCall` interface dans le thread souhaité et le `IDebugThreadCall` interface distribue l’appel à l’implémentation de votre choix. Le `IDebugThreadCall` interface convertit les informations de paramètre passées dans les paramètres vers le haut approprié.  
  
 Le `IDebugThreadCall` interface est un objet libre de threads.  
  
## <a name="methods"></a>Méthodes  
 Outre les méthodes héritées de `IUnknown`, le `IDebugThreadCall` interface expose les méthodes suivantes.  
  
|Méthode|Description|  
|------------|-----------------|  
|[IDebugThreadCall::ThreadCallHandler](../../winscript/reference/idebugthreadcall-threadcallhandler.md)|Gère les appels à exécuter du code dans un autre thread.|