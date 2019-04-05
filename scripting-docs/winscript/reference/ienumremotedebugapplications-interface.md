---
title: Interface IEnumRemoteDebugApplications | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IEnumRemoteDebugApplications interface
ms.assetid: ceb5fbe7-d131-4352-9dd1-af80acd3f3f7
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 430551002bc7603d86f9c7fb624ec438734bd766
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2019
ms.locfileid: "58150619"
---
# <a name="ienumremotedebugapplications-interface"></a>IEnumRemoteDebugApplications, interface
Énumère les objets d’application. Cette interface peut être utilisée pour énumérer les applications en cours d’exécution sur un ordinateur pour une boîte de dialogue « Attacher à application ».  
  
 Outre les méthodes héritées de `IUnknown`, le `IEnumRemoteDebugApplications` interface expose les méthodes suivantes.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
  
|Méthode|Description|  
|------------|-----------------|  
|[IEnumRemoteDebugApplications::Clone](../../winscript/reference/ienumremotedebugapplications-clone.md)|Crée un énumérateur qui contient le même état que l’énumérateur en cours.|  
|[IEnumRemoteDebugApplications::Next](../../winscript/reference/ienumremotedebugapplications-next.md)|Récupère un nombre spécifié de segments dans une séquence d’énumération.|  
|[IEnumRemoteDebugApplications::Reset](../../winscript/reference/ienumremotedebugapplications-reset.md)|Réinitialise une séquence d’énumération au début.|  
|[IEnumRemoteDebugApplications::Skip](../../winscript/reference/ienumremotedebugapplications-skip.md)|Ignore un nombre spécifié de segments dans une séquence d’énumération.|