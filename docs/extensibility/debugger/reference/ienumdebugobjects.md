---
title: IEnumDebugObjects | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IEnumDebugObjects
helpviewer_keywords: IEnumDebugObjects interface
ms.assetid: 0950364c-6c8a-4b6c-ba37-c6aa359fa72c
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 20f2d7695cfed89bc38cb73e2f00216060e2d970
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="ienumdebugobjects"></a>IEnumDebugObjects
> [!IMPORTANT]
>  Dans Visual Studio 2015, ce moyen d’implémenter des évaluateurs d’expression est déconseillée. Pour plus d’informations sur l’implémentation des évaluateurs d’expression CLR, consultez [évaluateurs d’Expression CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) et [exemple d’évaluateur d’Expression managé](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Cette interface représente une collection d’objets implémentant le [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) interface.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IEnumDebugObjects : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notes pour les implémenteurs  
 L’évaluateur d’expression implémente cette interface pour fournir des ensembles d’objets qui implémentent la [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) interface. Notez qu’il ne s’agit pas d’une énumération COM standard en raison de la présence de la [GetCount](../../../extensibility/debugger/reference/ienumdebugobjects-getcount.md) (méthode).  
  
## <a name="notes-for-callers"></a>Remarques pour les appelants  
 [GetElements](../../../extensibility/debugger/reference/idebugarrayobject-getelements.md) retourne cette interface.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l’ordre Vtable  
 Cette interface implémente les méthodes suivantes.  
  
|Méthode|Description|  
|------------|-----------------|  
|[Next](../../../extensibility/debugger/reference/ienumdebugobjects-next.md)|Récupère l’ensemble suivant de [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) objets à partir de l’énumération.|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugobjects-skip.md)|Ignore un nombre spécifié d’entrées.|  
|[Réinitialiser](../../../extensibility/debugger/reference/ienumdebugobjects-reset.md)|Réinitialise l’énumération à la première entrée.|  
|[Clone](../../../extensibility/debugger/reference/ienumdebugobjects-clone.md)|Récupère une copie de l’énumération actuelle.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugobjects-getcount.md)|Récupère le nombre d’entrées dans l’énumération.|  
  
## <a name="remarks"></a>Remarques  
 Cette interface permet à un moteur de débogage pour énumérer un ensemble d’objets dans un tableau.  
  
## <a name="requirements"></a>Spécifications  
 En-tête : ee.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)   
 [GetElements](../../../extensibility/debugger/reference/idebugarrayobject-getelements.md)