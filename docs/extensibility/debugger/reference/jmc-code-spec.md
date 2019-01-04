---
title: JMC_CODE_SPEC | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- JMC_CODE_SPEC
helpviewer_keywords:
- JMC_CODE_SPEC structure
ms.assetid: d89498f1-4234-46d9-b4e2-abbcbca5068a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 60febef76a02f45e1cbca859453bf56e9cd1e38e
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53850097"
---
# <a name="jmccodespec"></a>JMC_CODE_SPEC
Cette structure est utilisée pour définir les informations JustMyCode pour un module.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef struct _JMC_CODE_SPEC {  
   BOOL fIsUserCode;  
   BSTR bstrModuleName;  
} JMC_CODE_SPEC;  
```  
  
```csharp  
public struct JMC_CODE_SPEC {  
   public int    fIsUserCode;  
   public string bstrModuleName;  
};  
```  
  
## <a name="members"></a>Membres  
 fIsUserCode  
 Valeur différente de zéro (`TRUE`) si le module doit être considéré comme du code de l’utilisateur ; sinon, zéro (`FALSE`) si le module est à considérer comme du code externe et ne pas à déboguer.  
  
 bstrModuleName  
 Nom du module en question.  
  
## <a name="remarks"></a>Notes  
 Cette structure est passée comme une liste de telles structures à le [SetJustMyCodeState](../../../extensibility/debugger/reference/idebugengine3-setjustmycodestate.md) (méthode).  
  
## <a name="requirements"></a>Spécifications  
 En-tête : msdbg.h  
  
 Espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Structures et Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [SetJustMyCodeState](../../../extensibility/debugger/reference/idebugengine3-setjustmycodestate.md)