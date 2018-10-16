---
title: REFERENCE_COMPARE | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- REFERENCE_COMPARE
helpviewer_keywords:
- REFERENCE_COMPARE enumeration
ms.assetid: e31cdc78-f621-498b-9ca4-aefa790b9f6f
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a79a44fea6d8e44a1978f17b933d9f51ebe069f5
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49266836"
---
# <a name="referencecompare"></a>REFERENCE_COMPARE
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Spécifie le type de comparaison des références.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
enum enum_REFERENCE_COMPARE {   
   REF_COMPARE_EQUAL        = 0x0001,  
   REF_COMPARE_LESS_THAN    = 0x0002,  
   REF_COMPARE_GREATER_THAN = 0x0003  
};  
typedef DWORD REFERENCE_COMPARE;  
```  
  
```csharp  
public enum enum_REFERENCE_COMPARE {   
   REF_COMPARE_EQUAL        = 0x0001,  
   REF_COMPARE_LESS_THAN    = 0x0002,  
   REF_COMPARE_GREATER_THAN = 0x0003  
};  
```  
  
## <a name="members"></a>Membres  
 REF_COMPARE_EQUAL  
 Spécifie une comparaison égal à.  
  
 REF_COMPARE_LESS_THAN  
 Spécifie un inférieur-que la comparaison.  
  
 REF_COMPARE_GREATER_THAN  
 Spécifie un signe supérieur-que la comparaison.  
  
## <a name="remarks"></a>Notes  
 Passé en tant qu’argument à la [comparer](../../../extensibility/debugger/reference/idebugreference2-compare.md) (méthode).  
  
## <a name="requirements"></a>Configuration requise  
 En-tête : msdbg.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [Compare](../../../extensibility/debugger/reference/idebugreference2-compare.md)

