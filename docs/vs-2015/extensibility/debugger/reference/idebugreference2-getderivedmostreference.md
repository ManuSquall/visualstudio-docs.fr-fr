---
title: IDebugReference2::GetDerivedMostReference | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugReference2::GetDerivedMostReference
helpviewer_keywords:
- IDebugReference2::GetDerivedMostReference
ms.assetid: 07253b74-7d39-48e0-8e85-ac8dfd919f6e
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 44413531cf3a91c6677d9ce3d56e10646307ffd6
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58948412"
---
# <a name="idebugreference2getderivedmostreference"></a>IDebugReference2::GetDerivedMostReference
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Obtient la référence de la plus dérivée d’une référence. Réservé à un usage ultérieur.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
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
  
## <a name="remarks"></a>Notes  
 Par exemple, si cette propriété décrit un objet qui implémente `ClassRoot` mais qui est en fait une instanciation de `ClassDerived` qui est dérivée de `ClassRoot`, cette méthode retourne un [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) objet représentant une référence à la `ClassDerived` objet.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
