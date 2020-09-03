---
title: Implémentation des visualiseurs de type et des visionneuses personnalisées | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80738509"
---
# <a name="implement-type-visualizers-and-custom-viewers"></a>Implémenter des visualiseurs de type et des visionneuses personnalisées
> [!IMPORTANT]
> Dans Visual Studio 2015, cette façon d’implémenter les évaluateurs d’expression est déconseillée. Pour plus d’informations sur l’implémentation des évaluateurs d’expression CLR, consultez [évaluateur d’expression CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) et [exemple évaluateur d’expression managée](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Les visualiseurs de type et les visionneuses personnalisées permettent à un utilisateur d’afficher les données d’un type particulier d’une manière plus explicite qu’un simple dump hexadécimal de nombres. Un évaluateur d’expression (EE) peut associer des visionneuses personnalisées à des types spécifiques de données ou de variables. Ces visionneuses personnalisées sont implémentées par EE. Le EE peut également prendre en charge des visualiseurs de type externe, qui peuvent provenir d’un autre fournisseur tiers ou même de l’utilisateur final.

## <a name="discussion"></a>Discussion

### <a name="type-visualizers"></a>Visualiseurs de type
 Visual Studio demande une liste de visualiseurs de types et de visionneuses personnalisées pour chaque objet à afficher dans une fenêtre Espion. Un évaluateur d’expression (EE) fournit une telle liste pour chaque type pour lequel il souhaite prendre en charge des visualiseurs de type et des visionneuses personnalisées. Les appels à [GetCustomViewerCount](../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md) et [GetCustomViewerList](../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) démarrent tout le processus d’accès aux visualiseurs de types et aux visionneuses personnalisées (pour plus d’informations sur la séquence d’appel, consultez visualisation [et affichage des données](../../extensibility/debugger/visualizing-and-viewing-data.md) ).

### <a name="custom-viewers"></a>Visionneuses personnalisées
 Les visionneuses personnalisées sont implémentées dans EE pour un type de données spécifique et sont représentées par l’interface [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md) . Une visionneuse personnalisée n’est pas aussi flexible qu’une visionneuse de type, car elle n’est disponible que lorsque l’EE qui implémente cette visionneuse personnalisée particulière s’exécute. L’implémentation d’une visionneuse personnalisée est plus simple que l’implémentation de la prise en charge des visualiseurs de type. Toutefois, la prise en charge des visualiseurs de type offre une flexibilité maximale à l’utilisateur final pour visualiser ses données. Le reste de cette discussion concerne uniquement les visualiseurs de type.

## <a name="interfaces"></a>Interfaces
 L’EE implémente les interfaces suivantes pour prendre en charge les visualiseurs de type, pour être consommés par Visual Studio :

- [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md)

- [IPropertyProxyEESide](../../extensibility/debugger/reference/ipropertyproxyeeside.md)

- [IPropertyProxyProvider](../../extensibility/debugger/reference/ipropertyproxyprovider.md)

- [IEEDataStorage](../../extensibility/debugger/reference/ieedatastorage.md)

- [IDebugProperty3](../../extensibility/debugger/reference/idebugproperty3.md)

- [IDebugObject](../../extensibility/debugger/reference/idebugobject.md)

  L’EE utilise les interfaces suivantes pour prendre en charge les visualiseurs de type :

- [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md)

- [IEEVisualizerServiceProvider](../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)

- [IDebugBinder3](../../extensibility/debugger/reference/idebugbinder3.md)

## <a name="see-also"></a>Voir aussi
- [Écriture d’un évaluateur d’expression CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
- [Visualisation et affichage des données](../../extensibility/debugger/visualizing-and-viewing-data.md)
- [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md)
