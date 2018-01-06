---
title: IEnumCodePaths2::GetCount | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IEnumCodePaths2::GetCount
helpviewer_keywords: IEnumCodePaths2::GetCount
ms.assetid: 988c5092-fcc5-43a1-a94c-c261edd56ebf
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 8b1ff8c25beecc5591be9139162f2a81ffa7c854
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ienumcodepaths2getcount"></a>IEnumCodePaths2::GetCount
Retourne le nombre d’éléments dans l’énumération.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetCount(  
   ULONG* pcelt  
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
 Cette méthode n’est pas partie de l’interface d’énumération COM habituel qui spécifie que seules les `Next`, `Clone`, `Skip`, et `Reset` les méthodes doivent être implémentées.  
  
## <a name="see-also"></a>Voir aussi  
 [IEnumCodePaths2](../../../extensibility/debugger/reference/ienumcodepaths2.md)