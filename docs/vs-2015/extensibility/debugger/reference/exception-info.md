---
title: EXCEPTION_INFO | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- EXCEPTION_INFO
helpviewer_keywords:
- EXCEPTION_INFO structure
ms.assetid: d046957a-b97d-420b-b46b-c67cbaef709e
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 66af4d95707be99865df3df32751215cf5eb10b2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68181170"
---
# <a name="exception_info"></a>EXCEPTION_INFO
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Décrit une exception ou une erreur d’exécution levée par le programme en cours de débogage.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
typedef struct tagEXCEPTION_INFO {   
   IDebugProgram2* pProgram;  
   BSTR            bstrProgramName;  
   BSTR            bstrExceptionName;  
   DWORD           dwCode;  
   EXCEPTION_STATE dwState;  
   GUID            guidType;  
} EXCEPTION_INFO;  
```  
  
```csharp  
public struct EXCEPTION_INFO {   
   public IDebugProgram2 pProgram;  
   public string         bstrProgramName;  
   public string         bstrExceptionName;  
   public uint           dwCode;  
   public uint           dwState;  
   public Guid           guidType;  
};  
```  
  
## <a name="members"></a>Membres  
 pProgram  
 Objet [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) qui représente le programme dans lequel l’exception s’est produite.  
  
 bstrProgramName  
 Nom du programme dans lequel l’exception s’est produite.  
  
 bstrExceptionName  
 Nom de l'exception.  
  
 dwCode  
 Code d’identification de l’erreur d’exception ou d’exécution.  
  
 dwState  
 Valeur de l’énumération [EXCEPTION_STATE](../../../extensibility/debugger/reference/exception-state.md) qui définit l’état de l’exception.  
  
 guidType  
 Identificateur de langue GUID, `guidLang` ou `guidEng` .  
  
## <a name="remarks"></a>Notes  
 Cette structure est passée en tant que paramètre aux méthodes [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md) et [RemoveSetException](../../../extensibility/debugger/reference/idebugengine2-removesetexception.md) . Cette structure est également passée à la méthode [GetException](../../../extensibility/debugger/reference/idebugexceptionevent2-getexception.md) à remplir.  
  
## <a name="requirements"></a>Configuration requise  
 En-tête : msdbg. h  
  
 Espace de noms : Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Structures et unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [EXCEPTION_STATE](../../../extensibility/debugger/reference/exception-state.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md)   
 [RemoveSetException](../../../extensibility/debugger/reference/idebugengine2-removesetexception.md)   
 [GetException](../../../extensibility/debugger/reference/idebugexceptionevent2-getexception.md)
