---
title: IEnumDebugObjects | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IEnumDebugObjects
helpviewer_keywords:
- IEnumDebugObjects interface
ms.assetid: 0950364c-6c8a-4b6c-ba37-c6aa359fa72c
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c6956135476798445fed8352e8d6ca0677949a36
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58953986"
---
# <a name="ienumdebugobjects"></a>IEnumDebugObjects
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

> [!IMPORTANT]
>  Dans Visual Studio 2015, ce moyen d’implémenter des évaluateurs d’expression est déconseillée. Pour plus d’informations sur l’implémentation des évaluateurs d’expression CLR, consultez [évaluateurs d’Expression CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) et [exemple d’évaluateur d’Expression gérés](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Cette interface représente une collection d’objets qui implémentent le [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) interface.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IEnumDebugObjects : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notes de publication pour les implémenteurs  
 L’évaluateur d’expression implémente cette interface pour fournir des ensembles d’objets qui implémentent le [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) interface. Notez qu’il ne s’agit pas d’une énumération COM standard en raison de la présence de la [GetCount](../../../extensibility/debugger/reference/ienumdebugobjects-getcount.md) (méthode).  
  
## <a name="notes-for-callers"></a>Notes de publication pour les appelants  
 [GetElements](../../../extensibility/debugger/reference/idebugarrayobject-getelements.md) retourne cette interface.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l’ordre Vtable  
 Cette interface implémente les méthodes suivantes.  
  
|Méthode|Description|  
|------------|-----------------|  
|[Next](../../../extensibility/debugger/reference/ienumdebugobjects-next.md)|Récupère l’ensemble suivant de [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) objets à partir de l’énumération.|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugobjects-skip.md)|Ignore un nombre spécifié d’entrées.|  
|[Reset](../../../extensibility/debugger/reference/ienumdebugobjects-reset.md)|Réinitialise l’énumération à la première entrée.|  
|[Clone](../../../extensibility/debugger/reference/ienumdebugobjects-clone.md)|Récupère une copie de l’énumération actuelle.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugobjects-getcount.md)|Récupère le nombre d’entrées dans l’énumération.|  
  
## <a name="remarks"></a>Notes  
 Cette interface permet à un moteur de débogage énumérer un ensemble d’objets dans un tableau.  
  
## <a name="requirements"></a>Configuration requise  
 En-tête : ee.h  
  
 Espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)   
 [GetElements](../../../extensibility/debugger/reference/idebugarrayobject-getelements.md)
