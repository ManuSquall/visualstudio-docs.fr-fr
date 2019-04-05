---
title: IEnumDebugCustomAttributes | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IEnumCustomAttributes
helpviewer_keywords:
- IEnumDebugCustomAttributes interface
ms.assetid: 11aa768d-1852-44d6-9de3-17f9bafaded2
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7a0e1b361e99ef1e32a7dd327e531a1049f4009a
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58950992"
---
# <a name="ienumdebugcustomattributes"></a>IEnumDebugCustomAttributes
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Énumère les attributs personnalisés.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IEnumCustomAttributes : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notes de publication pour les implémenteurs  
 Un fournisseur de symboles implémente cette interface pour prendre en charge les attributs personnalisés (via le [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md) interface).  
  
## <a name="notes-for-callers"></a>Notes de publication pour les appelants  
 [EnumCustomAttributes](../../../extensibility/debugger/reference/idebugcustomattributequery2-enumcustomattributes.md) retourne cette interface.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
 Le tableau suivant présente les méthodes de `IEnumDebugCustomAttributes`.  
  
|Méthode|Description|  
|------------|-----------------|  
|[Next](../../../extensibility/debugger/reference/ienumdebugcustomattributes-next.md)|Récupère un nombre spécifié d’attributs personnalisés dans une séquence d’énumération.|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugcustomattributes-skip.md)|Ignore un nombre spécifié d’attributs personnalisés dans une séquence d’énumération.|  
|[Reset](../../../extensibility/debugger/reference/ienumdebugcustomattributes-reset.md)|Réinitialise une séquence d’énumération au début.|  
|[Clone](../../../extensibility/debugger/reference/ienumdebugcustomattributes-clone.md)|Crée un énumérateur qui contient le même état d’énumération que l’énumérateur en cours.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugcustomattributes-getcount.md)|Obtient le nombre d’attributs personnalisés dans un énumérateur.|  
  
## <a name="requirements"></a>Configuration requise  
 En-tête : sh.h  
  
 Espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces de fournisseur de symboles](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [EnumCustomAttributes](../../../extensibility/debugger/reference/idebugcustomattributequery2-enumcustomattributes.md)   
 [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)
