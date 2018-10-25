---
title: IDebugEngine2::SetLocale | Microsoft Docs
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
- IDebugEngine2::SetLocale
helpviewer_keywords:
- IDebugEngine2::SetLocale
ms.assetid: cd0d2cf1-2aac-43da-a830-4bb3d696c219
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 140034aa4328dccfbba47faa7e9d000cc097fc23
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49924443"
---
# <a name="idebugengine2setlocale"></a>IDebugEngine2::SetLocale
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Définit les paramètres régionaux du moteur de débogage (dé).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
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

