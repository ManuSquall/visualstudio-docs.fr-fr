---
title: DISASSEMBLY_STREAM_SCOPE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- DISASSEMBLY_STREAM_SCOPE
helpviewer_keywords:
- DISASSEMBLY_STREAM_SCOPE enumeration
ms.assetid: 43e2b364-cbbe-4755-a7e6-a03f3054c965
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3fddab6fc65848a5fa2577785d9f3db934f50086
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "55012935"
---
# <a name="disassemblystreamscope"></a>DISASSEMBLY_STREAM_SCOPE
Spécifie l’étendue du flux de code machine.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
enum enum_DISASSEMBLY_STREAM_SCOPE {   
   DSS_HUGE     = 0x10000000,  
   DSS_FUNCTION = 0x0001,  
   DSS_MODULE   = (DSS_HUGE) | 0x0002,  
   DSS_ALL      = (DSS_HUGE) | 0x0003  
};  
typedef DWORD DISASSEMBLY_STREAM_SCOPE;  
```  
  
```csharp  
public enum enum_DISASSEMBLY_STREAM_SCOPE {   
   DSS_HUGE     = 0x10000000,  
   DSS_FUNCTION = 0x0001,  
   DSS_MODULE   = (DSS_HUGE) | 0x0002,  
   DSS_ALL      = (DSS_HUGE) | 0x0003  
};  
```  
  
## <a name="members"></a>Membres  
 DSS_HUGE  
 Spécifie que le contexte de code de désassemblage générerait une sortie plus qu’un client veut généralement récupérer dans un seul appel.  
  
 DSS_FUNCTION  
 Spécifie que la fonction contenue dans le contexte de code doit être démontée. Spécifie que le flux de code machine représente une fonction, lorsque retournée par la [GetScope](../../../extensibility/debugger/reference/idebugdisassemblystream2-getscope.md) (méthode).  
  
 DSS_MODULE  
 Quand retournée par la `IDebugDisassemblyStream2::GetScope` méthode, spécifie que le flux de code machine représente un module.  
  
 DSS_ALL  
 Spécifie le code machine pour l’espace d’adressage entière.  
  
## <a name="remarks"></a>Notes  
 Passé en tant qu’argument à la [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md) méthode et retourné par le [GetScope](../../../extensibility/debugger/reference/idebugdisassemblystream2-getscope.md) (méthode).  
  
 Ces valeurs peuvent être combinées avec un opérateur de bits `OR`.  
  
## <a name="requirements"></a>Spécifications  
 En-tête : msdbg.h  
  
 Espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)   
 [GetScope](../../../extensibility/debugger/reference/idebugdisassemblystream2-getscope.md)