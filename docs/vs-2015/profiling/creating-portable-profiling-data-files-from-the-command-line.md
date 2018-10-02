---
title: Création de fichiers de données de profilage portables à partir de la ligne de commande | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2ceb63a7-b835-4988-b756-2afc3fcc4808
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 314dc97e5881949ee69131576932db1865969b2c
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47516767"
---
# <a name="creating-portable-profiling-data-files-from-the-command-line"></a>Création de fichiers de données de profilage portables à partir de la ligne de commande
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [création Portable profilage des données de fichiers à partir de la ligne de commande](https://docs.microsoft.com/visualstudio/profiling/creating-portable-profiling-data-files-from-the-command-line).  
  
Pour faciliter le partage des données de profilage, vous pouvez utiliser l’outil en ligne de commande [VSPerfReport](../profiling/vsperfreport.md) visant à incorporer les symboles pour une exécution de profilage dans le fichier .vsp.  
  
 Vous pouvez également créer un fichier de données de profilage pré-analysé (.vsps), plus petit et donc plus rapide à charger dans l’IDE.  
  
> [!NOTE]
>  Vérifiez que les fichiers de symboles (.pdb) sont disponibles pour **VSPerfReport**. Pour plus d’informations, consultez [Guide pratique pour spécifier les emplacements du fichier de symboles à partir de la ligne de commande](../profiling/how-to-specify-symbol-file-locations-from-the-command-line.md).  
>   
>  Pour plus d’informations sur le chemin de **VSReport**, consultez [Spécification du chemin des outils en ligne de commande](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  
>   
>  Les données de profilage d’un fichier .vsps ne peuvent pas être filtrées.  
  
### <a name="to-embed-the-symbols-for-a-profiling-run-into-a-profiling-data-vsp-file"></a>Pour incorporer les symboles d’une exécution de profilage dans un fichier de données de profilage (.vsp)  
  
-   Dans une fenêtre d’invite de commandes, tapez la commande suivante :  
  
     \<Chemin>**VSPerfReport \<** Fichier VSP> **/PackSymbols**  
  
     Par défaut, le fichier .vsps est nommé d’après le nom de base du fichier .vsp. Vous pouvez spécifier un autre nom avec l’option **Output**.  
  
### <a name="to-create-a-summary-profiling-data-file"></a>Pour créer un fichier récapitulatif des données de profilage  
  
-   Dans une fenêtre d’invite de commandes, tapez la commande suivante :  
  
     \<Chemin>**VSPerfReport \<** Fichier VSP> **/SummaryFile** [**/Output:**\<Nom de fichier>]  
  
     Par défaut, le fichier .vsps est nommé d’après le nom de base du fichier .vsp. Vous pouvez spécifier un autre nom avec l’option **Output**.



