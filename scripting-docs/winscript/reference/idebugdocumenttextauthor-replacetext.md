---
title: 'IDebugDocumentTextAuthor :: ReplaceText | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentTextAuthor.ReplaceText
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugDocumentTextAuthor::ReplaceText
ms.assetid: f89304e6-5be0-45a5-947d-2c59c3c0a05e
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: beca5d0ce19a38346ef9b03e39169769c90ea008
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572033"
---
# <a name="idebugdocumenttextauthorreplacetext"></a>IDebugDocumentTextAuthor::ReplaceText
Remplace le texte dans le document.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT ReplaceText(  
   ULONG    cCharacterPosition,  
   ULONG    cNumToReplace,  
   OLECHAR  pcharText[]  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `cCharacterPosition`  
 dans Emplacement de début de la plage de caractères à remplacer.  
  
 `cNumToReplace`  
 dans Nombre de caractères à remplacer.  
  
 `pcharText[]`  
 dans Mémoire tampon qui contient les nouveaux caractères pour remplacer les anciens caractères.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
 Cette méthode remplace le texte dans le document.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IDebugDocumentTextAuthor](../../winscript/reference/idebugdocumenttextauthor-interface.md)