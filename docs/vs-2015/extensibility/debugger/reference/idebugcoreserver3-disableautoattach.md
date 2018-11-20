---
title: IDebugCoreServer3::DisableAutoAttach | Microsoft Docs
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
- IDebugCoreServer3::DisableAutoAttach
helpviewer_keywords:
- IDebugCoreServer3::DisableAutoAttach
ms.assetid: 9d860a20-c154-4df4-ba15-636e0fcd42bf
caps.latest.revision: 7
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f91944d669557daabd40805be2f096538b160bce
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51733495"
---
# <a name="idebugcoreserver3disableautoattach"></a>IDebugCoreServer3::DisableAutoAttach
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Désactive l’attachement automatique pour tous les moteurs de débogage associés à ce serveur.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT DisableAutoAttach(  
   void  
);  
```  
  
```csharp  
int DisableAutoAttach();  
```  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne le code d’erreur.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)

