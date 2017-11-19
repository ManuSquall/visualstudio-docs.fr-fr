---
title: IDiaSectionContrib::get_notCached | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaSectionContrib::get_notCached method
ms.assetid: 5408ea53-f64c-431e-9f62-62819026b038
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7ff988df644afd95a7b1596ff35b1579df79e86d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="idiasectioncontribgetnotcached"></a>IDiaSectionContrib::get_notCached
Récupère un indicateur qui indique si la section ne peut pas être mis en cache.  
  
## <a name="syntax"></a>Syntaxe  
  
```C++  
HRESULT get_notCached (   
   BOOL* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pRetVal`  
 [out] Retourne `TRUE` si la section ne peut pas être mis en cache ; sinon, retourne `FALSE`.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`. Retourne `S_FALSE` si cette propriété n’est pas pris en charge. Sinon, retourne un code d'erreur.  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)