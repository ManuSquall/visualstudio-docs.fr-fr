---
title: 'IDebugDocumentText :: GetPositionOfContext | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentText.GetPositionOfContext
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentText::GetPositionOfContext
ms.assetid: 90fec730-c3fb-45fb-92ef-05ecc90dca38
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: da759eb98a6cdd28066ddaa8aafe785ede337a6e
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572133"
---
# <a name="idebugdocumenttextgetpositionofcontext"></a>IDebugDocumentText::GetPositionOfContext
Retourne la plage de position de caractère correspondant à un contexte de document.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetPositionOfContext(  
   IDebugDocumentContext*  psc,  
   ULONG*                  pcCharacterPosition,  
   ULONG*                  cNumChars  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `psc`  
 dans Objet de contexte de document.  
  
 `pcCharacterPosition`  
 à Emplacement de début de la plage de la position du caractère.  
  
 `cNumChars`  
 à Nombre de caractères dans la plage.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
 Le contexte de document fourni à cette méthode doit être associé à ce document.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IDebugDocumentText](../../winscript/reference/idebugdocumenttext-interface.md)