---
title: Spécification du chemin des outils en ligne de commande des outils de profilage | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 7047bf18-5779-4f6e-872c-66e2fc47c969
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1afb0b00a7e121c611dedbc235684a67cc9cec53
ms.sourcegitcommit: 1b9c1e333c2f096d35cfc77e846116f8e5054557
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2018
ms.locfileid: "34814493"
---
# <a name="specify-the-path-to-profiling-tools-command-line-tools"></a>Spécifier le chemin des outils en ligne de commande des outils de profilage
Le chemin d'accès aux outils de profilage en ligne de commande de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] n'est pas ajouté à la variable d'environnement PATH. Sur les ordinateurs 32 bits, les outils se trouvent dans un même répertoire. Il existe des versions 32 bits et 64 bits des outils de profilage sur les ordinateurs 64 bits.  
  
## <a name="32-bit-computers"></a>Ordinateurs 32 bits  
 Sur les ordinateurs 32 bits, le répertoire par défaut des outils de profilage est *lecteur\Program Files\Microsoft Visual Studio 11.0\Team Tools\Performance Tools*.  
  
## <a name="64-bit-computers"></a>Ordinateurs 64 bits  
 Sur les ordinateurs 64 bits, spécifiez le chemin d’accès en fonction de la plateforme cible de l’application profilée.  
  
-   Pour les applications 32 bits, le répertoire par défaut des outils de profilage est le suivant :  
  
     *lecteur\Program Files (x86)\Microsoft Visual Studio 11.0\Team Tools\Performance Tools*  
  
-   Pour les applications 64 bits, le répertoire par défaut des outils de profilage est le suivant :  
  
     *lecteur\Program Files (x86)\Microsoft Visual Studio 11.0\Team Tools\Performance Tools\x64*