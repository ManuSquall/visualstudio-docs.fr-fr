---
title: Implémentation de visualiseurs de Type et les visionneuses personnalisées | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], custom viewer
- debugging [Debugging SDK], type visualizer
ms.assetid: abef18c0-8272-4451-b82a-b4624edaba7d
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b8a515fb184d43478c07723e7fe1b15a15e99f50
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "55037380"
---
# <a name="implement-type-visualizers-and-custom-viewers"></a>Implémenter des visualiseurs de type et les visionneuses personnalisées
> [!IMPORTANT]
>  Dans Visual Studio 2015, ce moyen d’implémenter des évaluateurs d’expression est déconseillée. Pour plus d’informations sur l’implémentation des évaluateurs d’expression CLR, consultez [évaluateurs d’expression CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) et [exemple d’évaluateur d’expression managé](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample). 
  
 Visualiseurs de type et les visionneuses personnalisées permettent à un utilisateur d’afficher les données d’un type particulier d’une manière qui est plus significative qu’un vidage hexadécimal simple de nombres. Un évaluateur d’expression (EE) pouvez associer des visionneuses personnalisées à des types de données ou des variables. Ces visionneuses personnalisées sont implémentées par le EE. Le EE peut prennent également en charge les visualiseurs de type externe, qui peuvent provenir d’un autre fournisseur tiers ou même l’utilisateur final.  
  
## <a name="discussion"></a>Discussion  
  
### <a name="type-visualizers"></a>Visualiseurs de type  
 Visual Studio vous demande pour obtenir la liste de visualiseurs de type et des visionneuses personnalisées pour chaque objet à afficher dans une fenêtre Espion. Un évaluateur d’expression (EE) fournit une telle liste pour chaque type pour lequel il souhaite prendre en charge les visualiseurs de type et les visionneuses personnalisées. Les appels à [GetCustomViewerCount](../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md) et [GetCustomViewerList](../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) démarrer l’ensemble du processus d’accéder aux visualiseurs de type et les visionneuses personnalisées (voir [visualisation et affichage des données](../../extensibility/debugger/visualizing-and-viewing-data.md)pour plus d’informations sur la séquence d’appel).  
  
### <a name="custom-viewers"></a>Visionneuses personnalisées  
 Visionneuses personnalisées sont implémentées dans le EE pour un type de données spécifique et sont représentées par le [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md) interface. Une visionneuse personnalisée n’est pas aussi flexible qu’un visualiseur de type, dans la mesure où il est disponible uniquement lorsque le EE qui implémente cette visionneuse personnalisée particulière est en cours d’exécution. L’implémentation d’une visionneuse personnalisée est plus simple que celle prise en charge des visualiseurs de type. Toutefois, prenant en charge les visualiseurs de type y offre une flexibilité maximale à l’utilisateur final pour visualiser leurs données. Le reste de cet article concerne uniquement les visualiseurs de type.  
  
## <a name="interfaces"></a>Interfaces  
 Le EE implémente les interfaces suivantes pour prendre en charge les visualiseurs de type, pour être utilisées par Visual Studio :  
  
- [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md)  
  
- [IPropertyProxyEESide](../../extensibility/debugger/reference/ipropertyproxyeeside.md)  
  
- [IPropertyProxyProvider](../../extensibility/debugger/reference/ipropertyproxyprovider.md)  
  
- [IEEDataStorage](../../extensibility/debugger/reference/ieedatastorage.md)  
  
- [IDebugProperty3](../../extensibility/debugger/reference/idebugproperty3.md)  
  
- [IDebugObject](../../extensibility/debugger/reference/idebugobject.md)  
  
  Le EE consomme les interfaces suivantes pour prendre en charge les visualiseurs de type :  
  
- [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md)  
  
- [IEEVisualizerServiceProvider](../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)  
  
- [IDebugBinder3](../../extensibility/debugger/reference/idebugbinder3.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Écriture d’un évaluateur d’expression de CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)   
 [Visualisation et affichage des données](../../extensibility/debugger/visualizing-and-viewing-data.md)   
 [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md)