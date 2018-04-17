---
title: NATIVE_ADDRESS | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- NATIVE_ADDRESS
helpviewer_keywords:
- NATIVE_ADDRESS structure
ms.assetid: 7a0cd085-bfc8-45cc-a3d4-4459070e207a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: fb443816db82d6003536b36783fd6555ef45db24
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="nativeaddress"></a>NATIVE_ADDRESS
Cette structure représente une adresse native.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef struct _tagNATIVE_ADDRESS {  
   DWORD unknown;  
} NATIVE_ADDRESS;  
```  
  
```csharp  
public struct NATIVE_ADDRESS {  
   public uint unknown;  
}  
```  
  
## <a name="terms"></a>Termes  
 Inconnu  
 L’adresse native (la signification de ce dépend de l’exécution et le système d’exploitation).  
  
## <a name="remarks"></a>Notes  
 Cette structure est la partie de l’union dans la [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md) lors de la structure la `dwKind` champ le `DEBUG_ADDRESS_UNION` structure est définie sur `ADDRESS_KIND_NATIVE` (une valeur à partir de la [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md) énumération).  
  
## <a name="requirements"></a>Spécifications  
 En-tête : sh.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Structures et Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)