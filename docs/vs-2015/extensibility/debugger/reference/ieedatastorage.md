---
title: IEEDataStorage | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IEEDataStorage
helpviewer_keywords:
- IEEDataStorage interface
ms.assetid: 704e932d-2325-410e-89c4-ce88c6ec19da
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a5d102a4a9cf7946e135ec8f6cdbff44015d3b47
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58951130"
---
# <a name="ieedatastorage"></a>IEEDataStorage
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Cette interface représente un tableau d’octets.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IEEDataStorage : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notes de publication pour les implémenteurs  
 L’évaluateur d’expression (EE) implémente cette interface pour représenter un tableau d’octets (utilisé par les visualiseurs de type pour extraire et modifier des données via le [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) interface). En général, le EE implémente cette interface pour prendre en charge les visualiseurs de type externe.  
  
## <a name="notes-for-callers"></a>Notes de publication pour les appelants  
 Les méthodes sur le `IPropertyProxyEESide` interface tous les retourner cette interface. Appelez [GetPropertyProxy](../../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md) pour obtenir le [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) interface. Appelez [QueryInterface](http://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) sur un [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) interface pour obtenir le [IPropertyProxyProvider](../../../extensibility/debugger/reference/ipropertyproxyprovider.md) interface.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l’ordre Vtable  
 Le `IEEDataStorage` interface implémente les méthodes suivantes :  
  
|Méthode|Description|  
|------------|-----------------|  
|[GetData](../../../extensibility/debugger/reference/ieedatastorage-getdata.md)|Récupère le nombre spécifié d’octets de données dans une mémoire tampon fournie.|  
|[GetSize](../../../extensibility/debugger/reference/ieedatastorage-getsize.md)|Récupère le nombre d’octets de données disponibles.|  
  
## <a name="remarks"></a>Notes  
 Cette interface est utilisée par un visualiseur de type pour accéder aux données détenues par un objet spécifique. Les données sont traitées en tant que tableau d’octets, ce qui permet le visualiseur de type manipuler de façon est nécessaire pour présenter à l’utilisateur.  
  
 Une visionneuse personnalisée peut également utiliser cette interface, si vous le souhaitez, bien qu’en règle générale, une visionneuse personnalisée utilisent une interface personnalisée, [GetMemoryBytes](../../../extensibility/debugger/reference/idebugproperty2-getmemorybytes.md) ou [GetStringChars](../../../extensibility/debugger/reference/idebugproperty3-getstringchars.md) (pour les données orientée sur la chaîne).  
  
## <a name="requirements"></a>Configuration requise  
 En-tête : msdbg.h  
  
 Espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces principales](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)   
 [Visualiseur de type et visionneuse personnalisée](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
