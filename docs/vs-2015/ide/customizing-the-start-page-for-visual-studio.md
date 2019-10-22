---
title: Personnalisation de la page de démarrage | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.startpage
- VS.StartPage.HowDoI
- vs.ToolsOptionsPages.Startup
helpviewer_keywords:
- Start Page [Visual Studio]
- customizing Start Page [Visual Studio]
- Visual Studio Start page
ms.assetid: 925d42eb-ec34-426e-ad81-19db8630e536
caps.latest.revision: 48
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f1c3dfb145e70665156c921cc9a6f740539bc4e6
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72665849"
---
# <a name="customizing-the-start-page-for-visual-studio"></a>Personnalisation de la page de démarrage pour Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous pouvez personnaliser la page de démarrage de Visual Studio de plusieurs façons standard, par exemple en affichant la boîte de dialogue **Ouvrir un projet** ou en ouvrant la solution chargée en dernier. Vous pouvez également afficher une page de démarrage personnalisée, qui est une page WAML WPF (Windows Presentation Foundation) qui s'exécute dans une fenêtre d'outil et peut exécuter des commandes internes à Visual Studio.

## <a name="customizing-the-default-start-page"></a>Personnalisation de la page de démarrage par défaut

1. Dans la barre de menus, sélectionnez **Outils**, **Options**.

2. Développez **Environnement**, puis choisissez **Démarrage**.

3. Dans la liste **Au démarrage**, choisissez l’élément de personnalisation souhaité.

## <a name="show-a-custom-start-page"></a>Afficher une page de démarrage personnalisée

1. Installez une page de démarrage personnalisée en procédant d'une des manières suivantes :

    - Installez-la à partir de la [Place de marché Visual Studio](https://marketplace.visualstudio.com/), d’un autre site web ou d’une page sur votre intranet local.

        > [!NOTE]
        > Si vous aimez une page ciblée pour une version antérieure de Visual Studio, vous pouvez mettre à niveau cette page à l'aide du Kit de développement logiciel Visual Studio. Consultez [Guide pratique pour mettre à niveau une page de démarrage personnalisée Visual Studio](../misc/how-to-upgrade-a-visual-studio-custom-start-page.md).

         Ouvrez un fichier .vsix contenant une page de démarrage personnalisée ou effectuez un copier-coller des fichiers de la page de démarrage dans le dossier **%USERPROFILE% \My Documents\Visual Studio 2015\StartPages** sur votre ordinateur.

    - Créez votre propre page de démarrage si vous avez installé le kit SDK Visual Studio.

         Consultez [Création de votre propre page de démarrage](../misc/creating-your-own-start-page.md).

2. Dans la barre de menus, sélectionnez **Outils**, **Options**.

3. Développez **Environnement**, puis choisissez **Démarrage**.

4. Dans la liste **Personnaliser la page de démarrage**, choisissez la page que vous souhaitez.

> [!NOTE]
> Si une erreur dans une page de démarrage personnalisée provoque le blocage de Visual Studio, vous pouvez démarrer Visual Studio en mode sans erreur, puis le configurer pour utiliser la page de démarrage par défaut. Consultez [/SafeMode (devenv.exe)](../ide/reference/safemode-devenv-exe.md).

## <a name="see-also"></a>Voir aussi
 [Personnalisation des paramètres de développement dans Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3) [Création de votre propre page de démarrage](../misc/creating-your-own-start-page.md)
