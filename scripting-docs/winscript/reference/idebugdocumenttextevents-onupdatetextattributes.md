---
title: IDebugDocumentTextEvents::onUpdateTextAttributes | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentTextEvents.onUpdateTextAttributes
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugDocumentTextEvents::onUpdateTextAttributes
ms.assetid: 24a6d409-3137-4a7a-ac24-0955c109902f
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 746339cb281d4d039759f350bb5516456ce142cf
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62989796"
---
# <a name="idebugdocumenttexteventsonupdatetextattributes"></a>IDebugDocumentTextEvents::onUpdateTextAttributes
Indique que les attributs de texte associés à la plage de position de caractère sous-jacente ont changé.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT onUpdateTextAttributes(  
   ULONG  cCharacterPosition,  
   ULONG  cNumToUpdate  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `cCharacterPosition`  
 [in] La position de caractère du premier caractère qui les attributs ont été modifiés.  
  
 `cNumToUpdate`  
 [in] Le nombre de caractères dans la plage.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Value|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
 Cette méthode indique que les attributs de texte associés à la plage de position de caractère sous-jacente ont changé.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IDebugDocumentTextEvents](../../winscript/reference/idebugdocumenttextevents-interface.md)