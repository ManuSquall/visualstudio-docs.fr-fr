---
title: Interface IEnumDebugCodeContexts | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IEnumDebugCodeContexts interface
ms.assetid: 47f17dc9-14bc-43c8-b874-00b5802076eb
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4e90e19a4bd12dfeeeef1b8f5498f729aa076adb
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2019
ms.locfileid: "58156045"
---
# <a name="ienumdebugcodecontexts-interface"></a>IEnumDebugCodeContexts, interface
Énumère les contextes de code qui correspondent à un contexte de document.  
  
 Outre les méthodes héritées de `IUnknown`, le `IEnumDebugCodeContexts` interface expose les méthodes suivantes.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
  
|Méthode|Description|  
|------------|-----------------|  
|[IEnumDebugCodeContexts::Next](../../winscript/reference/ienumdebugcodecontexts-next.md)|Récupère un nombre spécifié de segments dans la séquence d’énumération.|  
|[IEnumDebugCodeContexts::Skip](../../winscript/reference/ienumdebugcodecontexts-skip.md)|Ignore un nombre spécifié de segments dans une séquence d’énumération.|  
|[IEnumDebugCodeContexts::Reset](../../winscript/reference/ienumdebugcodecontexts-reset.md)|Réinitialise une séquence d’énumération au début.|  
|[IEnumDebugCodeContexts::Clone](../../winscript/reference/ienumdebugcodecontexts-clone.md)|Crée un énumérateur qui contient le même état que l’énumérateur en cours.|