---
title: Lignes, vue - Données d’échantillonnage de mémoire .NET | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Lines view
ms.assetid: 6631ab87-0e62-4c76-a063-4ea7222b07da
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a3aa0c91cb6f26dd2a914195791c12421798c43b
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47494916"
---
# <a name="lines-view---net-memory-sampling-data"></a>Lignes, vue - Données d’échantillonnage de mémoire .NET
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [vue lignes - données d’échantillonnage de mémoire .NET](https://docs.microsoft.com/visualstudio/profiling/lines-view-dotnet-memory-sampling-data).  
  
La vue Lignes des données de profilage d’allocation de mémoire .NET qui utilisent la méthode d’échantillonnage répertorie les instructions ayant alloué la mémoire pendant l’exécution du profilage. Les colonnes incluent également la taille et le nombre d’allocations.  
  
 Dans un fichier source, une instruction peut couvrir plusieurs lignes d'un fichier source, et une ligne unique peut inclure plusieurs instructions.  
  
 Une instruction est identifiée par les éléments suivants :  
  
-   Le fichier source contenant l’instruction de fonction.  
  
-   La fonction contenant l’instruction.  
  
-   La ligne source au niveau de laquelle l’instruction commence.  
  
-   Le caractère de la ligne source au niveau duquel l’instruction commence.  
  
-   La ligne source au niveau de laquelle l’instruction se termine.  
  
-   Le caractère de la ligne source au niveau duquel l’instruction se termine.  
  
 La colonne Nom de ligne fournit une concaténation des données d’identificateur pouvant être triée.  
  
 Par définition, une instruction n’appelle pas d’autres fonctions. Par conséquent, seules les valeurs exclusives apparaissent.  
  
|Colonne|Description|  
|------------|-----------------|  
|**ID du processus**|ID du processus (PID) de l'exécution du profilage.|  
|**Nom du processus**|Nom du processus.|  
|**Nom du module**|Nom du module qui contient l’instruction.|  
|**Chemin du module**|Chemin du module qui contient l’instruction.|  
|**Fichier source**|Fichier source qui contient l’instruction.|  
|**Nom de la fonction**|Nom de la fonction qui contient l’instruction.|  
|**Numéro de ligne de fonction**|Numéro de ligne du début de cette fonction dans le fichier source.|  
|**Adresse de la fonction**|Adresse de départ de la fonction.|  
|**Début ligne source**|Numéro de la ligne de début dans le fichier source au niveau duquel l’allocation a eu lieu.|  
|**Fin ligne source**|Numéro de la ligne de fin dans le fichier source au niveau duquel l’allocation a eu lieu.|  
|**Début caractère source**|Décalage du caractère de début dans la ligne de fichier source au niveau de laquelle l’allocation a eu lieu.|  
|**Fin du caractère source**|Décalage du caractère de fin dans la ligne de fichier source au niveau de laquelle l’allocation a eu lieu.|  
|**Nom de ligne**|Identificateur généré par le profileur de la ligne avec la syntaxe suivante :`Source File`**;[**`Line Number Start`**,**`Character Start`**]->;[**`Line Number Start,Character Start`**]**|  
|**Allocations exclusives**|Nombre total d’objets créés dans cette ligne.|  
|**% d’allocations exclusives**|Pourcentage de tous les objets créés dans le cadre de l’exécution du profilage qui ont été alloués dans cette ligne.|  
|**Octets exclusifs**|Pourcentage de tous les octets de mémoire alloués dans le cadre de l’exécution du profilage qui ont été alloués dans cette ligne.|  
|**% d’octets exclusifs**|Pourcentage de tous les octets de mémoire alloués dans le cadre de l’exécution du profilage qui ont été alloués dans cette ligne.|  
  
## <a name="see-also"></a>Voir aussi  
 [Lignes, vue](../profiling/lines-view-sampling-data.md)



