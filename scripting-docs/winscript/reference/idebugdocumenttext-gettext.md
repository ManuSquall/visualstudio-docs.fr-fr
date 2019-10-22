---
title: 'IDebugDocumentText :: GetText | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentText.GetText
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentText::GetText
ms.assetid: 3c940a30-6c0f-4deb-aa4d-21a0bdef8461
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e6472c40802fff4dad6e5ecc8f2729c95459e09f
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572084"
---
# <a name="idebugdocumenttextgettext"></a>IDebugDocumentText::GetText
Récupère les caractères et/ou les attributs de caractère associés à une plage de position de caractère.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetText(  
   ULONG              cCharacterPosition,  
   WCHAR*             pcharText,  
   SOURCE_TEXT_ATTR*  pstaTextAttr,  
   ULONG*             pcNumChars,  
   ULONG              cMaxChars  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `cCharacterPosition`  
 dans Emplacement de début de la plage de la position du caractère.  
  
 `pcharText`  
 [in, out] Mémoire tampon de texte de caractères. La mémoire tampon doit être suffisamment grande pour contenir `cMaxChars` caractères. Si ce paramètre a la valeur NULL, la méthode ne retourne pas de caractères.  
  
 `pstaTextAttr`  
 [in, out] Mémoire tampon d’attribut de caractère. La mémoire tampon doit être suffisamment grande pour contenir `cMaxChars` caractères. Si ce paramètre a la valeur NULL, la méthode ne retourne pas d’attributs.  
  
 `pcNumChars`  
 [in, out] Nombre de caractères/attributs retournés. Ce paramètre doit avoir la valeur zéro avant d’appeler cette méthode.  
  
 `cMaxChars`  
 dans Nombre de caractères dans la plage de la position du caractère. Spécifie également le nombre maximal de caractères à retourner.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
 Cette méthode récupère les caractères et/ou les attributs de caractère associés à une plage de position de caractère. La plage de la position du caractère est spécifiée par une position de caractère et un nombre de caractères.  
  
## <a name="see-also"></a>Voir aussi  
 @No__t_1 de l' [interface IDebugDocumentText](../../winscript/reference/idebugdocumenttext-interface.md)  
 [Énumération SOURCE_TEXT_ATTR](../../winscript/reference/source-text-attr-enumeration.md)