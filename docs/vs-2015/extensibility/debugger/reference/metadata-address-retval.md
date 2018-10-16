---
title: METADATA_ADDRESS_RETVAL | Microsoft Docs
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
- METADATA_ADDRESS_RETVAL
helpviewer_keywords:
- METADATA_ADDRESS_RETVAL structure
ms.assetid: 5b0ec0fb-84b3-4ce7-8e24-becf3d881d7d
caps.latest.revision: 7
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3fd6a5d6992ac91c2c37718e29b23b4a7bae2259
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49279459"
---
# <a name="metadataaddressretval"></a>METADATA_ADDRESS_RETVAL
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Cette structure représente une valeur de retour à partir d’une méthode ou une fonction.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef struct _tagMETADATA_ADDRESS_RETVAL {  
   _mdToken tokMethod;  
   DWORD    dwCorType;  
   DWORD    dwSigSize;  
   BYTE     rgSig[10];  
} METADATA_ADDRESS_RETVAL;  
```  
  
```csharp  
public struct METADATA_ADDRESS_RETVAL {  
   public int    tokMethod;  
   public uint   dwCorType;  
   public uint   dwSigSize;  
   public byte[] rgSig;  
}  
```  
  
## <a name="terms"></a>Termes  
 tokMethod  
 ID de la méthode pour cette valeur de retour.  
  
 dwCorType  
 Le type de base de la valeur de retour. Il s’agit d’une valeur comprise entre le `CorElementType` énumération définie dans le [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] fichier corhdr.h de kit de développement logiciel.  
  
 dwSigSize  
 La taille de la signature de la valeur de retour (tel que stocké dans `rgSig`).  
  
 rgSig  
 Un tableau d’octets qui forment la signature de la valeur de retour.  
  
## <a name="remarks"></a>Notes  
 Cette structure fait partie de l’union dans le [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md) structure lorsque le `dwKind` champ la `DEBUG_ADDRESS_UNION` structure est définie sur `ADDRESS_KIND_RETVAL` (une valeur comprise entre le [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md) énumération).  
  
## <a name="requirements"></a>Configuration requise  
 En-tête : sh.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Structures et Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)   
 [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)

