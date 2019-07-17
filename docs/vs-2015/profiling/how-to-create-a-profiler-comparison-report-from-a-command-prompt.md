---
title: 'Procédure : Créer un rapport de comparaison du profileur à partir d’une invite de commandes | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 00548d16-eb5b-46f7-8a65-862f98a43831
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8c6dabbae5f2d3758aebe0562f99767ee6993d80
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68179574"
---
# <a name="how-to-create-a-profiler-comparison-report-from-a-command-prompt"></a>Procédure : Créer un rapport de comparaison de profileur à partir d’une invite de commandes
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous pouvez générer un rapport des Outils de profilage [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] qui compare les données de performances de deux fichiers de données de profilage (.VSP et/ou .VSPS). Le rapport montre les différences, les régressions de performances et les améliorations qui se sont produites d’une session de profilage à l’autre. Les valeurs du rapport présentent le delta, ou la modification, à partir de la base de référence du premier fichier que vous spécifiez. Le delta est calculé en déterminant la différence entre l’ancienne valeur, qui est la valeur de la base de référence, et la valeur résultant de la nouvelle analyse. Les comparaisons des données du profileur peuvent être basées sur les fonctions du code, les modules de l’application, les lignes, les pointeurs d’instruction et les types.  
  
 Pour lister les identificateurs des catégories et des champs de la comparaison, tapez la ligne de commande suivante :  
  
 **VSPerfReport /querydifftables**  *NomFichierVsp1* *NomFichierVsp2*  
  
 Utilisez la syntaxe suivante pour créer le rapport de comparaison :  
  
 **VSPerfReport /diff**  `VspFileName1` *NomFichierVsp2* [ **/** `Options`]  
  
 Vous pouvez ajouter des options du tableau suivant à la ligne de commande **VSPerfReport /diff**.  
  
|Option|Description|  
|------------|-----------------|  
|**DiffThreshold:** [*Valeur*]|Ignore la différence si elle est inférieure à cette valeur de seuil de pourcentage. De même, les nouvelles données avec des valeurs inférieures à ce seuil n’apparaissent pas.|  
|**DiffTable :** *TableName*|Utilise ce tableau pour comparer les fichiers. Par défaut, le tableau des fonctions est utilisé. Spécifiez l’identificateur qui est répertorié dans **VSPerfReport /querydifftables**.|  
|**DiffColumn :** *ColumnName*|Utiliser cette colonne pour comparer les valeurs. Par défaut, la colonne de pourcentage d’échantillons exclusifs est utilisée. Spécifiez l’identificateur qui est répertorié dans **VSPerfReport /querydifftables**.|
