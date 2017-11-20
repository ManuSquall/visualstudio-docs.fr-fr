---
title: IDebugCustomAttributeQuery2 | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugCustomAttributeQuery2
helpviewer_keywords:
- IDebugCustomAttributeQuery interface
- IDebugCustomAttributeQuery2 interface
ms.assetid: 7cfa23e4-a05a-47a3-af6c-bd40c655014b
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 57e31ef81b9f03943597e32428cc97993aa30936
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="idebugcustomattributequery2"></a>IDebugCustomAttributeQuery2
Détermine l’existence d’un attribut personnalisé de ce champ et, si elle existe, retourne les informations d’attribut.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDebugCustomAttributeQuery2 : IDebugCustomAttributeQuery  
```  
  
## <a name="notes-for-implementers"></a>Notes pour les implémenteurs  
 Un fournisseur de symbole implémente cette interface sur le même objet qui implémente [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) pour prendre en charge les attributs personnalisés.  
  
## <a name="notes-for-callers"></a>Remarques pour les appelants  
 Utilisez [QueryInterface](/cpp/atl/queryinterface) pour obtenir cette interface à partir de la [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) interface.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
 Le tableau suivant présente les méthodes de la **IDebugCustomAttributeQuery** interface.  
  
|Méthode|Description|  
|------------|-----------------|  
|[IsCustomAttributeDefined](../../../extensibility/debugger/reference/idebugcustomattributequery2-iscustomattributedefined.md)|Détermine si un attribut personnalisé existe par nom.|  
|[GetCustomAttributeByName](../../../extensibility/debugger/reference/idebugcustomattributequery2-getcustomattributebyname.md)|Obtient les informations d’attribut pour l’attribut personnalisé.|  
  
 Outre la **IDebugCustomAttributeQuery** méthodes, `IDebugCustomAttributeQuery2` implémente la méthode suivante :  
  
|Méthode|Description|  
|------------|-----------------|  
|[EnumCustomAttributes](../../../extensibility/debugger/reference/idebugcustomattributequery2-enumcustomattributes.md)|Obtient un énumérateur pour tous les attributs personnalisés attachés à ce champ.|  
  
## <a name="remarks"></a>Remarques  
 Le [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md) méthode peut retourner un énumérateur pour tous les attributs personnalisés définis pour ce champ.  
  
## <a name="requirements"></a>Spécifications  
 En-tête : sh.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces de fournisseur de symboles](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)