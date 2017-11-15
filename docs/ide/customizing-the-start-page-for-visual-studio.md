---
title: "Personnaliser la page de démarrage de Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 02/01/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.startpage
- VS.StartPage.HowDoI
- vs.ToolsOptionsPages.Startup
helpviewer_keywords:
- Start Page [Visual Studio]
- customizing Start Page [Visual Studio]
- Visual Studio Start page
ms.assetid: 925d42eb-ec34-426e-ad81-19db8630e536
caps.latest.revision: "45"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 178c20c9c4c3af8f5252e70ca603cdf8f8335e52
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="customize-the-start-page-for-visual-studio"></a>Personnaliser la page de démarrage de Visual Studio
Vous pouvez personnaliser la page de démarrage de Visual Studio de plusieurs façons standard, par exemple en affichant la boîte de dialogue **Ouvrir un projet** ou en ouvrant la solution chargée en dernier. Vous pouvez également afficher une page de démarrage personnalisée, qui est une page WAML WPF (Windows Presentation Foundation) qui s'exécute dans une fenêtre d'outil et peut exécuter des commandes internes à Visual Studio.  

## <a name="customize-the-default-start-page"></a>Personnaliser la page de démarrage par défaut  

1.  Dans la barre de menus, sélectionnez **Outils**, **Options**.  

2.  Développez **Environnement**, puis choisissez **Démarrage**.  

3.  Dans la liste **Au démarrage**, choisissez l’élément de personnalisation souhaité.  

## <a name="show-a-custom-start-page"></a>Afficher une page de démarrage personnalisée  

1.  Installez une page de démarrage personnalisée en procédant d'une des manières suivantes :  

    -   Installez-la à partir de la [galerie Visual Studio](http://visualstudiogallery.msdn.microsoft.com/site/search?f%5B0%5D.Type=SearchText&f%5B0%5D.Value=start%20page), d’un autre site web ou d’une page sur votre intranet local.  

        Ouvrez un fichier .vsix contenant une page de démarrage personnalisée ou effectuez un copier-coller des fichiers de la page de démarrage dans le dossier **%USERPROFILE% \My Documents\Visual Studio 2017\StartPages** sur votre ordinateur.  

    -   Créez votre propre page de démarrage si vous avez installé le kit SDK Visual Studio.  

         Consultez [Création d’une page de démarrage personnalisée](../extensibility/creating-a-custom-start-page.md).  

2.  Dans la barre de menus, sélectionnez **Outils**, **Options**.  

3.  Développez **Environnement**, puis choisissez **Démarrage**.  

4.  Dans la liste **Personnaliser la page de démarrage**, choisissez la page que vous souhaitez.  

> [!NOTE]
>  Si une erreur dans une page de démarrage personnalisée provoque le blocage de Visual Studio, vous pouvez démarrer Visual Studio en mode sans erreur, puis le configurer pour utiliser la page de démarrage par défaut. Consultez [/SafeMode (devenv.exe)](../ide/reference/safemode-devenv-exe.md).  

## <a name="see-also"></a>Voir aussi  
 [Personnaliser l’IDE Visual Studio](../ide/personalizing-the-visual-studio-ide.md)   
