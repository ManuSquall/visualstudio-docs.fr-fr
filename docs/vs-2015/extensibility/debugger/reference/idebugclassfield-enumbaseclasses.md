---
title: 'IDebugClassField :: EnumBaseClasses | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugClassField::EnumBaseClasses
helpviewer_keywords:
- IDebugClassField::EnumBaseClasses method
ms.assetid: 78749674-ef75-46d3-a1f4-ff33afd90e32
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: acfdc872ba5f7cf1989ea1d9ec67f82f1c0419b0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68191050"
---
# <a name="idebugclassfieldenumbaseclasses"></a>IDebugClassField::EnumBaseClasses
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Crée un énumérateur pour les classes de base de cette classe.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
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
 à Retourne un objet [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) représentant la liste des classes de base. Retourne une valeur null s’il n’existe aucune classe de base.  
  
## <a name="return-value"></a>Valeur renvoyée  
 En cas de réussite, retourne S_OK, retourne S_SH_NO_BASE_CLASSES s’il n’existe aucune classe de base (et que le `ppEnum` paramètre est défini sur une valeur null); sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 Les classes de base de l’objet énumérateur sont spécifiées dans l’ordre de la classe de base la plus immédiate (ou la plus dérivée) à la classe de base distante la plus éloignée. Par exemple, étant donné les classes C++ :  
  
```  
class Root { }  
class Level1 : Root { }  
class Level2 : Level1 { }  
class MyClass : Level2 { }  
```  
  
 L’énumération retourne les classes de base dans l’ordre `Level2` , `Level1` , `Root` .  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
