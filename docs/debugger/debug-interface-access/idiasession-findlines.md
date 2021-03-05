---
description: Récupère les numéros de ligne dans le module de journalisation et les identificateurs de fichier source spécifiés.
title: IDiaSession::findLines | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::findLines method
ms.assetid: d6e84916-fd55-457e-b057-57f97b51fe73
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: a887436555f1ac3d4880c53f1a9103d0fa285df0
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102147715"
---
# <a name="idiasessionfindlines"></a>IDiaSession::findLines
Récupère les numéros de ligne dans le module de journalisation et les identificateurs de fichier source spécifiés.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT findLines ( 
   IDiaSymbol*           compiland,
   IDiaSourceFile*       file,
   IDiaEnumLineNumbers** ppResult
);
```

#### <a name="parameters"></a>Paramètres
 `compiland`

dans Objet [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) représentant le compiland. Utilisez cette interface comme contexte dans lequel rechercher les numéros de ligne.

 `file`

dans Objet [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md) représentant le fichier source dans lequel rechercher les numéros de ligne.

 `ppResult`

à Retourne un objet [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md) qui contient une liste des numéros de ligne récupérés.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="see-also"></a>Voir aussi
- [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
