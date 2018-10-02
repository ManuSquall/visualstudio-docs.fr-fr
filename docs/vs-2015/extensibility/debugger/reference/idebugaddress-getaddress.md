---
title: IDebugAddress::GetAddress | Microsoft Docs
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
- IDebugAddress::GetAddress
helpviewer_keywords:
- IDebugAddress:GetAddress method
ms.assetid: 2590387b-5d36-4116-9a75-737957b8898e
caps.latest.revision: 7
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e4a469ba1e6f85a1ac83ba06efa45ba2b6c4fcbc
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47505410"
---
# <a name="idebugaddressgetaddress"></a>IDebugAddress::GetAddress
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [IDebugAddress::GetAddress](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugaddress-getaddress).  
  
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
 [in, out] Un [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) structure est remplie par cette méthode.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne S_OK ; Sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 Le [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) structure est passée à cette méthode, qui ensuite le remplit avec les informations appropriées. Interprétation de ces informations varie selon le type d’informations renvoyées et le Gestionnaire de symbole lui-même. Consultez [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) pour plus d’informations.  
  
## <a name="see-also"></a>Voir aussi  
 [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)

