---
title: IDebugDocumentTextEvents::onRemoveText | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentTextEvents.onRemoveText
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugDocumentTextEvents::onRemoveText
ms.assetid: c5dfe674-c42f-4e57-9d48-8380d5aa206b
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 506d7c5349cf074ce4a4cbe60e33459a09a91b67
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62946711"
---
# <a name="idebugdocumenttexteventsonremovetext"></a>IDebugDocumentTextEvents::onRemoveText
Indique que le texte a été supprimé à partir du document.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT onRemoveText(  
   ULONG  cCharacterPosition,  
   ULONG  cNumToRemove  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `cCharacterPosition`  
 [in] La position de caractère du premier caractère supprimé.  
  
 `cNumToRemove`  
 [in] Le nombre de caractères supprimés.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Value|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
 Cette méthode indique que le texte a été supprimé à partir du document.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugDocumentTextEvents Interface](../../winscript/reference/idebugdocumenttextevents-interface.md)   
 [IDebugDocumentTextEvents::onInsertText](../../winscript/reference/idebugdocumenttextevents-oninserttext.md)