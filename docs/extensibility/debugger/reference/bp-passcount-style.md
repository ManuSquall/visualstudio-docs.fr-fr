---
title: BP_PASSCOUNT_STYLE | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: BP_PASSCOUNT_STYLE
helpviewer_keywords: BP_PASSCOUNT_STYLE structure
ms.assetid: 0a647047-e2d5-4724-a0b8-68108425ecad
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 58baa5aca9ef5bddf5d7060fdc88022952bc9ce3
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="bppasscountstyle"></a>BP_PASSCOUNT_STYLE
Spécifie la condition associée le nombre de passe de point d’arrêt, le point d’arrêt sont activés.  
  
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
 Ne spécifie aucun style de nombre passe de point d’arrêt.  
  
 BP_PASSCOUNT_EQUAL  
 Définit le style de nombre passe de point d’arrêt pour être égale. Le point d’arrêt se déclenche lorsque le nombre de fois où que le point d’arrêt est égale au nombre de test.  
  
 BP_PASSCOUNT_EQUAL_OR_GREATER  
 Définit le style de nombre de passage de point d’arrêt sur égale ou supérieure. Le point d’arrêt se déclenche lorsque le nombre de fois où que le point d’arrêt est égal à ou supérieur au nombre de test.  
  
 BP_PASSCOUNT_MOD  
 Spécifie un modulo passer le nombre. Par exemple, si le compteur transmis est de type `BP_PASSCOUNT_MOD` et passe la valeur du nombre est 4, le se déclenche de point d’arrêt chaque fois que le nombre d’accès est un multiple de 4.  
  
## <a name="remarks"></a>Remarques  
 Utilisé pour le `stylePassCount` membre de la [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md) structure qui est à son tour un membre de la [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) et [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) structures.  
  
## <a name="requirements"></a>Spécifications  
 En-tête : msdbg.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md)   
 [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)   
 [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)