---
title: IDiaEnumSymbols::Skip | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSymbols::Skip method
ms.assetid: e601fbc9-b10b-41c7-8180-959e57efabe8
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 65e96f2f03229b12c378a096ecfd7555af1f5cce
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2018
ms.locfileid: "31459020"
---
# <a name="idiaenumsymbolsskip"></a>IDiaEnumSymbols::Skip
Ignore un nombre spécifié de symboles dans une séquence d’énumération.  
  
## <a name="syntax"></a>Syntaxe  
  
```C++  
HRESULT Skip (   
   ULONG celt  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 celt  
 [in] Le nombre de symboles dans la séquence d’énumération à ignorer.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne `S_FALSE` s’il n’y a plus aucun symbole à ignorer.  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)