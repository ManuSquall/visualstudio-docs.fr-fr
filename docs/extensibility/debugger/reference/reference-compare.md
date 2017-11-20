---
title: REFERENCE_COMPARE | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: REFERENCE_COMPARE
helpviewer_keywords: REFERENCE_COMPARE enumeration
ms.assetid: e31cdc78-f621-498b-9ca4-aefa790b9f6f
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 07d8b5ade6e80c0629d4f0c3eedee2941f9b95a5
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="referencecompare"></a>REFERENCE_COMPARE
Spécifie le type de comparaison de références.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
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
 Spécifie un caractère supérieur-que la comparaison.  
  
## <a name="remarks"></a>Remarques  
 Est passé comme argument à la [comparer](../../../extensibility/debugger/reference/idebugreference2-compare.md) (méthode).  
  
## <a name="requirements"></a>Spécifications  
 En-tête : msdbg.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [Compare](../../../extensibility/debugger/reference/idebugreference2-compare.md)