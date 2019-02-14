---
title: IDiaAddressMap::set_imageHeaders | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap::set_imageHeaders method
ms.assetid: a46b9d0e-43e6-433f-b2c7-aa203981e4e4
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e2435d009197c77945476fbc173b1b74e33a9be9
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54943641"
---
# <a name="idiaaddressmapsetimageheaders"></a>IDiaAddressMap::set_imageHeaders
Jeux en-têtes pour activer la traduction d’adresse virtuelle relative de l’image.  
  
## <a name="syntax"></a>Syntaxe  
  
```C++  
HRESULT set_imageHeaders (   
   DWORD cbData,  
   BYTE  data[],  
   BOOL  originalHeaders  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 cbData  
 [in] Nombre d’octets de données d’en-tête. Doit être `n*sizeof(IMAGE_SECTION_HEADER)` où `n` est le nombre d’en-têtes de section dans le fichier exécutable.  
  
 data[]  
 [in] Un tableau de `IMAGE_SECTION_HEADER` structures à utiliser comme en-têtes de l’image.  
  
 originalHeaders  
 [in] La valeur `FALSE` si les en-têtes de l’image sont à partir de la nouvelle image, `TRUE` si elles reflètent l’image d’origine avant une mise à niveau. En règle générale, cela aurait la valeur `TRUE` uniquement en association avec les appels à la [IDiaAddressMap::set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md) (méthode).  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Remarques  
 Le `IMAGE_SECTION_HEADER` structure est déclarée dans Winnt.h et représente le format d’en-tête de section de l’exécutable.  
  
 Calculs de l’adresse virtuelle relative varient selon le `IMAGE_SECTION_HEADER` valeurs. En règle générale, le DIA récupère ces à partir du fichier de base de données (.pdb) de programme. Si ces valeurs sont manquantes, le DIA est impossible de calculer les adresses virtuelles relatives et [IDiaAddressMap::get_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md) retourne de la méthode `FALSE`. Le client doit appeler ensuite la [IDiaAddressMap::put_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-relativevirtualaddressenabled.md) méthode pour activer les calculs d’adresse virtuelle relative après avoir entré les en-têtes d’image manquant à partir de l’image elle-même.  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [IDiaAddressMap::set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)   
 [IDiaAddressMap::get_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md)   
 [IDiaAddressMap::put_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-relativevirtualaddressenabled.md)