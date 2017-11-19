---
title: IDebugReference2::GetDerivedMostReference | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugReference2::GetDerivedMostReference
helpviewer_keywords: IDebugReference2::GetDerivedMostReference
ms.assetid: 07253b74-7d39-48e0-8e85-ac8dfd919f6e
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 018f843e9e62430c780df1d3d15f06634a31908d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="idebugreference2getderivedmostreference"></a>IDebugReference2::GetDerivedMostReference
Obtient la référence de la plus dérivée d’une référence. Réservé à un usage ultérieur.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetDerivedMostReference(   
   IDebugReference2** ppDerivedMost  
);  
```  
  
```csharp  
int GetDerivedMostReference(   
   out IDebugReference2 ppDerivedMost  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `ppDerivedMost`  
 [out] Retourne un [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) objet qui représente la propriété la plus dérivée.  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne toujours `E_NOTIMPL`.  
  
## <a name="remarks"></a>Remarques  
 Par exemple, si cette propriété décrit un objet qui implémente `ClassRoot` mais qui est réellement une instanciation de `ClassDerived` qui est dérivée de `ClassRoot`, cette méthode retourne un [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) objet qui représente une référence à la `ClassDerived` objet.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)