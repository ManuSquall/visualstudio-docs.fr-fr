---
title: PROGRAM_DESTROY_FLAGS | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- PROGRAM_DESTROY_FLAGS enumeration
ms.assetid: be00d4a3-d5b8-4159-b632-64577f534883
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 7746f85eeec41b708bd4c1537ee725d2096c41ef
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49920623"
---
# <a name="programdestroyflags"></a>PROGRAM_DESTROY_FLAGS
Énumère les valeurs du programme détruire des indicateurs.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
enum enum_PPROGRAM_DESTROY_FLAGS  
{  
   PROGRAM_DESTROY_CONTINUE_DEBUGGING = 0x1  
};  
typedef DWORD PROGRAM_DESTROY_FLAGS;  
```  
  
```csharp  
public enum enum_PPROGRAM_DESTROY_FLAGS  
{  
   PROGRAM_DESTROY_CONTINUE_DEBUGGING = 0x1  
};  
```  
  
## <a name="terms"></a>Termes  
 PROGRAM_DESTROY_CONTINUE_DEBUGGING  
 Détruire le programme, mais continuer à déboguer.  
  
## <a name="remarks"></a>Notes  
 L’énumération est retournée par la [GetFlags](../../../extensibility/debugger/reference/idebugprogramdestroyeventflags2-getflags.md) (méthode).  
  
## <a name="requirements"></a>Configuration requise  
 En-tête : Msdbg.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetFlags](../../../extensibility/debugger/reference/idebugprogramdestroyeventflags2-getflags.md)