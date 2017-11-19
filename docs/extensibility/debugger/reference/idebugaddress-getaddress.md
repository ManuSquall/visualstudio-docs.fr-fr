---
title: IDebugAddress::GetAddress | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugAddress::GetAddress
helpviewer_keywords: IDebugAddress:GetAddress method
ms.assetid: 2590387b-5d36-4116-9a75-737957b8898e
caps.latest.revision: "6"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3ed14b69dbc116514b191aadf58d209b4d39e458
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="idebugaddressgetaddress"></a>IDebugAddress::GetAddress
Retourne une structure qui décrit un objet et son emplacement dans son étendue ou le conteneur.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetAddress (  
   DEBUG_ADDRESS * pAddress  
);  
```  
  
```csharp  
int GetAddress(  
   DEBUG_ADDRESS[] pAddress  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pAddress`  
 [dans, out] A [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) structure est remplie par cette méthode.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne S_OK ; Sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Remarques  
 Le [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) structure est passée à cette méthode, puis le remplit avec les informations appropriées. Interprétation de ces informations varie selon le type d’informations renvoyées et le Gestionnaire de symboles proprement dit. Consultez [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) pour plus d’informations.  
  
## <a name="see-also"></a>Voir aussi  
 [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)