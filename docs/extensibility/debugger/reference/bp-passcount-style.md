---
title: BP_PASSCOUNT_STYLE | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- BP_PASSCOUNT_STYLE
helpviewer_keywords:
- BP_PASSCOUNT_STYLE structure
ms.assetid: 0a647047-e2d5-4724-a0b8-68108425ecad
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f382c83813eb794fc48e33310ba8381030b424fc
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49846120"
---
# <a name="bppasscountstyle"></a>BP_PASSCOUNT_STYLE
Spécifie la condition associée au nombre de passage de point d’arrêt qui provoque le point d’arrêt à déclencher.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
enum enum_BP_PASSCOUNT_STYLE {   
   BP_PASSCOUNT_NONE             = 0x0000,  
   BP_PASSCOUNT_EQUAL            = 0x0001,  
   BP_PASSCOUNT_EQUAL_OR_GREATER = 0x0002,  
   BP_PASSCOUNT_MOD              = 0x0003  
};  
typedef DWORD BP_PASSCOUNT_STYLE;  
```  
  
```csharp  
public enum enum_BP_PASSCOUNT_STYLE {   
   BP_PASSCOUNT_NONE             = 0x0000,  
   BP_PASSCOUNT_EQUAL            = 0x0001,  
   BP_PASSCOUNT_EQUAL_OR_GREATER = 0x0002,  
   BP_PASSCOUNT_MOD              = 0x0003  
};  
```  
  
## <a name="members"></a>Membres  
 BP_PASSCOUNT_NONE  
 Ne spécifie aucun style de nombre de pass de point d’arrêt.  
  
 BP_PASSCOUNT_EQUAL  
 Définit le style de nombre de pass de point d’arrêt à égal. Le point d’arrêt se déclenche lorsque le nombre de fois où que le point d’arrêt est atteint égale au nombre de pass.  
  
 BP_PASSCOUNT_EQUAL_OR_GREATER  
 Définit le style de nombre de pass de point d’arrêt comme égale ou supérieure. Le point d’arrêt se déclenche lorsque le nombre de fois où que le point d’arrêt est atteint est égal à ou supérieur au nombre de pass.  
  
 BP_PASSCOUNT_MOD  
 Spécifie un modulo passer le nombre. Par exemple, si le nombre de pass est du type `BP_PASSCOUNT_MOD` et la valeur du nombre pass est 4, le se de point d’arrêt déclenche chaque fois que le nombre d’accès est un multiple de 4.  
  
## <a name="remarks"></a>Notes  
 Utilisé pour le `stylePassCount` membre de la [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md) structure qui est à son tour un membre de la [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) et [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) structures.  
  
## <a name="requirements"></a>Configuration requise  
 En-tête : msdbg.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md)   
 [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)   
 [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)