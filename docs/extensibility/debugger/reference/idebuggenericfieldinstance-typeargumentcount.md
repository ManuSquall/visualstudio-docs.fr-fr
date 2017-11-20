---
title: IDebugGenericFieldInstance::TypeArgumentCount | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- TypeArgumentCount
- IDebugGenericFieldInstance::TypeArgumentCount
ms.assetid: e662c5ea-a5c1-478e-a268-5980dadffcd1
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ddaf2ff3323bb7e4e1da55eb1b8ad8cd8931f9c5
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="idebuggenericfieldinstancetypeargumentcount"></a>IDebugGenericFieldInstance::TypeArgumentCount
Retourne le nombre de types des arguments de paramètre pour cette instance.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT TypeArgumentCount(  
   ULONG32* pcArgs  
);  
```  
  
```csharp  
int TypeArgumentCount(  
   ref uint pcArgs  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pcArgs`  
 [dans, out] Nombre d’arguments de paramètre de type pour cette instance.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Remarques  
 Par exemple, si liste\<int >, cette méthode retourne 1 et, s’il liste\<int, float2 > cette méthode retourne la valeur 2. Cette méthode retourne 0 si il n’existe aucun argument de type.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugGenericFieldInstance](../../../extensibility/debugger/reference/idebuggenericfieldinstance.md)