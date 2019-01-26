---
title: IPropertyProxyProvider | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IPropertyProxyProvider
helpviewer_keywords:
- IPropertyProxyProvider interface
ms.assetid: 52e9f7fc-6fe0-4d23-890b-5673dca8c3cb
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 716f3caedd2b3da9ce115148ecf15b33834238fc
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54953875"
---
# <a name="ipropertyproxyprovider"></a>IPropertyProxyProvider
Cette interface fournit une interface proxy pour afficher et modifier les données d’un objet.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IPropertyProxyProvider : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notes de publication pour les implémenteurs  
 L’évaluateur d’expression (EE) implémente cette interface sur le même objet qui implémente le [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) interface dans le cadre de la prise en charge de la EE de visualiseurs de type.  
  
## <a name="notes-for-callers"></a>Notes de publication pour les appelants  
 Appelez [QueryInterface](/cpp/atl/queryinterface) sur un `IDebugProperty3` interface pour obtenir cette interface.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l’ordre Vtable  
 Le `IPropertyProxyProvider` interface implémente la méthode suivante :  
  
|Méthode|Description|  
|------------|-----------------|  
|[GetPropertyProxy](../../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md)|Récupère une interface de proxy de propriété pour afficher les données sur un objet.|  
  
## <a name="remarks"></a>Notes  
 Bien que le EE implémente cette interface, l’implémentation de [GetPropertyProxy](../../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md) est généralement contrôlée par [GetPropertyProxy](../../../extensibility/debugger/reference/ieevisualizerservice-getpropertyproxy.md). Consultez [visualisation et affichage des données](../../../extensibility/debugger/visualizing-and-viewing-data.md) pour plus d’informations sur l’obtention de l’interface IEEVisualizerService.  
  
## <a name="requirements"></a>Spécifications  
 En-tête : msdbg.h  
  
 Espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces principales](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetPropertyProxy](../../../extensibility/debugger/reference/ieevisualizerservice-getpropertyproxy.md)   
 [Visualiseur de type et visionneuse personnalisée](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)   
 [Visualisation et affichage des données](../../../extensibility/debugger/visualizing-and-viewing-data.md)