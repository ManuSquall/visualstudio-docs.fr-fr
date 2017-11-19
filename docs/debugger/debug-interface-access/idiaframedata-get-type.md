---
title: IDiaFrameData::get_type | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaFrameData::get_type method
ms.assetid: efca38b5-c479-4d0a-a164-f903f25c5509
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 127b1314b2d56d39595843895dee795c2db6abce
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="idiaframedatagettype"></a>IDiaFrameData::get_type
Récupère le type de frame de spécifiques au compilateur.  
  
## <a name="syntax"></a>Syntaxe  
  
```C++  
HRESULT get_type (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pRetVal`  
 [out] Retourne une valeur de la [stackframetypeenum, énumération](../../debugger/debug-interface-access/stackframetypeenum.md) énumération qui indique le type de frame de spécifiques au compilateur.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`. Retourne `S_FALSE` si cette propriété n’est pas pris en charge. Sinon, retourne un code d'erreur.  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)   
 [StackFrameTypeEnum (énumération)](../../debugger/debug-interface-access/stackframetypeenum.md)