---
title: IDebugClassField::GetEnclosingClass | Microsoft Docs
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
- IDebugClassField::GetEnclosingClass
helpviewer_keywords:
- IDebugClassField::GetEnclosingClass method
ms.assetid: a0c12e3c-9ea0-4dfb-9e45-8cea18725022
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 69c9359fe8d9f337a09e0ab3fae4f92b0fc4c264
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49924737"
---
# <a name="idebugclassfieldgetenclosingclass"></a>IDebugClassField::GetEnclosingClass
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Obtient la classe qui définit cette classe.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT GetEnclosingClass(   
   IDebugClassField** ppClassField  
);  
```  
  
```csharp  
int GetEnclosingClass(  
   out IDebugClassField ppClassField  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `ppClassField`  
 [out] Retourne un [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) objet représentant la forme de classe. Retourne une valeur null si aucune classe englobante.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne S_OK ; Sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 Si la classe représentée par ce [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) objet est une classe imbriquée, puis le `ppClassField` paramètre renvoie un `IDebugClassField` classe d’objet qui représente la forme. Par exemple, étant donné cette définition de classe :  
  
```  
class RootClass {  
   class NestedClass { }  
};  
```  
  
 Appelant le `GetEnclosingClass` méthode sur le `IDebugClassField` objet représentant le `NestedClass` classe retourne un `IDebugClassField` objet représentant la classe `RootClass`.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)

