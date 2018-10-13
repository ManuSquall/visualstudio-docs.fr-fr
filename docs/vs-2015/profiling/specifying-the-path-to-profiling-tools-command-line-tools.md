---
title: Spécification du chemin des outils en ligne de commande des outils de profilage | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7047bf18-5779-4f6e-872c-66e2fc47c969
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 407ed292bea2b6b7b47e07a3a5e30183f411f991
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49242903"
---
# <a name="specifying-the-path-to-profiling-tools-command-line-tools"></a>Spécification du chemin d’accès aux outils en ligne de commande des outils de profilage
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Le chemin d’accès aux outils de profilage en ligne de commande de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] n’est pas ajouté à la variable d’environnement PATH. Sur les ordinateurs 32 bits, les outils se trouvent dans un même répertoire. Il existe des versions 32 bits et 64 bits des outils de profilage sur les ordinateurs 64 bits.  
  
## <a name="32-bit-computers"></a>Ordinateurs 32 bits  
 Sur les ordinateurs 32 bits, le répertoire par défaut des outils de profilage est *Lecteur*\Program Files\Microsoft Visual Studio 11.0\Team Tools\Performance Tools.  
  
## <a name="64-bit-computers"></a>Ordinateurs 64 bits  
 Sur les ordinateurs 64 bits, spécifiez le chemin d'accès en fonction de la plateforme cible de l'application profilée.  
  
-   Pour les applications 32 bits, le répertoire par défaut des outils de profilage est le suivant :  
  
     *Lecteur*\Program Files (x86)\Microsoft Visual Studio 11.0\Team Tools\Performance Tools  
  
-   Pour les applications 64 bits, le répertoire par défaut des outils de profilage est le suivant :  
  
     *Lecteur*\Program Files (x86)\Microsoft Visual Studio 11.0\Team Tools\Performance Tools\x64



