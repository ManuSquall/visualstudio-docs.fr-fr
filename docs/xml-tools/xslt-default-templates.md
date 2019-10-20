---
title: Modèles par défaut XSLT
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 773dd34e-67d3-4997-8df9-b71e7f880d88
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 81a764aa45eb74ba110d8b3b5965ede1e62bdadd
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72607782"
---
# <a name="xslt-default-templates"></a>Modèles par défaut XSLT

Un modèle par défaut est utilisé pendant le traitement XSLT en l'absence de règle de modèle explicite correspondante dans la feuille de style. Le modèle par défaut, également appelé règle de modèle intégrée, est défini dans la section 5.8 de la recommandation du W3C sur XSLT 1.0. Il permet au processeur XSLT de traiter un nœud, même en l'absence de règle de modèle explicite correspondante. Cependant, du fait que la règle de modèle intégrée ne soit pas explicitement définie dans la feuille de style, des résultats de la transformation XSLT confus ou inattendus peuvent en découler.

Le débogueur XSLT affiche maintenant le code des modèles XSLT par défaut. Lorsque vous effectuez pas à pas une transformation XSLT, si un modèle par défaut est utilisé, le débogueur l'affiche dans une fenêtre. Ainsi, vous pouvez parcourir le code du modèle par défaut et définir des points d'arrêt sur ses instructions.

## <a name="see-also"></a>Voir aussi

- [Débogage XSLT](../xml-tools/debugging-xslt.md)