---
title: IDebugGenericFieldDefinition::GetFormalTypeParams | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- GetFormalTypeParams
- IDebugGenericFieldDefinition::GetFormalTypeParams
ms.assetid: cadbd6a1-bc7c-4aff-8777-5396b7a23c3e
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6490a8ad013907c77d205838db6218a853e717bd
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "55029168"
---
# <a name="idebuggenericfielddefinitiongetformaltypeparams"></a>IDebugGenericFieldDefinition::GetFormalTypeParams
Récupère les paramètres de type étant données le nombre de paramètres.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetFormalTypeParams(  
   ULONG32                   cParams,  
   IDebugGenericParamField** ppParams,  
   ULONG32*                  pcParams  
);  
```  
  
```csharp  
int GetFormalTypeParams(  
   uint                          cParams,  
   out IDebugGenericParamField[] ppParams,  
   ref uint                      pcParams  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `cParams`  
 [in] Nombre de paramètres.  
  
 `ppParams`  
 [out] Tableau de paramètres de type.  
  
 `pcParams`  
 [in, out] Nombre de paramètres dans le `ppParams` tableau.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 Retourner les paramètres de type dans l’ordre de gauche à droite. Par exemple, dictionnaire\<K, V > retourne IDebugFormalGenericParameters {K, V}.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugGenericFieldDefinition](../../../extensibility/debugger/reference/idebuggenericfielddefinition.md)