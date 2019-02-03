---
title: IDiaSegment::get_execute | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSegment::get_execute method
ms.assetid: 746cdf8e-9097-415d-ba10-069854153185
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c126ec1c809284bd2f720680b1b51b5f3839670c
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54928995"
---
# <a name="idiasegmentgetexecute"></a>IDiaSegment::get_execute
Récupère un indicateur qui indique si le segment est exécutable.  
  
## <a name="syntax"></a>Syntaxe  
  
```C++  
HRESULT get_execute (   
   BOOL* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pRetVal`  
 [out] Retourne `TRUE` si le segment est marqué comme exécutable ; sinon, retourne `FALSE`.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`. Retourne `S_FALSE` si cette propriété n’est pas pris en charge. Sinon, retourne un code d'erreur.  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)