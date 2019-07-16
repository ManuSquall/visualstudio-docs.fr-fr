---
title: IDiaAddressMap::get_addressMapEnabled | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap::get_addressMapEnabled method
ms.assetid: 6183dc5e-befa-4e5a-ae5a-f4aa24f3ed9e
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 0cf874590d6bcf7f259d7a59eee1b81b79ffe1a4
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68178245"
---
# <a name="idiaaddressmapgetaddressmapenabled"></a>IDiaAddressMap::get_addressMapEnabled
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Indique si un mappage d’adresse a été établi pour une session particulière.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT get_addressMapEnabled (   
   BOOL* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 pRetVal  
 [out] Retourne `TRUE` si le mappage d’adresse est activé.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 Exécutables post-processeurs parfois mettre à jour que le fichier exécutable. DIA contient un mécanisme pour prendre en charge la traduction de symboles de la nouvelle disposition.  
  
 Les applications clientes peuvent définir le mappage d’adresses pour une session particulière en obtenant le [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md) interface à partir de la [IDiaSession](../../debugger/debug-interface-access/idiasession.md) interface et en appelant le [IDiaAddressMap::set_ addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md) méthode suivie par un appel à la [IDiaAddressMap::put_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md) (méthode). Le `get_addressMapEnabled` méthode renvoie les résultats de l’appel le `put_addressMapEnabled` (méthode).  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaAddressMap::set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)   
 [IDiaAddressMap::put_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md)
