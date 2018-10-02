---
title: IDebugProperty2 | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugProperty2
helpviewer_keywords:
- IDebugProperty2 interface
ms.assetid: a7d5c70f-a1a5-4120-9f70-184e01c25bff
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8c728c2e4955d35e2954fbda0a4a4432c550666d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47506944"
---
# <a name="idebugproperty2"></a>IDebugProperty2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [IDebugProperty2](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugproperty2).  
  
Cette interface représente une propriété de frame de pile, une propriété de document du programme ou une autre propriété. La propriété est généralement le résultat d’une évaluation d’expression.  
  
> [!NOTE]
>  Cette utilisation de « property » ne doit pas être confondue avec cette variable de membre d’une classe, ce qui signifie que même si un `IDebugProperty2` peut représenter une telle entité.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDebugProperty2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notes de publication pour les implémenteurs  
 Le D’implémente cette interface pour représenter un type particulier de valeur. Par exemple, la valeur peut être une valeur numérique à la suite d’une évaluation d’expression, un contexte de mémoire utilisé pour afficher la mémoire, ou une liste de registres et leurs valeurs.  
  
## <a name="notes-for-callers"></a>Notes de publication pour les appelants  
 Appelez [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) ou [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) pour obtenir cette interface, qui représente le résultat de l’évaluation. `IDebugExpression2::EvaluateAsync` Retourne cette interface en envoyant un [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) interface pour le SDM, qui à son tour appelle [GetResult](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getresult.md) pour récupérer la propriété.  
  
 [GetDebugProperty](../../../extensibility/debugger/reference/idebugpropertycreateevent2-getdebugproperty.md) retourne cette interface pour fournir le document de script associé.  
  
 [GetReturnValue](../../../extensibility/debugger/reference/idebugreturnvalueevent2-getreturnvalue.md) retourne cette interface pour représenter la valeur de retour d’une fonction.  
  
 [GetDebugProperty](../../../extensibility/debugger/reference/idebugprogram2-getdebugproperty.md) retourne cette interface pour représenter les différentes propriétés du programme comme un nom ou un contexte de la mémoire.  
  
 [GetDebugProperty](../../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md) retourne cette interface pour représenter les différentes propriétés du frame de pile tels que des variables locales.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
 Le tableau suivant présente les méthodes de `IDebugProperty2`.  
  
|Méthode|Description|  
|------------|-----------------|  
|[GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)|Renseigne un [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) structure qui décrit une propriété.|  
|[SetValueAsString](../../../extensibility/debugger/reference/idebugproperty2-setvalueasstring.md)|Définit la valeur d’une propriété à partir d’une chaîne.|  
|[SetValueAsReference](../../../extensibility/debugger/reference/idebugproperty2-setvalueasreference.md)|Définit la valeur de la propriété à partir de la valeur d’une référence donnée.|  
|[EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)|Énumère les enfants d’une propriété.|  
|[GetParent](../../../extensibility/debugger/reference/idebugproperty2-getparent.md)|Retourne le parent d’une propriété.|  
|[GetDerivedMostProperty](../../../extensibility/debugger/reference/idebugproperty2-getderivedmostproperty.md)|Retourne la propriété qui décrit la propriété la plus dérivée d’une propriété.|  
|[GetMemoryBytes](../../../extensibility/debugger/reference/idebugproperty2-getmemorybytes.md)|Retourne les octets de mémoire qui composent la valeur d’une propriété.|  
|[GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md)|Retourne le contexte de la mémoire pour une valeur de propriété.|  
|[GetSize](../../../extensibility/debugger/reference/idebugproperty2-getsize.md)|Retourne la taille, en octets, de la valeur de propriété.|  
|[GetReference](../../../extensibility/debugger/reference/idebugproperty2-getreference.md)|Retourne une référence à la valeur de cette propriété.|  
|[GetExtendedInfo](../../../extensibility/debugger/reference/idebugproperty2-getextendedinfo.md)|Retourne les informations étendues d’une propriété.|  
  
## <a name="remarks"></a>Notes  
 Une propriété, telle que représentée par un `IDebugProperty2` l’interface, peut être considéré comme une valeur avec un nom, un type et une adresse. Dans des conditions plus générales, un `IDebugProperty2` peut représenter tout ce qui a une structure hiérarchique, avec les parents et nœuds enfants.  
  
 Une propriété est généralement transitoire, une durée d’uniquement tant que le frame de pile actuel, par exemple. En revanche, une référence, telle que représentée par un [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) d’interface, est valable tant que la valeur reste en mémoire.  
  
 L’IDE peut utiliser le `IDebugProperty2` interface pour permettre aux utilisateurs de parcourir et modifier les propriétés au moment de l’exécution.  
  
## <a name="requirements"></a>Configuration requise  
 En-tête : msdbg.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces principales](../../../extensibility/debugger/reference/core-interfaces.md)   
 [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)   
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)

