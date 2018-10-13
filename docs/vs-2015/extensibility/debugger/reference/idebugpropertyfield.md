---
title: IDebugPropertyField | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugPropertyField
helpviewer_keywords:
- IDebugPropertyField interface
ms.assetid: b50edb2c-fb8d-4def-993d-17d23d2027c1
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9f49093679f975afa5f8d4d23689373bc327f764
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49242045"
---
# <a name="idebugpropertyfield"></a>IDebugPropertyField
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Cette interface fournit les fonctions qui permettent d’obtenir et de définir une propriété.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDebugPropertyField : IDebugContainerField  
```  
  
## <a name="notes-for-implementers"></a>Notes de publication pour les implémenteurs  
 Un fournisseur de symboles implémente cette interface sur le même objet qui implémente le [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md). Cette interface est une spécialisation qui prend en charge le concept de propriétés sur une classe.  
  
## <a name="notes-for-callers"></a>Notes de publication pour les appelants  
 Utilisez [QueryInterface](http://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) pour obtenir cette interface à partir de la [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) interface si le [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) méthode retourne `FIELD_KIND_PROP`.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
 Outre les méthodes sur le [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) et [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) interfaces, cette interface implémente les méthodes suivantes :  
  
|Méthode|Description|  
|------------|-----------------|  
|[GetPropertyGetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertygetter.md)|Obtient la méthode qui obtient la propriété.|  
|[GetPropertySetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertysetter.md)|Obtient la méthode qui définit la propriété.|  
  
## <a name="remarks"></a>Notes  
 Une propriété est un concept de code managé et représente une méthode qui est traitée comme une variable. Propriétés n’existent pas dans C++ non managé.  
  
## <a name="requirements"></a>Configuration requise  
 En-tête : sh.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces de fournisseur de symboles](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)

