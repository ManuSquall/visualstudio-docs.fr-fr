---
title: IPropertyProxyProvider | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IPropertyProxyProvider
helpviewer_keywords:
- IPropertyProxyProvider interface
ms.assetid: 52e9f7fc-6fe0-4d23-890b-5673dca8c3cb
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: ca7c86466fa23fb21a932f26dc24e37c71cf29b4
ms.openlocfilehash: 73a1a1a189e4922d662081a92738b1c35c6bb291
ms.contentlocale: fr-fr
ms.lasthandoff: 04/05/2017

---
# <a name="ipropertyproxyprovider"></a>IPropertyProxyProvider
Cette interface fournit une interface proxy pour afficher et modifier les données d’un objet.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IPropertyProxyProvider : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notes pour les implémenteurs  
 L’évaluateur d’expression (EE) implémente cette interface sur le même objet qui implémente le [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) interface dans le cadre de la prise en charge de la EE de visualiseurs de type.  
  
## <a name="notes-for-callers"></a>Remarques pour les appelants  
 Appelez [QueryInterface](/cpp/atl/queryinterface) sur une `IDebugProperty3` interface pour obtenir cette interface.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l’ordre Vtable  
 Le `IPropertyProxyProvider` interface implémente la méthode suivante :  
  
|Méthode|Description|  
|------------|-----------------|  
|[GetPropertyProxy](../../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md)|Récupère une interface proxy de propriété pour afficher les données sur un objet.|  
  
## <a name="remarks"></a>Notes  
 Bien que le EE implémente cette interface, l’implémentation de [GetPropertyProxy](../../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md) est généralement contrôlée par [GetPropertyProxy](../../../extensibility/debugger/reference/ieevisualizerservice-getpropertyproxy.md). Consultez [Visualizing et affichage des données](../../../extensibility/debugger/visualizing-and-viewing-data.md) pour plus d’informations sur l’obtention de l’interface IEEVisualizerService.  
  
## <a name="requirements"></a>Spécifications  
 En-tête : msdbg.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetPropertyProxy](../../../extensibility/debugger/reference/ieevisualizerservice-getpropertyproxy.md)   
 [Visualiseur de type et de la visionneuse personnalisée](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)   
 [Visualisation et affichage des données](../../../extensibility/debugger/visualizing-and-viewing-data.md)
