---
title: IDebugContainerField | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugContainerField
helpviewer_keywords:
- IDebugContainerField interface
ms.assetid: a8bbe061-c382-4fe9-a193-3f7d12216041
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 51b88bf0302c404883ccbc3d476cb0262eb1e948
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53910307"
---
# <a name="idebugcontainerfield"></a>IDebugContainerField
Cette interface représente un symbole ou un type qui est un conteneur pour d’autres symboles ou les types.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDebugContainerField : IDebugField  
```  
  
## <a name="notes-for-implementers"></a>Notes de publication pour les implémenteurs  
 Un fournisseur de symboles implémente cette interface sur le même objet qui implémente le [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) interface. Cette interface est également la classe de base pour toutes les interfaces qui représentent des conteneurs.  
  
## <a name="notes-for-callers"></a>Notes de publication pour les appelants  
 De nombreuses méthodes sur le nombre d’interfaces retournent cette interface. Comme il s’agit d’une classe de base pour tous les conteneurs, des interfaces plus spécialisées peut obtenu à partir de cette interface à l’aide de [QueryInterface](/cpp/atl/queryinterface). Ces interfaces comprennent [IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md), [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md), [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md), et [IDebugPropertyField](../../../extensibility/debugger/reference/idebugpropertyfield.md).  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
 Outre les méthodes sur le [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) interface, cette interface implémente la méthode suivante :  
  
|Méthode|Description|  
|------------|-----------------|  
|[EnumFields](../../../extensibility/debugger/reference/idebugcontainerfield-enumfields.md)|Crée un énumérateur pour les champs du conteneur.|  
  
## <a name="remarks"></a>Notes  
 Tableaux (conteneurs pour les variables), des classes (conteneurs pour les méthodes et variables) et des méthodes (conteneurs pour les paramètres et variables locales) sont des exemples de conteneurs.  
  
## <a name="requirements"></a>Spécifications  
 En-tête : sh.h  
  
 Espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces de fournisseur de symboles](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)