---
title: IDebugModule3::SetJustMyCodeState | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugModule3::SetJustMyCodeState
helpviewer_keywords: IDebugModule3::SetJustMyCodeState
ms.assetid: 68f8166d-ef64-49ae-ad5e-79604f43bbd4
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f0d34dba427106f2f8f99b3cfe4bc586579ee4be
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="idebugmodule3setjustmycodestate"></a>IDebugModule3::SetJustMyCodeState
Marque le module comme étant le code utilisateur ou non.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT SetJustMyCodeState(  
   BOOL fIsUserCode  
);  
```  
  
```csharp  
int SetJustMyCodeState(  
   int fIsUserCode  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `fIsUserCode`  
 [in] Différent de zéro (`TRUE`) si le module doit être considérée comme code utilisateur, zéro (`FALSE`) s’il ne doit pas.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne le code d’erreur.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)