---
title: IEnumDebugPorts2 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IEnumDebugPorts2
helpviewer_keywords:
- IEnumDebugPorts2
ms.assetid: 1754eef3-cf62-42e0-b218-1911acba77d4
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 07018391b51424b65bf1e8b9040f637f6f22213e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="ienumdebugports2"></a>IEnumDebugPorts2
Cette interface énumère les ports d’un fournisseur de l’ordinateur ou le port.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IEnumDebugPorts2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notes pour les implémenteurs  
 Un fournisseur de port personnalisé implémente cette interface pour représenter une liste de ports créé par le fournisseur. Visual Studio implémente cette interface pour prendre en charge son propre fournisseur de port.  
  
## <a name="notes-for-callers"></a>Remarques pour les appelants  
 Appelez [EnumPorts](../../../extensibility/debugger/reference/idebugportsupplier2-enumports.md) pour obtenir cette interface qui représente une liste de ports créé par le fournisseur de port. Appelez [EnumPersistedPorts](../../../extensibility/debugger/reference/idebugportsupplier3-enumpersistedports.md) pour obtenir cette interface qui représente une liste de ports qui ont été enregistrés sur le disque.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
 Le tableau suivant présente les méthodes de `IEnumDebugPorts2`.  
  
|Méthode|Description|  
|------------|-----------------|  
|[Next](../../../extensibility/debugger/reference/ienumdebugports2-next.md)|Récupère un nombre spécifié de ports dans une séquence d’énumération.|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugports2-skip.md)|Ignore un nombre spécifié de ports dans une séquence d’énumération.|  
|[Réinitialiser](../../../extensibility/debugger/reference/ienumdebugports2-reset.md)|Réinitialise la séquence d’énumération au début.|  
|[Clone](../../../extensibility/debugger/reference/ienumdebugports2-clone.md)|Crée un énumérateur qui contient le même état d’énumération que l’énumérateur actuel.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugports2-getcount.md)|Obtient le nombre de ports d’un énumérateur.|  
  
## <a name="remarks"></a>Notes  
 Visual Studio utilise cette interface pour aider à remplir une liste des ports utilisés pour l’attachement au processus.  
  
 En règle générale, un moteur de débogage n’utilise pas cette interface.  
  
## <a name="requirements"></a>Spécifications  
 En-tête : msdbg.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [EnumPorts](../../../extensibility/debugger/reference/idebugcoreserver2-enumports.md)   
 [EnumPorts](../../../extensibility/debugger/reference/idebugportsupplier2-enumports.md)