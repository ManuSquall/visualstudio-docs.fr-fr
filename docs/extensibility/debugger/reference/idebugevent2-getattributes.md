---
title: IDebugEvent2::GetAttributes | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugEvent2::GetAttributes
helpviewer_keywords:
- IDebugEvent2::GetAttributes
ms.assetid: 2ac5b5fb-da17-43f7-811a-313f677e60d7
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6d6305d7000456eb81cf01c9e85e6c2a421ed800
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="idebugevent2getattributes"></a>IDebugEvent2::GetAttributes
Obtient les attributs de cet événement de débogage.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetAttribute(   
   DWORD* pdwAttrib  
);  
```  
  
```csharp  
int GetAttribute(   
   out uint pdwAttrib  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pdwAttrib`  
 [out] Une combinaison d’indicateurs à partir de la [EVENTATTRIBUTES](../../../extensibility/debugger/reference/eventattributes.md) énumération.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 Le [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) interface est commune à tous les événements. Cette méthode décrit le type d’événement ; par exemple, est l’événement synchrone ou asynchrone, et il est un événement d’arrêt.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [EVENTATTRIBUTES](../../../extensibility/debugger/reference/eventattributes.md)