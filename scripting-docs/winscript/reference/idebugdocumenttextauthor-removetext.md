---
title: IDebugDocumentTextAuthor::RemoveText | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentTextAuthor.RemoveText
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugDocumentTextAuthor::RemoveText
ms.assetid: 2b74d850-c0b1-4a3c-a37c-2c8d06d1ae02
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 989031a6d4b207c69d1a58b2ff99e5797a629440
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63007761"
---
# <a name="idebugdocumenttextauthorremovetext"></a>IDebugDocumentTextAuthor::RemoveText
Supprime le texte du document.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT RemoveText(  
   ULONG  cCharacterPosition,  
   ULONG  cNumToRemove  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `cCharacterPosition`  
 [in] Démarrer l’emplacement de la plage de caractères à supprimer.  
  
 `cNumToRemove`  
 [in] Nombre de caractères à supprimer.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Value|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
 Cette méthode supprime le texte du document.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugDocumentTextAuthor Interface](../../winscript/reference/idebugdocumenttextauthor-interface.md)   
 [IDebugDocumentTextAuthor::InsertText](../../winscript/reference/idebugdocumenttextauthor-inserttext.md)