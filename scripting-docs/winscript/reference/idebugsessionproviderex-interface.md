---
title: Interface IDebugSessionProviderEx | Microsoft Docs
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
ms.openlocfilehash: fae1cf673f47d3be586f83320b2d2c38c817e2cf
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/16/2019
ms.locfileid: "54349216"
---
# <a name="idebugsessionproviderex-interface"></a>IDebugSessionProviderEx, interface
L’interface principale fournie par un débogueur IDE pour activer le débogage d’initiée par l’hôte et par le langage. Il établit une session de débogage pour une application en cours d’exécution. Cette interface est implémentée par le Gestionnaire de débogage d’ordinateur.  
  
 Outre les méthodes héritées de `IUnknown`, le `IDebugSessionProviderEx` interface expose les méthodes suivantes.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
  
|Méthode|Description|  
|------------|-----------------|  
|[IDebugSessionProviderEx:CanJITDebug](../../winscript/reference/idebugsessionproviderex-canjitdebug.md)|Détermine si le débogage juste à temps est possible avec l’application spécifiée.|  
|[IDebugSessionProviderEx:StartDebugSession](../../winscript/reference/idebugsessionproviderex-startdebugsession.md)|Lance une session de débogage avec l’application spécifiée.|