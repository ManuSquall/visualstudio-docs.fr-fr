---
title: "TYPE_INFO | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "TYPE_INFO"
helpviewer_keywords: 
  - "Structure TYPE_INFO"
ms.assetid: d725cb68-a565-49d1-a16f-ff0445c587a0
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# TYPE_INFO
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Cette structure spécifie différents types d'informations sur un type de champ.  
  
## Syntaxe  
  
```cpp#  
struct _tagTYPE_INFO_UNION {  
   dwTYPE_KIND dwKind;  
   union {  
      METADATA_TYPE typeMeta;  
      PDB_TYPE      typePdb;  
      BUILT_TYPE    typeBuilt;  
      DWORD         unused;  
   } type;  
} TYPE_INFO;  
```  
  
```c#  
public struct TYPE_INFO {  
   public uint   dwKind;  
   public IntPtr unionmember;  
};  
```  
  
#### Paramètres  
 dwKind  
 une valeur de l'énumération de [dwTYPE\_KIND](../../../extensibility/debugger/reference/dwtype-kind.md) qui détermine comment interpréter l'union.  
  
 type.typeMeta  
 \[C\+\+\] uniquement contient une structure de [METADATA\_TYPE](../../../extensibility/debugger/reference/metadata-type.md) si `dwKind` est `TYPE_KIND_METADATA`.  
  
 type.typePdb  
 \[C\+\+\] uniquement contient une structure de [PDB\_TYPE](../../../extensibility/debugger/reference/pdb-type.md) si `dwKind` est `TYPE_KIND_PDB`.  
  
 type.typeBuilt  
 \[C\+\+\] uniquement contient une structure de [BUILT\_TYPE](../../../extensibility/debugger/reference/built-type.md) si `dwKind` est `TYPE_KIND_BUILT`.  
  
 type.unused  
 Remplissage inutilisée.  
  
 type  
 nom de l'union.  
  
 unionmember  
 \[C\#\] uniquement marshaler le type approprié de structure en fonction `dwKind`.  
  
## Notes  
 Cette structure est passée à la méthode d' [GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md) où elle est terminée.  Comment le contenu de la structure est interprète est basé sur le champ d' `dwKind` .  
  
> [!NOTE]
>  \[C\+\+\] uniquement si `dwKind` égale `TYPE_KIND_BUILT`, il est nécessaire de libérer l'objet sous\-jacent d' [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) en détruire la structure d' `TYPE_INFO` .  Cela est fait en appelant `typeInfo.type.typeBuilt.pUnderlyingField->Release()`.  
  
 \[C\#\] uniquement le tableau suivant montre comment interpréter le membre d' `unionmember` pour chaque genre de type.  L'exemple montre comment cela est fait à un genre de type.  
  
|`dwKind`|`unionmember` a interprète comme|  
|--------------|--------------------------------------|  
|`TYPE_KIND_METADATA`|[METADATA\_TYPE](../../../extensibility/debugger/reference/metadata-type.md)|  
|`TYPE_KIND_PDB`|[PDB\_TYPE](../../../extensibility/debugger/reference/pdb-type.md)|  
|`TYPE_KIND_BUILT`|[BUILT\_TYPE](../../../extensibility/debugger/reference/built-type.md)|  
  
## Exemple  
 Cet exemple montre comment interpréter le membre d' `unionmember` de la structure d' `TYPE_INFO` en c\#.  Cet exemple montre interpréter un seul type \(`TYPE_KIND_METADATA`\) mais les autres sont interprètes de la même façon.  
  
```c#  
using System;  
using System.Runtime.Interop.Services;  
using Microsoft.VisualStudio.Debugger.Interop;  
  
namespace MyPackage  
{  
    public class MyClass  
    {  
        public void Interpret(TYPE_INFO ti)  
        {  
            if (ti.dwKind == (uint)enum_dwTypeKind.TYPE_KIND_METADATA)  
            {  
                 METADATA_TYPE dataType = (METADATA_TYPE)Marshal.PtrToStructure(ti.unionmember,  
                                               typeof(METADATA_TYPE));  
            }  
        }  
    }  
}  
```  
  
## Configuration requise  
 en\-tête : sh.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [Structures et Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [dwTYPE\_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)   
 [GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md)   
 [METADATA\_TYPE](../../../extensibility/debugger/reference/metadata-type.md)   
 [PDB\_TYPE](../../../extensibility/debugger/reference/pdb-type.md)   
 [BUILT\_TYPE](../../../extensibility/debugger/reference/built-type.md)