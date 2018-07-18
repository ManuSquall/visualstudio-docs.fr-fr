---
title: IDiaEnumTables::Skip | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumTables::Skip method
ms.assetid: 5c9db956-0654-4f1a-8775-530aa980d8ec
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1ee3835a0c07f903dcbe31d967c1fc3014fefaa0
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2018
ms.locfileid: "31458513"
---
# <a name="idiaenumtablesskip"></a>IDiaEnumTables::Skip
Ignore un nombre spécifié de tables dans une séquence d’énumération.  
  
## <a name="syntax"></a>Syntaxe  
  
```C++  
HRESULT Skip (   
   ULONG celt  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `celt`  
 [in] Le nombre de tables dans la séquence d’énumération à ignorer.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne `S_FALSE` si aucune table plus à ignorer.  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md)