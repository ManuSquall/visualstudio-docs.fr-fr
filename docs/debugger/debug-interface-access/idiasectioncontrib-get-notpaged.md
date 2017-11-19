---
title: IDiaSectionContrib::get_notPaged | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaSectionContrib::get_notPaged method
ms.assetid: bb6baa40-fece-4a4c-aba9-f4b41f418f8b
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 25003d786b9467f62756fad164df135112c25f62
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="idiasectioncontribgetnotpaged"></a>IDiaSectionContrib::get_notPaged
Récupère un indicateur qui indique si la section ne peut pas être paginée en dehors de la mémoire.  
  
## <a name="syntax"></a>Syntaxe  
  
```C++  
HRESULT get_notPaged (   
   BOOL* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pRetVal`  
 [out, retval] Retourne `TRUE` si la section ne peut pas être paginée ; sinon, retourne `FALSE`.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`. Retourne `S_FALSE` si cette propriété n’est pas pris en charge. Sinon, retourne un code d'erreur.  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)