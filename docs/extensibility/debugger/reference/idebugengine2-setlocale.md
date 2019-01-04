---
title: IDebugEngine2::SetLocale | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugEngine2::SetLocale
helpviewer_keywords:
- IDebugEngine2::SetLocale
ms.assetid: cd0d2cf1-2aac-43da-a830-4bb3d696c219
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6881a217ba1d5db885c8c963885eb69e4257b26e
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53908408"
---
# <a name="idebugengine2setlocale"></a>IDebugEngine2::SetLocale
Définit les paramètres régionaux du moteur de débogage (dé).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT SetLocale(   
   WORD wLangID  
);  
```  
  
```csharp  
int SetLocale(   
   ushort wLangID  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `wLangID`  
 [in] Spécifie les paramètres régionaux de langue. Par exemple, 1033 pour l’anglais.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 Cette méthode est appelée par le Gestionnaire de session de débogage (SDM) pour propager les paramètres régionaux de l’IDE afin que les chaînes retournées par l’Allemagne sont correctement localisés.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)