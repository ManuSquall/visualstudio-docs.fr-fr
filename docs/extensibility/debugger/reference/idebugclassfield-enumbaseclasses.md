---
title: IDebugClassField::EnumBaseClasses | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugClassField::EnumBaseClasses
helpviewer_keywords:
- IDebugClassField::EnumBaseClasses method
ms.assetid: 78749674-ef75-46d3-a1f4-ff33afd90e32
caps.latest.revision: 9
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
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: 21e2de0ff49be7b1ef25d2b9d5be81ef0aafc6dd
ms.contentlocale: fr-fr
ms.lasthandoff: 09/26/2017

---
# <a name="idebugclassfieldenumbaseclasses"></a>IDebugClassField::EnumBaseClasses
Crée un énumérateur pour les classes de base de cette classe.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT EnumBaseClasses(   
   IEnumDebugFields** ppEnum  
);  
```  
  
```csharp  
int EnumBaseClasses(  
   out IEnumDebugFields ppEnum  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `ppEnum`  
 [out] Retourne un [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) objet représentant la liste des classes de base. Retourne une valeur null si aucune classe de base.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne S_OK, renvoie la valeur S_SH_NO_BASE_CLASSES si aucune classe de base (et le `ppEnum` paramètre est défini sur une valeur null) ; sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Remarques  
 Les classes de base dans l’objet énumérateur sont spécifiés dans l’ordre de la classe de base plus immédiate (ou plus dérivée) à la classe de base plus à distance. Par exemple, étant donné les classes C++ :  
  
```  
class Root { }  
class Level1 : Root { }  
class Level2 : Level1 { }  
class MyClass : Level2 { }  
```  
  
 L’énumération retournerait les classes de base dans l’ordre `Level2`, `Level1`, `Root`.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
