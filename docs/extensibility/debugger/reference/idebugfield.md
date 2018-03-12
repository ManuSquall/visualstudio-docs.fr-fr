---
title: IDebugField | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugField
helpviewer_keywords:
- IDebugField interface
ms.assetid: adecdd1c-b1b9-4027-92da-74cbe910636f
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 00d3113f0151b9a2ad32259b24cc45dcca8bbccf
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="idebugfield"></a>IDebugField
Cette interface représente un champ, autrement dit, une description d’un symbole ou d’un type.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDebugField : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notes pour les implémenteurs  
 Un fournisseur de symbole implémente cette interface en tant que classe de base pour tous les champs.  
  
## <a name="notes-for-callers"></a>Remarques pour les appelants  
 Cette interface est la classe de base pour tous les champs. Selon la valeur de retour de [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md), cette interface peut retourner des interfaces plus spécialisées à l’aide de [QueryInterface](/cpp/atl/queryinterface). En outre, de retour de nombreuses interfaces `IDebugField` objets à partir de différentes méthodes.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
 Le tableau suivant présente les méthodes de `IDebugField`.  
  
|Méthode|Description|  
|------------|-----------------|  
|[GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md)|Obtient des informations peut être affichées sur le symbole ou d’un type.|  
|[GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md)|Obtient le type de champ.|  
|[GetType](../../../extensibility/debugger/reference/idebugfield-gettype.md)|Obtient le type du champ.|  
|[GetContainer](../../../extensibility/debugger/reference/idebugfield-getcontainer.md)|Obtient le conteneur du champ.|  
|[GetAddress](../../../extensibility/debugger/reference/idebugfield-getaddress.md)|Obtient l’adresse du champ.|  
|[GetSize](../../../extensibility/debugger/reference/idebugfield-getsize.md)|Obtient la taille d’un champ, en octets.|  
|[GetExtendedInfo](../../../extensibility/debugger/reference/idebugfield-getextendedinfo.md)|Obtient des informations étendues sur un champ.|  
|[Égal à](../../../extensibility/debugger/reference/idebugfield-equal.md)|Compare deux champs.|  
|[GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md)|Obtient les indépendante du type d’informations sur le symbole ou d’un type.|  
  
## <a name="remarks"></a>Notes  
 Un type est équivalent à un langage C `typedef`.  
  
 Dans l’exemple de langage C++ suivant, `weather` est un type de classe, et `sunny` et `stormy` sont des symboles :  
  
```cpp  
class weather;  
weather sunny;  
weather stormy;  
```  
  
 Si un champ représente un symbole ou type peut être déterminé en appelant [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) et en examinant le [FIELD_KIND](../../../extensibility/debugger/reference/field-kind.md) résultat. Si le `FIELD_KIND_TYPE` bit est défini, le champ est un type et si le `FIELD_KIND_SYMBOL` bit est défini, il s’agit d’un symbole.  
  
## <a name="requirements"></a>Configuration requise  
 En-tête : sh.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Symbol Provider Interfaces](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)