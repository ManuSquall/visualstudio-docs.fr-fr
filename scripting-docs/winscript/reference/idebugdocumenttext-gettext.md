---
title: IDebugDocumentText::GetText | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 77cc255bcd04754cbfde4638b67a85f6fdc0a922
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54091986"
---
# <a name="idebugdocumenttextgettext"></a>IDebugDocumentText::GetText
Récupère les caractères et/ou les attributs de caractère associés à une plage de la position de caractère.  
  
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
 [in] Emplacement de la plage de position de caractère de début.  
  
 `pcharText`  
 [in, out] Une mémoire tampon de texte caractères. La mémoire tampon doit être suffisamment grande pour contenir `cMaxChars` caractères. Si ce paramètre est NULL, la méthode ne retourne pas de caractères.  
  
 `pstaTextAttr`  
 [in, out] Une mémoire tampon de caractères attribut. La mémoire tampon doit être suffisamment grande pour contenir `cMaxChars` caractères. Si ce paramètre est NULL, la méthode ne retourne pas les attributs.  
  
 `pcNumChars`  
 [in, out] Le nombre de caractères/attributs renvoyés. Ce paramètre doit être défini à zéro avant d’appeler cette méthode.  
  
 `cMaxChars`  
 [in] Nombre de caractères dans la plage de position de caractère. Spécifie également le nombre maximal de caractères à retourner.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Value|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
 Cette méthode récupère les caractères et/ou les attributs de caractère associés à une plage de la position de caractère. La plage de position de caractère est spécifiée par une position de caractère et un nombre de caractères.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugDocumentText (Interface)](../../winscript/reference/idebugdocumenttext-interface.md)   
 [Énumération SOURCE_TEXT_ATTR](../../winscript/reference/source-text-attr-enumeration.md)