---
title: IDiaAddressMap::put_imageAlign | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap::put_imageAlign method
ms.assetid: f9ce875d-c263-43e5-a534-f34c37f9866f
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5e0fa57c38c8451bde84d96ab32bc7980c5e2d8b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90839597"
---
# <a name="idiaaddressmapput_imagealign"></a>IDiaAddressMap::put_imageAlign
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Définit l’alignement de l’image.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT put_imageAlign (   
   DWORD NewVal  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 NewVal  
 dans Nouvelle valeur d’alignement d’image pour l’exécutable.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.  
  
## <a name="remarks"></a>Remarques  
 Les images (exécutables chargés) sont alignées sur les limites de mémoire spécifiées. Cet alignement peut être affecté par l’architecture système actuelle et par les options de compilation et de liaison temporelle. L’alignement d’image est toujours sur les limites d’octets. Les valeurs d’alignement d’image suivantes sont valides : 1, 2, 4, 8, 16, 32 et 64 limites d’octets.  
  
 L’alignement de l’image actuelle peut être récupéré à l’aide d’un appel à la méthode [IDiaAddressMap :: get_imageAlign](../../debugger/debug-interface-access/idiaaddressmap-get-imagealign.md) .  
  
> [!NOTE]
> L’image est déjà chargée au moment où cette méthode peut être appelée. La `put_imageAlign` méthode est généralement utilisée lorsque l’image a été déplacée ou modifiée et qu’un nouvel alignement est nécessaire.  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [IDiaAddressMap::get_imageAlign](../../debugger/debug-interface-access/idiaaddressmap-get-imagealign.md)
