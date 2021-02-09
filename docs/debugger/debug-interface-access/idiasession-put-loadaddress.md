---
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
ms.openlocfilehash: 3642c17f342f824ea920fcf4adf0e11f5ef93215
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99855031"
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

## <a name="remarks"></a>Remarques
 Les propriétés d’adresse virtuelle de symbole (VA) sont calculées à l’aide de la valeur de cette méthode. Les adresses virtuelles ne sont pas calculées, sauf si cette propriété est définie sur une valeur différente de zéro.

> [!NOTE]
> Vous devez appeler cette méthode lorsque vous récupérez l’objet [IDiaSession](../../debugger/debug-interface-access/idiasession.md) et avant de commencer à utiliser l’objet si vous devez utiliser des propriétés virtuelles sur les symboles.

## <a name="see-also"></a>Voir aussi
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)