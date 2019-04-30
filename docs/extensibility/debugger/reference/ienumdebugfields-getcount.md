---
title: IEnumDebugFields::GetCount | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IEnumDebugFields::GetCount
helpviewer_keywords:
- IEnumDebugFields::GetCount method
ms.assetid: 3f471b40-4db3-49f7-b504-58b2476eef74
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 9c6aa7969e2c0e3836df5c710983b1c57c92c045
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62914758"
---
# <a name="ienumdebugfieldsgetcount"></a>IEnumDebugFields::GetCount
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Cette méthode retourne le nombre d’éléments dans l’énumération.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT GetCount(  
   [out] ULONG* pcelt  
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
 Cette méthode ne fait pas partie de l’interface d’énumération COM habituel qui spécifie qu’uniquement suivant Clone, Skip et réinitialisation doivent être implémentées.  
  
## <a name="see-also"></a>Voir aussi  
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
