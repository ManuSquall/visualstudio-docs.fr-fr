---
title: 'DA0002 : VSPerfCorProf.dll est manquant | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.performance.DA0002
- vs.performance.2
- vs.performance.rules.DAVsPerfCorProfMissing
- vs.performance.rules.DA0002
ms.assetid: 76e614b3-ad7e-4b92-b7be-88dc1329be1d
caps.latest.revision: 19
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5723506415a0ddbf816b896e23e93eaa706bf7e7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68158727"
---
# <a name="da0002-vsperfcorprofdll-is-missing"></a>DA0002 : VSPerfCorProf.dll est manquant
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

ID de règle | DA0002 |  
| Catégorie | Utilisation de Outils de profilage |  
| Méthodes de profilage | Profilage à l’aide des outils en ligne de commande VSPerfCmd et VSPerfASPNETCmd |  
| Message | Il semble que le fichier ait été collecté sans définir correctement les variables d’environnement avec VSPerfCLREnv. cmd. Les symboles des fichiers binaires managés peuvent ne pas être résolus.|  
| Type de règle | Informations |  
  
## <a name="cause"></a>Cause :  
 Le profileur n’a pas trouvé VSPerfCorProf.dll lors de l’exécution du profilage. Cet avertissement se produit quand les outils en ligne de commande pour la collecte de données du profileur sont utilisés sans l’outil VSPerfCLREnv.cmd pour initialiser les variables d’environnement nécessaires. L’avertissement peut également se déclencher si un autre profileur est en cours d’exécution quand les outils de profilage démarrent.  
  
## <a name="rule-description"></a>Description de la règle  
 Des variables d’environnement spécifiques doivent être définies avant l’exécution d’un profilage pour que le profileur résolve les symboles dans les fichiers binaires .NET Framework. Cet avertissement suggère que l’outil VSPerfCLREnv.cmd n’a pas été exécuté avant la collecte des données de profilage. Les symboles pour des fichiers binaires managés peuvent ne pas être résolus. Pour plus d’informations sur l’utilisation de la Outils de profilage à partir de la ligne de commande, consultez [profilage à partir de la ligne de commande](../profiling/using-the-profiling-tools-from-the-command-line.md)  
  
## <a name="how-to-fix-violations"></a>Comment corriger les violations  
 Quand vous profilez des applications managées en utilisant les outils en ligne de commande des Outils de profilage [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], exécutez l’outil en ligne de commande [VSPerfCLREnv](../profiling/vsperfclrenv.md) avant de commencer la collecte de données.
