---
title: 'IDebugDocumentText :: GetLineOfPosition | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentText.GetLineOfPosition
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentText::GetLineOfPosition
ms.assetid: fe8d4802-ea16-49ca-8973-89dcaf6c915b
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e8ce32e46c42ee864a88e169a79539efb8b05633
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572115"
---
# <a name="idebugdocumenttextgetlineofposition"></a>IDebugDocumentText::GetLineOfPosition
Retourne le numéro de ligne et, éventuellement, l’offset de caractère dans la ligne qui correspond à la position de caractère donnée.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetLineOfPosition(  
   ULONG   cCharacterPosition,  
   ULONG*  pcLineNumber,  
   ULONG*  pcCharacterOffsetInLine  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `cCharacterPosition`  
 dans Emplacement de début de la plage de la position du caractère.  
  
 `pcLineNumber`  
 à Numéro de ligne de la plage.  
  
 `pcCharacterOffsetInLine`  
 [in, out] Offset de caractère de la plage dans la ligne `pcLineNumber`. Si ce paramètre est `NULL`, la méthode ne retourne pas de valeur.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
 Cette méthode retourne le numéro de ligne et, éventuellement, l’offset de caractère dans la ligne qui correspond à la position de caractère donnée.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IDebugDocumentText](../../winscript/reference/idebugdocumenttext-interface.md)