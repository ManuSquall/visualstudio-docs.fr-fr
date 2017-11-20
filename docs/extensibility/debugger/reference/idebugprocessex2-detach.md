---
title: IDebugProcessEx2::Detach | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProcessEx2::Detach
helpviewer_keywords: IDebugProcessEx2::Detach method
ms.assetid: 66d54c2c-9302-47c8-9975-f30ed988ab29
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d810008391398741e644da7215de174918db604f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="idebugprocessex2detach"></a>IDebugProcessEx2::Detach
Cette méthode permet d’informer le processus qu’une session de débogage n’est plus le processus.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT Detach(   
   IDebugSession2* pSession  
);  
```  
  
```csharp  
int Detach(  
   IDebugSession2 pSession  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pSession`  
 [in] Une valeur qui identifie de façon unique la session pour ce processus à partir de détachement.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Remarques  
 L’interface est passée dans `pSession` est considérée uniquement comme un cookie, une valeur qui identifie de façon unique le Gestionnaire de session de débogage qui a initialement associée à ce processus ; aucune des méthodes sur l’interface fournie sont fonctionnels.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugProcessEx2](../../../extensibility/debugger/reference/idebugprocessex2.md)