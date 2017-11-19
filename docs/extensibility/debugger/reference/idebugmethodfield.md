---
title: IDebugMethodField | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugMethodField
helpviewer_keywords: IDebugMethodField interface
ms.assetid: a7dc9030-fc98-4cf1-b943-37a4003300b6
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 818fdbcf236a1965eb1ea657f65a9d28421b42ce
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="idebugmethodfield"></a>IDebugMethodField
Cette interface décrit une méthode.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDebugMethodField : IDebugContainerField  
```  
  
## <a name="notes-for-implementers"></a>Notes pour les implémenteurs  
 Un fournisseur de symbole implémente cette interface sur le même objet qui implémente le [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) interface. Cette interface est une spécialisation qui présente une méthode.  
  
## <a name="notes-for-callers"></a>Remarques pour les appelants  
 Utilisez [QueryInterface](/cpp/atl/queryinterface) pour obtenir cette interface à partir de la [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) interface si [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) retourne `FIELD_TYPE_METHOD`. En outre, les méthodes, [GetPropertyGetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertygetter.md), [GetPropertySetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertysetter.md), et [EnumConstructors](../../../extensibility/debugger/reference/idebugclassfield-enumconstructors.md), retournent toutes la `IDebugMethodField` interface.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
 Outre les méthodes sur le [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) et [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) interfaces, cette interface implémente les méthodes suivantes :  
  
|Méthode|Description|  
|------------|-----------------|  
|[EnumParameters](../../../extensibility/debugger/reference/idebugmethodfield-enumparameters.md)|Crée un énumérateur pour les paramètres de la méthode.|  
|[Get :](../../../extensibility/debugger/reference/idebugmethodfield-getthis.md)|Obtient le pointeur « this » de l’objet qui contient la méthode.|  
|[EnumAllLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumalllocals.md)|Crée un énumérateur pour toutes les variables locales de la méthode.|  
|[EnumLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md)|Crée un énumérateur pour les variables locales sélectionnés de la méthode.|  
|[IsCustomAttributeDefined](../../../extensibility/debugger/reference/idebugmethodfield-iscustomattributedefined.md)|Détermine si un attribut personnalisé spécifique a été défini.|  
|[EnumStaticLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumstaticlocals.md)|Crée un énumérateur pour les variables locales statiques de la méthode.|  
|[GetGlobalContainer](../../../extensibility/debugger/reference/idebugmethodfield-getglobalcontainer.md)|Obtient le conteneur global de la méthode.|  
|[EnumArguments](../../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md)|Crée un énumérateur pour le type de chaque argument requis pour appeler la méthode.|  
  
## <a name="remarks"></a>Remarques  
 Une méthode peut contenir des paramètres, ainsi que des variables locales.  
  
## <a name="requirements"></a>Spécifications  
 En-tête : sh.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces de fournisseur de symboles](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)