---
title: "Installation d’Outils R pour Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 4/28/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-r
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3ff60292-1b88-4ee9-b2b2-edd957f1a519
caps.latest.revision: 1
author: kraigb
ms.author: kraigb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 90b2481b0ec4f9387fe3a2c0b733a103e8c03845
ms.openlocfilehash: bc0b1112fe6f3acf2605101a863d831f41bb5f6d
ms.contentlocale: fr-fr
ms.lasthandoff: 05/23/2017

---

# <a name="how-to-install-r-tools-for-visual-studio"></a>Comment installer Outils R pour Visual Studio

Dans cette rubrique :

- [Versions prises en charge de Visual Studio](#supported-versions-of-visual-studio)
- [Installation de RTVS dans Visual Studio 2017](#installing-rtvs-in-visual-studio-2017)
- [Installation de RTVS dans Visual Studio 2015](#installing-rtvs-in-visual-studio-2015)
- [Installation hors connexion](#offline-installation-of-visual-studio-and-rtvs)

> [!Note]
> Après avoir installé Outils R, vous pouvez configurer une disposition optimisée pour les scientifiques des donnée dans Visual Studio, comme décrit dans la rubrique [Options](options.md#data-scientist-layout).

## <a name="supported-versions-of-visual-studio"></a>Versions prises en charge de Visual Studio

Outils R pour Visual Studio (RTVS) est pris en charge dans les éditions Community, Professional et Enterprise de [Visual Studio 2015 Update 3 (ou ultérieur)](http://go.microsoft.com/fwlink/?LinkId=691129) et de [Visual Studio 2017](https://www.visualstudio.com/downloads/). 

Si vous disposez uniquement de Visual Studio Shell, qui est fourni avec d’autres produits tels que Visual Studio Test Professional et SQL Server Management Studio, l’installation de RTVS échoue. Cela vient du fait que Visual Studio Shell ne dispose pas des composants nécessaires pour prendre en charge RTVS.


## <a name="installing-rtvs-in-visual-studio-2017"></a>Installation de RTVS dans Visual Studio 2017

> [!Important]
> L’installation de RTVS dans Visual Studio 2017 sur Windows 7 est actuellement bloquée, comme le décrit le [problème n° 3561 sur GitHub](https://github.com/Microsoft/RTVS/issues/3561). Ce problème sera résolu dans la mise à jour 15.3 de Visual Studio 2017.

1. Exécutez le programme d’installation de Visual Studio.
2. Sélectionnez la charge de travail **Applications de science et analyse des données** :

    ![Applications de science et analyse des données dans VS2017](~/docs/rtvs/media/installation-data-science-workload.png)

3. Définissez toute option supplémentaire à droite sous le même nom de charge de travail. Notez que, par défaut, cette charge de travail prend en charge F# et Python. Pour R, vous devez au minimum sélectionner **Prise en charge du langage R**, **Prise en charge du runtime pour les outils de développement R** et **Microsoft R Client**.

RTVS est installé dans le répertoire suivant : `%ProgramFiles(x86)%\Microsoft Visual Studio\<version>\<edition>Common7\IDE\Extensions\Microsoft\R Tools for Visual Studio` où `<version>` a généralement la valeur `2017` et `<edition>` la valeur `Community`, `Professional` ou `Enterprise`.

## <a name="installing-rtvs-in-visual-studio-2015"></a>Installation de RTVS dans Visual Studio 2015

Si vous utilisez Visual Studio 2015, vous devez installer Outils R et un interpréteur R séparément.

### <a name="install-an-r-interpreter"></a>Installer un interpréteur R

RTVS nécessite une installation 64 bits de R version 3.2.1 ou ultérieure à partir d’une ou plusieurs des sources suivantes :

* [Microsoft R Open](https://mran.microsoft.com/download/)
* [Microsoft R Client](https://msdn.microsoft.com/microsoft-r/r-client-get-started)
* [CRAN R](https://cran.r-project.org/bin/windows/base/)

Microsoft R Open et CRAN R autorisent tous deux plusieurs versions côte à côte. Microsoft R Client, cependant, ne prend en charge qu’une version et utilise toujours la plus récente que vous avez installée.

### <a name="install-the-r-tools"></a>Installer Outils R

Téléchargez la version actuelle de RTVS à partir du site suivant : [https://aka.ms/rtvs-current](https://aka.ms/rtvs-current). RTVS recherche une version appropriée de Visual Studio et vous aide à installer un interpréteur R si vous ne l’avez pas déjà fait.

RTVS est installé dans le répertoire suivant :`%ProgramFiles(x86)%\Microsoft Visual Studio 14\Common7\IDE\Extensions\Microsoft\R Tools for Visual Studio`

## <a name="offline-installation-of-visual-studio-and-rtvs"></a>Installation hors connexion de Visual Studio et de RTVS

Effectuez une installation hors connexion si les ordinateurs ne sont pas connectés à Internet :

1. Suivez les instructions ci-dessous pour créer un programme d’installation en mode hors connexion pour votre version de Visual Studio. 

    - [Visual Studio 2017](../install/create-an-offline-installation-of-visual-studio.md)
    - [Visual Studio 2015](https://msdn.microsoft.com/library/mt706497.aspx)

1. Installez Visual Studio à partir du programme d’installation en mode hors connexion.
1. [Téléchargez RTVS](https://aka.ms/rtvs-current) et installez-le normalement.

## <a name="see-also"></a>Voir aussi

- [Bien démarrer avec R](getting-started-with-r.md)
- [Exemples de projets Outils R](getting-started-samples.md)
- [Obtention d’aide](getting-started-help.md)
- [Paramètres des options](options.md)

