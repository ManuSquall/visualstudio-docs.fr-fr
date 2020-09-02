---
title: 'DA0004 : Utilisation intensive du processeur | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.performance.rules.DAHighProcessorUsage
- vs.performance.rules.DA0004
- vs.performance.DA0004
- vs.performance.4
ms.assetid: 2c4fb569-929e-4f1d-8c50-b590ee371351
caps.latest.revision: 17
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a0e14a7400b937c56c2aac49a43d1d59cf96eba0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68158698"
---
# <a name="da0004-high-processor-usage"></a>DA0004 : Utilisation intensive du processeur
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

ID de règle | DA0004 |  
| Catégorie | Utilisation de Outils de profilage |  
| Méthodes de profilage | Échantillonnage d’instrumentation |  
| Message | L’utilisation de votre processeur est toujours au-dessus de 75%. Utilisez le mode d’échantillonnage pour les applications utilisant le processeur de manière intensive.|  
| Type de règle | Informations |  
  
 Lorsque vous effectuez un profilage à l’aide de la méthode d’échantillonnage, de mémoire .NET ou de conflit des ressources, vous devez collecter au moins 10 échantillons pour déclencher cette règle.  
  
## <a name="cause"></a>Cause :  
 L’utilisation du processeur (UC) était très élevée dans les données de profilage qui ont été collectées à l’aide de la méthode d’instrumentation. Utilisez la méthode de profilage par échantillonnage lorsque vous profilez une application utilisant le processeur de manière intensive.  
  
## <a name="rule-description"></a>Description de la règle  
 Pendant cette exécution de profilage, le ou les processeurs étaient constamment très occupés. Une utilisation élevée du processeur peut indiquer qu’une application utilise le processeur de manière intensive. Les profils instrumentés ne sont généralement pas les plus efficaces pour étudier les scénarios d’utilisation du processeur. L’échantillonnage est généralement plus efficace lorsque vous profilez des applications qui consacrent beaucoup de temps à exécuter des instructions dans le processeur.  
  
## <a name="how-to-fix-violations"></a>Comment corriger les violations  
 Profilez votre application à l’aide de la méthode d’échantillonnage au lieu de la méthode d’instrumentation, sauf si vous avez besoin de minutage de fonctions ou si vous êtes plus intéressé par les E/S que par les goulots d’étranglement du processeur.
