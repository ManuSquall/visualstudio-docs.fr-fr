---
title: IDebugField::GetExtendedInfo | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugField::GetExtendedInfo
helpviewer_keywords: IDebugField::GetExtendedInfo method
ms.assetid: 46c0dd4d-4fd5-4efd-a908-71e4248e8e8d
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a5b52c5634b4b34edf11ddb8a56317cc237063bf
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
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
 [in] Sélectionne les informations à retourner. Les valeurs valides sont les suivantes :  
  
|Valeur|Description|  
|-----------|-----------------|  
|`guidConstantValue`|La valeur comme une séquence d’octets.|  
|`guidConstantType`|Le type en tant qu’une signature de type.|  
  
 `prgBuffer`  
 [out] Retourne les informations étendues.  
  
 `pdwLen`  
 [dans, out] Retourne la taille des informations étendues, en octets.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Remarques  
 Actuellement, cette méthode retourne uniquement le type ou la valeur d’une constante. L’appelant doit libérer la mémoire tampon retournée dans `prgBuffer` par un appel de COM `CoTaskMemFree` (fonction) (C++) ou <xref:System.Runtime.InteropServices.Marshal.FreeCoTaskMem%2A> (c#).  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)