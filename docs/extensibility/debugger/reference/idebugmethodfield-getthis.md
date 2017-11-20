---
title: IDebugMethodField::GetThis | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugMethodField::GetThis
helpviewer_keywords: IDebugMethodField::GetThis method
ms.assetid: cc235bea-e909-4d8c-ab54-936736c803fc
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 91c4e2b693ffcca1a88cde1372197026758eb7d3
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="idebugmethodfieldgetthis"></a>IDebugMethodField::GetThis
Obtient le `this` (`Me` dans [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)]) pointeur de l’objet qui contient la méthode.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetThis(   
   IDebugClassField** ppClass  
);  
```  
  
```csharp  
int GetThis(  
   out IDebugClassField ppClass  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `ppClass`  
 [out] Retourne un [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) objet représentant le pointeur « this ».  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne S_OK ; Sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Remarques  
 Dans les langages orientés objet, il y a généralement un pointeur implicite à l’instanciation actuelle d’une classe. Il s’agit en tant que `this` en C# / C++ et en tant que `Me` dans [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)].  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)   
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)