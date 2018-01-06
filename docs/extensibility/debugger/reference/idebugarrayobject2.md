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
ms.workload: vssdk
ms.openlocfilehash: 13e522497a0046ebfc99c60c7c3d771acfd4fbca
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
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
  
## <a name="remarks"></a>Notes  
 Évaluateur d’expression utilise cette interface pour représenter des tableaux managés dans une arborescence d’analyse.  
  
## <a name="requirements"></a>Configuration requise  
 En-tête : Ee.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll