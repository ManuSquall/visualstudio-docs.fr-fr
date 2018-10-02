---
title: Personnalisation de la Page de démarrage pour Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
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
caps.latest.revision: 48
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 7bc8c27c98127bbbdfd7a1dddbab7124b8dc1d32
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47493930"
---
# <a name="customizing-the-start-page-for-visual-studio"></a>Personnalisation de la page de démarrage pour Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [personnaliser la Page de démarrage de Visual Studio](https://docs.microsoft.com/visualstudio/ide/customizing-the-start-page-for-visual-studio).  
  
Vous pouvez personnaliser la page de démarrage de Visual Studio de plusieurs façons standard, par exemple en affichant la boîte de dialogue **Ouvrir un projet** ou en ouvrant la solution chargée en dernier. Vous pouvez également afficher une page de démarrage personnalisée, qui est une page WAML WPF (Windows Presentation Foundation) qui s'exécute dans une fenêtre d'outil et peut exécuter des commandes internes à Visual Studio.  
  
## <a name="customizing-the-default-start-page"></a>Personnalisation de la page de démarrage par défaut  
  
1.  Dans la barre de menus, sélectionnez **Outils**, **Options**.  
  
2.  Développez **Environnement**, puis choisissez **Démarrage**.  
  
3.  Dans la liste **Au démarrage**, choisissez l’élément de personnalisation souhaité.  
  
## <a name="show-a-custom-start-page"></a>Afficher une page de démarrage personnalisée  
  
1.  Installez une page de démarrage personnalisée en procédant d'une des manières suivantes :  
  
    -   Installez-la à partir de la [galerie Visual Studio](http://visualstudiogallery.msdn.microsoft.com/site/search?f%5B0%5D.Type=SearchText&f%5B0%5D.Value=start%20page), d’un autre site web ou d’une page sur votre intranet local.  
  
        > [!NOTE]
        >  Si vous aimez une page ciblée pour une version antérieure de Visual Studio, vous pouvez mettre à niveau cette page à l'aide du Kit de développement logiciel Visual Studio. Consultez [Comment : mettre à niveau une Page de démarrage personnalisée Visual Studio](../misc/how-to-upgrade-a-visual-studio-custom-start-page.md).  
  
         Ouvrez un fichier .vsix contenant une page de démarrage personnalisée, ou copiez et collez les fichiers de page de démarrage dans le **% PROFIL_UTILISATEUR % documents\Visual Studio 2015\StartPages** dossier sur votre ordinateur.  
  
    -   Créez votre propre page de démarrage si vous avez installé le kit SDK Visual Studio.  
  
         Consultez [créer votre propre Page de démarrage](../misc/creating-your-own-start-page.md).  
  
2.  Dans la barre de menus, sélectionnez **Outils**, **Options**.  
  
3.  Développez **Environnement**, puis choisissez **Démarrage**.  
  
4.  Dans la liste **Personnaliser la page de démarrage**, choisissez la page que vous souhaitez.  
  
> [!NOTE]
>  Si une erreur dans une page de démarrage personnalisée provoque le blocage de Visual Studio, vous pouvez démarrer Visual Studio en mode sans erreur, puis le configurer pour utiliser la page de démarrage par défaut. Consultez [/SafeMode (devenv.exe)](../ide/reference/safemode-devenv-exe.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Personnalisation des paramètres de développement dans Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)   
 [Création de votre propre Page de démarrage](../misc/creating-your-own-start-page.md)



