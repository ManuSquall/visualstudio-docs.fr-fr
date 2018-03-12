---
title: dwTYPE_KIND | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- dwTYPE_KIND
helpviewer_keywords:
- dwTYPE_KIND enumeration
ms.assetid: 6ff56b0f-c502-4e6c-9829-bfa05361b783
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 97136c781fa0ba6b3eb79250a4ecbe0bd2e4e694
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="dwtypekind"></a>dwTYPE_KIND
Indique comment interpréter le type d’un [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) objet.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
enum enum_dwTYPE_KIND {  
   TYPE_KIND_METADATA = 0x0001,  
   TYPE_KIND_PDB      = 0x0002,  
   TYPE_KIND_BUILT    = 0x0003,  
};  
  
typedef DWORD dwTYPE_KIND;  
```  
  
```csharp  
public enum enum_dwTYPE_KIND {  
   TYPE_KIND_METADATA = 0x0001,  
   TYPE_KIND_PDB      = 0x0002,  
   TYPE_KIND_BUILT    = 0x0003,  
};  
```  
  
#### <a name="parameters"></a>Paramètres  
 TYPE_KIND_METADATA  
 Le [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) union doit être interprétée comme un [METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md) structure.  
  
 TYPE_KIND_PDB  
 Le `TYPE_INFO` union doit être interprétée comme un [PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md) structure.  
  
 TYPE_KIND_BUILT  
 Le `TYPE_INFO` union doit être interprétée comme un [BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md) structure.  
  
## <a name="remarks"></a>Notes  
 Les valeurs de cette énumération apparaissent dans le `dwKind` champ le [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) structurer et sont utilisés pour déterminer comment interpréter le `type` membre d’union. Le `TYPE_INFO` structure est retournée par un appel à la [GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md) (méthode).  
  
## <a name="requirements"></a>Configuration requise  
 En-tête : sh.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)   
 [GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md)   
 [METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md)   
 [PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md)   
 [BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md)