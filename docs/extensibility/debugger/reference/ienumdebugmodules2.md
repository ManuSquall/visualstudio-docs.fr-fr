---
title: IEnumDebugModules2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IEnumDebugModules2
helpviewer_keywords:
- IEnumDebugModules2
ms.assetid: 4fe28074-a960-41ad-b74d-b57f04c0c0ad
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a78023b8c09139368e736a32ae349c566457035a
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54928137"
---
# <a name="ienumdebugmodules2"></a>IEnumDebugModules2
Cette interface énumère une liste de modules.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IEnumDebugModules2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notes de publication pour les implémenteurs  
 Le moteur de débogage (dé) implémente cette interface pour représenter une liste de modules chargés pour un programme.  
  
## <a name="notes-for-callers"></a>Notes de publication pour les appelants  
 Les appels de Visual Studio [EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md) pour obtenir cette interface.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
 Le tableau suivant présente les méthodes de `IEnumDebugModules2`.  
  
|Méthode|Description|  
|------------|-----------------|  
|[Next](../../../extensibility/debugger/reference/ienumdebugmodules2-next.md)|Récupère un nombre spécifié de modules dans une séquence d’énumération.|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugmodules2-skip.md)|Ignore un nombre spécifié de modules dans une séquence d’énumération.|  
|[Reset](../../../extensibility/debugger/reference/ienumdebugmodules2-reset.md)|Réinitialise une séquence d’énumération au début.|  
|[Clone](../../../extensibility/debugger/reference/ienumdebugmodules2-clone.md)|Crée un énumérateur qui contient le même état d’énumération que l’énumérateur en cours.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugmodules2-getcount.md)|Obtient le nombre de modules.|  
  
## <a name="remarks"></a>Notes  
 Visual Studio utilise cette interface principalement pour mettre à jour le **Modules** fenêtre.  
  
 Dans le cadre du débogage dans Visual Studio, un programme est une séquence logique d’instructions de code qui peut franchir les limites de module, par conséquent, la nécessité d’une liste de modules pour un seul [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) interface. Le premier module dans la liste contient généralement le point d’entrée initiale pour le programme associé.  
  
## <a name="requirements"></a>Spécifications  
 En-tête : msdbg.h  
  
 Espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces principales](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md)