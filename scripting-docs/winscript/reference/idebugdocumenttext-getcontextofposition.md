---
title: 'IDebugDocumentText :: GetContextOfPosition | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentText.GetContextOfPosition
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentText::GetContextOfPosition
ms.assetid: 86560853-d9b1-499a-a1b5-ea06aa1f1f5c
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d6a35a85a6e4761e1bd0db67caafd0913e7e28a3
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572141"
---
# <a name="idebugdocumenttextgetcontextofposition"></a>IDebugDocumentText::GetContextOfPosition
Crée un objet de contexte de document correspondant à la plage de positions de caractères fournie.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetContextOfPosition(  
   ULONG                    cCharacterPosition,  
   ULONG                    cNumChars,  
   IDebugDocumentContext**  ppsc  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `cCharacterPosition`  
 dans Emplacement de début de la plage de la position du caractère.  
  
 `cNumChars`  
 dans Nombre de caractères dans la plage.  
  
 `ppsc`  
 à Objet de contexte de document correspondant à la plage de positions de caractères spécifiée.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
 Cette méthode crée un objet de contexte de document correspondant à la plage de positions de caractères fournie.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IDebugDocumentText](../../winscript/reference/idebugdocumenttext-interface.md)