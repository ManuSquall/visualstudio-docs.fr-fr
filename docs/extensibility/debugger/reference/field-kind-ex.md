---
title: FIELD_KIND_EX | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- FIELD_KIND_EX enumeration
ms.assetid: 922c3208-1e94-485f-b70a-3bc96affeff8
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b6954aaf92c5d77ad4d8f51e6b342bfc021b37a7
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53870873"
---
# <a name="fieldkindex"></a>FIELD_KIND_EX
Énumère les types de champs supplémentaires qui un [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) objet peut contenir. Cette énumération étend la [FIELD_KIND](../../../extensibility/debugger/reference/field-kind.md) énumération.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
enum enum_FIELD_KIND_EX  
{  
   FIELD_KIND_EX_NONE = 0,  
   FIELD_TYPE_EX_METHODVAR = 0x1,  
   FIELD_TYPE_EX_CLASSVAR = 0x2  
} ;  
typedef DWORD FIELD_KIND_EX;  
```  
  
```csharp  
public enum enum_FIELD_KIND_EX  
{  
   FIELD_KIND_EX_NONE = 0,  
   FIELD_TYPE_EX_METHODVAR = 0x1,  
   FIELD_TYPE_EX_CLASSVAR = 0x2  
};  
```  
  
## <a name="members"></a>Membres  
 FIELD_KIND_EX_NONE  
 Champ ne contient pas un type étendu.  
  
 FIELD_TYPE_EX_METHODVAR  
 Champ contient une variable de méthode.  
  
 FIELD_TYPE_EX_CLASSVAR  
 Champ contient une variable de classe.  
  
## <a name="requirements"></a>Spécifications  
 En-tête : SH.h  
  
 Espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetExtendedKind](../../../extensibility/debugger/reference/idebugextendedfield-getextendedkind.md)