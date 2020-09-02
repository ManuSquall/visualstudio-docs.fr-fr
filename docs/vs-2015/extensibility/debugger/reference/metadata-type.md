---
title: METADATA_TYPE | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- METADATA_TYPE
helpviewer_keywords:
- METADATA_TYPE structure
ms.assetid: 2d8b78f6-0aef-4d79-809a-cff9b2c24659
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1be7cb6071a0307a56285b8929e52e038c263fdc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62546822"
---
# <a name="metadata_type"></a>METADATA_TYPE
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Cette structure spécifie des informations sur un type de champ issu de métadonnées.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
typedef struct _tagTYPE_METADATA {  
   ULONG32  ulAppDomainID;  
   GUID     guidModule;  
   _mdToken tokClass;  
} METADATA_TYPE;  
```  
  
```csharp  
public struct METADATA_TYPE {  
   public uint ulAppDomainID;  
   public Guid guidModule;  
   public int  tokClass;  
};  
```  
  
#### <a name="parameters"></a>Paramètres  
 ulAppDomainID  
 ID de l’application à partir de laquelle le symbole a été obtenu. Cela permet d’identifier de manière unique une instance de l’application.  
  
 guidModule  
 GUID du module qui contient ce champ.  
  
 tokClass  
 ID de jeton de métadonnées de ce type.  
  
 (C++) `_mdToken` est un `typedef` pour un 32 bits `int` .  
  
## <a name="remarks"></a>Notes  
 Cette structure apparaît dans le cadre de l’Union dans la structure [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) lorsque le `dwKind` champ de la `TYPE_INFO` structure a la valeur `TYPE_KIND_METADATA` (une valeur de l’énumération [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md) ).  
  
 La `tokClass` valeur est un jeton de métadonnées qui identifie de façon unique un type. Pour plus d’informations sur la façon d’interpréter les bits supérieurs de l’ID de jeton de métadonnées, consultez l' `CorTokenType` énumération dans le fichier corhdr. h dans le [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] Kit de développement logiciel (SDK).  
  
## <a name="requirements"></a>Configuration requise  
 En-tête : SH. h  
  
 Espace de noms : Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Structures et unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)   
 [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)
