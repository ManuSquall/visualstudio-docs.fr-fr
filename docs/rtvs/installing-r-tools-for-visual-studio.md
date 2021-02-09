---
title: Installation des outils R
description: Guide pratique pour installer les outils R pour Visual Studio 2017 et Visual Studio 2015, y compris les installations en mode hors connexion.
ms.date: 01/24/2018
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jmartens
ms.workload:
- data-science
monikerRange: vs-2017
ms.openlocfilehash: fa5346d65a94646a0fa5e922f3b0055d8cdb6c0d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99908662"
---
# <a name="how-to-install-r-tools-for-visual-studio"></a>Comment installer Outils R pour Visual Studio

Contenu de cet article :

- [Versions prises en charge de Visual Studio](#supported-versions-of-visual-studio)
- [Installer RTVS dans Visual Studio 2017](#install-rtvs-in-visual-studio-2017)
- [Installer RTVS dans Visual Studio 2015](#install-rtvs-in-visual-studio-2015)
- [Installation hors connexion](#offline-installation-of-visual-studio-and-rtvs)

> [!Note]
> Après avoir installé les Outils R, vous pouvez configurer une disposition optimisée pour les scientifiques des données dans Visual Studio, comme décrit dans l’article [Options](options-for-r-tools-in-visual-studio.md).

## <a name="supported-versions-of-visual-studio"></a>Versions prises en charge de Visual Studio

Les outils R pour Visual Studio (RTVS) sont pris en charge sur Windows avec les éditions Community (gratuite), Professional et Enterprise de [Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) et de [Visual Studio 2015 Update 3 (ou version ultérieure)](http://htmlpreview.github.io/?https://github.com/lixzhang/R-MRO-MRS/blob/master/Introduction_to_MRO_and_MRS.html) (téléchargement direct).

RTVS n’est pas pris en charge avec Visual Studio pour Mac.

Si vous disposez uniquement de Visual Studio Shell, qui est fourni avec des produits tels que Visual Studio Test Professional et SQL Server Management Studio, l’installation de RTVS échoue. Visual Studio Shell ne dispose pas des composants nécessaires pour prendre en charge RTVS.

## <a name="install-rtvs-in-visual-studio-2017"></a>Installer RTVS dans Visual Studio 2017

1. Exécutez Visual Studio Installer, puis sélectionnez l’option **Modifier** (pour plus d’informations, consultez [Modifier Visual Studio](../install/modify-visual-studio.md)). Si Visual Studio n’est pas encore installé, consultez [Installer Visual Studio](../install/install-visual-studio.md). Sous Windows 7, vérifiez que votre programme d’installation est à jour et affiche la version *15.2 build 26430.12* de Visual Studio 2017 ou une version ultérieure.

1. Sélectionnez la charge de travail **Applications de science et analyse des données** :

    ![Applications de science et analyse des données dans VS2017](media/installation-data-science-workload.png)

1. Définissez toute option supplémentaire à droite sous le même nom de charge de travail. Par défaut, cette charge de travail prend en charge F# et Python. Pour R, la configuration minimale requiert **Prise en charge du langage R**, **Prise en charge du runtime pour les outils de développement R** et **Microsoft R Client**.

RTVS est installé dans : *% ProgramFiles (x86)% \ Microsoft Visual Studio \<version> \<edition> Common7\IDE\Extensions\Microsoft\R Tools pour Visual Studio* où *\<version>* est généralement `2017` et *\<edition>* est `Community` , `Professional` ou `Enterprise` .

## <a name="install-rtvs-in-visual-studio-2015"></a>Installer RTVS dans Visual Studio 2015

Si vous utilisez Visual Studio 2015, vous devez installer Outils R et un interpréteur R séparément.

### <a name="install-an-r-interpreter"></a>Installer un interpréteur R

RTVS nécessite une installation 64 bits de R version 3.2.1 ou ultérieure à partir d’une ou plusieurs des sources suivantes :

- [Microsoft R Open](https://mran.microsoft.com/download/)
- [Microsoft R Client](/machine-learning-server/r-client/what-is-microsoft-r-client)
- [CRAN R](https://cran.r-project.org/bin/windows/base/)

Microsoft R Open et CRAN R autorisent tous deux plusieurs versions côte à côte. Microsoft R Client, cependant, ne prend en charge qu’une version et utilise toujours la plus récente que vous avez installée.

### <a name="install-the-r-tools"></a>Installer Outils R

Téléchargez le RTVS actuel pour Visual Studio 2015 à partir de [https://rtvs.blob.core.windows.net/download/RTVS_2017-12-18.1.exe](https://rtvs.blob.core.windows.net/download/RTVS_2017-12-18.1.exe) . RTVS recherche une version appropriée de Visual Studio et vous aide à installer un interpréteur R si vous ne l’avez pas déjà fait.

> [!Note]
> Le programme d’installation de RTVS autonome fonctionne uniquement avec Visual Studio 2015 ; avec Visual Studio 2017. Installez la prise en charge de R via la [charge de travail Applications de science et analyse des données](#install-rtvs-in-visual-studio-2017) comme décrit précédemment.

RTVS pour Visual Studio 2015 est installé dans : `%ProgramFiles(x86)%\Microsoft Visual Studio 14\Common7\IDE\Extensions\Microsoft\R Tools for Visual Studio`

## <a name="offline-installation-of-visual-studio-and-rtvs"></a>Installation hors connexion de Visual Studio et de RTVS

Effectuez une installation hors connexion si les ordinateurs ne sont pas connectés à Internet :

1. Accédez à [Créer une installation hors connexion de Visual Studio 2017](../install/create-an-offline-installation-of-visual-studio.md).

1. Si vous utilisez Visual Studio 2015, sélectionnez **2015** dans le sélecteur au-dessus de la table des matières.

1. Suivez les instructions de la page web pour créer une installation hors ligne.

1. Pour Visual Studio 2015, téléchargez les programmes d’installation RTVS hors connexion à partir de [https://rtvs.blob.core.windows.net/download/RTVS_2017-12-18.1.zip](https://rtvs.blob.core.windows.net/download/RTVS_2017-12-18.1.zip) et [https://rtvs.blob.core.windows.net/download/RTVS_Remote_2017-12-12.1.zip](https://rtvs.blob.core.windows.net/download/RTVS_Remote_2017-12-12.1.zip) .

1. Installez Visual Studio et RTVS à partir des programmes d’installation en mode hors connexion.

## <a name="see-also"></a>Voir aussi

- [Bien démarrer avec R](getting-started-with-r.md)
- [Exemples de projets Outils R](getting-started-samples.md)
- [Aide dans Outils R](getting-started-help.md)
- [Options de R Tools](options-for-r-tools-in-visual-studio.md)
- [Microsoft Machine Learning Server (anciennement R Server)](/machine-learning-server/)
