---
title: IDiaAddressMap::put_relativeVirtualAddressEnabled | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap::put_relativeVirtualAddressEnabled method
ms.assetid: 767c078e-8ad7-4940-9e00-cae7704aadee
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 14c9924346471e098d9ba9f1abb52fda0d3c9969
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68198668"
---
# <a name="idiaaddressmapput_relativevirtualaddressenabled"></a>IDiaAddressMap::put_relativeVirtualAddressEnabled
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Permet au client d’activer ou de désactiver le calcul et l’utilisation des adresses virtuelles relatives (RVA).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT put_relativeVirtualAddressEnabled (   
   BOOL NewVal  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 NewVal  
 dans Affectez la valeur `TRUE` pour activer ou `FALSE` Désactiver.  
  
## <a name="return-value"></a>Valeur renvoyée  
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.  
  
## <a name="remarks"></a>Notes  
 Les adresses des objets de débogage décrits par les interfaces DIA et relatives à la base d’image de l’exécutable peuvent être récupérées en tant qu’adresses virtuelles relatives.  
  
 L’utilisation des adresses RVA est activée lorsque les segments sont initialement chargés à partir d’un fichier PDB. Pour connaître l’état actuel de l’utilisation des adresses RVA, appelez la méthode [IDiaAddressMap :: get_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md) .  
  
 La `put_relativeVirtualAddress` méthode doit être appelée pour activer les adresses RVA après un appel réussi à la méthode [IDiaAddressMap :: set_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md) a établi de nouveaux en-têtes d’image.  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [IDiaAddressMap :: get_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md)   
 [IDiaAddressMap::set_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md)
