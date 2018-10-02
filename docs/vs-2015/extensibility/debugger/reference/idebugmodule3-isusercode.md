---
title: IDebugModule3::IsUserCode | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugModule3::IsUserCode
helpviewer_keywords:
- IDebugModule3::IsUserCode
ms.assetid: 77022946-bb8b-4114-aa81-614df6e54b13
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f6e633006cd41cfd88c85d8213498786c13fad9b
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47503245"
---
# <a name="idebugmodule3isusercode"></a>IDebugModule3::IsUserCode
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [IDebugModule3::IsUserCode](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugmodule3-isusercode).  
  
Récupère des informations sur indique si le module représente le code utilisateur ou non.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT IsUserCode(  
   BOOL* pfUser  
);  
```  
  
```csharp  
int IsUserCode(  
   out int pfUser  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pfUser`  
 [out] Différent de zéro (`TRUE`) si le module représente le code utilisateur, zéro (`FALSE`) si elle n’est pas le cas.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne le code d’erreur.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)

