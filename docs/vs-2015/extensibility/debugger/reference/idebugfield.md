---
title: IDebugField | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugField
helpviewer_keywords:
- IDebugField interface
ms.assetid: adecdd1c-b1b9-4027-92da-74cbe910636f
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8bc18204d3cbe20635ab0680a50b4d1555dce2ce
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65690309"
---
# <a name="idebugfield"></a>IDebugField
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Cette interface représente un champ, autrement dit, une description d’un symbole ou d’un type.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDebugField : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notes pour les implémenteurs  
 Un fournisseur de symboles implémente cette interface comme classe de base pour tous les champs.  
  
## <a name="notes-for-callers"></a>Notes pour les appelants  
 Cette interface est la classe de base pour tous les champs. En fonction de la valeur de retour de [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md), cette interface peut retourner des interfaces plus spécialisées à l’aide de [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3). De plus, de nombreuses interfaces retournent `IDebugField` des objets à partir de différentes méthodes.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
 Le tableau suivant présente les méthodes de `IDebugField` .  
  
|Méthode|Description|  
|------------|-----------------|  
|[GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md)|Obtient des informations affichables sur le symbole ou le type.|  
|[GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md)|Obtient le type de champ.|  
|[GetType](../../../extensibility/debugger/reference/idebugfield-gettype.md)|Obtient le type de champ.|  
|[GetContainer](../../../extensibility/debugger/reference/idebugfield-getcontainer.md)|Obtient le conteneur du champ.|  
|[GetAddress](../../../extensibility/debugger/reference/idebugfield-getaddress.md)|Obtient l’adresse du champ.|  
|[GetSize](../../../extensibility/debugger/reference/idebugfield-getsize.md)|Obtient la taille d’un champ, en octets.|  
|[GetExtendedInfo](../../../extensibility/debugger/reference/idebugfield-getextendedinfo.md)|Obtient des informations étendues sur un champ.|  
|[Égal](../../../extensibility/debugger/reference/idebugfield-equal.md)|Compare deux champs.|  
|[GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md)|Obtient des informations indépendantes du type sur le symbole ou le type.|  
  
## <a name="remarks"></a>Notes  
 Un type est équivalent à un langage C `typedef` .  
  
 Dans l’exemple de langage C++ suivant, `weather` est un type de classe et `sunny` et sont des `stormy` symboles :  
  
```cpp#  
class weather;  
weather sunny;  
weather stormy;  
```  
  
 Si un champ représente un symbole ou un type peut être déterminé en appelant [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) et en examinant le résultat [FIELD_KIND](../../../extensibility/debugger/reference/field-kind.md) . Si le `FIELD_KIND_TYPE` bit est défini, le champ est un type et, si le `FIELD_KIND_SYMBOL` bit est défini, il s’agit d’un symbole.  
  
## <a name="requirements"></a>Configuration requise  
 En-tête : SH. h  
  
 Espace de noms : Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces des fournisseurs de symboles](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
