---
title: IDiaImageData::get_virtualAddress | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaImageData::get_virtualAddress method
ms.assetid: 67ecdc8c-d342-4d0b-b02a-c6b88e22fd02
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e9e369b78d5eda7f7d807dde5ff1174d23c545a4
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47508452"
---
# <a name="idiaimagedatagetvirtualaddress"></a>IDiaImageData::get_virtualAddress
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [IDiaImageData::get_virtualAddress](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idiaimagedata-get-virtualaddress).  
  
Récupère l’emplacement dans la mémoire virtuelle de l’image.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT get_virtualAddress (   
   ULONGLONG* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pRetVal`  
 [out] Retourne l’adresse virtuelle de l’image.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaImageData](../../debugger/debug-interface-access/idiaimagedata.md)



