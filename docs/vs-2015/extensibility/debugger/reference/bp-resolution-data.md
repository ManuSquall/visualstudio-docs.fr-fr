---
title: BP_RESOLUTION_DATA | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- BP_RESOLUTION_DATA
helpviewer_keywords:
- BP_RESOLUTION_DATA structure
ms.assetid: 9e0b9000-6a84-47b9-b07a-367a75764389
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1139663c24e8341bd7f46131355ef32a05e0c074
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47503266"
---
# <a name="bpresolutiondata"></a>BP_RESOLUTION_DATA
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [BP_RESOLUTION_DATA](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/bp-resolution-data).  
  
Décrit le résultat de la liaison d’un point d’arrêt de données.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
typedef struct _BP_RESOLUTION_DATA {   
   BSTR              bstrDataExpr;  
   BSTR              bstrFunc;  
   BSTR              bstrImage;  
   BP_RES_DATA_FLAGS dwFlags;  
} BP_RESOLUTION_DATA;  
```  
  
```csharp  
public struct BP_RESOLUTION_DATA {   
   public string bstrDataExpr;  
   public string bstrFunc;  
   public string bstrImage;  
   public uint   dwFlags;  
};  
```  
  
## <a name="members"></a>Membres  
 `bstrDataExpr`  
 L’expression de données qui a été liée.  
  
 `bstrFunc`  
 Le nom de la fonction du point d’arrêt a lié dans (le cas échéant).  
  
 `bstrImage`  
 Le nom du module (MyModule.dll, par exemple) que le point d’arrêt a lié dans.  
  
 `dwFlags`  
 Une valeur comprise entre le [BP_RES_DATA_FLAGS](../../../extensibility/debugger/reference/bp-res-data-flags.md) énumération, décrivant la façon dont le point d’arrêt de données est implémentée.  
  
## <a name="remarks"></a>Notes  
 Cette structure est un membre de la [BP_RESOLUTION_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md) structure, qui est d’activer un membre de la [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) structure retournée par le [GetResolutionInfo](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)(méthode).  
  
## <a name="requirements"></a>Configuration requise  
 En-tête : msdbg.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Structures et Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [BP_RESOLUTION_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md)   
 [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)   
 [GetResolutionInfo](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)

