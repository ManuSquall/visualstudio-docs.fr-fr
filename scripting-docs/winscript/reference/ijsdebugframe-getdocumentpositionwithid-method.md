---
title: 'IJsDebugFrame :: GetDocumentPositionWithId, méthode | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugFrame.GetDocumentPositionWithId
apilocation:
- jscript9diag.dll
ms.assetid: 48f8eb26-8ae4-4d5c-bd94-796023b03bcb
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f35f6fb84db95950fe83d571c9f5e5e7db9de1e8
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573861"
---
# <a name="ijsdebugframegetdocumentpositionwithid-method"></a>IJsDebugFrame::GetDocumentPositionWithId, méthode
Retourne la position actuelle de ce frame de pile dans le document au niveau de l’utilisateur.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetDocumentPositionWithId(  
   UINT64 *pDocumentId,  
   DWORD *pCharacterOffset,  
   DWORD *pStatementCharCount  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pDocumentId`  
 à ID unique d’un document source (pointeur vers IDebugDocumentText).  
  
 `pCharacterOffset`  
 à Offset de caractère de base zéro à partir du début du script.  
  
 `pStatementCharCount`  
 à Longueur de l’instruction en cours, qui commence à * pCharacterOffset, en caractères.  
  
## <a name="return-value"></a>Valeur de retour  
  
## <a name="requirements"></a>spécifications  
 **En-tête :** jscript9diag. h  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IJsDebugFrame](../../winscript/reference/ijsdebugframe-interface.md)