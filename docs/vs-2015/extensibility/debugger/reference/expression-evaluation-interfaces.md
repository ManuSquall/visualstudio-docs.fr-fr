---
title: Interfaces d’évaluation d’expression | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- expression evaluation, interfaces
ms.assetid: 2d259f60-2cd7-460e-b02d-24a8fb202850
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8a710019390120768b665cf3b27174831a67f0cc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90839473"
---
# <a name="expression-evaluation-interfaces"></a>Interfaces d’évaluation des expressions
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

> [!IMPORTANT]
> Dans Visual Studio 2015, cette façon d’implémenter les évaluateurs d’expression est déconseillée. Pour plus d’informations sur l’implémentation des évaluateurs d’expression CLR, consultez [évaluateur d’expression CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) et [exemple évaluateur d’expression managée](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Voici les interfaces d’évaluation d’expression pour le [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] Kit de développement logiciel (SDK) de débogage.  
  
## <a name="discussion"></a>Discussion  
 Ces interfaces sont utilisées pour évaluer des expressions dans une pile des appels en mode arrêt. Elles sont implémentées uniquement pour les évaluateurs d’expression de Common Language Runtime (EE).  
  
 Chaque interface du tableau indique le composant qui peut l’implémenter à partir de la liste suivante :  
  
- Moteur DE débogage (DE)  
  
- Évaluateur d’expression (EE)  
  
- Visual Studio (VS)  
  
|Interface|Implémenté par|Description|  
|---------------|--------------------|-----------------|  
|[IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)|EE|Représente un alias numérique pour une variable.|  
|[IDebugAlias2](../../../extensibility/debugger/reference/idebugalias2.md)|EE|Représente un alias numérique pour une variable et permet à un évaluateur d’expression (EE) d’obtenir le domaine d’application pour l’alias.|  
|[IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)|EE|Représente un objet tableau.|  
|[IDebugArrayObject2](../../../extensibility/debugger/reference/idebugarrayobject2.md)|EE|Représente un objet tableau managé et permet à un évaluateur d’expression (EE) de déterminer l’index de base (limites inférieures) du tableau.|  
|[IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)|DE|Représente un Binder qui lie des symboles de débogage à des adresses réelles en mémoire.|  
|[IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)|DE|Identique à l’interface [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) , mais permet d’accéder aux types, aux alias et aux visualiseurs personnalisés.|  
|[IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)|EE|Représente l'évaluateur d'expression.|  
|[IDebugExpressionEvaluator2](../../../extensibility/debugger/reference/idebugexpressionevaluator2.md)|EE|Représente une version améliorée d’un évaluateur d’expression (EE).|  
|[IDebugExpressionEvaluator3](../../../extensibility/debugger/reference/idebugexpressionevaluator3.md)|EE|Représente un évaluateur d’expression (EE) avec une arborescence d’analyseur améliorée.|  
|[IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)|EE|Représente une fonction.|  
|[IDebugFunctionObject2](../../../extensibility/debugger/reference/idebugfunctionobject2.md)|EE|Représente une fonction et améliore l’interface [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) .|  
|[IDebugIDECallback](../../../extensibility/debugger/reference/idebugidecallback.md)|DE|Active un évaluateur d’expression (EE) pour afficher un message dans la fenêtre sortie du débogueur.|  
|[IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md)|EE|Représente un objet de code managé.|  
|[IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)|EE|Interface de base qui représente tout symbole lié à une adresse mémoire.|  
|[IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)|EE|Identique à l’interface [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) , mais permet d’accéder à des informations supplémentaires.|  
|[IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md)|EE|Représente une expression analysée prête à être évaluée.|  
|[IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)|EE|Représente un pointeur.|  
|[IDebugPointerObject3](../../../extensibility/debugger/reference/idebugpointerobject3.md)|EE|Représente un pointeur dans une arborescence d’analyse et étend l’interface **IDebugPointerObject** .|  
|[IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)|EE|Offre la possibilité de modifier la valeur d’un type par le biais d’un visualiseur de type.|  
|[IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)|VS|Fournit l’accès aux visualiseurs personnalisés et aux visualiseurs de type.|  
|[IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)|VS|Offre la possibilité de créer un objet [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md) .|  
|[IEnumDebugObjects](../../../extensibility/debugger/reference/ienumdebugobjects.md)|EE|Représente une collection d’objets [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) .|  
  
## <a name="see-also"></a>Voir aussi  
 [Référence d’API](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)   
 [Écriture d’un évaluateur d’expression CLR](../../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)   
 [Visualiseur de type et visionneuse personnalisée](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
