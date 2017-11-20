---
title: IDebugClassField::GetEnclosingClass | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugClassField::GetEnclosingClass
helpviewer_keywords: IDebugClassField::GetEnclosingClass method
ms.assetid: a0c12e3c-9ea0-4dfb-9e45-8cea18725022
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: fbec5ac48280cf10bc89e73faca0779384bf3549
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="idebugclassfieldgetenclosingclass"></a>IDebugClassField::GetEnclosingClass
Obtient la classe qui définit cette classe.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
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
 [out] Retourne un [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) classe d’objet qui représente la forme. Retourne une valeur null si aucune classe englobante.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne S_OK ; Sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Remarques  
 Si la classe représentée par ce [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) objet est une classe imbriquée, puis le `ppClassField` paramètre retourne un `IDebugClassField` classe d’objet qui représente la forme. Par exemple, étant donné cette définition de classe :  
  
```  
class RootClass {  
   class NestedClass { }  
};  
```  
  
 Appel de la `GetEnclosingClass` méthode sur le `IDebugClassField` objet représentant le `NestedClass` classe retourne une `IDebugClassField` objet représentant la classe `RootClass`.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)