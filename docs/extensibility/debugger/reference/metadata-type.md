---
title: METADATA_TYPE | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- METADATA_TYPE
helpviewer_keywords:
- METADATA_TYPE structure
ms.assetid: 2d8b78f6-0aef-4d79-809a-cff9b2c24659
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 66a1632198a0af5490e66a843458fc55bcad2d6d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31134719"
---
# <a name="metadatatype"></a>METADATA_TYPE
Cette structure fournit des informations sur un type de champ extraites à partir des métadonnées.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
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
 ID de l’application d'où provenance le symbole. Cela est utilisé pour identifier de façon unique une instance de l’application.  
  
 guidModule  
 Le GUID du module qui contient ce champ.  
  
 tokClass  
 ID de jeton de métadonnées de ce type.  
  
 (C++) `_mdToken` est un `typedef` pour 32 bits `int`.  
  
## <a name="remarks"></a>Notes  
 Cette structure s’affiche dans le cadre de l’union dans la [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) lors de la structure la `dwKind` champ le `TYPE_INFO` structure est définie sur `TYPE_KIND_METADATA` (une valeur à partir de la [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md) énumération).  
  
 Le `tokClass` valeur est un jeton de métadonnées qui identifie un type. Pour plus d’informations sur la façon d’interpréter les bits de l’ID de jeton de métadonnées, consultez la `CorTokenType` énumération dans le fichier corhdr.h dans le [!INCLUDE[dnprdnshort](../../../code-quality/includes/dnprdnshort_md.md)] Kit de développement logiciel.  
  
## <a name="requirements"></a>Spécifications  
 En-tête : sh.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Structures et Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)   
 [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)