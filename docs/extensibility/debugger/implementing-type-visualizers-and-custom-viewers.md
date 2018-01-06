---
title: "Implémentation de visualiseurs de types et des visionneuses personnalisées | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], custom viewer
- debugging [Debugging SDK], type visualizer
ms.assetid: abef18c0-8272-4451-b82a-b4624edaba7d
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 301c0311b8398ae14b36fedca5653d607b3274c0
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="implementing-type-visualizers-and-custom-viewers"></a>Implémentation de visualiseurs de types et des visionneuses personnalisées
> [!IMPORTANT]
>  Dans Visual Studio 2015, ce moyen d’implémenter des évaluateurs d’expression est déconseillée. Pour plus d’informations sur l’implémentation des évaluateurs d’expression CLR, consultez [évaluateurs d’Expression CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) et [exemple d’évaluateur d’Expression managé](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Visualiseurs de types et des visionneuses personnalisées permettent un utilisateur d’afficher les données d’un type particulier d’une manière plus explicite qu’un vidage hexadécimal de nombres en simple. Évaluateur d’expression (EE) pouvez associer des visionneuses personnalisées à des types de données ou des variables. Ces visionneuses personnalisées sont implémentées par le Java EE. Le EE peut prennent également en charge les visualiseurs de type externe, ce qui peuvent provenir d’un autre fournisseur tiers ou même l’utilisateur final.  
  
## <a name="discussion"></a>Discussion  
  
### <a name="type-visualizers"></a>Visualiseurs de type  
 Visual Studio vous demande pour une liste de visualiseurs de types et des visionneuses personnalisées pour chaque objet à afficher dans une fenêtre Espion. Évaluateur d’expression (EE) fournit la liste pour chaque type pour lequel il souhaite prendre en charge les visualiseurs de types et des visionneuses personnalisées. Les appels à [GetCustomViewerCount](../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md) et [GetCustomViewerList](../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) démarrer l’ensemble du processus d’accéder aux visualiseurs de types et des visionneuses personnalisées (voir [Visualizing et affichage des données](../../extensibility/debugger/visualizing-and-viewing-data.md)pour plus d’informations sur la séquence d’appel).  
  
### <a name="custom-viewers"></a>Visionneuses personnalisées  
 Les visionneuses personnalisées sont implémentées dans le EE pour un type de données spécifique et sont représentées par le [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md) interface. Une visionneuse personnalisée n’est pas aussi flexible qu’un visualiseur de type, car il est disponible uniquement lorsque le EE qui implémente cette visionneuse personnalisée particulière est en cours d’exécution. Implémentation d’une visionneuse personnalisée est plus simple que celle prise en charge des visualiseurs de types. Toutefois, prenant en charge les visualiseurs de types offre d’une flexibilité maximale pour l’utilisateur final de visualisation de ses propres données. Le reste de cette rubrique concerne uniquement les visualiseurs de types.  
  
## <a name="interfaces"></a>Interfaces  
 Le EE implémente les interfaces suivantes pour prendre en charge les visualiseurs de type à être consommés par Visual Studio :  
  
-   [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md)  
  
-   [IPropertyProxyEESide](../../extensibility/debugger/reference/ipropertyproxyeeside.md)  
  
-   [IPropertyProxyProvider](../../extensibility/debugger/reference/ipropertyproxyprovider.md)  
  
-   [IEEDataStorage](../../extensibility/debugger/reference/ieedatastorage.md)  
  
-   [IDebugProperty3](../../extensibility/debugger/reference/idebugproperty3.md)  
  
-   [IDebugObject](../../extensibility/debugger/reference/idebugobject.md)  
  
 Le EE consomme les interfaces suivantes pour prendre en charge les visualiseurs de types :  
  
-   [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md)  
  
-   [IEEVisualizerServiceProvider](../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)  
  
-   [IDebugBinder3](../../extensibility/debugger/reference/idebugbinder3.md)  
  
## <a name="see-also"></a>Voir aussi  
 [L’écriture d’un évaluateur d’Expression CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)   
 [Visualisation et l’affichage des données](../../extensibility/debugger/visualizing-and-viewing-data.md)   
 [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md)