---
title: IDebugClassField::EnumNestedClasses | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugClassField::EnumNestedClasses
helpviewer_keywords: IDebugClassField::EnumNestedClasses method
ms.assetid: 2ba5ef0c-395e-4006-9e3c-9b06e1d711d0
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 51b8c582d221ced72380cf5450fc0af9b014d148
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="idebugclassfieldenumnestedclasses"></a>IDebugClassField::EnumNestedClasses
Crée un énumérateur pour les classes imbriquées dans cette classe.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
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
 [out] Retourne un [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) objet représentant la liste des classes imbriquées. Retourne une valeur null si aucune classe imbriquée.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne S_OK ou retourne S_FALSE si aucune classe imbriquée. Sinon, retourne un code d'erreur.  
  
## <a name="remarks"></a>Remarques  
 Chaque élément de l’énumération est un [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) objet décrivant une classe imbriquée.  
  
 Une classe imbriquée est une classe définie à l’intérieur d’une autre classe. Exemple :  
  
```  
class RootClass {  
   class NestedClass { }  
};  
```  
  
 Le [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) énumération contient un objet représentant la `NestedClass` classe.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)