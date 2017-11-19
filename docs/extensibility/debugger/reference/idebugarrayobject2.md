---
title: IDebugArrayObject2 | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: IDebugArrayObject2 interface
ms.assetid: be6e504d-4ab3-4141-a61b-0953ee0e038e
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1363f2cf7ad14c6d95dcf710d3489172857a9587
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="idebugarrayobject2"></a>IDebugArrayObject2
> [!IMPORTANT]
>  Dans Visual Studio 2015, ce moyen d’implémenter des évaluateurs d’expression est déconseillée. Pour plus d’informations sur l’implémentation des évaluateurs d’expression CLR, consultez [évaluateurs d’Expression CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) et [exemple d’évaluateur d’Expression managé](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Représente un objet de tableau managé et permet à un évaluateur d’expression (EE) pour déterminer l’index de base (limites inférieures) pour le tableau.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDebugArrayObject2 : IDebugArrayObject  
```  
  
## <a name="notes-for-implementers"></a>Notes pour les implémenteurs  
 Cela est implémenté par le moteur de débogage managés (DE).  
  
## <a name="methods"></a>Méthodes  
 Outre les méthodes sur le [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md) interface, cette interface implémente les méthodes suivantes :  
  
|Méthode|Description|  
|------------|-----------------|  
|[GetBaseIndices](../../../extensibility/debugger/reference/idebugarrayobject2-getbaseindices.md)|Récupère l’index de base (limites inférieures) pour chaque index étant donné le nombre de dimensions dans le tableau.|  
|[HasBaseIndices](../../../extensibility/debugger/reference/idebugarrayobject2-hasbaseindices.md)|Détermine si le tableau comporte des index de base (limites inférieures) défini.|  
  
## <a name="remarks"></a>Remarques  
 Évaluateur d’expression utilise cette interface pour représenter des tableaux managés dans une arborescence d’analyse.  
  
## <a name="requirements"></a>Spécifications  
 En-tête : Ee.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll