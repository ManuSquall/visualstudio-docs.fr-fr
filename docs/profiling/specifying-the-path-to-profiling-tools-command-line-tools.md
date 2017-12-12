---
title: "Spécification du chemin des outils en ligne de commande des outils de profilage | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7047bf18-5779-4f6e-872c-66e2fc47c969
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d6b05de013143c1def53044a40977657fdd2cfcb
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="specifying-the-path-to-profiling-tools-command-line-tools"></a>Spécification du chemin des outils en ligne de commande des outils de profilage
Le chemin des outils en ligne de commande des Outils de profilage [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] n'est pas ajouté à la variable d'environnement PATH. Sur les ordinateurs 32 bits, les outils se trouvent dans un même répertoire. Il existe des versions 32 bits et 64 bits des outils de profilage sur les ordinateurs 64 bits.  
  
## <a name="32-bit-computers"></a>Ordinateurs 32 bits  
 Sur les ordinateurs 32 bits, le répertoire par défaut des outils de profilage est *Lecteur*\Program Files\Microsoft Visual Studio 11.0\Team Tools\Performance Tools.  
  
## <a name="64-bit-computers"></a>Ordinateurs 64 bits  
 Sur les ordinateurs 64 bits, spécifiez le chemin d'accès en fonction de la plateforme cible de l'application profilée.  
  
-   Pour les applications 32 bits, le répertoire par défaut des outils de profilage est le suivant :  
  
     *Lecteur*\Program Files (x86)\Microsoft Visual Studio 11.0\Team Tools\Performance Tools  
  
-   Pour les applications 64 bits, le répertoire par défaut des outils de profilage est le suivant :  
  
     *Lecteur*\Program Files (x86)\Microsoft Visual Studio 11.0\Team Tools\Performance Tools\x64