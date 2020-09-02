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
ms.openlocfilehash: ad398380c7c951b99e7d84283355ee9d31955173
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65704729"
---
# <a name="ieedatastorage"></a>IEEDataStorage
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Cette interface représente un tableau d’octets.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IEEDataStorage : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notes pour les implémenteurs  
 L’évaluateur d’expression (EE) implémente cette interface pour représenter un tableau d’octets (utilisé par les visualiseurs de type pour récupérer et modifier des données via l’interface [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) ). L’EE implémente généralement cette interface pour prendre en charge les visualiseurs de types externes.  
  
## <a name="notes-for-callers"></a>Notes pour les appelants  
 Les méthodes sur l' `IPropertyProxyEESide` interface retournent toutes cette interface. Appelez [GetPropertyProxy](../../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md) pour obtenir l’interface [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) . Appelez [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) sur une interface [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) pour obtenir l’interface [IPropertyProxyProvider](../../../extensibility/debugger/reference/ipropertyproxyprovider.md) .  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l’ordre vtable  
 L' `IEEDataStorage` interface implémente les méthodes suivantes :  
  
|Méthode|Description|  
|------------|-----------------|  
|[GetData](../../../extensibility/debugger/reference/ieedatastorage-getdata.md)|Récupère le nombre spécifié d’octets de données dans une mémoire tampon fournie.|  
|[GetSize](../../../extensibility/debugger/reference/ieedatastorage-getsize.md)|Récupère le nombre d’octets de données disponibles.|  
  
## <a name="remarks"></a>Notes  
 Cette interface est utilisée par un visualiseur de type pour accéder aux données détenues par un objet spécifique. Les données sont traitées comme un tableau d’octets, ce qui permet au visualiseur de type de le manipuler de la manière qui est nécessaire pour le présenter à l’utilisateur.  
  
 Une visionneuse personnalisée peut également utiliser cette interface, si vous le souhaitez, bien que plus généralement, une visionneuse personnalisée utilise une interface personnalisée, [GetMemoryBytes](../../../extensibility/debugger/reference/idebugproperty2-getmemorybytes.md) ou [GetStringChars](../../../extensibility/debugger/reference/idebugproperty3-getstringchars.md) (pour les données orientées chaîne).  
  
## <a name="requirements"></a>Configuration requise  
 En-tête : msdbg. h  
  
 Espace de noms : Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces principales](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)   
 [Visualiseur de type et visionneuse personnalisée](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
