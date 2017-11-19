---
title: IEnumDebugReferenceInfo2 | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IEnumDebugReferenceInfo2
helpviewer_keywords: IEnumDebugReferenceInfo2
ms.assetid: 7ed01441-686f-4032-8268-a4c750f19f85
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b913f0eb4f3dfa4e1ff8fa5bf6719a8f6fed4e3a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="ienumdebugreferenceinfo2"></a>IEnumDebugReferenceInfo2
Cette interface énumère [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) structures.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IEnumDebugReferenceInfo2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notes pour les implémenteurs  
 Le moteur de débogage (DE) implémente cette interface dans le cadre de sa prise en charge pour les références aux objets en mémoire. Cette interface doit être implémentée uniquement si les références sont prises en charge.  
  
## <a name="notes-for-callers"></a>Remarques pour les appelants  
 Appels de Visual Studio [EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md) pour obtenir cette interface.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
 Le tableau suivant présente les méthodes de `IEnumDebugReferenceInfo2`.  
  
|Méthode|Description|  
|------------|-----------------|  
|[Next](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-next.md)|Récupère un nombre spécifié de [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) structures dans une séquence d’énumération.|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-skip.md)|Ignore un nombre spécifié de [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) structures dans la séquence d’énumération.|  
|[Réinitialiser](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-reset.md)|Réinitialise la séquence d’énumération au début.|  
|[Clone](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-clone.md)|Crée un énumérateur qui contient le même état d’énumération que l’énumérateur actuel.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-getcount.md)|Obtient le nombre de [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) structures dans un énumérateur.|  
  
## <a name="remarks"></a>Remarques  
 Une référence est essentiellement un type et une adresse, tandis qu’une propriété est un nom, un type et une adresse. Une référence persiste tant que l’objet référencé existe en mémoire. Consultez [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) pour plus d’informations.  
  
## <a name="requirements"></a>Spécifications  
 En-tête : msdbg.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)   
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)   
 [EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md)