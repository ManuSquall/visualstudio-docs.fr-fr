---
title: "IDebugApplicationNode100 (interface) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugApplicationNode100 (interface)"
ms.assetid: 43966d4e-5f89-4a04-a08d-782347d00c2d
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# IDebugApplicationNode100 (interface)
L'interface d' `IDebugApplicationNode100` étend les fonctionnalités d' [IDebugApplicationNode, interface](../../winscript/reference/idebugapplicationnode-interface.md).  Vous pouvez obtenir une instance de cette interface en appelant QueryInterface sur une implémentation d' [IDebugApplicationNode, interface](../../winscript/reference/idebugapplicationnode-interface.md).  
  
> [!IMPORTANT]
>  Cette interface est implémentée par PDM v10.0 et supérieur.  Trouvé dans activdbg100.h.  
  
## Méthodes  
 L'interface `IDebugApplicationNode100` expose les méthodes suivantes :  
  
|Méthode|Description|  
|-------------|-----------------|  
|[IDebugApplicationNode100::GetExcludedDocuments](../../winscript/reference/idebugapplicationnode100-getexcludeddocuments.md)|Obtient les documents texte qui sont masqués par le filtre spécifié.|  
|[IDebugApplicationNode100::QueryIsChildNode](../../winscript/reference/idebugapplicationnode100-queryischildnode.md)|Détermine si le document spécifié appartient à l'un des nœuds enfants de ce nœud.|  
|[IDebugApplicationNode100::SetFilterForEventSink](../../winscript/reference/idebugapplicationnode100-setfilterforeventsink.md)|Définit le filtre sur une implémentation particulière d' [IDebugApplicationNodeEvents, interface](../../winscript/reference/idebugapplicationnodeevents-interface.md) .  Elle permet aux débogueurs de script pour filtrer les nœuds d'application enfants générés par le compilateur afin que le PDM n'envoie plusieurs événements lorsque les nœuds sont créés ou supprimés.  Par défaut, tous les nœuds sont envoyés.|