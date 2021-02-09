---
title: Init | Microsoft Docs
description: Utilisez la méthode Init () de Vsgdbg, pour préparer le composant dans l’application de Graphics Diagnostics pour enregistrer des informations graphiques.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c55ddec8-9101-4673-979b-4109caca9146
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 17b2490641a85a9a38bdeb2c5cd20038639de6f0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99891811"
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
 `vsgLogGetter` Entité pouvant être appelée, telle qu’une fonction, un pointeur de fonction, une expression lambda ou un objet de fonction, qui prend comme paramètres la longueur d’une mémoire tampon composée de `wchar_t` et d’un pointeur vers cette mémoire tampon, et retourne `void` . Lorsqu’elle est appelée, l’entité pouvant être appelée détermine le nom du fichier qui sera utilisé pour enregistrer les informations graphiques et l’écrit dans la mémoire tampon spécifiée avant de retourner.

## <a name="remarks"></a>Remarques
 La `Init` fonction est appelée automatiquement lorsqu’une instance de la `VsgDbg` classe est construite en spécifiant le `bDefaultInit` paramètre de son constructeur comme `true` ; sinon, `Init` doit être appelé explicitement pour que vous puissiez capturer et enregistrer activement les informations graphiques.

 Vous pouvez finaliser et fermer le fichier journal de graphisme actif en appelant `UnInit` , puis capturer et enregistrer des informations graphiques supplémentaires dans un nouveau fichier journal de graphisme en rappelant `Init` . Vous pouvez répéter cette opération autant de fois que vous le souhaitez pour créer plusieurs fichiers journaux graphiques indépendants à l’aide de la même `VsgDbg` instance.

## <a name="see-also"></a>Voir aussi
- [UnInit](init.md)