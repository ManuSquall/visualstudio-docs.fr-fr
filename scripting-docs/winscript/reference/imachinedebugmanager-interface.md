---
title: Interface IMachineDebugManager | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IMachineDebugManager interface
ms.assetid: 0b7133bb-5a52-4036-b4db-d69260790db7
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9d491b03ba04d346e3a14a08d5e2b6b9d34c7d97
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573922"
---
# <a name="imachinedebugmanager-interface"></a>IMachineDebugManager, interface
Interface principale du gestionnaire de débogage de l’ordinateur. Cette interface est similaire à l’interface `IMachineDebugManagerCookie`.  
  
 En plus des méthodes héritées de `IUnknown`, l’interface `IMachineDebugManager` expose les méthodes suivantes.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
  
|Méthode|Description|  
|------------|-----------------|  
|[IMachineDebugManager::AddApplication](../../winscript/reference/imachinedebugmanager-addapplication.md)|Ajoute une application à la liste des applications en cours d’exécution.|  
|[IMachineDebugManager::RemoveApplication](../../winscript/reference/imachinedebugmanager-removeapplication.md)|Supprime une application de la liste des applications en cours d’exécution.|  
|[IMachineDebugManager::EnumApplications](../../winscript/reference/imachinedebugmanager-enumapplications.md)|Retourne un énumérateur de la liste actuelle des applications en cours d’exécution.|  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IMachineDebugManagerCookie](../../winscript/reference/imachinedebugmanagercookie-interface.md)