---
title: IDebugDocumentTextEvents::onInsertText | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugDocumentTextEvents.onInsertText
apilocation: scrobj.dll
helpviewer_keywords: IDebugDocumentTextEvents::onInsertText
ms.assetid: 775881de-497a-47a9-86ab-823d77745a72
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a00adb996711dc6364edd44babf0c3cde1595947
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="idebugdocumenttexteventsoninserttext"></a>IDebugDocumentTextEvents::onInsertText
Indique que le nouveau texte a été ajouté au document.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT onInsertText(  
   ULONG  cCharacterPosition,  
   ULONG  cNumToInsert  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `cCharacterPosition`  
 [in] Position du caractère où le nouveau texte a été inséré.  
  
 `cNumToInsert`  
 [in] Le nombre de caractères qui ont été insérés.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Remarques  
 Cette méthode est généralement appelée par un hôte qui charge progressivement le contenu, comme un navigateur Web.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugDocumentTextEvents (Interface)](../../winscript/reference/idebugdocumenttextevents-interface.md)   
 [IDebugDocumentTextEvents::onRemoveText](../../winscript/reference/idebugdocumenttextevents-onremovetext.md)