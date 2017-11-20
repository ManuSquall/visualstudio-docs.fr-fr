---
title: "Ijsdebugframe::getdocumentpositionwithid, méthode | Documents Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IJsDebugFrame.GetDocumentPositionWithId
apilocation: jscript9diag.dll
ms.assetid: 48f8eb26-8ae4-4d5c-bd94-796023b03bcb
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f11e9ad51094522adec99ef82681f42ac500a251
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="ijsdebugframegetdocumentpositionwithid-method"></a>IJsDebugFrame::GetDocumentPositionWithId, méthode
Retourne la position actuelle de ce frame de pile dans le document au niveau de l’utilisateur.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetDocumentPositionWithId(  
   UINT64 *pDocumentId,  
   DWORD *pCharacterOffset,  
   DWORD *pStatementCharCount  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pDocumentId`  
 [out] ID unique d’un document source (pointeur vers le IDebugDocumentText).  
  
 `pCharacterOffset`  
 [out] L’offset de base zéro du caractère à partir du début du script.  
  
 `pStatementCharCount`  
 [out] La longueur de l’instruction actuelle, qui commence à * pCharacterOffset, en caractères.  
  
## <a name="return-value"></a>Valeur de retour  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** jscript9diag.h  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IJsDebugFrame](../../winscript/reference/ijsdebugframe-interface.md)