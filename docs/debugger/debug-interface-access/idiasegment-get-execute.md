---
title: IDiaSegment::get_execute | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSegment::get_execute method
ms.assetid: 746cdf8e-9097-415d-ba10-069854153185
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 7851d379793ee21562b2993c89442a7fb728ec00
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62839392"
---
# <a name="idiasegmentgetexecute"></a>IDiaSegment::get_execute
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Récupère un indicateur qui indique si le segment est exécutable.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
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
