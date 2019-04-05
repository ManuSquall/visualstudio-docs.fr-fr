---
title: IEEVisualizerService | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IEEVisualizerService
helpviewer_keywords:
- IEEVisualizerService interface
ms.assetid: 3bdb124b-c582-47ba-b465-13c6a1cdb702
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1512431be4718c33d418f128948cb61fcbfad314
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58952922"
---
# <a name="ieevisualizerservice"></a>IEEVisualizerService
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

> [!IMPORTANT]
>  Dans Visual Studio 2015, ce moyen d’implémenter des évaluateurs d’expression est déconseillée. Pour plus d’informations sur l’implémentation des évaluateurs d’expression CLR, consultez [évaluateurs d’Expression CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) et [exemple d’évaluateur d’Expression gérés](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Cette interface implémente des méthodes clés qui offrent des fonctionnalités à la [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) et [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) interfaces.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IEEVisualizerService : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notes de publication pour les implémenteurs  
 Visual Studio implémente cette interface afin d’autoriser un évaluateur d’expression (EE) pour prendre en charge les visualiseurs de type.  
  
## <a name="notes-for-callers"></a>Notes de publication pour les appelants  
 Les appels EE [CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md) pour obtenir cette interface dans le cadre de sa prise en charge pour les visualiseurs de type.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l’ordre Vtable  
  
|Méthode|Description|  
|------------|-----------------|  
|[GetCustomViewerCount](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md)|Récupère le nombre de visionneuses personnalisées sur qui sait ce service.|  
|[GetCustomViewerList](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md)|Récupère la liste des visionneuses personnalisées.|  
|[GetPropertyProxy](../../../extensibility/debugger/reference/ieevisualizerservice-getpropertyproxy.md)|Retourne un objet proxy pour une propriété.|  
|[GetValueDisplayStringCount](../../../extensibility/debugger/reference/ieevisualizerservice-getvaluedisplaystringcount.md)|Récupère le nombre de chaînes de valeur à afficher pour la propriété spécifiée ou du champ.|  
  
## <a name="remarks"></a>Notes  
 L’IDE utilise le [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) interface pour déterminer s’il existe des visionneuses personnalisées ou tapez visualiseurs pour la propriété. En créant un service de visualiseur (avec [CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md)), le EE peut fournir la fonctionnalité à la `IDebugProperty3` et [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) (qui prend en charge l’affichage et modification d’un valeur de la propriété) des interfaces et ainsi prendre en charge les visualiseurs de type.  
  
 Si un EE a des visionneuses personnalisées elle-même implémente, le EE peut ajouter le `CLSID`s de ces visionneuses personnalisées à la fin de la liste renvoyée par [GetCustomViewerList](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md). Cela permet une EE prendre en charge les visualiseurs de type et ses propres visionneuses personnalisées. Assurez-vous juste que [GetCustomViewerCount](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md) reflète l’ajout de n’importe quel visionneuses personnalisées.  
  
 Consultez [visualiseur de Type et Visionneuse de personnalisé](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md) pour une présentation de la différence entre les visualiseurs et les visionneuses.  
  
## <a name="requirements"></a>Configuration requise  
 En-tête : ee.h  
  
 Espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces de l’évaluation d’expression](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)   
 [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)   
 [CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md)   
 [Visualiseur de type et visionneuse personnalisée](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
