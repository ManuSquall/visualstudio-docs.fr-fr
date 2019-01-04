---
title: IDebugEvent2::GetAttributes | Microsoft Docs
ms.date: 11/04/2016
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
ms.openlocfilehash: d523a055f27961fe0d7676ba4f8e914b3d0f97be
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53950158"
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
 [out] Une combinaison d’indicateurs de la [EVENTATTRIBUTES](../../../extensibility/debugger/reference/eventattributes.md) énumération.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 Le [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) interface est commune à tous les événements. Cette méthode décrit le type d’événement ; par exemple, est l’événement synchrone ou asynchrone et il est un événement d’arrêt.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [EVENTATTRIBUTES](../../../extensibility/debugger/reference/eventattributes.md)