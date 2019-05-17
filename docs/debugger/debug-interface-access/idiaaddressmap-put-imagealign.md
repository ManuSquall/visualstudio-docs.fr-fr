---
title: IDiaAddressMap::put_imageAlign | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap::put_imageAlign method
ms.assetid: f9ce875d-c263-43e5-a534-f34c37f9866f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4e07bdd71300ed485862a4a95f1f9cbc06b32772
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63402647"
---
# <a name="idiaaddressmapputimagealign"></a>IDiaAddressMap::put_imageAlign
Définit l’alignement de l’image.

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
 Images (fichiers exécutables chargés) sont alignés sur des limites de mémoire spécifié. Cet alignement peut être affecté par l’architecture du système actuel et par les options de temps de compilation et de liaison. Alignement de l’image est toujours sur les limites d’octets. Les valeurs d’alignement image suivantes sont valides : limites de 1, 2, 4, 8, 16, 32 et 64 octets.

 L’alignement de l’image actuelle peut être récupéré avec un appel à la [IDiaAddressMap::get_imageAlign](../../debugger/debug-interface-access/idiaaddressmap-get-imagealign.md) (méthode).

> [!NOTE]
> L’image est déjà chargée au moment où que cette méthode peut être appelée. Le `put_imageAlign` méthode est généralement utilisée lorsque l’image a été déplacé ou modifié et un nouvel alignement est nécessaire.

## <a name="see-also"></a>Voir aussi
- [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)
- [IDiaAddressMap::get_imageAlign](../../debugger/debug-interface-access/idiaaddressmap-get-imagealign.md)