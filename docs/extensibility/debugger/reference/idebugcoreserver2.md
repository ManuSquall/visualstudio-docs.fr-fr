---
title: IDebugCoreServer2 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugCoreServer2
helpviewer_keywords:
- IDebugCoreServer2 interface
ms.assetid: 9c47d0a6-9eb1-464e-bd44-fa2b552d4d36
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ce3e4c0c933527a5db754dcd96de97283e6e8260
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31107564"
---
# <a name="idebugcoreserver2"></a>IDebugCoreServer2
Cette interface est utilisée pour représenter et obtenir des informations à partir d’un serveur sur un ordinateur sur le réseau.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDebugCoreServer2 : IUknown  
```  
  
## <a name="notes-for-implementers"></a>Notes pour les implémenteurs  
 Visual Studio implémente cette interface pour représenter un serveur. Chaque instance de Visual Studio crée une instance de cette interface.  
  
## <a name="notes-for-callers"></a>Remarques pour les appelants  
 Un fournisseur de port personnalisé reçoit cette interface dans un appel à [événement](../../../extensibility/debugger/reference/idebugportevents2-event.md).  
  
 Un moteur de débogage peut obtenir cette interface indirectement via un appel à [GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md) (qui retourne [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md), une interface qui est dérivée de `IDebugCoreServer2`).  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
 Le tableau suivant présente les méthodes de `IDebugCoreServer2`.  
  
|Méthode|Description|  
|------------|-----------------|  
|[GetMachineInfo](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineinfo.md)|Obtient le nom et les attributs d’un ordinateur.|  
|[GetMachineName](../../../extensibility/debugger/reference/idebugcoreserver2-getmachinename.md)|Obtient le nom d’un ordinateur.|  
|[GetPortSupplier](../../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)|Obtient un fournisseur de port qui existe sur un ordinateur.|  
|[GetPort](../../../extensibility/debugger/reference/idebugcoreserver2-getport.md)|Obtient un port qui existe déjà sur un ordinateur.|  
|[EnumPorts](../../../extensibility/debugger/reference/idebugcoreserver2-enumports.md)|Crée un énumérateur pour tous les ports sur un ordinateur.|  
|[EnumPortSuppliers](../../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md)|Crée un énumérateur pour tous les fournisseurs de port sur un ordinateur.|  
|[GetMachineUtilities_V7](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineutilities-v7.md)|Obtient les utilitaires d’ordinateur pour un ordinateur.|  
  
## <a name="remarks"></a>Notes  
 Cette interface est également utilisée par Visual Studio pour parcourir les processus qui s’exécutent sur des ordinateurs sur le réseau.  
  
## <a name="requirements"></a>Spécifications  
 En-tête : msdbg.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)   
 [Événement](../../../extensibility/debugger/reference/idebugportevents2-event.md)   
 [GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md)   
 [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)