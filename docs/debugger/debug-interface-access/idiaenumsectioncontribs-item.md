---
title: IDiaEnumSectionContribs::Item | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSectionContribs::Item method
ms.assetid: 63a28f23-0ca0-44a7-b11b-ca0206d642a0
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d021b5016bd0e0039f2bf175102dc44f04dabaab
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72744294"
---
# <a name="idiaenumsectioncontribsitem"></a>IDiaEnumSectionContribs::Item
Récupère les contributions de section au moyen d’un index.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT Item ( 
   DWORD                index,
   IDiaSectionContrib** section
);
```

#### <a name="parameters"></a>Paramètres
 index

dans Index de l’objet [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md) à récupérer. L’index se trouve dans la plage 0 à `count`-1, où `count` est retourné par la méthode [IDiaEnumSectionContribs :: get_Count](../../debugger/debug-interface-access/idiaenumsectioncontribs-get-count.md) .

 section

à Retourne un objet [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md) représentant la contribution de la section souhaitée.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK` ; Sinon, retourne un code d’erreur.

## <a name="see-also"></a>Voir aussi
- [IDiaEnumSectionContribs::get_Count](../../debugger/debug-interface-access/idiaenumsectioncontribs-get-count.md)
- [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)