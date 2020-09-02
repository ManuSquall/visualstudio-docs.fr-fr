---
title: BP_LOCATION_CODE_ADDRESS | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- BP_LOCATION_CODE_ADDRESS
helpviewer_keywords:
- BP_LOCATION_CODE_ADDRESS structure
ms.assetid: 83c9da8b-19d9-4be5-b225-854543654901
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b23073c41f5da7d1563a6be46e0d114334527b35
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68153508"
---
# <a name="bp_location_code_address"></a>BP_LOCATION_CODE_ADDRESS
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Décrit l’emplacement d’un point d’arrêt à une adresse dans le code.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
typedef struct _BP_LOCATION_CODE_ADDRESS {   
   BSTR bstrContext;  
   BSTR bstrModuleUrl;  
   BSTR bstrFunction;  
   BSTR bstrAddress;  
} BP_LOCATION_CODE_ADDRESS;  
```  
  
## <a name="members"></a>Membres  
 `bstrContext`  
 Contexte du point d’arrêt, en général une méthode ou un nom de fonction tel qu’il apparaît sur une pile des appels.  
  
 `bstrModuleUrl`  
 URL du module qui contient le point d’arrêt.  
  
 `bstrFunction`  
 Nom de la fonction qui contient le point d’arrêt.  
  
 `bstrAddress`  
 Adresse du point d’arrêt, qui est analysée par un évaluateur d’expression pour le lier à un objet [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) .  
  
## <a name="remarks"></a>Notes  
 Cette structure est un membre de la structure [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) dans le cadre d’une Union.  
  
## <a name="requirements"></a>Configuration requise  
 En-tête : msdbg. h  
  
 Espace de noms : Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Structures et unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)   
 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
