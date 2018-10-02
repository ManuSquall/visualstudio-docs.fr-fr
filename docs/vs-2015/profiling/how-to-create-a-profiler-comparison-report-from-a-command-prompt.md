---
title: Guide pratique pour créer un rapport de comparaison du profileur à partir d’une invite de commandes | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 00548d16-eb5b-46f7-8a65-862f98a43831
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3cb31a79af25fbe66112efd6be0aacd9b3c3820d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47501172"
---
# <a name="how-to-create-a-profiler-comparison-report-from-a-command-prompt"></a>Comment : créer un rapport de comparaisons du profileur à partir d'une invite de commandes
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [Comment : créer un rapport de comparaison de Profiler à partir d’une invite de commandes](https://docs.microsoft.com/visualstudio/profiling/how-to-create-a-profiler-comparison-report-from-a-command-prompt).  
  
Vous pouvez générer un rapport des Outils de profilage [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] qui compare les données de performances de deux fichiers de données de profilage (.VSP et/ou .VSPS). Le rapport affiche les différences, les régressions des performances et les améliorations qui se sont produites à partir d’une session de profilage à l’autre. Les valeurs du rapport présentent le delta, ou la modification, à partir de la base de référence du premier fichier que vous spécifiez. Le delta est calculé en déterminant la différence entre l’ancienne valeur, qui est la valeur de la base de référence, et la valeur résultant de la nouvelle analyse. Les comparaisons des données du profileur peuvent être basées sur les fonctions du code, les modules de l’application, les lignes, les pointeurs d’instruction et les types.  
  
 Pour lister les identificateurs des catégories et des champs de la comparaison, tapez la ligne de commande suivante :  
  
 **VSPerfReport /querydifftables**  *NomFichierVsp1* *NomFichierVsp2*  
  
 Utilisez la syntaxe suivante pour créer le rapport de comparaison :  
  
 **VSPerfReport /diff**  `VspFileName1` *NomFichierVsp2* [**/**`Options`]  
  
 Vous pouvez ajouter des options du tableau suivant à la ligne de commande **VSPerfReport /diff**.  
  
|Option|Description|  
|------------|-----------------|  
|**DiffThreshold:**[*Valeur*]|Ignore la différence si elle est inférieure à cette valeur de seuil de pourcentage. De même, les nouvelles données avec des valeurs inférieures à ce seuil n’apparaissent pas.|  
|**DiffTable:** *NomTableau*|Utilise ce tableau pour comparer les fichiers. Par défaut, le tableau des fonctions est utilisé. Spécifiez l’identificateur qui est répertorié dans **VSPerfReport /querydifftables**.|  
|**DiffColumn:** *NonColonne*|Utiliser cette colonne pour comparer les valeurs. Par défaut, la colonne de pourcentage d’échantillons exclusifs est utilisée. Spécifiez l’identificateur qui est répertorié dans **VSPerfReport /querydifftables**.|



