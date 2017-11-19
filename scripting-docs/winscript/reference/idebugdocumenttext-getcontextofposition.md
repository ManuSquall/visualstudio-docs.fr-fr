---
title: IDebugDocumentText::GetContextOfPosition | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugDocumentText.GetContextOfPosition
apilocation: pdm.dll
helpviewer_keywords: IDebugDocumentText::GetContextOfPosition
ms.assetid: 86560853-d9b1-499a-a1b5-ea06aa1f1f5c
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f1be8bb6d350a2ca68912622396af52f1625985a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="idebugdocumenttextgetcontextofposition"></a>IDebugDocumentText::GetContextOfPosition
Crée un objet de contexte de document correspondant à la plage de position de caractère fourni.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetContextOfPosition(  
   ULONG                    cCharacterPosition,  
   ULONG                    cNumChars,  
   IDebugDocumentContext**  ppsc  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `cCharacterPosition`  
 [in] Emplacement de la plage de position de caractère de début.  
  
 `cNumChars`  
 [in] Nombre de caractères dans la plage.  
  
 `ppsc`  
 [out] L’objet de contexte de document correspondant à la plage de position de caractère spécifiée.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Remarques  
 Cette méthode crée un objet de contexte de document correspondant à la plage de position de caractère fourni.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IDebugDocumentText](../../winscript/reference/idebugdocumenttext-interface.md)