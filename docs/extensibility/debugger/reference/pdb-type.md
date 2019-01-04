---
title: PDB_TYPE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- PDB_TYPE
helpviewer_keywords:
- PDB_TYPE structure
ms.assetid: 1c1bb772-77d6-4870-90b2-fd9247d0004e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: caa171ec3f0d9718f40f2c1c77b2ba692466b3cb
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53910501"
---
# <a name="pdbtype"></a>PDB_TYPE
Cette structure spécifie des informations sur un type de champ extraites à partir d’un symbole PDB.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef struct _tagTYPE_PDB {  
   ULONG32 ulAppDomainID;  
   GUID    guidModule;  
   DWORD   symid;  
} PDB_TYPE;  
```  
  
```csharp  
public struct PDB_TYPE {  
   public uint ulAppDomainID;  
   public Guid guidModule;  
   public uint symid;  
};  
```  
  
#### <a name="parameters"></a>Paramètres  
 ulAppDomainID  
 ID de l’application d'où provenance le symbole. Cela est utilisé pour identifier de manière unique une instance de l’application.  
  
 guidModule  
 Le GUID du module qui contient ce champ.  
  
 SymID  
 ID de symbole qui correspond à ce champ.  
  
## <a name="remarks"></a>Notes  
 Cette structure apparaît dans le cadre de l’union dans le [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) structure lorsque le `dwKind` champ la `TYPE_INFO` structure est définie sur `TYPE_KIND_PDB` (une valeur comprise entre le [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md) énumération).  
  
## <a name="requirements"></a>Spécifications  
 En-tête : sh.h  
  
 Espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Structures et Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)   
 [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)