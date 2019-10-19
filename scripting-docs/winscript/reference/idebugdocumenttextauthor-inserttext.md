---
title: 'IDebugDocumentTextAuthor :: InsertText | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentTextAuthor.InsertText
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugDocumentTextAuthor::InsertText
ms.assetid: ef4e6a5b-8efa-4290-b498-c0f8a6aac09b
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ad927f417c44b471a3fcee96695a1109d33ed17e
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572066"
---
# <a name="idebugdocumenttextauthorinserttext"></a>IDebugDocumentTextAuthor::InsertText
Insère un nouveau texte dans le document.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT InsertText(  
   ULONG    cCharacterPosition,  
   ULONG    cNumToInsert,  
   OLECHAR  pcharText[]  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `cCharacterPosition`  
 dans Emplacement où insérer du texte.  
  
 `cNumToInsert`  
 dans Nombre de caractères à insérer.  
  
 `pcharText[]`  
 dans Mémoire tampon qui contient les caractères à insérer.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
 Cette méthode insère un nouveau texte dans le document.  
  
## <a name="see-also"></a>Voir aussi  
 @No__t_1 de l' [interface IDebugDocumentTextAuthor](../../winscript/reference/idebugdocumenttextauthor-interface.md)  
 [IDebugDocumentTextAuthor::RemoveText](../../winscript/reference/idebugdocumenttextauthor-removetext.md)