---
title: IDiaEnumFrameData::Item | Microsoft Docs
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
- IDiaEnumFrameData::Item method
ms.assetid: 2761a72d-1868-4f5b-a32e-c2a1d9358c91
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 758a1282918e7e3802c04add14cea6589f8f5fcb
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47505592"
---
# <a name="idiaenumframedataitem"></a>IDiaEnumFrameData::Item
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [IDiaEnumFrameData::Item](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idiaenumframedata-item).  
  
Récupère un élément de données d’image au moyen d’un index.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT Item (   
   DWORD           index,  
   IDiaFrameData** section  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 index  
 [in] Index de la [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md) objet à récupérer. L’index est comprise entre 0 et `count`-1, où `count` est retourné par la [IDiaEnumFrameData::get_Count](../../debugger/debug-interface-access/idiaenumframedata-get-count.md) (méthode).  
  
 section  
 [out] Retourne un [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md) objet représentant l’élément de données d’images souhaitée.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)   
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)



