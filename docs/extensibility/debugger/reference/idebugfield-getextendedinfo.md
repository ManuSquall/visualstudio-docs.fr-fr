---
title: IDebugField::GetExtendedInfo | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugField::GetExtendedInfo
helpviewer_keywords:
- IDebugField::GetExtendedInfo method
ms.assetid: 46c0dd4d-4fd5-4efd-a908-71e4248e8e8d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ef431fbc3bf14124ee0ea08a2439c0473e958a91
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53945208"
---
# <a name="idebugfieldgetextendedinfo"></a>IDebugField::GetExtendedInfo
Cette méthode obtient des informations étendue sur un champ.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
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
 [in] Sélectionne les informations devant être retournées. Les valeurs valides sont les suivantes :  
  
|Value|Description|  
|-----------|-----------------|  
|`guidConstantValue`|La valeur comme une séquence d’octets.|  
|`guidConstantType`|Le type en tant qu’une signature de type.|  
  
 `prgBuffer`  
 [out] Retourne les informations étendues.  
  
 `pdwLen`  
 [in, out] Retourne la taille des informations étendues, en octets.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 Actuellement, cette méthode retourne uniquement le type ou la valeur d’une constante. L’appelant doit libérer la mémoire tampon retournée dans `prgBuffer` par l’appel de COM `CoTaskMemFree` (fonction) (C++) ou <xref:System.Runtime.InteropServices.Marshal.FreeCoTaskMem%2A> (c#).  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)