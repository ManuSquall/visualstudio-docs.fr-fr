---
title: Init | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c55ddec8-9101-4673-979b-4109caca9146
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0b2ed132e072d9ca8a0b9c98bfc5be6e25931805
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72735003"
---
# <a name="init"></a>Init
Prépare le composant dans l’application de Graphics Diagnostics pour capturer et enregistrer activement les informations graphiques dans un fichier journal de graphisme.

## <a name="syntax"></a>Syntaxe

```C++
void Init(
  std::function<void (int len, wchar_t * pszBuffer)> vsgLogGetter
);
```

#### <a name="parameters"></a>Paramètres
 `vsgLogGetter` une entité pouvant être appelée, telle qu’une fonction, un pointeur de fonction, une expression lambda ou un objet de fonction, qui prend comme paramètres la longueur d’une mémoire tampon composée de `wchar_t` et un pointeur vers cette mémoire tampon, et retourne `void`. Lorsqu’elle est appelée, l’entité pouvant être appelée détermine le nom du fichier qui sera utilisé pour enregistrer les informations graphiques et l’écrit dans la mémoire tampon spécifiée avant de retourner.

## <a name="remarks"></a>Notes
 La fonction `Init` est appelée automatiquement lorsqu’une instance de la classe `VsgDbg` est construite en spécifiant le paramètre `bDefaultInit` de son constructeur en tant que `true` ; dans le cas contraire, `Init` doit être appelé explicitement pour que vous puissiez capturer et enregistrer activement les informations graphiques.

 Vous pouvez finaliser et fermer le fichier journal de graphisme actif en appelant `UnInit`, puis capturer et enregistrer des informations graphiques supplémentaires dans un nouveau fichier journal de graphisme en appelant à nouveau `Init`. Vous pouvez répéter cette opération autant de fois que vous le souhaitez pour créer plusieurs fichiers journaux graphiques indépendants à l’aide de la même instance de `VsgDbg`.

## <a name="see-also"></a>Voir aussi
- [UnInit](init.md)