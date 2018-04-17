---
title: IDebugMethodField::EnumArguments | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugMethodField::EnumArguments
helpviewer_keywords:
- IDebugMethodField::EnumArguments method
ms.assetid: 3ab55488-2437-4ff6-a9ae-78ea6d7b23a8
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: dc92dc6b560332509f69a975eca63ddb5c191fab
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="idebugmethodfieldenumarguments"></a>IDebugMethodField::EnumArguments
Crée un énumérateur pour le type de chaque argument requis pour appeler la méthode.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT EnumArguments(   
   IEnumDebugFields** ppParams  
);  
```  
  
```csharp  
int EnumArguments(  
   out IEnumDebugFields ppParams  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `ppParams`  
 [out] Retourne un [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) objet représentant la liste des types d’arguments. Retourne une valeur null s’il n’existe aucun argument.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne S_OK ou retourne S_FALSE si il n’existe aucun argument. Sinon, retourne un code d'erreur.  
  
## <a name="remarks"></a>Notes  
 Chaque élément est un [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) objet représentant les types de chaque paramètre. Appelez le [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md) méthode pour récupérer des informations sur le type de chaque paramètre.  
  
 Si le nom du paramètre est requis, ainsi que le type, puis appelez le [EnumParameters](../../../extensibility/debugger/reference/idebugmethodfield-enumparameters.md) (méthode).  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [EnumParameters](../../../extensibility/debugger/reference/idebugmethodfield-enumparameters.md)