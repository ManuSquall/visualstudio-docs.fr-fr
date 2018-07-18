---
title: CODE_PATH | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- CODE_PATH
helpviewer_keywords:
- CODE_PATH structure
ms.assetid: 2d4b2890-4c9d-47e1-83c0-df9c6436427f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6c88737638b20eafdef0ef84f5c45e494cf39607
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31109783"
---
# <a name="codepath"></a>CODE_PATH
Décrit un appel de méthode ou fonction.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef struct tagCODE_PATH {   
   BSTR                bstrName;  
   IDebugCodeContext2* pCode;  
} CODE_PATH;  
```  
  
```csharp  
public struct CODE_PATH {  
   public string            bstrName;  
   public IDebugCodeContext pCode;  
}  
```  
  
## <a name="members"></a>Membres  
 bstrName  
 Le nom du chemin d’accès du code.  
  
 pCode  
 Le [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) objet identifie où dans le code pas à pas une fonction.  
  
## <a name="remarks"></a>Notes  
 Cette structure est utilisée pour implémenter le pas à pas détaillé dans une fonction. [EnumCodePaths](../../../extensibility/debugger/reference/idebugprogram2-enumcodepaths.md) renvoie tous les appels de l’emplacement actuel dans le programme en cours de débogage. Cette structure représente un appel de ce type.  
  
## <a name="requirements"></a>Spécifications  
 En-tête : msdbg.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Structures et Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)   
 [EnumCodePaths](../../../extensibility/debugger/reference/idebugprogram2-enumcodepaths.md)