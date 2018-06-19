---
title: IDebugClassField::EnumConstructors | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugClassField::EnumConstructors
helpviewer_keywords:
- IDebugClassField::EnumConstructors method
ms.assetid: 66a250b2-75a0-45aa-8d58-40f91cc4bf7b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: aa525f50a0ffd18f136cfa23ae05a8e2ba193d0d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31101730"
---
# <a name="idebugclassfieldenumconstructors"></a>IDebugClassField::EnumConstructors
Crée un énumérateur pour les constructeurs de cette classe.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT EnumConstructors(   
   CONSTRUCTOR_ENUM   cMatch,  
   IEnumDebugFields** ppEnum  
);  
```  
  
```csharp  
int EnumConstructors(  
   CONSTRUCTOR_ENUM     cMatch,   
   out IEnumDebugFields ppEnum  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `cMatch`  
 [in] Une valeur à partir de la [CONSTRUCTOR_ENUM](../../../extensibility/debugger/reference/constructor-enum.md) énumération qui spécifie le type d’énumération des constructeurs.  
  
 `ppEnum`  
 [out] Retourne un [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) objet représentant la liste des constructeurs. Retourne une valeur null s’il n’y a aucuns constructeurs.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne S_OK ou retourne S_FALSE, s’il n’y a aucuns constructeurs. Sinon, retourne un code d'erreur.  
  
## <a name="remarks"></a>Notes  
 Chaque élément de l’énumération est un [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md) objet décrivant une méthode de constructeur.  
  
 En règle générale, la liste des constructeurs n’inclut pas les constructeurs par défaut fournis par un compilateur.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)   
 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)   
 [CONSTRUCTOR_ENUM](../../../extensibility/debugger/reference/constructor-enum.md)