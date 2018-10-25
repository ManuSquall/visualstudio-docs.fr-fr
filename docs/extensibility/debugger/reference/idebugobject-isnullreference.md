---
title: IDebugObject::IsNullReference | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugObject::IsNullReference
helpviewer_keywords:
- IDebugObject::IsNullReference method
ms.assetid: 6dbfcdb0-954f-4486-8fac-7ea8d003e3a9
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d6b5108d9fd830c047c020d4b3adab2526854e6c
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49939694"
---
# <a name="idebugobjectisnullreference"></a>IDebugObject::IsNullReference
Teste si cet objet est une référence null.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT IsNullReference(   
   BOOL* pfIsNull  
);  
```  
  
```csharp  
int IsNullReference(  
   out int pfIsNull  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pfIsNull`  
 [out] Retourne zéro (`TRUE`) si cet objet est une référence null ; sinon, retourne la valeur zéro (`FALSE`).  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne S_OK ; Sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 Une référence null signifie qu’un objet vide ou un objet qui n’a pas été affecté à.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)