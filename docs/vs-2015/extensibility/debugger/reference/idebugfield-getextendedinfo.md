---
title: 'IDebugField :: GetExtendedInfo | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugField::GetExtendedInfo
helpviewer_keywords:
- IDebugField::GetExtendedInfo method
ms.assetid: 46c0dd4d-4fd5-4efd-a908-71e4248e8e8d
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 3de21bc984a36db87f8ce1567f4ff7d97212c40e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62547557"
---
# <a name="idebugfieldgetextendedinfo"></a>IDebugField::GetExtendedInfo
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Cette méthode obtient des informations étendues sur un champ.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT GetExtendedInfo(   
   REFGUID guidExtendedInfo,  
   BYTE**  prgBuffer,  
   DWORD*  pdwLen  
);  
```  
  
```csharp  
int GetExtendedInfo(  
   ref Guid guidExtendedInfo,   
   IntPtr[] prgBuffer,   
   ref uint pdwLen  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `guidExtendedInfo`  
 dans Sélectionne les informations à retourner. Les valeurs autorisées sont :  
  
|Valeur|Description|  
|-----------|-----------------|  
|`guidConstantValue`|Valeur sous la forme d’une séquence d’octets.|  
|`guidConstantType`|Type comme une signature de type.|  
  
 `prgBuffer`  
 à Retourne les informations étendues.  
  
 `pdwLen`  
 [in, out] Retourne la taille des informations étendues, en octets.  
  
## <a name="return-value"></a>Valeur renvoyée  
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.  
  
## <a name="remarks"></a>Notes  
 Actuellement, cette méthode retourne uniquement le type ou la valeur d’une constante. L’appelant doit libérer la mémoire tampon retournée dans `prgBuffer` en appelant la fonction de com `CoTaskMemFree` (C++) ou <xref:System.Runtime.InteropServices.Marshal.FreeCoTaskMem%2A> (C#).  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
