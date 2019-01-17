---
title: Interface IDebugSessionProvider | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugSessionProvider interface
ms.assetid: 1b898423-7af9-44f5-8dda-987005309c99
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d6d17546d5461a1ad76b144bf2652672ab4aa675
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/16/2019
ms.locfileid: "54345147"
---
# <a name="idebugsessionprovider-interface"></a>IDebugSessionProvider, interface
La principale interface fournie par un débogueur IDE pour activer l’hôte et le langage initiée par le débogage. Il établit une session de débogage pour une application en cours d’exécution. Cette interface est implémentée par le Gestionnaire de débogage d’ordinateur.  
  
 Outre les méthodes héritées de `IUnknown`, le `IDebugSessionProvider` interface expose les méthodes suivantes.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
  
|Méthode|Description|  
|------------|-----------------|  
|[IDebugSessionProvider::StartDebugSession](../../winscript/reference/idebugsessionprovider-startdebugsession.md)|Lance une session de débogage avec l’application spécifiée.|