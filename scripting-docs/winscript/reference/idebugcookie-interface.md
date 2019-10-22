---
title: Interface IDebugCookie | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugCookie interface
ms.assetid: 0dbc75d9-6f33-400f-a5bf-9122cf534082
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 47b48b917ee3376c417beffd9972d76a444513ef
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573196"
---
# <a name="idebugcookie-interface"></a>IDebugCookie, interface
Permet de définir le cookie de débogage pour une utilisation avec l’interface `IMachineDebugManagerCookie`. Pour plus d’informations, consultez [IMachineDebugManagerCookie interface](../../winscript/reference/imachinedebugmanagercookie-interface.md). Cette interface est implémentée par le gestionnaire de débogage de processus (PDM) et utilisée par les débogueurs de script.  
  
## <a name="methods"></a>Méthodes  
 En plus des méthodes héritées de `IUnknown`, l’interface `IDebugCookie` expose les méthodes suivantes.  
  
|Méthode|Description|  
|------------|-----------------|  
|[IDebugCookie::SetDebugCookie](../../winscript/reference/idebugcookie-setdebugcookie.md)|Définit le cookie de l’application de débogage.|  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IMachineDebugManagerCookie](../../winscript/reference/imachinedebugmanagercookie-interface.md)