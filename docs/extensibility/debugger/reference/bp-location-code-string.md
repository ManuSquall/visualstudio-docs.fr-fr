---
title: BP_LOCATION_CODE_STRING | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- BP_LOCATION_CODE_STRING
helpviewer_keywords:
- BP_LOCATION_CODE_STRING structure
ms.assetid: a4cd71c6-5052-45fe-907b-ebc6ca1df2e4
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6fedefecdc59c7daf8dd1aa1b2ab015a5071ea25
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "55000212"
---
# <a name="bplocationcodestring"></a>BP_LOCATION_CODE_STRING
Utilisée pour définir des points d’arrêt de code basés sur une chaîne que l’utilisateur peut entrer dans l’environnement de développement intégré (IDE).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef struct _BP_LOCATION_CODE_STRING {   
   BSTR bstrContext;  
   BSTR bstrCodeExpr;  
} BP_LOCATION_CODE_STRING;  
```  
  
## <a name="members"></a>Membres  
 `bstrContext`  
 Le contexte de point d’arrêt dans le code, généralement un nom de méthode ou fonction tels que présentés sur une pile des appels.  
  
 `bstrCodeExpr`  
 La chaîne que l’utilisateur tape dans pour décrire le point d’arrêt du code.  
  
## <a name="remarks"></a>Notes  
 Cette structure est un membre de la [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) structure dans le cadre d’une union.  
  
## <a name="requirements"></a>Spécifications  
 En-tête : msdbg.h  
  
 Espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Structures et Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)