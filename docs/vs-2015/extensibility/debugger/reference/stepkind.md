---
title: STEPKIND | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- STEPKIND
helpviewer_keywords:
- STEPKIND enumeration
ms.assetid: d3d8cf76-24bf-455e-803e-0e3e28f0b262
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: eb1a09f27f44254e7f3930f00efa3921faae710a
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49178514"
---
# <a name="stepkind"></a>STEPKIND
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Spécifie le type d’étape pour l’exécution pas à pas.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
enum enum_STEPKIND {   
   STEP_INTO      = 0,  
   STEP_OVER      = 1,  
   STEP_OUT       = 2,  
   STEP_BACKWARDS = 3  
};  
typedef DWORD STEPKIND;  
```  
  
```csharp  
public enum enum_STEPKIND {   
   STEP_INTO      = 0,  
   STEP_OVER      = 1,  
   STEP_OUT       = 2,  
   STEP_BACKWARDS = 3  
};  
```  
  
## <a name="members"></a>Membres  
 STEP_INTO  
 Étapes dans une fonction.  
  
 DECALAGE_PASSES  
 Exécute une fonction.  
  
 STEP_OUT  
 Sort une fonction.  
  
 STEP_BACKWARDS  
 Étapes vers l’arrière dans une fonction.  
  
## <a name="remarks"></a>Notes  
 Passé en tant qu’argument à la [étape](../../../extensibility/debugger/reference/idebugprocess3-step.md) (méthode).  
  
## <a name="requirements"></a>Configuration requise  
 En-tête : msdbg.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [Step](../../../extensibility/debugger/reference/idebugprocess3-step.md)

