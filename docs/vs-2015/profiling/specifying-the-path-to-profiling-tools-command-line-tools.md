---
title: Spécification du chemin des outils en ligne de commande des outils de profilage | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 7047bf18-5779-4f6e-872c-66e2fc47c969
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 209c2263e35bc4e6c5bfffb03b4a760e8cc15a45
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54791750"
---
# <a name="specifying-the-path-to-profiling-tools-command-line-tools"></a>Spécification du chemin d’accès aux outils en ligne de commande des outils de profilage
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Le chemin d’accès aux outils de profilage en ligne de commande de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] n’est pas ajouté à la variable d’environnement PATH. Sur les ordinateurs 32 bits, les outils se trouvent dans un même répertoire. Il existe des versions 32 bits et 64 bits des outils de profilage sur les ordinateurs 64 bits.  
  
## <a name="32-bit-computers"></a>Ordinateurs 32 bits  
 Sur les ordinateurs 32 bits, le répertoire par défaut des outils de profilage est *Lecteur*\Program Files\Microsoft Visual Studio 11.0\Team Tools\Performance Tools.  
  
## <a name="64-bit-computers"></a>Ordinateurs 64 bits  
 Sur les ordinateurs 64 bits, spécifiez le chemin d’accès en fonction de la plateforme cible de l’application profilée.  
  
-   Pour les applications 32 bits, le répertoire par défaut des outils de profilage est le suivant :  
  
     *Lecteur*\Program Files (x86)\Microsoft Visual Studio 11.0\Team Tools\Performance Tools  
  
-   Pour les applications 64 bits, le répertoire par défaut des outils de profilage est le suivant :  
  
     *Lecteur*\Program Files (x86)\Microsoft Visual Studio 11.0\Team Tools\Performance Tools\x64
