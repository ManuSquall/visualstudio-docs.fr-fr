---
title: IDebugObject2::IsUserData | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugObject2::IsUserData
helpviewer_keywords:
- IDebugObject2::IsUserData method
ms.assetid: 6ffa0d0e-f742-496d-acc7-db74c248bc45
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8c20b4e531284156b8790b1ca65b32c85d1db997
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="idebugobject2isuserdata"></a>IDebugObject2::IsUserData
Détermine si l’objet représente les données utilisateur.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT IsUserData(  
   BOOL* pfUser  
);  
```  
  
```csharp  
int IsUserData(  
   out int pfUser  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pfUser`  
 [out] Retourne zéro (`TRUE`) si l’objet représente les données utilisateur ; zéro (`FALSE`) si elle n’est pas le cas.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne S_OK ; Sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 Données utilisateur sont un objet qui fait partie d’un module désigné comme JustMyCode (une option configurable par l’utilisateur qui marque un module comme du code utilisateur et sont donc visibles dans une trace de pile).  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)