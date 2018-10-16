---
title: IDebugProcessEx2::Detach | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugProcessEx2::Detach
helpviewer_keywords:
- IDebugProcessEx2::Detach method
ms.assetid: 66d54c2c-9302-47c8-9975-f30ed988ab29
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b86de470e52ae99ed7850b7a84c01c54de72b3b1
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49171430"
---
# <a name="idebugprocessex2detach"></a>IDebugProcessEx2::Detach
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Cette méthode informe le processus qu’une session est le débogage n’est plus le processus.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
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
 [in] Une valeur qui identifie de façon unique la session pour détacher ce processus à partir de l’utilisateur.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 L’interface passée dans `pSession` est traité uniquement comme un cookie, une valeur qui identifie de façon unique le Gestionnaire de débogage de session qui a initialement attachée à ce processus ; aucune des méthodes sur l’interface fournie sont fonctionnels.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugProcessEx2](../../../extensibility/debugger/reference/idebugprocessex2.md)

