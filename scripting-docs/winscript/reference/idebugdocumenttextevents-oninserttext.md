---
title: 'IDebugDocumentTextEvents :: onInsertText | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentTextEvents.onInsertText
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugDocumentTextEvents::onInsertText
ms.assetid: 775881de-497a-47a9-86ab-823d77745a72
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c926caf8ff99cf183e41b2caf825aa828fb60de4
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572909"
---
# <a name="idebugdocumenttexteventsoninserttext"></a>IDebugDocumentTextEvents::onInsertText
Indique que le nouveau texte a été ajouté au document.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT onInsertText(  
   ULONG  cCharacterPosition,  
   ULONG  cNumToInsert  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `cCharacterPosition`  
 dans Position du caractère où le nouveau texte a été inséré.  
  
 `cNumToInsert`  
 dans Nombre de caractères insérés.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
 Cette méthode est généralement appelée par un hôte qui charge progressivement du contenu, tel qu’un navigateur Web.  
  
## <a name="see-also"></a>Voir aussi  
 @No__t_1 de l' [interface IDebugDocumentTextEvents](../../winscript/reference/idebugdocumenttextevents-interface.md)  
 [IDebugDocumentTextEvents::onRemoveText](../../winscript/reference/idebugdocumenttextevents-onremovetext.md)