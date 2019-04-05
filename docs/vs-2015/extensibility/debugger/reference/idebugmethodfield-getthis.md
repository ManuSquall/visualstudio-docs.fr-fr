---
title: IDebugMethodField::GetThis | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugMethodField::GetThis
helpviewer_keywords:
- IDebugMethodField::GetThis method
ms.assetid: cc235bea-e909-4d8c-ab54-936736c803fc
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 786f3986875518470ed5756a0f7b57f4f93f5ca2
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58954077"
---
# <a name="idebugmethodfieldgetthis"></a>IDebugMethodField::GetThis
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Obtient le `this` (`Me` dans [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]) pointeur de l’objet qui contient la méthode.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
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
  
## <a name="remarks"></a>Notes  
 Dans les langages orientés objet, il est généralement un pointeur implicite à l’instanciation actuelle d’une classe. Il s’agit `this` en C# / C++ et en tant que `Me` dans [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)].  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)   
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
