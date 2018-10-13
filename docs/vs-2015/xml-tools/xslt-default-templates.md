---
title: Modèles par défaut XSLT | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 773dd34e-67d3-4997-8df9-b71e7f880d88
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 4a26349a60c40552d350f156bf1109544a03d411
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49181348"
---
# <a name="xslt-default-templates"></a>Modèles par défaut XSLT
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Un modèle par défaut est utilisé pendant le traitement XSLT en l'absence de règle de modèle explicite correspondante dans la feuille de style. Le modèle par défaut, également appelé règle de modèle intégrée, est défini dans la section 5.8 de la recommandation du W3C sur XSLT 1.0. Il permet au processeur XSLT de traiter un nœud, même en l'absence de règle de modèle explicite correspondante. Cependant, du fait que la règle de modèle intégrée ne soit pas explicitement définie dans la feuille de style, des résultats de la transformation XSLT confus ou inattendus peuvent en découler.  
  
 Le débogueur XSLT affiche maintenant le code des modèles XSLT par défaut. Lorsque vous effectuez pas à pas une transformation XSLT, si un modèle par défaut est utilisé, le débogueur l'affiche dans une fenêtre. Ainsi, vous pouvez parcourir le code du modèle par défaut et définir des points d'arrêt sur ses instructions.  
  
## <a name="see-also"></a>Voir aussi  
 [Débogage XSLT](../xml-tools/debugging-xslt.md)

