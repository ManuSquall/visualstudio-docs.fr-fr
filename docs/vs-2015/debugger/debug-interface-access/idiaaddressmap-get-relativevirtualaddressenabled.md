---
title: IDiaAddressMap::get_relativeVirtualAddressEnabled | Microsoft Docs
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
- IDiaAddressMap::get_relativeVirtualAddressEnabled method
ms.assetid: 4c48af81-7148-4d9a-818e-dbe62cbfc638
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d64f41285c0114d78df4035d11a6d92c714717bd
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47507543"
---
# <a name="idiaaddressmapgetrelativevirtualaddressenabled"></a>IDiaAddressMap::get_relativeVirtualAddressEnabled
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [IDiaAddressMap::get_relativeVirtualAddressEnabled](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled).  
  
Indique si le calcul et l’utilisation d’adresses virtuelles relatives (RVA) est activé.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT get_relativeVirtualAddressEnabled (   
   BOOL* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 pRetVal  
 [out] Retourne `TRUE` si le calcul de RVA est activé.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 RVA est activées si les segments ont été initialement chargées à partir d’un fichier PDB. L’utilisation de RVA peut être temporairement désactivée en appelant le [IDiaAddressMap::put_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-relativevirtualaddressenabled.md) (méthode).  
  
 En outre, les nouveaux en-têtes de l’image peuvent être établies en appelant le [IDiaAddressMap::set_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md) méthode suivie par un appel à la `put_relativeVirtualAddressEnabled` méthode pour permettre l’utilisation des adresses virtuelles relatives à l’aide de nouveaux en-têtes de l’image.  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [IDiaAddressMap::set_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md)   
 [IDiaAddressMap::put_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-relativevirtualaddressenabled.md)



