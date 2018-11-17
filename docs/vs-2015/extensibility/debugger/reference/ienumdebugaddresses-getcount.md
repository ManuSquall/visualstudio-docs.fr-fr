---
title: IEnumDebugAddresses::GetCount | Microsoft Docs
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
- IEnumDebugAddresses::GetCount
helpviewer_keywords:
- IEnumDebugAddresses::GetCount method
ms.assetid: f2ca8ff8-539f-457c-83f8-9bbf97618065
caps.latest.revision: 6
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1b9ce150eac3137c9fd078fd111b83a517f1b825
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51729915"
---
# <a name="ienumdebugaddressesgetcount"></a>IEnumDebugAddresses::GetCount
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Cette méthode retourne le nombre d’éléments dans l’énumération.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT GetCount(  
   [out] ULONG* pcelt  
);  
```  
  
```csharp  
int GetCount(  
   out uint pcelt  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pcelt`  
 [out] Retourne le nombre d’éléments dans l’énumération.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 Cette méthode ne fait pas partie de l’interface d’énumération COM habituel qui spécifie qu’uniquement suivant Clone, Skip et réinitialisation doivent être implémentées.  
  
## <a name="see-also"></a>Voir aussi  
 [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md)

