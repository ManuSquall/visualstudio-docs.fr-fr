---
title: 'DA0004 : Utilisation intensive du processeur | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.performance.rules.DAHighProcessorUsage
- vs.performance.rules.DA0004
- vs.performance.DA0004
- vs.performance.4
ms.assetid: 2c4fb569-929e-4f1d-8c50-b590ee371351
caps.latest.revision: 17
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a942a26bb4cd8ccca94fd442250fe8a239cba4ed
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51764030"
---
# <a name="da0004-high-processor-usage"></a>DA0004 : Utilisation intensive du processeur
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Id de règle | DA0004 |  
| Catégorie | Utilisation des outils de profilage |  
| Méthodes de profilage | Échantillonnage de l’instrumentation |  
| Message | Utilisation de votre processeur est constamment supérieure à 75 %. Envisagez d’utiliser le mode d’échantillonnage pour les applications de processeur de manière intensive. |  
| Type de règle | Informations |  
  
 Lorsque vous effectuez un profilage à l’aide de la méthode d’échantillonnage, de mémoire .NET ou de conflit des ressources, vous devez collecter au moins 10 échantillons pour déclencher cette règle.  
  
## <a name="cause"></a>Cause  
 L’utilisation du processeur (UC) était très élevée dans les données de profilage qui ont été collectées à l’aide de la méthode d’instrumentation. Utilisez la méthode de profilage par échantillonnage lorsque vous profilez une application utilisant le processeur de manière intensive.  
  
## <a name="rule-description"></a>Description de la règle  
 Pendant cette exécution de profilage, le ou les processeurs étaient constamment très occupés. Une utilisation élevée du processeur peut indiquer qu’une application utilise le processeur de manière intensive. Les profils instrumentés ne sont généralement pas les plus efficaces pour étudier les scénarios d’utilisation du processeur. L’échantillonnage est généralement plus efficace lorsque vous profilez des applications qui consacrent beaucoup de temps à exécuter des instructions dans le processeur.  
  
## <a name="how-to-fix-violations"></a>Comment corriger les violations  
 Profilez votre application à l’aide de la méthode d’échantillonnage au lieu de la méthode d’instrumentation, sauf si vous avez besoin de minutage de fonctions ou si vous êtes plus intéressé par les E/S que par les goulots d’étranglement du processeur.




