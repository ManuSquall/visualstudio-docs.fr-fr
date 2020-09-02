---
title: IDebugContainerField | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugContainerField
helpviewer_keywords:
- IDebugContainerField interface
ms.assetid: a8bbe061-c382-4fe9-a193-3f7d12216041
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2656d3f5a3313a4538e3e0e6454dd671da635904
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65686970"
---
# <a name="idebugcontainerfield"></a>IDebugContainerField
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Cette interface représente un symbole ou un type qui est un conteneur pour d’autres symboles ou types.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDebugContainerField : IDebugField  
```  
  
## <a name="notes-for-implementers"></a>Notes pour les implémenteurs  
 Un fournisseur de symboles implémente cette interface sur le même objet qui implémente l’interface [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) . Cette interface est également la classe de base pour toutes les interfaces qui représentent des conteneurs.  
  
## <a name="notes-for-callers"></a>Notes pour les appelants  
 De nombreuses méthodes sur de nombreuses interfaces retournent cette interface. Étant donné qu’il s’agit d’une classe de base pour tous les conteneurs, des interfaces plus spécialisées peuvent être obtenues à partir de cette interface à l’aide de [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3). Ces interfaces sont [IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md), [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md), [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)et [IDebugPropertyField](../../../extensibility/debugger/reference/idebugpropertyfield.md).  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
 Outre les méthodes sur l’interface [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) , cette interface implémente la méthode suivante :  
  
|Méthode|Description|  
|------------|-----------------|  
|[EnumFields](../../../extensibility/debugger/reference/idebugcontainerfield-enumfields.md)|Crée un énumérateur pour les champs du conteneur.|  
  
## <a name="remarks"></a>Notes  
 Les tableaux (conteneurs pour les variables), les classes (conteneurs pour les méthodes et les variables) et les méthodes (conteneurs pour les paramètres et les variables locales) sont tous des exemples de conteneurs.  
  
## <a name="requirements"></a>Configuration requise  
 En-tête : SH. h  
  
 Espace de noms : Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces du fournisseur de symboles](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
