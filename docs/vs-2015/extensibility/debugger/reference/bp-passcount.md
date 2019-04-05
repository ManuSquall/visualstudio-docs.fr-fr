---
title: BP_PASSCOUNT | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- BP_PASSCOUNT
helpviewer_keywords:
- BP_PASSCOUNT structure
ms.assetid: 791ac175-b897-4c70-873e-240da7e0ac89
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b99cbd777755a9a48869299b5cea523ecacbb4a4
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58948801"
---
# <a name="bppasscount"></a>BP_PASSCOUNT
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Décrit le nombre et les conditions sur lequel un point d’arrêt conditionnel est déclenché.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
typedef struct _BP_PASSCOUNT {   
   DWORD              dwPassCount;  
   BP_PASSCOUNT_STYLE stylePassCount;  
} BP_PASSCOUNT;  
```  
  
```csharp  
public struct BP_PASSCOUNT {   
   public uint dwPassCount;  
   public uint stylePassCount;  
};  
```  
  
## <a name="members"></a>Membres  
 `dwPassCount`  
 Le nombre de fois à passer sur le point d’arrêt avant de déclencher l’il.  
  
 `stylePassCount`  
 Une valeur comprise entre le [BP_PASSCOUNT_STYLE](../../../extensibility/debugger/reference/bp-passcount-style.md) énumération qui spécifie le style du point d’arrêt passer le nombre.  
  
## <a name="remarks"></a>Notes  
 Cette structure est un membre de la [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) structure.  
  
 Cette structure est également passée en tant que paramètre à la[SetPassCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setpasscount.md) et[SetPassCount](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setpasscount.md) méthodes.  
  
## <a name="requirements"></a>Configuration requise  
 En-tête : msdbg.h  
  
 Espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Structures et Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)   
 [SetPassCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setpasscount.md)   
 [SetPassCount](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setpasscount.md)   
 [BP_PASSCOUNT_STYLE](../../../extensibility/debugger/reference/bp-passcount-style.md)
