---
title: Lignes, vue | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.performance.view.lines
helpviewer_keywords:
- profiling tools reports, Line view
- profiling tools, Line view
- Lines view
ms.assetid: 71ec0781-6031-4e17-af09-f50226018437
caps.latest.revision: 18
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 975b5e7386b69e17366c48e2c7dab7c974c49689
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47507931"
---
# <a name="lines-view"></a>Lignes, vue
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [vue lignes](https://docs.microsoft.com/visualstudio/profiling/lines-view).  
  
La vue Lignes est disponible uniquement pour les données du profileur collectées à l’aide de la méthode d’échantillonnage. Elle n’est pas disponible pour les données collectées à l’aide de l’instrumentation.  
  
 Pour les données de profil d’échantillonnage, la vue Lignes identifie les instructions d’une fonction qui s’exécutait directement lors de la collecte de l’échantillon. Pour les données de mémoire .NET, elle identifie les instructions qui allouent la mémoire.  
  
 Dans un fichier source, une instruction peut couvrir plusieurs lignes d’un fichier source, et une ligne unique peut inclure plusieurs instructions.  
  
 Une instruction est identifiée par les éléments suivants :  
  
-   Le fichier source contenant l’instruction de fonction.  
  
-   La fonction contenant l’instruction.  
  
-   La ligne source au niveau de laquelle l’instruction commence.  
  
-   Le caractère de la ligne source au niveau duquel l’instruction commence.  
  
-   La ligne source au niveau de laquelle l’instruction se termine.  
  
-   Le caractère de la ligne source au niveau duquel l’instruction se termine.  
  
## <a name="see-also"></a>Voir aussi  
 [Lignes, vue - Données d’échantillonnage](../profiling/lines-view-sampling-data.md)   
 [Lignes, vue - Échantillonnage](../profiling/lines-view-dotnet-memory-sampling-data.md)   
 [Lignes, vue](../profiling/lines-view-contention-data.md)



