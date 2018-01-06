---
title: IEEVisualizerDataProvider | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IEEVisualizerDataProvider
helpviewer_keywords: IEEVisualizerDataProvider interface
ms.assetid: 5fdfe6e3-b94e-4edb-acc5-41d8773d8ca5
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: edf2cfe689caa58e1c0402a91fa31237cb2c7215
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ieevisualizerdataprovider"></a>IEEVisualizerDataProvider
> [!IMPORTANT]
>  Dans Visual Studio 2015, ce moyen d’implémenter des évaluateurs d’expression est déconseillée. Pour plus d’informations sur l’implémentation des évaluateurs d’expression CLR, consultez [évaluateurs d’Expression CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) et [exemple d’évaluateur d’Expression managé](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Cette interface fournit la capacité de modifier la valeur d’un objet via un visualiseur de type.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IEEVisualizerDataProvider : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notes pour les implémenteurs  
 L’évaluateur d’expression implémente cette interface pour prendre en charge la modification des données sur un objet de propriété via un visualiseur de type.  
  
## <a name="notes-for-callers"></a>Remarques pour les appelants  
 Cette interface est utilisée pour la création du [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md) objet via un appel à [CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md). Consultez [Visualizing et affichage des données](../../../extensibility/debugger/visualizing-and-viewing-data.md) pour plus d’informations.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l’ordre Vtable  
  
|Méthode|Description|  
|------------|-----------------|  
|[CanSetObjectForVisualizer](../../../extensibility/debugger/reference/ieevisualizerdataprovider-cansetobjectforvisualizer.md)|Détermine s’il est possible de mettre à jour l’objet (et par la suite, sa valeur) qui est représentant ce visualiseur.|  
|[GetNewObjectForVisualizer](../../../extensibility/debugger/reference/ieevisualizerdataprovider-getnewobjectforvisualizer.md)|Force une nouvelle évaluation de l’objet pour le visualiseur.|  
|[GetObjectForVisualizer](../../../extensibility/debugger/reference/ieevisualizerdataprovider-getobjectforvisualizer.md)|Obtient un objet existant de ce visualiseur (aucune évaluation n’est effectuée).|  
|[SetObjectForVisualizer](../../../extensibility/debugger/reference/ieevisualizerdataprovider-setobjectforvisualizer.md)|Met à jour l’objet pour le visualiseur, modifiant ainsi la valeur que présente du visualiseur.|  
  
## <a name="remarks"></a>Notes  
 Le service de visualiseur (telle que représentée par le [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md) de l’interface et retournée par [CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md)) conserve une référence à l’objet qui implémente le `IEEVisualizerDataProvider` interface . Par conséquent, le `IEEVisualizerDataProvider` interface ne doit pas être implémenté sur le même objet qui implémente le [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) si cet objet conserve une référence à la `IEEVisualizerService` objet : résultats de la référence circulaire et une un blocage se produit lorsque les objets sont détruits. L’approche recommandée consiste à implémenter `IEEVisualizerDataProvider` sur un objet distinct dans lequel le `IDebugProperty2` sans appeler les délégués de l’objet `IUnknown::AddRef` dessus.  
  
## <a name="requirements"></a>Configuration requise  
 En-tête : ee.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces de l’évaluation d’expression](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)   
 [IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)   
 [Visualisation et affichage des données](../../../extensibility/debugger/visualizing-and-viewing-data.md)