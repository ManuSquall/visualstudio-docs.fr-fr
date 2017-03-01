---
title: IDebugReference2::SetValueAsReference | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugReference2::SetValueAsReference
helpviewer_keywords:
- IDebugReference2::SetValueAsReference
ms.assetid: 94a545d2-16b9-45e9-b2e7-4e49ff90aad0
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 36c017b6579d5f6fa1e99f44470836e68640321f
ms.lasthandoff: 02/22/2017

---
# <a name="idebugreference2setvalueasreference"></a>IDebugReference2::SetValueAsReference
Définit la valeur d’une référence à partir d’une autre référence. Réservé à un usage ultérieur.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT SetValueAsReference (   
   IDebugReference2** rgpArgs,  
   DWORD              dwArgCount,  
   IDebugReference2*  pValue,  
   DWORD              dwTimeout  
);  
```  
  
```cpp#  
int SetValueAsReference (   
   IDebugReference2[] rgpArgs,  
   uint               dwArgCount,  
   IDebugReference2   pValue,  
   uint               dwTimeout  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `rgpArgs`  
 [in] Un tableau de [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) des objets utilisés pour déterminer comment définir la valeur de référence.  
  
 `dwArgCount`  
 [in] Le nombre de références dans le tableau.  
  
 `pValue`  
 [in] Un [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) objet à partir duquel la valeur de propriété.  
  
 `dwTimeout`  
 [in] Temps maximal, en millisecondes, d’attente avant le retour de cette méthode. Utilisez `INFINITE` pour attendre indéfiniment.  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne toujours `E_NOTIMPL`.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
