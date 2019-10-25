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
ms.openlocfilehash: 9cd1e419e1d08120274fc627a672eb52331ca50f
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72742886"
---
# <a name="idiapropertystoragereadmultiple"></a>IDiaPropertyStorage::ReadMultiple
Lit les propriétés spécifiées à partir du jeu de propriétés actuel.

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

dans Nombre de propriétés spécifiées dans le tableau de `rgpspec`. Si la valeur est zéro, la méthode ne retourne aucune propriété, mais retourne `S_OK` en tant que code de réussite.

 `rgpspec`

dans Tableau de propriétés à lire. Les propriétés peuvent être spécifiées à l’aide d’un ID de propriété ou d’un nom de chaîne facultatif. Il n’est pas nécessaire de spécifier des propriétés dans un ordre particulier dans le tableau. Le tableau peut contenir des propriétés dupliquées, ce qui génère des valeurs de propriété en double au retour pour les propriétés simples. Les propriétés non simples doivent retourner l’accès refusé pour une tentative de les ouvrir une deuxième fois. Le tableau peut contenir un mélange d’ID de propriété et d’ID de chaîne. Ce tableau doit avoir au moins `cpspec` nombre de valeurs de propriété.

 `rgvar`

[in, out] Tableau de structures `PROPVARIANT` (dans l’espace de noms Microsoft. VisualStudio. OLE. Interop) à remplir avec des valeurs pour chaque propriété. La taille du tableau doit être au moins `cpspec` éléments. L’appelant n’a pas besoin d’initialiser les valeurs dans le tableau.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK`. Retourne `S_FALSE` si une ou plusieurs des propriétés sont introuvables. Sinon, retourne un code d’erreur.

## <a name="remarks"></a>Notes
 Si une propriété est introuvable, l’entrée correspondante dans le tableau `rgvar` contient une `VARIANT` avec le type de `VT_EMPTY`.

## <a name="see-also"></a>Voir aussi
- [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)