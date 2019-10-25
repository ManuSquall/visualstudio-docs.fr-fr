---
title: IDiaEnumSourceFiles::Item | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSourceFiles::Item method
ms.assetid: 3c19d7ed-0232-4b0e-9b10-f33ed9e0c93b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 352c9516180c0ee0021fca4e0913f154f3b8d46f
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72744092"
---
# <a name="idiaenumsourcefilesitem"></a>IDiaEnumSourceFiles::Item
Récupère un fichier source au moyen d’un index.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT Item ( 
   DWORD            index,
   IDiaSourceFile** sourceFile
);
```

#### <a name="parameters"></a>Paramètres
 index

dans Index de l’objet [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md) à récupérer. L’index se trouve dans la plage 0 à `count`-1, où `count` est retourné par la méthode [IDiaEnumSourceFiles :: get_Count](../../debugger/debug-interface-access/idiaenumsourcefiles-get-count.md) .

 sourceFile

à Retourne un objet [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md) représentant le fichier source souhaité.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK` ; Sinon, retourne un code d’erreur.

## <a name="see-also"></a>Voir aussi
- [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md)
- [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)