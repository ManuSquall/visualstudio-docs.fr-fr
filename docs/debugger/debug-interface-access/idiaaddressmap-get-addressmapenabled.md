---
title: IDiaAddressMap::get_addressMapEnabled | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap::get_addressMapEnabled method
ms.assetid: 6183dc5e-befa-4e5a-ae5a-f4aa24f3ed9e
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: cacee6377eebcc4e73f8f650bff4f4d3e500af66
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2018
ms.locfileid: "31458750"
---
# <a name="idiaaddressmapgetaddressmapenabled"></a>IDiaAddressMap::get_addressMapEnabled
Indique si une table d’adresses a été établie pour une session particulière.  
  
## <a name="syntax"></a>Syntaxe  
  
```C++  
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
 Post-processeurs exécutables parfois mettre à jour que le fichier exécutable. DIA contient un mécanisme pour prendre en charge la traduction de symboles pour la nouvelle disposition.  
  
 Les applications clientes peuvent définir le mappage d’adresse pour une session particulière en obtenant la [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md) de l’interface à partir de la [IDiaSession](../../debugger/debug-interface-access/idiasession.md) interface et en appelant le [IDiaAddressMap::set_ addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md) méthode suivie par un appel à la [IDiaAddressMap::put_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md) (méthode). Le `get_addressMapEnabled` méthode retourne les résultats de l’appel de la `put_addressMapEnabled` (méthode).  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaAddressMap::set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)   
 [IDiaAddressMap::put_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md)