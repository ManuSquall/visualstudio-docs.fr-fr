---
title: IDebugContainerField | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
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
ms.openlocfilehash: 4bee04d21e3181d4590f26b64c794164ab1a84b6
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31105224"
---
# <a name="idebugcontainerfield"></a>IDebugContainerField
Cette interface représente un symbole ou un type qui est un conteneur pour d’autres symboles ou les types.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDebugContainerField : IDebugField  
```  
  
## <a name="notes-for-implementers"></a>Notes pour les implémenteurs  
 Un fournisseur de symbole implémente cette interface sur le même objet qui implémente le [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) interface. Cette interface est également la classe de base pour toutes les interfaces qui représentent des conteneurs.  
  
## <a name="notes-for-callers"></a>Remarques pour les appelants  
 De nombreuses méthodes de nombreuses interfaces retournent cette interface. Car il s’agit d’une classe de base pour tous les conteneurs, des interfaces plus spécialisées peut obtenu à partir de cette interface à l’aide de [QueryInterface](/cpp/atl/queryinterface). Ces interfaces incluent [IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md), [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md), [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md), et [IDebugPropertyField](../../../extensibility/debugger/reference/idebugpropertyfield.md).  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
 Outre les méthodes sur le [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) interface, cette interface implémente la méthode suivante :  
  
|Méthode|Description|  
|------------|-----------------|  
|[EnumFields](../../../extensibility/debugger/reference/idebugcontainerfield-enumfields.md)|Crée un énumérateur pour les champs du conteneur.|  
  
## <a name="remarks"></a>Notes  
 Tableaux (conteneurs pour les variables), les classes (conteneurs pour les méthodes et variables) et les méthodes (conteneurs pour les paramètres et variables locales) sont des exemples de conteneurs.  
  
## <a name="requirements"></a>Spécifications  
 En-tête : sh.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces de fournisseur de symboles](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)