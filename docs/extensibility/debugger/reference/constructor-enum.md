---
title: CONSTRUCTOR_ENUM | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- CONSTRUCTOR_ENUM
helpviewer_keywords:
- CONSTRUCTOR_ENUM enumeration
ms.assetid: 6d335b2c-66bc-460c-a4a6-4f3f1b697c2c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b4abc7e2eb8b29a0a7486264732778502c032f42
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31099712"
---
# <a name="constructorenum"></a>CONSTRUCTOR_ENUM
Sélectionne les différents types de constructeurs.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef enum ConstructorMatchOptions {   
   crAll       = 0,  
   crNonStatic = 1,  
   crStatic    = 2  
} CONSTRUCTOR_ENUM;  
```  
  
```csharp  
public enum ConstructorMatchOptions {   
   crAll       = 0,  
   crNonStatic = 1,  
   crStatic    = 2  
};  
```  
  
## <a name="members"></a>Membres  
 crAll  
 Sélectionne tous les constructeurs.  
  
 crNonStatic  
 Sélectionne les constructeurs non statique.  
  
 crStatic  
 Sélectionne les constructeurs statiques.  
  
## <a name="remarks"></a>Notes  
 Est passé comme argument à la [EnumConstructors](../../../extensibility/debugger/reference/idebugclassfield-enumconstructors.md) (méthode).  
  
## <a name="requirements"></a>Spécifications  
 En-tête : sh.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md)