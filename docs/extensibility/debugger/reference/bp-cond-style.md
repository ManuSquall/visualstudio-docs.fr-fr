---
title: BP_COND_STYLE | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: BP_COND_STYLE
helpviewer_keywords: BP_COND_STYLE enumeration
ms.assetid: a93b1412-f447-48a1-af9d-38f3dbb3092f
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a2dd89bd7e70e619bea5f1f2cb17b70e98eecaf3
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="bpcondstyle"></a>BP_COND_STYLE
Spécifie le style de condition de point d’arrêt pour en attente et les points d’arrêt liés.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
enum enum_BP_COND_STYLE {   
   BP_COND_NONE         = 0x0000,  
   BP_COND_WHEN_TRUE    = 0x0001,  
   BP_COND_WHEN_CHANGED = 0x0002  
};  
typedef DWORD BP_COND_STYLE;  
```  
  
```csharp  
public enum enum_BP_COND_STYLE {   
   BP_COND_NONE         = 0x0000,  
   BP_COND_WHEN_TRUE    = 0x0001,  
   BP_COND_WHEN_CHANGED = 0x0002  
};  
```  
  
## <a name="members"></a>Membres  
 BP_COND_NONE  
 Se déclenche le point d’arrêt lorsque position du point d’arrêt est atteinte. Aucune condition de point d’arrêt spécifiée.  
  
 BP_COND_WHEN_TRUE  
 Se déclenche le point d’arrêt uniquement lorsque l’expression conditionnelle associé avec le point d’arrêt a la valeur `true`.  
  
 BP_COND_WHEN_CHANGED  
 Se déclenche le point d’arrêt uniquement lorsque le point d’arrêt associé à la valeur de l’expression conditionnelle a changé depuis son évaluation précédente.  
  
## <a name="remarks"></a>Remarques  
 Utilisé pour le `styleCondition` membre de la [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md) structure.  
  
## <a name="requirements"></a>Spécifications  
 En-tête : msdbg.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md)