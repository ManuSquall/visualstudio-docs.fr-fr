---
title: 'IJsDebugDataTarget :: ReadNullTerminatedString, méthode | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugDataTarget.ReadNullTerminatedString
apilocation:
- jscript9diag.dll
ms.assetid: 64683b39-6fc2-40c4-82ae-2a6f58d392d5
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 67d6ee6c8dad81865767b0b944ef311fc0de0063
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572403"
---
# <a name="ijsdebugdatatargetreadnullterminatedstring-method"></a>IJsDebugDataTarget::ReadNullTerminatedString, méthode
Lit le nombre spécifié de caractères à partir de la cible.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT ReadNullTerminatedString(  
   UINT64 address,  
   UINT16 characterSize,  
   UINT32 maxCharacters,  
   BSTR *pString  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `address`  
 dans Adresse à partir de laquelle effectuer la lecture.  
  
 `characterSize`  
 [in] taille de chaque caractère de la chaîne  
  
 `maxCharacters`  
 dans Nombre maximal de caractères à lire. maxCharacters doit être raisonnable. Toute demande de plus de 128 Mo de mémoire échoue.  Si la chaîne est supérieure à maxCharacters, la chaîne de résultat est tronquée après maxCharacters.  
  
 `pString`  
 à BSTR lu à partir de la cible.  
  
## <a name="return-value"></a>Valeur de retour  
  
## <a name="remarks"></a>Notes  
 Retourne S_FALSE s’il est tronqué.  
  
## <a name="requirements"></a>spécifications  
 **En-tête :** jscript9diag. h  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IJsDebugDataTarget](../../winscript/reference/ijsdebugdatatarget-interface.md)