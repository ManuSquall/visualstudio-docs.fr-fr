---
title: IDiaSourceFile::get_checksum | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSourceFile::get_checksum method
ms.assetid: aad63a7e-4e22-44e4-8a5b-81b5174ced1e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1ff6b04322bca213d5eeddfbc0f7ea4b01bb9226
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/27/2020
ms.locfileid: "85465306"
---
# <a name="idiasourcefileget_checksum"></a>IDiaSourceFile::get_checksum
Récupère les octets de somme de contrôle.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_checksum ( 
   DWORD  cbData,
   DWORD* pcbData,
   BYTE   data[]
);
```

#### <a name="parameters"></a>Paramètres
 `cbData`

dans Taille de la mémoire tampon de données, en octets.

 `pcbData`

à Retourne le nombre d’octets de somme de contrôle. Ce paramètre ne peut pas être `NULL`.

 `data`

[in, out] Mémoire tampon remplie avec les octets de somme de contrôle. Si ce paramètre a `NULL` la valeur, `pcbData` retourne le nombre d’octets requis.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="remarks"></a>Remarques
 Pour déterminer le type d’algorithme de somme de contrôle utilisé pour générer les octets de somme de contrôle, appelez la méthode [IDiaSourceFile :: get_checksumType](../../debugger/debug-interface-access/idiasourcefile-get-checksumtype.md) .

 La somme de contrôle est généralement générée à partir de l’image du fichier source, de sorte que les modifications apportées au fichier source sont reflétées dans les modifications de la somme de contrôle en octets. Si les octets de somme de contrôle ne correspondent pas à une somme de contrôle générée à partir de l’image chargée du fichier, le fichier doit être considéré comme endommagé ou falsifié.

 Les sommes de contrôle typiques n’ont jamais plus de 32 octets, mais elles ne supposent pas que représente la taille maximale d’une somme de contrôle. Définissez le `data` paramètre sur `NULL` pour obtenir le nombre d’octets requis pour récupérer la somme de contrôle. Allouez ensuite une mémoire tampon de la taille appropriée et appelez cette méthode une fois de plus avec la nouvelle mémoire tampon.

## <a name="see-also"></a>Voir aussi
- [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)
- [IDiaSourceFile::get_checksumType](../../debugger/debug-interface-access/idiasourcefile-get-checksumtype.md)