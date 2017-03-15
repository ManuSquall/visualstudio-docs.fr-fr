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
caps.latest.revision: 12
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
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: e272f7b5e314e09d111ca3996870f5131ebdc3d0
ms.lasthandoff: 02/22/2017

---
# <a name="idebugfield"></a>IDebugField
Cette interface représente un champ, autrement dit, une description d’un symbole ou d’un type.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDebugField : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notes relatives à l’attention des implémenteurs  
 Un fournisseur de symboles implémente cette interface en tant que classe de base pour tous les champs.  
  
## <a name="notes-for-callers"></a>Remarques pour les appelants  
 Cette interface est la classe de base pour tous les champs. Selon la valeur de retour de [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md), cette interface peut retourner des interfaces plus spécialisées à l’aide de [QueryInterface](/visual-cpp/atl/queryinterface). En outre, plusieurs interfaces renvoie `IDebugField` objets à partir de différentes méthodes.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
 Le tableau suivant présente les méthodes de `IDebugField`.  
  
|Méthode|Description|  
|------------|-----------------|  
|[GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md)|Obtient des informations affichables sur le symbole ou le type.|  
|[GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md)|Obtient le type de champ.|  
|[GetType](../../../extensibility/debugger/reference/idebugfield-gettype.md)|Obtient le type de champ.|  
|[GetContainer](../../../extensibility/debugger/reference/idebugfield-getcontainer.md)|Obtient le conteneur du champ.|  
|[GetAddress](../../../extensibility/debugger/reference/idebugfield-getaddress.md)|Obtient l’adresse du champ.|  
|[GetSize](../../../extensibility/debugger/reference/idebugfield-getsize.md)|Obtient la taille d’un champ, en octets.|  
|[GetExtendedInfo](../../../extensibility/debugger/reference/idebugfield-getextendedinfo.md)|Obtient des informations étendues sur un champ.|  
|[Égal à](../../../extensibility/debugger/reference/idebugfield-equal.md)|Compare deux champs.|  
|[GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md)|Obtient les indépendant du type d’informations sur le symbole ou le type.|  
  
## <a name="remarks"></a>Remarques  
 Un type est équivalent à un langage C `typedef`.  
  
 Dans l’exemple de langage C++ suivant, `weather` est un type de classe, et `sunny` et `stormy` sont des symboles :  
  
```cpp#  
class weather;  
weather sunny;  
weather stormy;  
```  
  
 Si un champ représente un symbole ou type peut être déterminé en appelant [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) et en examinant le [FIELD_KIND](../../../extensibility/debugger/reference/field-kind.md) résultat. Si le `FIELD_KIND_TYPE` bit est défini, le champ est un type et si le `FIELD_KIND_SYMBOL` bit est défini, il est un symbole.  
  
## <a name="requirements"></a>Spécifications  
 En-tête : sh.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces de fournisseur de symboles](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
