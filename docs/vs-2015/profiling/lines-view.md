---
title: Lignes, vue | Microsoft Docs
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
ms.openlocfilehash: fdf3249974f2e04cc3794c3437b0d31cef7b9ef9
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49205131"
---
# <a name="lines-view"></a>Lignes, vue
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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



