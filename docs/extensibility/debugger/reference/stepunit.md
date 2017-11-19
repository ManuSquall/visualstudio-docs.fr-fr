---
title: STEPUNIT | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: STEPUNIT
helpviewer_keywords: STEPUNIT enumeration
ms.assetid: cb8441f2-f744-4e73-acfe-ae8542df9649
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e0f4dab5124e3f7d6924c5f02f552832e8b0fd36
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="stepunit"></a>STEPUNIT
Spécifie l’unité d’étape pour l’exécution pas à pas.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
enum enum_STEPUNIT {   
   STEP_STATEMENT   = 0,  
   STEP_LINE        = 1,  
   STEP_INSTRUCTION = 2  
};  
typedef DWORD STEPUNIT;  
```  
  
```csharp  
enum enum_STEPUNIT {   
   STEP_STATEMENT   = 0,  
   STEP_LINE        = 1,  
   STEP_INSTRUCTION = 2  
};  
```  
  
## <a name="members"></a>Membres  
 STEP_STATEMENT  
 Étapes de l’instruction.  
  
 STEP_LINE  
 Opérations en ligne.  
  
 STEP_INSTRUCTION  
 Étapes de l’instruction.  
  
## <a name="remarks"></a>Remarques  
 Est passé comme argument à la [étape](../../../extensibility/debugger/reference/idebugprocess3-step.md) (méthode).  
  
## <a name="requirements"></a>Spécifications  
 En-tête : msdbg.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [Step](../../../extensibility/debugger/reference/idebugprocess3-step.md)