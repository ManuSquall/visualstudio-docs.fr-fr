---
title: 'IDebugDocumentText :: obtient | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentText.GetSize
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentText::GetSize
ms.assetid: 9da53856-613a-44b2-a84c-99454a2a1548
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ef6f75b396dddec80fb2ae89c71f8579ce3c29b9
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572093"
---
# <a name="idebugdocumenttextgetsize"></a>IDebugDocumentText::GetSize
Retourne le nombre de lignes et le nombre de caractères dans le document.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetSize(  
   ULONG*  pcNumLines,  
   ULONG*  pcNumChars  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pcNumLines`  
 à Nombre de lignes dans le document. Si ce paramètre a la valeur NULL, la méthode ne retourne pas de valeur.  
  
 `pcNumChars`  
 à Nombre de caractères dans le document. Si ce paramètre a la valeur NULL, la méthode ne retourne pas de valeur.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
 Cette méthode retourne le nombre de lignes et le nombre de caractères dans le document.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IDebugDocumentText](../../winscript/reference/idebugdocumenttext-interface.md)