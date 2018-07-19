---
title: Ijsdebugdatatarget::readnullterminatedstring, méthode | Documents Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 94cb90b8b44aa5dab13a2e916dec22ae950e77ef
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24729499"
---
# <a name="ijsdebugdatatargetreadnullterminatedstring-method"></a>IJsDebugDataTarget::ReadNullTerminatedString, méthode
Lit le nombre spécifié de caractères à partir de la cible.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT ReadNullTerminatedString(  
   UINT64 address,  
   UINT16 characterSize,  
   UINT32 maxCharacters,  
   BSTR *pString  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `address`  
 [in] L’adresse à lire.  
  
 `characterSize`  
 [in] taille de chaque caractère dans la chaîne  
  
 `maxCharacters`  
 [in] Le nombre maximal de caractères à lire. maxCharacters doit être raisonnable. Toute demande de plus de 128 Mo de mémoire échoue.  Si la chaîne est supérieure à maxCharacters, la chaîne de résultat sera tronquée après maxCharacters.  
  
 `pString`  
 [out] Le BSTR lire à partir de la cible.  
  
## <a name="return-value"></a>Valeur de retour  
  
## <a name="remarks"></a>Remarques  
 Retourne S_FALSE si tronquée.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** jscript9diag.h  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IJsDebugDataTarget](../../winscript/reference/ijsdebugdatatarget-interface.md)