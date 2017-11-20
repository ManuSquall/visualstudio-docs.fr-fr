---
title: METADATA_ADDRESS_ARRAYELEM | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: METADATA_ADDRESS_ARRAYELEM
helpviewer_keywords: METADATA_ADDRESS_ARRAYELEM structure
ms.assetid: 24321be5-7c17-4038-82a1-c20a2b68ff3c
caps.latest.revision: "6"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0a3d0cf905750aede0c2b9c29f45f63840226787
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="metadataaddressarrayelem"></a>METADATA_ADDRESS_ARRAYELEM
Cette structure représente un élément de tableau dans un tableau.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef struct _tagMETADATA_ADDRESS_ARRAYELEM {  
   _mdToken tokMethod;  
   DWORD    dwIndex;  
} METADATA_ADDRESS_ARRAYELEM;  
```  
  
```csharp  
public struct METADATA_ADDRESS_ARRAYELEM {  
   public int  tokMethod;  
   public uint dwIndex;  
}  
```  
  
## <a name="terms"></a>Termes  
 tokMethod  
 L’ID du tableau de cet élément est une partie de.  
  
 (C++) `_mdToken` est un `typedef` pour 32 bits `int`.  
  
 dwIndex  
 L’index de cet élément dans le tableau.  
  
## <a name="remarks"></a>Remarques  
 Cette structure est la partie de l’union dans la [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md) lors de la structure la `dwKind` champ le `DEBUG_ADDRESS_UNION` structure est définie sur `ADDRESS_KIND_ARRAYELEM` (une valeur à partir de la [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md) énumération).  
  
## <a name="requirements"></a>Spécifications  
 En-tête : sh.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Structures et Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)   
 [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)