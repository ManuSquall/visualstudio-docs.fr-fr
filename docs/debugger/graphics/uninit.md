---
title: UnInit | Microsoft Docs
description: Utilisez la méthode Uninit () de Vsgdbg, pour finaliser et fermer le fichier journal de graphisme et libérer des ressources de journalisation.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 4cd4fc0b-974a-4e61-9ea8-0aaa1a0c52ea
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 7cead2d7c1c98e4f481e6057c9ab79c8dc908683
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99905017"
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