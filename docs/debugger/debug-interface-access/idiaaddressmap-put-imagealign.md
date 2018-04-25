---
title: IDiaAddressMap::put_imageAlign | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap::put_imageAlign method
ms.assetid: f9ce875d-c263-43e5-a534-f34c37f9866f
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e1c87592dc04c244e394f1df06cfa46d77f595a1
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2018
---
# <a name="idiaaddressmapputimagealign"></a>IDiaAddressMap::put_imageAlign
Définit l’alignement d’image.  
  
## <a name="syntax"></a>Syntaxe  
  
```C++  
HRESULT put_imageAlign (   
   DWORD NewVal  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 NewVal  
 [in] La nouvelle valeur d’alignement image pour le fichier exécutable.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 Images (fichiers exécutables chargés) sont alignés sur des limites de mémoire spécifié. Cet alignement peut être affecté par l’architecture du système actuel et options de temps de compilation et de liaison. Alignement de l’image est toujours sur les limites d’octets. Les valeurs d’alignement image suivantes sont valides : les limites de 1, 2, 4, 8, 16, 32 et 64 octets.  
  
 L’alignement d’image actuelle peut être récupérée par un appel à la [IDiaAddressMap::get_imageAlign](../../debugger/debug-interface-access/idiaaddressmap-get-imagealign.md) (méthode).  
  
> [!NOTE]
>  L’image est déjà chargée au moment où que cette méthode peut être appelée. Le `put_imageAlign` méthode est généralement utilisée lorsque l’image a été déplacée ou modifiée et un nouvel alignement est nécessaire.  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [IDiaAddressMap::get_imageAlign](../../debugger/debug-interface-access/idiaaddressmap-get-imagealign.md)