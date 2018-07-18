---
title: Idebugsessionproviderex, Interface | Documents Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 26c5da2d-8c93-4d2b-94d2-97aaa377dcfe
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 545b60f13e86e59143ce0e57f454b13f61041f11
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24726929"
---
# <a name="idebugsessionproviderex-interface"></a>IDebugSessionProviderEx, interface
L’interface principale fournie par un débogueur IDE pour activer le débogage d’initiée par l’hôte et par le langage. Il établit une session de débogage pour une application en cours d’exécution. Cette interface est implémentée par la Machine Debug Manager.  
  
 Outre les méthodes héritées de `IUnknown`, le `IDebugSessionProviderEx` interface expose les méthodes suivantes.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
  
|Méthode|Description|  
|------------|-----------------|  
|[IDebugSessionProviderEx:CanJITDebug](../../winscript/reference/idebugsessionproviderex-canjitdebug.md)|Détermine si le débogage juste à temps est possible avec l’application spécifiée.|  
|[IDebugSessionProviderEx:StartDebugSession](../../winscript/reference/idebugsessionproviderex-startdebugsession.md)|Lance une session de débogage avec l’application spécifiée.|