---
title: IDiaStackFrame::get_rawLVarInstanceValue | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackFrame::get_rawLVarInstanceValue method
ms.assetid: ce526259-85a6-475b-9274-0b3a21d95db2
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 69e6fc35d9ac5dcc57ffe136d88069003635fe8c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
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
 [in] Nombre maximal d’octets dans la mémoire tampon pointée par `pbData`. Cela peut être un maximum de 8 octets (`sizeof(ULONGLONG)`).  
  
 `pcbData`  
 [out] Retourne le nombre réel d’octets stockés dans la mémoire tampon.  
  
 `pbData`  
 [out] Une mémoire tampon doit être remplie avec les données. Cela ne peut pas être `NULL`.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)