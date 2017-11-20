---
title: BSTR_ARRAY | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: BSTR_ARRAY
helpviewer_keywords: BSTR_ARRAY structure
ms.assetid: 48da37f7-a237-48a9-9ff9-389c1a00862c
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 32ef5a93cc5051e2431305dd5181908e9cb7b153
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="bstrarray"></a>BSTR_ARRAY
Une structure qui décrit un tableau de chaînes.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef struct tagBSTR_ARRAY {  
   DWORD dwCount;  
   BSTR* Members;  
} BSTR_ARRAY;  
```  
  
```csharp  
struct BSTR_ARRAY {  
   DWORD    dwCount;  
   string[] Members;  
}  
```  
  
## <a name="terms"></a>Termes  
 dwCount  
 Nombre de chaînes dans `Members` tableau.  
  
 Membres  
 Tableau de chaînes.  
  
## <a name="remarks"></a>Remarques  
 Cette structure est retournée à partir de la [EnumPersistedPorts](../../../extensibility/debugger/reference/idebugportsupplier3-enumpersistedports.md) (méthode).  
  
 (C++ uniquement) Chaque chaîne individuelle doit être libérée à l’aide de `SysFreeString`et le `Members` tableau doit être libéré avec `CoTaskMemFree`.  
  
## <a name="requirements"></a>Spécifications  
 En-tête : msdbg.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Structures et Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [EnumPersistedPorts](../../../extensibility/debugger/reference/idebugportsupplier3-enumpersistedports.md)