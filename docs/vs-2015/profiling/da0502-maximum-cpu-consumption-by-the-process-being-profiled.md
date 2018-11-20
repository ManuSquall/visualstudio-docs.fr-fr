---
title: 'DA0502 : Consommation CPU maximale par le processus en cours de profilage | Microsoft Docs'
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
- vs.performance.rules.DA0502
- vs.performance.DA0502
- vs.performance.502
ms.assetid: 1ee53df5-b0dc-4265-9d4f-527830d08725
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dd2665e9b8055812678fc1a17c0b9df0f0405e42
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51731250"
---
# <a name="da0502-maximum-cpu-consumption-by-the-process-being-profiled"></a>DA0502 : consommation processeur maximale par le processus en cours de profilage
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Id de règle | DA0502 |  
| Catégorie | Surveillance des ressources |  
| Méthode de profilage | Tous les |  
| Message | Cette règle est pour information uniquement. Le compteur Processus()\\% temps processus mesure la consommation CPU du processus que vous profilez. La valeur signalée correspond au maximum observé pour tous les intervalles de mesure. |  
| Type de règle | D’information |  
  
 Lorsque vous effectuez un profilage à l’aide de la méthode d’échantillonnage, de mémoire .NET ou de conflit des ressources, vous devez collecter au moins 10 échantillons pour déclencher cette règle.  
  
## <a name="rule-description"></a>Description de la règle  
 Ce message indique le temps maximal, en pourcentage, pendant lequel un processeur a exécuté des instructions à partir de l’application. La valeur signalée correspond à la valeur maximale de tous les intervalles de mesure pendant lesquels le processus profilé était actif. Cette valeur peut être supérieure à 100 % sur les ordinateurs qui comprennent plusieurs processeurs.  
  
## <a name="how-to-use-the-rule-data"></a>Comment utiliser des données de règle  
 Utilisez la valeur de la règle pour comparer les performances des différentes versions du programme ou pour comprendre les performances de l’application dans différents scénarios de profilage.



