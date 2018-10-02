---
title: IDebugProgram2::GetDisassemblyStream | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugProgram2::GetDisassemblyStream
helpviewer_keywords:
- IDebugProgram2::GetDisassemblyStream
ms.assetid: beda0da5-267e-4bf3-96c4-b659d29e2254
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 35c18db634e814bb07a29d858218795fcfa0dbcc
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47503430"
---
# <a name="idebugprogram2getdisassemblystream"></a>IDebugProgram2::GetDisassemblyStream
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [IDebugProgram2::GetDisassemblyStream](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugprogram2-getdisassemblystream).  
  
Obtient le flux de code machine pour ce programme ou une partie de ce programme.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT GetDisassemblyStream(   
   DISASSEMBLY_STREAM_SCOPE   dwScope,  
   IDebugCodeContext2*        pCodeContext,  
   IDebugDisassemblyStream2** ppDisassemblyStream  
);  
```  
  
```csharp  
int GetDisassemblyStream(   
   enum_DISASSEMBLY_STREAM_SCOPE  dwScope,  
   IDebugCodeContext2             pCodeContext,  
   out IDebugDisassemblyStream2   ppDisassemblyStream  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `dwScope`  
 [in] Spécifie une valeur à partir de la [DISASSEMBLY_STREAM_SCOPE](../../../extensibility/debugger/reference/disassembly-stream-scope.md) énumération qui définit l’étendue du flux de code machine.  
  
 `pCodeContext`  
 [in] Un [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) objet qui représente la position où commencer le flux de code machine.  
  
 `ppDisassemblyStream`  
 [out] Retourne un [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md) objet qui représente le flux de code machine.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur. Retourne `E_DISASM_NOTSUPPORTED` si le code machine n’est pas pris en charge pour cette architecture particulière.  
  
## <a name="remarks"></a>Notes  
 Si le `dwScopes` paramètre a la `DSS_HUGE` indicateur de la [DISASSEMBLY_STREAM_SCOPE](../../../extensibility/debugger/reference/disassembly-stream-scope.md) énumération définie, puis le code machine est supposé retourner un grand nombre d’instructions de code machine, par exemple, pour un fichier entier ou un module. Si le `DSS_HUGE` indicateur n’est pas défini, puis le code machine est censé se limiter à une région de petite, généralement que d’une fonction unique.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [DISASSEMBLY_STREAM_SCOPE](../../../extensibility/debugger/reference/disassembly-stream-scope.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)   
 [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)

