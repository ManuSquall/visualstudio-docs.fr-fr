---
title: IDebugGenericFieldDefinition::GetFormalTypeParams | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- GetFormalTypeParams
- IDebugGenericFieldDefinition::GetFormalTypeParams
ms.assetid: cadbd6a1-bc7c-4aff-8777-5396b7a23c3e
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c3eb40b1b24ca70e0ce1f44490c80231827b5fe1
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47493591"
---
# <a name="idebuggenericfielddefinitiongetformaltypeparams"></a>IDebugGenericFieldDefinition::GetFormalTypeParams
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [IDebugGenericFieldDefinition::GetFormalTypeParams](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebuggenericfielddefinition-getformaltypeparams).  
  
Récupère les paramètres de type étant données le nombre de paramètres.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
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

