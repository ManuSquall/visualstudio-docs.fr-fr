---
title: IDebugDocumentTextEvents::onUpdateTextAttributes | Documents Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 1ea7caa1c1632e1a85e12010ec39593b8e0a6d63
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24727349"
---
# <a name="idebugdocumenttexteventsonupdatetextattributes"></a>IDebugDocumentTextEvents::onUpdateTextAttributes
Indique que les attributs de texte associés à la plage de position de caractère sous-jacente ont changé.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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
  
|Valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Remarques  
 Cette méthode indique que les attributs de texte associés à la plage de position de caractère sous-jacente ont changé.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IDebugDocumentTextEvents](../../winscript/reference/idebugdocumenttextevents-interface.md)