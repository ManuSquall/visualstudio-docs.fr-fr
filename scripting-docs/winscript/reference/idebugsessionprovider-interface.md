---
title: IDebugSessionProvider (Interface) | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- IDebugSessionProvider interface
ms.assetid: 1b898423-7af9-44f5-8dda-987005309c99
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4e61b1e5e794c68e34250f958cdda0f50b68334c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="idebugsessionprovider-interface"></a>IDebugSessionProvider, interface
La principale interface fournie par un débogueur IDE pour activer l’ordinateur hôte et la langue initiée par le débogage. Il établit une session de débogage pour une application en cours d’exécution. Cette interface est implémentée par le Gestionnaire de débogage d’ordinateur.  
  
 Outre les méthodes héritées de `IUnknown`, le `IDebugSessionProvider` interface expose les méthodes suivantes.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
  
|Méthode|Description|  
|------------|-----------------|  
|[IDebugSessionProvider::StartDebugSession](../../winscript/reference/idebugsessionprovider-startdebugsession.md)|Lance une session de débogage avec l’application spécifiée.|