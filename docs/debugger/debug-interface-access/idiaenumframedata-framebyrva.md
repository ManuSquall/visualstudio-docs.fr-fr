---
title: IDiaEnumFrameData::frameByRVA | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumFrameData::frameByRVA method
ms.assetid: 4b8dec05-e76c-4cc4-9644-2369d583849f
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6806532c6d70048c621e8c079ea4ead317eb0707
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49835889"
---
# <a name="idiaenumframedataframebyrva"></a>IDiaEnumFrameData::frameByRVA
Retourne un cadre par adresse virtuelle relative (RVA).  
  
## <a name="syntax"></a>Syntaxe  
  
```C++  
HRESULT frameByRVA(   
   DWORD           relativeVirtualAddress,  
   IDiaFrameData** frame  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 relativeVirtualAddress  
 [in] Adresse RVA du frame d’intérêt.  
  
 frame  
 [out] Retourne un [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md) objet représentant le frame qui contient l’adresse fournie.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`. Retourne `S_FALSE` si aucune donnée de frame correspond à l’adresse spécifiée. Sinon, retourne un code d'erreur.  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)   
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)