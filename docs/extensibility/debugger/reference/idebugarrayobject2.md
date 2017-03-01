---
title: IDebugArrayObject2 | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IDebugArrayObject2 interface
ms.assetid: be6e504d-4ab3-4141-a61b-0953ee0e038e
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 35f267fc6b7cecd252119e1b8edc2557decf6483
ms.lasthandoff: 02/22/2017

---
# <a name="idebugarrayobject2"></a>IDebugArrayObject2
> [!IMPORTANT]
>  Dans Visual Studio 2015, ce moyen d’implémenter des évaluateurs d’expression est déconseillée. Pour plus d’informations sur l’implémentation des évaluateurs d’expression CLR, consultez [évaluateurs d’Expression CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) et [exemple d’évaluateur d’Expression gérés](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Représente un objet de tableau managé et permet un évaluateur d’expression (EE) pour déterminer l’index de base (limite inférieure) pour le tableau.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDebugArrayObject2 : IDebugArrayObject  
```  
  
## <a name="notes-for-implementers"></a>Notes relatives à l’attention des implémenteurs  
 Cela est implémenté par le moteur de débogage managés (DE).  
  
## <a name="methods"></a>Méthodes  
 Outre les méthodes sur le [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md) interface, cette interface implémente les méthodes suivantes :  
  
|Méthode|Description|  
|------------|-----------------|  
|[GetBaseIndices](../../../extensibility/debugger/reference/idebugarrayobject2-getbaseindices.md)|Récupère l’index de base (limite inférieure) pour chaque index étant donné le nombre de dimensions dans le tableau.|  
|[HasBaseIndices](../../../extensibility/debugger/reference/idebugarrayobject2-hasbaseindices.md)|Détermine si le tableau a des index de base (limite inférieure) défini.|  
  
## <a name="remarks"></a>Remarques  
 Un évaluateur d’expression utilise cette interface pour représenter les tableaux managés dans une arborescence d’analyse.  
  
## <a name="requirements"></a>Spécifications  
 En-tête : Ee.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll
