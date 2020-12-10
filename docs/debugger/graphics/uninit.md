---
title: UnInit | Microsoft Docs
description: Utilisez la méthode Uninit () de Vsgdbg, pour finaliser et fermer le fichier journal de graphisme et libérer des ressources de journalisation.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 4cd4fc0b-974a-4e61-9ea8-0aaa1a0c52ea
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1f79b39ced4f3285815412b9b231692868e5e00f
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "96996056"
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