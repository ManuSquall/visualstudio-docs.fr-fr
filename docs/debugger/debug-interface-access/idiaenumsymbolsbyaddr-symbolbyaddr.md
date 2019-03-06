---
title: IDiaEnumSymbolsByAddr::symbolByAddr | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSymbolsByAddr::symbolByAddr method
ms.assetid: 0b6f5a68-8402-4f29-8219-20576fda8166
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8620dcf7367914e25411fad7ac54a34a5bac54c2
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56598804"
---
# <a name="idiaenumsymbolsbyaddrsymbolbyaddr"></a>IDiaEnumSymbolsByAddr::symbolByAddr
Positionne l’énumérateur en effectuant une recherche par numéro de section d’image et le décalage.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT symbolByAddr ( 
   DWORD**      isect,
   DWORD**      offsect,
   IDiaSymbol** ppsymbol
);
```

#### <a name="parameters"></a>Paramètres
 isect

[in] Numéro de section d’image.

 offsect

[in] Décalage dans la section.

 ppsymbol

[out] Retourne un [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) objet qui représente le symbole trouvé.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK`. Retourne `S_FALSE` si le symbole est introuvable. Sinon, retourne un code d'erreur.

## <a name="see-also"></a>Voir aussi
- [IDiaEnumSymbolsByAddr](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)