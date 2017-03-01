---
title: IDebugReference2::GetDerivedMostReference | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugReference2::GetDerivedMostReference
helpviewer_keywords:
- IDebugReference2::GetDerivedMostReference
ms.assetid: 07253b74-7d39-48e0-8e85-ac8dfd919f6e
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
ms.openlocfilehash: 1cb281e93eb462de607f83a4e1d2d72785cef9a2
ms.lasthandoff: 02/22/2017

---
# <a name="idebugreference2getderivedmostreference"></a>IDebugReference2::GetDerivedMostReference
Obtient la référence de la plus dérivée d’une référence. Réservé à un usage ultérieur.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT GetDerivedMostReference(   
   IDebugReference2** ppDerivedMost  
);  
```  
  
```c#  
int GetDerivedMostReference(   
   out IDebugReference2 ppDerivedMost  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `ppDerivedMost`  
 [out] Retourne un [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) objet qui représente la propriété plus dérivé.  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne toujours `E_NOTIMPL`.  
  
## <a name="remarks"></a>Remarques  
 Par exemple, si cette propriété décrit un objet qui implémente `ClassRoot` , mais qui est en fait une instanciation de `ClassDerived` qui est dérivée de `ClassRoot`, cette méthode retourne un [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) objet représentant une référence à la `ClassDerived` objet.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
