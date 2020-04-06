---
title: Mise en œuvre de visualisateurs de type et de téléspectateurs personnalisés (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], custom viewer
- debugging [Debugging SDK], type visualizer
ms.assetid: abef18c0-8272-4451-b82a-b4624edaba7d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c2ebbb5c8e27df4ae4baf2d9a9f1c3314188e2b3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738509"
---
# <a name="implement-type-visualizers-and-custom-viewers"></a>Implémenter des visualisateurs de type et des téléspectateurs personnalisés
> [!IMPORTANT]
> Dans Visual Studio 2015, cette façon de mettre en œuvre les évaluateurs d’expression est dépréciée. Pour obtenir de l’information sur la mise en œuvre des évaluateurs de l’expression CLR, consultez [les évaluateurs de l’expression CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) et [l’échantillon d’évaluateur d’expression gérée](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Les visualisateurs de type et les téléspectateurs personnalisés permettent à un utilisateur de visualiser des données d’un type particulier d’une manière qui est plus significative qu’un simple dépotoir hexadecimal de nombres. Un évaluateur d’expression (EE) peut associer les téléspectateurs personnalisés à des types spécifiques de données ou de variables. Ces téléspectateurs personnalisés sont implémenté par l’EE. L’EE peut également prendre en charge les visualisateurs de type externe, qui peuvent provenir d’un autre fournisseur tiers ou même de l’utilisateur final.

## <a name="discussion"></a>Discussions

### <a name="type-visualizers"></a>Visualisateurs de type
 Visual Studio demande une liste de visualisateurs de type et de téléspectateurs personnalisés pour chaque objet à afficher dans une fenêtre de montre. Un évaluateur d’expression (EE) fournit une telle liste pour chaque type pour lequel il veut prendre en charge les visualisateurs de type et les téléspectateurs personnalisés. Les appels à [GetCustomViewerCount](../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md) et [GetCustomViewerList](../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) démarrent l’ensemble du processus d’accès aux visualisateurs de type et aux téléspectateurs personnalisés (voir [Visualizing et Visualizing Data](../../extensibility/debugger/visualizing-and-viewing-data.md) pour plus de détails sur la séquence d’appels).

### <a name="custom-viewers"></a>Téléspectateurs personnalisés
 Les téléspectateurs personnalisés sont implémentés dans l’EE pour un type de données spécifique et sont représentés par l’interface [IDebugCustomViewer.](../../extensibility/debugger/reference/idebugcustomviewer.md) Un visualiseur personnalisé n’est pas aussi flexible qu’un visualisateur de type, puisqu’il n’est disponible que lorsque l’EE qui implémente ce visualiseur personnalisé particulier exécute. La mise en œuvre d’un visualiseur personnalisé est plus simple que la mise en œuvre d’un support pour les visualisateurs de type. Toutefois, les visualisateurs de type supportant donnent une flexibilité maximale à l’utilisateur final pour visualiser ses données. Le reste de cette discussion ne concerne que les visualisateurs de type.

## <a name="interfaces"></a>Interfaces
 L’EE implémente les interfaces suivantes pour prendre en charge les visualisateurs de type, à consommer par Visual Studio :

- [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md)

- [IPropertyProxyEESide](../../extensibility/debugger/reference/ipropertyproxyeeside.md)

- [IPropertyProxyProvider](../../extensibility/debugger/reference/ipropertyproxyprovider.md)

- [IEEDataStorage](../../extensibility/debugger/reference/ieedatastorage.md)

- [IDebugProperty3](../../extensibility/debugger/reference/idebugproperty3.md)

- [IDebugObject](../../extensibility/debugger/reference/idebugobject.md)

  L’EE consomme les interfaces suivantes pour prendre en charge les visualisateurs de type :

- [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md)

- [IEEVisualizerServiceProvider](../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)

- [IDebugBinder3](../../extensibility/debugger/reference/idebugbinder3.md)

## <a name="see-also"></a>Voir aussi
- [Rédaction d’un évaluateur d’expression CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
- [Visualisation et visualisation des données](../../extensibility/debugger/visualizing-and-viewing-data.md)
- [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md)
