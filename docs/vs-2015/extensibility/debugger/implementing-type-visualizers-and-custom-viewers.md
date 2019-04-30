---
title: Implémentation de visualiseurs de Type et les visionneuses personnalisées | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], custom viewer
- debugging [Debugging SDK], type visualizer
ms.assetid: abef18c0-8272-4451-b82a-b4624edaba7d
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b780f2115400fd43e8915a5109c960cab99bf131
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63430225"
---
# <a name="implementing-type-visualizers-and-custom-viewers"></a>Implémentation de visualiseurs de type et de visionneuses personnalisées
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

> [!IMPORTANT]
> Dans Visual Studio 2015, ce moyen d’implémenter des évaluateurs d’expression est déconseillée. Pour plus d’informations sur l’implémentation des évaluateurs d’expression CLR, consultez [évaluateurs d’Expression CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) et [exemple d’évaluateur d’Expression gérés](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Visualiseurs de type et les visionneuses personnalisées autoriser un utilisateur à afficher les données d’un type particulier d’une manière qui est plus significative qu’un vidage hexadécimal simple de nombres. Un évaluateur d’expression (EE) pouvez associer des visionneuses personnalisées à des types de données ou des variables. Ces visionneuses personnalisées sont implémentées par le EE. Le EE peut prennent également en charge les visualiseurs de type externe, qui peuvent provenir d’un autre fournisseur tiers ou même l’utilisateur final.  
  
## <a name="discussion"></a>Discussion  
  
### <a name="type-visualizers"></a>Visualiseurs de type  
 Visual Studio vous demande pour obtenir la liste de visualiseurs de type et des visionneuses personnalisées pour chaque objet à afficher dans une fenêtre Espion. Un évaluateur d’expression (EE) fournit une telle liste pour chaque type pour lequel il souhaite prendre en charge les visualiseurs de type et les visionneuses personnalisées. Les appels à [GetCustomViewerCount](../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md) et [GetCustomViewerList](../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) démarrer l’ensemble du processus d’accéder aux visualiseurs de type et les visionneuses personnalisées (voir [visualisation et affichage des données](../../extensibility/debugger/visualizing-and-viewing-data.md)pour plus d’informations sur la séquence d’appel).  
  
### <a name="custom-viewers"></a>Visionneuses personnalisées  
 Visionneuses personnalisées sont implémentées dans le EE pour un type de données spécifique et sont représentées par le [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md) interface. Une visionneuse personnalisée n’est pas aussi flexible qu’un visualiseur de type, dans la mesure où il est disponible uniquement lorsque le EE qui implémente cette visionneuse personnalisée particulière est en cours d’exécution. L’implémentation d’une visionneuse personnalisée est plus simple que celle prise en charge des visualiseurs de type. Toutefois, prenant en charge les visualiseurs de type flexibilité maximale à l’utilisateur final pour visualiser ses données. Le reste de cet article concerne uniquement les visualiseurs de type.  
  
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
 [Écriture d’un évaluateur d’Expression de CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)   
 [Visualisation et affichage des données](../../extensibility/debugger/visualizing-and-viewing-data.md)   
 [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md)
