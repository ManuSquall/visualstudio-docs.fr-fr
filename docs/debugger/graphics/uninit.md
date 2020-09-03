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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72734820"
---
# <a name="uninit"></a>UnInit
Finalise le fichier journal de graphisme, le ferme et libère les ressources qui ont été utilisées pendant que l’application enregistrait activement des informations graphiques.

## <a name="syntax"></a>Syntaxe

```C++
void UnInit();
```

## <a name="remarks"></a>Notes
 `UnInit` est appelé automatiquement lorsqu’une instance de la `VsgDbg` classe est détruite. Si l' `VsgDbg` instance n’enregistrait pas activement les informations graphiques, cela n’a aucun effet.

 Une fois que `UnInit` a été appelé sur une instance de la `VsgDbg` classe, un nouveau fichier journal de graphisme peut être créé en appelant `Init` et finalisé en appelant `UnInit` . Vous pouvez répéter cette opération autant de fois que vous le souhaitez pour utiliser la même `VsgDbg` instance afin de créer plusieurs fichiers journaux graphiques indépendants.

## <a name="see-also"></a>Voir aussi
- [Init](init.md)