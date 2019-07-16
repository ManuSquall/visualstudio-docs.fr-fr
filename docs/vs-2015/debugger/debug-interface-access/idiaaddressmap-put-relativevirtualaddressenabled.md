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
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68198668"
---
# <a name="idiaaddressmapputrelativevirtualaddressenabled"></a>IDiaAddressMap::put_relativeVirtualAddressEnabled
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Permet au client activer ou désactiver le calcul et l’utilisation d’adresses virtuelles relatives (RVA).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT put_relativeVirtualAddressEnabled (   
   BOOL NewVal  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 NewVal  
 [in] La valeur `TRUE` pour activer, ou `FALSE` à désactiver.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 Adresses pour les objets de débogage décrites par les interfaces DIA et par rapport à l’image de l’exécutable base, peuvent être récupérés sous forme d’adresses virtuelles relatives.  
  
 L’utilisation de RVA est activée lorsque les segments sont initialement chargées à partir d’un fichier PDB. Pour obtenir l’état actuel de l’utilisation des adresses virtuelles relatives, appelez le [IDiaAddressMap::get_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md) (méthode).  
  
 Le `put_relativeVirtualAddress` méthode doit être appelée pour activer le RVA après un appel réussi au [IDiaAddressMap::set_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md) méthode a établi des nouveaux en-têtes de l’image.  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [IDiaAddressMap::get_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md)   
 [IDiaAddressMap::set_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md)
