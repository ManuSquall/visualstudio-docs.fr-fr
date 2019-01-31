---
title: Spécification du chemin des outils en ligne de commande des outils de profilage | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 7047bf18-5779-4f6e-872c-66e2fc47c969
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a42774d2f91afe0e3b469a97a17763950b4bdc2e
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54968123"
---
# <a name="specify-the-path-to-profiling-tools-command-line-tools"></a>Spécifier le chemin des outils en ligne de commande des outils de profilage
Le chemin d’accès aux outils de profilage en ligne de commande de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] n’est pas ajouté à la variable d’environnement PATH. Sur les ordinateurs 32 bits, les outils se trouvent dans un même répertoire. Il existe des versions 32 bits et 64 bits des outils de profilage sur les ordinateurs 64 bits.  
  
## <a name="32-bit-computers"></a>Ordinateurs 32 bits  
 Pour le code natif, les API du profileur Visual Studio se trouvent dans *VSPerf.dll*. Le fichier d’en-tête, *VSPerf.h*, et la bibliothèque d’importation, *VSPerf.lib*, se trouvent dans le répertoire *Microsoft Visual Studio\2017\Team Tools\Performance Tools\PerfSDK*.
  
 Pour le code managé, les API du profileur se trouvent dans *Microsoft.VisualStudio.Profiler.dll*. Cette DLL se trouve dans le répertoire *Microsoft Visual Studio\Shared\Common\VSPerfCollectionTools*.
  
## <a name="64-bit-computers"></a>Ordinateurs 64 bits  
 Sur les ordinateurs 64 bits, spécifiez le chemin d’accès en fonction de la plateforme cible de l’application profilée.  
  
-   Pour les applications 32 bits, le répertoire par défaut des outils de profilage est le suivant :  
  
     (natif) *Microsoft Visual Studio\2017\Team Tools\Performance Tools\PerfSDK* (managé) *Microsoft Visual Studio\Shared\Common\VSPerfCollectionTools*  
  
-   Pour les applications 64 bits, le répertoire par défaut des outils de profilage est le suivant :  
  
     (natif) *Microsoft Visual Studio\2017\Team Tools\Performance Tools\x64\PerfSDK* (managé) *Microsoft Visual Studio\Shared\Common\VSPerfCollectionTools\x64*