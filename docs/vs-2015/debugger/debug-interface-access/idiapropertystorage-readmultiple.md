---
title: IDiaPropertyStorage::ReadMultiple | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage::ReadMultiple
ms.assetid: 6ccc9397-ce41-4f72-b261-72ac252cd4a5
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 40cd84e00f2e6abea285368a6206c7400abf8877
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62538081"
---
# <a name="idiapropertystoragereadmultiple"></a>IDiaPropertyStorage::ReadMultiple
Lit les propriétés de l’ensemble actuel de la propriété spécifiées.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT ReadMultiple( 
   ULONG          cpspec,
   PROPSPEC const rgpspec,
   PROPVARIANT    rgvar
);
```

#### <a name="parameters"></a>Paramètres
 `cpspec`

[in] Nombre de propriétés spécifiées dans le `rgpspec` tableau. Si zéro, la méthode ne retourne aucune propriété mais retourne `S_OK` comme un code de réussite.

 `rgpspec`

[in] Un tableau de propriétés à lire. Propriétés peuvent être spécifiées par un ID de propriété ou d’un nom de chaîne facultative. Il n’est pas nécessaire de spécifier des propriétés dans un ordre particulier dans le tableau. Le tableau peut contenir des propriétés en double, ce qui entraîne des valeurs de propriété en double en retour pour les propriétés simples. Les propriétés non-simple doivent retourner l’accès refusé lors d’une tentative pour les ouvrir une deuxième fois. Le tableau peut contenir un mélange d’ID de propriété et de chaîne. Ce tableau doit avoir au moins `cpspec` nombre de valeurs de propriété.

 `rgvar`

[in, out] Un tableau de `PROPVARIANT` structures (dans l’espace de noms d’assemblys Microsoft.VisualStudio.OLE.Interop) à remplir avec des valeurs pour chaque propriété. Le tableau doit être au moins `cpspec` éléments de taille. L’appelant n’a pas besoin initialiser les valeurs dans le tableau.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK`. Retourne `S_FALSE` si un ou plusieurs des propriétés sont introuvable. Sinon, retourne un code d’erreur.

## <a name="remarks"></a>Notes
 Si une propriété est introuvable, l’entrée correspondante dans le `rgvar` tableau contient un `VARIANT` avec le type de `VT_EMPTY`.

## <a name="see-also"></a>Voir aussi
- [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)