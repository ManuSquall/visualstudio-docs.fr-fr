---
title: Modèles par défaut XSLT
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 773dd34e-67d3-4997-8df9-b71e7f880d88
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ee9356724d9915bf3e19d8a892fb1a4b12c4fd16
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
---
# <a name="xslt-default-templates"></a>Modèles par défaut XSLT

Un modèle par défaut est utilisé pendant le traitement XSLT en l'absence de règle de modèle explicite correspondante dans la feuille de style. Le modèle par défaut, également appelé règle de modèle intégrée, est défini dans la section 5.8 de la recommandation du W3C sur XSLT 1.0. Il permet au processeur XSLT de traiter un nœud, même en l'absence de règle de modèle explicite correspondante. Cependant, du fait que la règle de modèle intégrée ne soit pas explicitement définie dans la feuille de style, des résultats de la transformation XSLT confus ou inattendus peuvent en découler.

Le débogueur XSLT affiche maintenant le code des modèles XSLT par défaut. Lorsque vous effectuez pas à pas une transformation XSLT, si un modèle par défaut est utilisé, le débogueur l'affiche dans une fenêtre. Ainsi, vous pouvez parcourir le code du modèle par défaut et définir des points d'arrêt sur ses instructions.

## <a name="see-also"></a>Voir aussi

- [Débogage XSLT](../xml-tools/debugging-xslt.md)