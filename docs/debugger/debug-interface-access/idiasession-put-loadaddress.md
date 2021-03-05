---
description: Définit l’adresse de chargement du fichier exécutable qui correspond aux symboles dans ce magasin de symboles.
title: IDiaSession::put_loadAddress | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::put_loadAddress method
ms.assetid: b157b245-1ea0-4b80-8962-d8b278dbc742
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 05dc21a67a88270c4d3bce46387e46ed5a8e8497
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102156999"
---
# <a name="idiasessionput_loadaddress"></a>IDiaSession::put_loadAddress
Définit l’adresse de chargement du fichier exécutable qui correspond aux symboles dans ce magasin de symboles.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT put_loadAddress ( 
   ULONGLONG NewVal
);
```

#### <a name="parameters"></a>Paramètres
 `NewVal`

dans Adresse de chargement du fichier exécutable.

## <a name="remarks"></a>Notes
 Les propriétés d’adresse virtuelle de symbole (VA) sont calculées à l’aide de la valeur de cette méthode. Les adresses virtuelles ne sont pas calculées, sauf si cette propriété est définie sur une valeur différente de zéro.

> [!NOTE]
> Vous devez appeler cette méthode lorsque vous récupérez l’objet [IDiaSession](../../debugger/debug-interface-access/idiasession.md) et avant de commencer à utiliser l’objet si vous devez utiliser des propriétés virtuelles sur les symboles.

## <a name="see-also"></a>Voir aussi
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
