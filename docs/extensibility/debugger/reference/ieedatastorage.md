---
title: IEEDataStorage | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IEEDataStorage
helpviewer_keywords: IEEDataStorage interface
ms.assetid: 704e932d-2325-410e-89c4-ce88c6ec19da
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: daf5f3e7547ee32b641ccf4c1448eaa9a80b72fa
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="ieedatastorage"></a>IEEDataStorage
Cette interface représente un tableau d’octets.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IEEDataStorage : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notes pour les implémenteurs  
 L’évaluateur d’expression (EE) implémente cette interface pour représenter un tableau d’octets (utilisé par les visualiseurs de types pour extraire et modifier des données via le [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) interface). En général, le EE implémente cette interface pour prendre en charge les visualiseurs de type externe.  
  
## <a name="notes-for-callers"></a>Remarques pour les appelants  
 Les méthodes sur le `IPropertyProxyEESide` interface tous les retourner cette interface. Appelez [GetPropertyProxy](../../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md) pour obtenir le [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) interface. Appelez [QueryInterface](/cpp/atl/queryinterface) sur une [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) interface pour obtenir le [IPropertyProxyProvider](../../../extensibility/debugger/reference/ipropertyproxyprovider.md) interface.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l’ordre Vtable  
 Le `IEEDataStorage` interface implémente les méthodes suivantes :  
  
|Méthode|Description|  
|------------|-----------------|  
|[GetData](../../../extensibility/debugger/reference/ieedatastorage-getdata.md)|Récupère le nombre spécifié d’octets de données dans une mémoire tampon fournie.|  
|[GetSize](../../../extensibility/debugger/reference/ieedatastorage-getsize.md)|Récupère le nombre d’octets de données disponibles.|  
  
## <a name="remarks"></a>Remarques  
 Cette interface est utilisée par un visualiseur de type pour accéder aux données détenues par un objet spécifique. Les données sont traitées en tant que tableau d’octets, ce qui permet le visualiseur de type à manipuler de manière est requis pour présenter à l’utilisateur.  
  
 Une visionneuse personnalisée peut également utiliser cette interface, si vous le souhaitez, bien qu’en règle générale, une visionneuse personnalisée utilisent une interface personnalisée, [GetMemoryBytes](../../../extensibility/debugger/reference/idebugproperty2-getmemorybytes.md) ou [GetStringChars](../../../extensibility/debugger/reference/idebugproperty3-getstringchars.md) (pour les données chaîne).  
  
## <a name="requirements"></a>Spécifications  
 En-tête : msdbg.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)   
 [Visualiseur de type et visionneuse personnalisée](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)