---
title: 'IDebugDocumentTextAuthor :: RemoveText | Microsoft Docs'
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
ms.openlocfilehash: 119a55d4ebd20e51890358ef8c5780a2ac8e4509
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572048"
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
 dans Emplacement de début de la plage de caractères à supprimer.  
  
 `cNumToRemove`  
 dans Nombre de caractères à supprimer.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
 Cette méthode supprime le texte du document.  
  
## <a name="see-also"></a>Voir aussi  
 @No__t_1 de l' [interface IDebugDocumentTextAuthor](../../winscript/reference/idebugdocumenttextauthor-interface.md)  
 [IDebugDocumentTextAuthor::InsertText](../../winscript/reference/idebugdocumenttextauthor-inserttext.md)