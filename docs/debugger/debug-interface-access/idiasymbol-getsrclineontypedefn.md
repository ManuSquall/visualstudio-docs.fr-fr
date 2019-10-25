---
title: IDiaSymbol::getSrcLineOnTypeDefn | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: ad554d18-9988-4b64-ad71-e7594c266e94
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9f28dc5e60343cc6aacdf456d5475afbfc7db5e9
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72738783"
---
# <a name="idiasymbolgetsrclineontypedefn"></a>IDiaSymbol::getSrcLineOnTypeDefn
Récupère le fichier source et le numéro de ligne qui indiquent où un type défini par l’utilisateur spécifié est défini.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT getSrcLineOnTypeDefn(
   IDiaLineNumber **ppResult);
```

#### <a name="parameters"></a>Paramètres
 `ppResult`

à Objet `IDiaLineNumber` qui contient le fichier source et le numéro de ligne où l’utilisateur est défini.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK` ; Sinon, retourne `S_FALSE` ou un code d’erreur.

## <a name="see-also"></a>Voir aussi
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)