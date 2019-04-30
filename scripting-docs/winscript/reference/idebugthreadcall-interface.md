---
title: Interface IDebugThreadCall | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 89f0fba2f5210cdcf4bb8f17443f948cb9ba1f4e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63004858"
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