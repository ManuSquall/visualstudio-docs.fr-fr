---
title: IDiaStackFrame::get_rawLVarInstanceValue | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackFrame::get_rawLVarInstanceValue method
ms.assetid: ce526259-85a6-475b-9274-0b3a21d95db2
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2aca4ea4468409937cd0b90b7c2201898a9f93a0
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47506454"
---
# <a name="idiastackframegetrawlvarinstancevalue"></a>IDiaStackFrame::get_rawLVarInstanceValue
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [IDiaStackFrame::get_rawLVarInstanceValue](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idiastackframe-get-rawlvarinstancevalue).  
  
Cette méthode récupère la valeur de la variable locale spécifiée comme octets bruts.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
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
 [out] Une mémoire tampon à remplir avec des données. Cela ne peut pas être `NULL`.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)



