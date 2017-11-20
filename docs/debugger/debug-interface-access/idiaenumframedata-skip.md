---
title: IDiaEnumFrameData::Skip | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaEnumFrameData::Skip method
ms.assetid: 67140b4c-7125-4895-932d-42412326da29
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3284b550d2c55780fa4cc840645113d5c48df09f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="idiaenumframedataskip"></a>IDiaEnumFrameData::Skip
Ignore un nombre spécifié d’éléments de données d’image dans une séquence d’énumération.  
  
## <a name="syntax"></a>Syntaxe  
  
```C++  
HRESULT Skip (   
   ULONG celt  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 celt  
 [in] Le nombre d’éléments de données d’image dans la séquence d’énumération à ignorer.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne `S_FALSE` s’il n’y aucun plus d’enregistrements à ignorer.  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)