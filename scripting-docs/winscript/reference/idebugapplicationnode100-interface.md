---
title: IDebugApplicationNode100 (Interface) | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- IDebugApplicationNode100 Interface
ms.assetid: 43966d4e-5f89-4a04-a08d-782347d00c2d
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: af79614d38ef55776b660329f51931be70b7f52e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="idebugapplicationnode100-interface"></a>IDebugApplicationNode100 (interface)
Le `IDebugApplicationNode100` interface étend les fonctionnalités de la [IDebugApplicationNode (Interface)](../../winscript/reference/idebugapplicationnode-interface.md). Vous pouvez obtenir une instance de cette interface en appelant QueryInterface sur une implémentation de [IDebugApplicationNode (Interface)](../../winscript/reference/idebugapplicationnode-interface.md).  
  
> [!IMPORTANT]
>  Cette interface est implémentée par PDM v10.0 et supérieures. Trouvée dans activdbg100.h.  
  
## <a name="methods"></a>Méthodes  
 L'interface `IDebugApplicationNode100` expose les méthodes suivantes :  
  
|Méthode|Description|  
|------------|-----------------|  
|[IDebugApplicationNode100::GetExcludedDocuments](../../winscript/reference/idebugapplicationnode100-getexcludeddocuments.md)|Obtient les documents de texte qui sont masqués par le filtre spécifié.|  
|[IDebugApplicationNode100::QueryIsChildNode](../../winscript/reference/idebugapplicationnode100-queryischildnode.md)|Détermine si le document spécifié appartient à un des nœuds enfants de ce nœud.|  
|[IDebugApplicationNode100::SetFilterForEventSink](../../winscript/reference/idebugapplicationnode100-setfilterforeventsink.md)|Définit le filtre sur un particulier [idebugapplicationnodeevents, Interface](../../winscript/reference/idebugapplicationnodeevents-interface.md) implémentation. Il permet de filtrer les nœuds d’application générées par le compilateur l’enfant afin que le PDM n’envoie plus les événements lorsque les nœuds sont créés ou supprimés, les débogueurs de script. Par défaut, tous les nœuds seront envoyées.|