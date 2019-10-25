---
title: UnInit | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 4cd4fc0b-974a-4e61-9ea8-0aaa1a0c52ea
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ef809b646a0af58e46b8c68dc5a8cf7633692bcc
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72734820"
---
# <a name="uninit"></a>UnInit
Finalise le fichier journal de graphisme, le ferme et libère les ressources qui ont été utilisées pendant que l’application enregistrait activement des informations graphiques.

## <a name="syntax"></a>Syntaxe

```C++
void UnInit();
```

## <a name="remarks"></a>Notes
 `UnInit` est appelé automatiquement lorsqu’une instance de la classe `VsgDbg` est détruite. Si l’instance `VsgDbg` n’enregistrait pas activement les informations graphiques, cela n’a aucun effet.

 Une fois `UnInit` appelée sur une instance de la classe `VsgDbg`, un nouveau fichier journal de graphisme peut être créé en appelant `Init` et finalisé en appelant `UnInit`. Vous pouvez répéter cette opération autant de fois que vous le souhaitez à l’aide de la même instance de `VsgDbg` pour créer plusieurs fichiers journaux graphiques indépendants.

## <a name="see-also"></a>Voir aussi
- [Init](init.md)