---
title: Lignes, vue - Données de conflit | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Lines view
ms.assetid: 859b02d2-eddf-4ad3-95de-0df67ee2ab03
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8cb6b8191b39bfc79615bf0bbcd4fb469395f8d8
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54779048"
---
# <a name="lines-view---contention-data"></a>Lignes, vue - Données de conflit
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La vue Lignes des données de conflit répertorie les données de performance pour les instructions qui étaient en cours d’exécution au moment de la collecte des échantillons dans le cadre de l’exécution du profilage. Dans un fichier source, une instruction peut couvrir plusieurs lignes d'un fichier source, et une ligne unique peut inclure plusieurs instructions.  
  
 Une instruction est identifiée par les données suivantes :  
  
- Le fichier source contenant l’instruction de fonction.  
  
- La fonction contenant l’instruction.  
  
- La ligne source au niveau de laquelle l’instruction commence.  
  
- Le caractère de la ligne source au niveau duquel l’instruction commence.  
  
- La ligne source au niveau de laquelle l’instruction se termine.  
  
- Le caractère de la ligne source au niveau duquel l’instruction se termine.  
  
  La colonne Nom de ligne fournit une concaténation des données d’identificateur pouvant être triée.  
  
  Le tableau suivant décrit les colonnes du rapport de vue Lignes.  
  
|Colonne|Description|  
|------------|-----------------|  
|**Temps bloqué exclusif**|Durée pendant laquelle cette instruction n’a pas pu exécuter le code qu’elle contient en raison d’un événement de conflit. Le temps bloqué dans les fonctions appelées par l’instruction n’est pas inclus.|  
|**% de temps bloqué exclusif**|Pourcentage du temps bloqué total dans le processus qui était un temps bloqué exclusif de l’instruction.|  
|**Conflits exclusifs**|Nombre de fois où cette instruction n’a pas pu exécuter le code qu’elle contient en raison d’un événement de conflit. Les événements de conflit dans les fonctions que l’instruction a appelées ne sont pas inclus.|  
|**% de conflits exclusifs**|Pourcentage de tous les événements de conflit dans le processus qui étaient des conflits exclusifs de cette instruction.|  
|**Adresse de la fonction**|Adresse de la fonction qui contient cette instruction.|  
|**Nom de la fonction**|Nom complet de la fonction qui contient cette instruction.|  
|**Temps bloqué inclusif**|Temps bloqué dans cette instruction et fonctions appelées dans cette dernière.|  
|**% de temps bloqué inclusif**|Pourcentage du temps bloqué total dans le processus qui était un temps bloqué inclusif de l’instruction.|  
|**Conflits inclusifs**|Nombre de fois où l’exécution de cette instruction et des fonctions appelées dans cette dernière a été bloquée.|  
|**% de conflits inclusifs**|Pourcentage de tous les événements de conflit dans le processus qui étaient des conflits inclusifs de cette instruction.|  
|**Nom de ligne**|Identificateur généré par le profileur de la ligne. L’identificateur utilise la syntaxe suivante :`SourceFile`**;[**`LineNumberStart`**,**`CharacterStart`**]->;[**`LineNumberEnd`**,**`CharacterEnd`**]**|  
|**Numéro de ligne de fonction**|Numéro de ligne du début de cette fonction dans le fichier source.|  
|**Nom du module**|Nom du module qui contient l’instruction.|  
|**Chemin du module**|Chemin du module qui contient l’instruction.|  
|**ID du processus**|ID de processus (PID) du processus profilé.|  
|**Nom du processus**|Nom du processus.|  
|**Début caractère source**|Décalage du caractère de début dans la ligne de fichier source au niveau de laquelle cette instruction commence.|  
|**Fin du caractère source**|Décalage du caractère de fin dans la ligne de fichier source au niveau de laquelle cette instruction se termine.|  
|**Fichier source**|Nom du fichier source contenant l’instruction de fonction.|  
|**Début ligne source**|Numéro de ligne dans le fichier source au niveau duquel l’instruction commence.|  
|**Fin ligne source**|Numéro de ligne dans le fichier source au niveau duquel l’instruction se termine.|  
  
## <a name="see-also"></a>Voir aussi  
 [Guide pratique pour personnaliser les colonnes de vue des rapports](../profiling/how-to-customize-report-view-columns.md)   
 [Lignes, vue](../profiling/lines-view.md)   
 [Lignes, vue - Échantillonnage](../profiling/lines-view-dotnet-memory-sampling-data.md)   
 [Lignes, vue](../profiling/lines-view-sampling-data.md)
