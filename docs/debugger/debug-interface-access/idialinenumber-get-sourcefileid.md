---
title: IDiaLineNumber::get_sourceFileId | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaLineNumber::get_sourceFileId method
ms.assetid: 4f482a1e-e85f-4173-98de-8e5f7622554b
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 26ad1cb7faeca9ef2aeadf15389c79815e23e893
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="idialinenumbergetsourcefileid"></a>IDiaLineNumber::get_sourceFileId
Récupère un identificateur de fichier source unique pour le fichier source qui a contribué à cette ligne.  
  
## <a name="syntax"></a>Syntaxe  
  
```C++  
HRESULT get_sourceFileId (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pRetVal`  
 [out] Retourne l’identificateur de fichier source unique pour le fichier source qui a contribué à cette ligne.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`. Retourne `S_FALSE` si cette propriété n’est pas pris en charge. Sinon, retourne un code d'erreur.  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)