---
title: IDebugIDECallback::DisplayMessage | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugIDECallback::DisplayMessage
ms.assetid: c19b48ee-b370-4fce-91fe-f82bf1e63179
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 23124c148d59c1a390f40e630d927e43d0d264cc
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58950910"
---
# <a name="idebugidecallbackdisplaymessage"></a>IDebugIDECallback::DisplayMessage
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Envoie la chaîne de message spécifié à la fenêtre de sortie du débogueur.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT DisplayMessage (  
   LPCOLESTR szMessage  
);  
```  
  
```csharp  
int DisplayMessage (  
   string szMessage  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `szMessage`  
 [in] Chaîne de message à afficher dans la fenêtre de sortie du débogueur.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugIDECallback](../../../extensibility/debugger/reference/idebugidecallback.md)
