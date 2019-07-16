---
title: IDebugGenericFieldInstance::TypeArgumentCount | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- TypeArgumentCount
- IDebugGenericFieldInstance::TypeArgumentCount
ms.assetid: e662c5ea-a5c1-478e-a268-5980dadffcd1
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 80c2aea4130fe7de0208d4c40b0f01afed06eecf
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68180858"
---
# <a name="idebuggenericfieldinstancetypeargumentcount"></a>IDebugGenericFieldInstance::TypeArgumentCount
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Retourne le nombre de type des arguments de paramètre pour cette instance.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
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
 [in, out] Nombre d’arguments de paramètre de type pour cette instance.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 Par exemple, si liste\<int >, cette méthode retourne 1 et, s’il liste\<int, float2 > cette méthode retourne la valeur 2. Cette méthode retourne 0 si n’inclut aucun argument de type.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugGenericFieldInstance](../../../extensibility/debugger/reference/idebuggenericfieldinstance.md)
