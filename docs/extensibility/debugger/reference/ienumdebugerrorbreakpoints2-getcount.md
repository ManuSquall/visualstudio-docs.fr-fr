---
title: IEnumDebugErrorBreakpoints2::GetCount | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IEnumDebugErrorBreakpoints2::GetCount
helpviewer_keywords:
- IEnumDebugErrorBreakpoints2::GetCount
ms.assetid: 56f7bb70-d55b-471c-8c65-09a9e7f4938e
caps.latest.revision: 11
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
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: 761305c9328ce7102579504ef3e3d959e8b68ec8
ms.contentlocale: fr-fr
ms.lasthandoff: 09/26/2017

---
# <a name="ienumdebugerrorbreakpoints2getcount"></a>IEnumDebugErrorBreakpoints2::GetCount
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
  
## <a name="remarks"></a>Remarques  
 Cette méthode n’est pas partie de l’interface d’énumération COM habituel qui spécifie que seules les `Next`, `Clone`, `Skip`, et `Reset` les méthodes doivent être implémentées.  
  
## <a name="see-also"></a>Voir aussi  
 [IEnumDebugErrorBreakpoints2](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2.md)
