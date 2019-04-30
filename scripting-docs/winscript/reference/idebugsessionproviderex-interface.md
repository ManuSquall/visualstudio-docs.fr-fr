---
title: Interface IDebugSessionProviderEx | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 26c5da2d-8c93-4d2b-94d2-97aaa377dcfe
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c9bf341adeaeb17c8986b1b30b12f58113aef562
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62978994"
---
# <a name="idebugsessionproviderex-interface"></a>IDebugSessionProviderEx, interface
L’interface principale fournie par un débogueur IDE pour activer le débogage d’initiée par l’hôte et par le langage. Il établit une session de débogage pour une application en cours d’exécution. Cette interface est implémentée par le Gestionnaire de débogage d’ordinateur.  
  
 Outre les méthodes héritées de `IUnknown`, le `IDebugSessionProviderEx` interface expose les méthodes suivantes.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
  
|Méthode|Description|  
|------------|-----------------|  
|[IDebugSessionProviderEx:CanJITDebug](../../winscript/reference/idebugsessionproviderex-canjitdebug.md)|Détermine si le débogage juste à temps est possible avec l’application spécifiée.|  
|[IDebugSessionProviderEx:StartDebugSession](../../winscript/reference/idebugsessionproviderex-startdebugsession.md)|Lance une session de débogage avec l’application spécifiée.|