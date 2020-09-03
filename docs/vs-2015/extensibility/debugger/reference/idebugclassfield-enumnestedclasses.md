---
title: 'IDebugClassField :: EnumNestedClasses | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugClassField::EnumNestedClasses
helpviewer_keywords:
- IDebugClassField::EnumNestedClasses method
ms.assetid: 2ba5ef0c-395e-4006-9e3c-9b06e1d711d0
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7745eea3f5b3264016a25defd696a9b85f2e9fb4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68191075"
---
# <a name="idebugclassfieldenumnestedclasses"></a>IDebugClassField::EnumNestedClasses
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Crée un énumérateur pour les classes imbriquées dans cette classe.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT EnumNestedClasses(   
   IEnumDebugFields** ppEnum  
);  
```  
  
```csharp  
int EnumNestedClasses(  
   out IEnumDebugFields ppEnum  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `ppEnum`  
 à Retourne un objet [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) représentant la liste des classes imbriquées. Retourne une valeur null s’il n’existe aucune classe imbriquée.  
  
## <a name="return-value"></a>Valeur renvoyée  
 En cas de réussite, retourne S_OK ou retourne S_FALSE s’il n’y a pas de classes imbriquées. Sinon, retourne un code d'erreur.  
  
## <a name="remarks"></a>Notes  
 Chaque élément de l’énumération est un objet [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) décrivant une classe imbriquée.  
  
 Une classe imbriquée est une classe définie à l’intérieur d’une autre classe. Par exemple :  
  
```  
class RootClass {  
   class NestedClass { }  
};  
```  
  
 L’énumération [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) contient un objet représentant la `NestedClass` classe.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
