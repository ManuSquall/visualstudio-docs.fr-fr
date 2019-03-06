---
title: IDiaSession::put_loadAddress | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::put_loadAddress method
ms.assetid: b157b245-1ea0-4b80-8962-d8b278dbc742
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b768b06e0702f7929b402086dcc6e11918f3e683
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56630091"
---
# <a name="idiasessionputloadaddress"></a>IDiaSession::put_loadAddress
Définit l’adresse de chargement du fichier exécutable qui correspond aux symboles dans ce magasin de symboles.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT put_loadAddress ( 
   ULONGLONG NewVal
);
```

#### <a name="parameters"></a>Paramètres
 `NewVal`

[in] Charge l’adresse du fichier exécutable.

## <a name="remarks"></a>Remarques
 Propriétés d’adresse virtuelle (VA) de symbole sont calculées à l’aide de la valeur de cette méthode. Adresses virtuelles ne sont pas calculés, sauf si cette propriété est définie zéro.

> [!NOTE]
>  Vous devez appeler cette méthode lorsque vous recevez le [IDiaSession](../../debugger/debug-interface-access/idiasession.md) de l’objet et avant de commencer à l’aide de l’objet si vous devez utiliser des propriétés virtuelles sur des symboles.

## <a name="see-also"></a>Voir aussi
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)