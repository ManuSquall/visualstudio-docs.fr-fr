---
title: IDebugClassField::EnumBaseClasses | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugClassField::EnumBaseClasses
helpviewer_keywords:
- IDebugClassField::EnumBaseClasses method
ms.assetid: 78749674-ef75-46d3-a1f4-ff33afd90e32
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 1b5210859115947115bce6525cd5b6cd15c4d59d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
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
  
## <a name="remarks"></a>Notes  
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