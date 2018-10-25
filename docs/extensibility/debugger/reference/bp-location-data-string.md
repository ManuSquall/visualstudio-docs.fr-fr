---
title: BP_LOCATION_DATA_STRING | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- BP_LOCATION_DATA_STRING
helpviewer_keywords:
- BP_LOCATION_DATA_STRING structure
ms.assetid: 445d6f3f-95b0-47ac-85e2-51b778240687
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8c740c853fff0701bf27d3c37d69141440525b44
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49875773"
---
# <a name="bplocationdatastring"></a>BP_LOCATION_DATA_STRING
Utilisée pour définir des points d’arrêt de données qui sont basées sur une chaîne de l’utilisateur peut entrer dans l’environnement de développement intégré (IDE).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef struct _BP_LOCATION_DATA_STRING {   
   IDebugThread2* pThread;  
   BSTR           bstrContext;  
   BSTR           bstrDataExpr;  
   DWORD          dwNumElements;  
} BP_LOCATION_DATA_STRING;  
```  
  
## <a name="members"></a>Membres  
 `pThread`  
 Le [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) objet qui représente le thread sur lequel le point d’arrêt se produit.  
  
 `bstrContext`  
 Le contexte de point d’arrêt dans le code, généralement un nom de méthode ou fonction tels que présentés sur une pile des appels.  
  
 `bstrDataExpr`  
 La chaîne de données passe à l’utilisateur pour définir le point d’arrêt.  
  
 `dwNumElements`  
 Le nombre d’éléments dans la chaîne de données dans laquelle le point d’arrêt se produit.  
  
## <a name="remarks"></a>Notes  
 Cette structure est un membre de la [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) structure dans le cadre d’une union.  
  
## <a name="requirements"></a>Configuration requise  
 En-tête : msdbg.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Structures et Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)