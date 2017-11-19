---
title: IDebugObject::GetValue | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugObject::GetValue
helpviewer_keywords: IDebugObject::GetValue method
ms.assetid: eec6051e-8ecb-49fa-bdd4-dd786f211692
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 4a9e79c808c02d5c2d04631e6a2981269c5e3a32
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="idebugobjectgetvalue"></a>IDebugObject::GetValue
Obtient la valeur de l’objet sous la forme d’une série consécutif d’octets.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetValue(   
   BYTE* pValue,  
   UINT  nSize  
);  
```  
  
```csharp  
int GetValue(  
   ref byte[] pValue,   
   uint nSize  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pValue`  
 [dans, out] Tableau qui est rempli avec une série consécutif d’octets qui représente la valeur de l’objet.  
  
 `nSize`  
 [in] Le nombre maximal d’octets à extraire.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne S_OK ; Sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Remarques  
 Obtenir le nombre total d’octets de valeur peuvent être extraites en appelant le [GetSize](../../../extensibility/debugger/reference/idebugobject-getsize.md) (méthode).  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)