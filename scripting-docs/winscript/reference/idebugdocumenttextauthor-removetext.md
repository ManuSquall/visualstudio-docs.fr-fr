---
title: IDebugDocumentTextAuthor::RemoveText | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 8972c0ed03a7d926d080382a7825c295ca7c72a1
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54097095"
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
 [IDebugDocumentTextAuthor (Interface)](../../winscript/reference/idebugdocumenttextauthor-interface.md)   
 [IDebugDocumentTextAuthor::InsertText](../../winscript/reference/idebugdocumenttextauthor-inserttext.md)