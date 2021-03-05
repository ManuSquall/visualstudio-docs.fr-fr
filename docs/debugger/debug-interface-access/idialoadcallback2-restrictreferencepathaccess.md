---
description: Détermine si la recherche d’un fichier. pdb est autorisée dans le chemin d’accès où se trouve le fichier. exe.
title: IDiaLoadCallback2::RestrictReferencePathAccess | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaLoadCallback2::RestrictReferencePathAccess method
ms.assetid: e20cb45c-0360-4ff0-a92c-b1b6f76d6e85
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d0801cd36af23e3a4e3ff911494e00f9bd232a4a
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102157398"
---
# <a name="idialoadcallback2restrictreferencepathaccess"></a>IDiaLoadCallback2::RestrictReferencePathAccess
Détermine si la recherche d’un fichier. pdb est autorisée dans le chemin d’accès où se trouve le fichier. exe.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT RestrictReferencePathAccess();
```

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
 Tout code de retour autre que `S_OK` pour empêcher la recherche d’un fichier. pdb dans le chemin d’accès où se trouve le fichier. exe.

## <a name="see-also"></a>Voir aussi
- [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)
