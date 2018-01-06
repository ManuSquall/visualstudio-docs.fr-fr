---
title: IEnumDebugAddresses::Skip | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IEnumDebugAddresses::Skip
helpviewer_keywords: IEnumDebugAddresses::Skip method
ms.assetid: ed9a8e71-30ef-414b-9da5-c9a2a251b84e
caps.latest.revision: "6"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: be85a2a24c55c37ae3e30a38e45695ca4f98d607
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ienumdebugaddressesskip"></a>IEnumDebugAddresses::Skip
Cette méthode ignore le nombre spécifié d’éléments.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT Skip(  
   [in] ULONG celt  
);  
```  
  
```csharp  
int Skip(  
   uint celt  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `celt`  
 [in] Nombre d’éléments à ignorer.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`. Retourne `S_FALSE` si `celt` est supérieur au nombre d’éléments restants ; sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 Si `celt` spécifie une valeur supérieure au nombre d’éléments restants, l’énumération est définie à la fin et `S_FALSE` est retourné.  
  
## <a name="see-also"></a>Voir aussi  
 [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md)