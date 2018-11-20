---
title: IDiaAddressMap::put_addressMapEnabled | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
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
- IDiaAddressMap::put_addressMapEnabled method
ms.assetid: 0f205337-4e59-4383-8059-7b1d207d6dcd
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6fccb88ae66e3db24144d5903ffbf8d9f58ef207
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51726573"
---
# <a name="idiaaddressmapputaddressmapenabled"></a>IDiaAddressMap::put_addressMapEnabled
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Spécifie si le mappage d’adresses doit être utilisé pour traduire les adresses de symbole.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT put_addressMapEnabled (   
   BOOL NewVal  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 NewVal  
 [in] La valeur `TRUE` pour activer la traduction de symboles, ou `FALSE` à désactiver.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 Exécutables post-processeurs parfois mettre à jour que le fichier exécutable. DIA contient un mécanisme pour prendre en charge la traduction de symboles de la nouvelle disposition.  
  
 Quand un fichier PDB est chargé, le mappage de l’adresse stocké dans le fichier est activé. Il existe, toutefois, une application cliente peut devez parfois fournir son propre mappage d’adresses en appelant le [IDiaAddressMap::set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md) (méthode). Si le `set_addressMap` méthode est réussie, l’application cliente doit appeler le `put_addressMapEnabled` méthode avec un `NewVal` paramètre de `TRUE` pour activer l’utilisation de ce mappage d’adresses.  
  
 L’état actuel de la carte d’adresse en cours d’activation peut être récupéré avec un appel à la [IDiaAddressMap::get_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-addressmapenabled.md) (méthode).  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [IDiaAddressMap::set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)   
 [IDiaAddressMap::get_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-addressmapenabled.md)



