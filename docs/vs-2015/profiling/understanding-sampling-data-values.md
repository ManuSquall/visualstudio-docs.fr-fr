---
title: Présentation des valeurs de données d’échantillonnage | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- sampling profiling method
- Profiling Tools, sampling
ms.assetid: fad540a8-24b6-4ff9-91ce-e67e9a58399d
caps.latest.revision: 27
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 91a4a50ecc745c0b56167d6a5dbb1932af7ed2bf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68145416"
---
# <a name="understanding-sampling-data-values"></a>Fonctionnement des valeurs de données d’échantillonnage
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La méthode de profilage par *échantillonnage* des outils de profilage de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] interrompt le processeur de l’ordinateur à des intervalles définis et collecte la pile des appels des fonctions. Une *pile des appels* est une structure dynamique qui stocke des informations sur les fonctions qui s’exécutent sur le processeur.  
  
 **Configuration requise**  
  
- [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
  L’analyse du profileur détermine si le processeur exécute du code dans le processus cible. Si le processeur n’exécute pas de code dans le processus cible, l’échantillon est ignoré.  
  
  Si le processeur exécute le code cible, le profileur incrémente le nombre d’échantillons pour chaque fonction sur la pile des appels. Au moment où l’échantillon est collecté, une seule fonction sur la pile des appels exécute du code. Les autres fonctions sur la pile sont des parents dans la hiérarchie des appels de fonctions qui sont en attente du retour de leurs enfants.  
  
  Pour l’événement échantillonné, le profileur incrémente le nombre d’échantillons *exclusifs* de la fonction qui exécute ses instructions à ce moment-là. Comme un échantillon exclusif fait également partie du total des échantillons (*inclusifs*) de la fonction, le nombre d’échantillons inclusifs de la fonction active est également incrémenté.  
  
  Le profileur incrémente le nombre d’échantillons inclusifs de toutes les autres fonctions sur la pile des appels.  
  
## <a name="inclusive-samples"></a>Échantillons inclusifs  
 Nombre total d’échantillons collectés pendant l’exécution de la fonction cible.  
  
 Ceci inclut les échantillons collectés pendant l’exécution directe du code de la fonction et les échantillons collectés pendant l’exécution des fonctions enfants qui sont appelées par la fonction cible.  
  
## <a name="exclusive-samples"></a>Échantillons exclusifs  
 Nombre total d’échantillons collectés pendant l’exécution directe des instructions de la fonction cible.  
  
 Les échantillons exclusifs n’incluent pas les échantillons collectés pendant l’exécution des fonctions qui sont appelées par la fonction cible.  
  
## <a name="inclusive-percent"></a>Pourcentage inclusif  
 Pourcentage du nombre total d’échantillons inclusifs lors de l’exécution du profilage qui sont des échantillons inclusifs de la fonction ou de la plage de données.  
  
## <a name="exclusive-percent"></a>Pourcentage exclusif  
 Pourcentage du nombre total d’échantillons exclusifs lors de l’exécution du profilage qui sont des échantillons exclusifs de la fonction ou de la plage de données.  
  
## <a name="see-also"></a>Voir aussi  
 [Comment : choisir des méthodes de collection](../profiling/how-to-choose-collection-methods.md)   
 [Analyse des données des outils d’analyse des performances](../profiling/analyzing-performance-tools-data.md)
