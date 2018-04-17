---
title: IEnumDebugModules2 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IEnumDebugModules2
helpviewer_keywords:
- IEnumDebugModules2
ms.assetid: 4fe28074-a960-41ad-b74d-b57f04c0c0ad
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: dd3ca02776aae4a7b4cd22485eba9827f4731d5d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="ienumdebugmodules2"></a>IEnumDebugModules2
Cette interface énumère une liste de modules.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IEnumDebugModules2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notes pour les implémenteurs  
 Le moteur de débogage (DE) implémente cette interface pour représenter une liste de modules chargés pour un programme.  
  
## <a name="notes-for-callers"></a>Remarques pour les appelants  
 Appels de Visual Studio [EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md) pour obtenir cette interface.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
 Le tableau suivant présente les méthodes de `IEnumDebugModules2`.  
  
|Méthode|Description|  
|------------|-----------------|  
|[Next](../../../extensibility/debugger/reference/ienumdebugmodules2-next.md)|Récupère un nombre spécifié de modules dans une séquence d’énumération.|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugmodules2-skip.md)|Ignore un nombre spécifié de modules dans une séquence d’énumération.|  
|[Réinitialiser](../../../extensibility/debugger/reference/ienumdebugmodules2-reset.md)|Réinitialise la séquence d’énumération au début.|  
|[Clone](../../../extensibility/debugger/reference/ienumdebugmodules2-clone.md)|Crée un énumérateur qui contient le même état d’énumération que l’énumérateur actuel.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugmodules2-getcount.md)|Obtient le nombre de modules.|  
  
## <a name="remarks"></a>Notes  
 Visual Studio utilise cette interface principalement pour mettre à jour le **Modules** fenêtre.  
  
 Dans le cadre du débogage dans Visual Studio, un programme est une séquence logique d’instructions de code qui traversent les limites de module, par conséquent, la nécessité d’une liste de modules pour un seul [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) interface. Le premier module dans la liste contient généralement le point d’entrée initiale pour le programme associé.  
  
## <a name="requirements"></a>Spécifications  
 En-tête : msdbg.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md)