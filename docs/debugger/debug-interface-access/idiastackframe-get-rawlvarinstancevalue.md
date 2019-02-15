---
title: IDiaStackFrame::get_rawLVarInstanceValue | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackFrame::get_rawLVarInstanceValue method
ms.assetid: ce526259-85a6-475b-9274-0b3a21d95db2
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 96851912abb6593ce1fe72bd3eebdd67c120c26b
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54992787"
---
# <a name="idiastackframegetrawlvarinstancevalue"></a>IDiaStackFrame::get_rawLVarInstanceValue
Cette méthode récupère la valeur de la variable locale spécifiée comme octets bruts.  
  
## <a name="syntax"></a>Syntaxe  
  
```C++  
HRESULT get_rawLVarInstanceValue(  
   IDiaLVarInstance* pInstance,  
   DWORD             cbDataMax,  
   DWORD*            pcbData,  
   BYTE*             pbData  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pInstance`  
 [in] Un `IDiaLVarInstance` objet représentant une instance d’une variable locale pour obtenir la valeur de.  
  
 `cbDataMax`  
 [in] Nombre maximal d’octets dans la mémoire tampon vers laquelle pointe `pbData`. Cela peut être un maximum de 8 octets (`sizeof(ULONGLONG)`).  
  
 `pcbData`  
 [out] Retourne le nombre réel d’octets stockés dans la mémoire tampon.  
  
 `pbData`  
 [out] Une mémoire tampon à remplir avec des données. Il ne peut pas être `NULL`.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)