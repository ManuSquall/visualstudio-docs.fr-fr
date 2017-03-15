---
title: "Personnalisation de la page de d&#233;marrage pour Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.startpage"
  - "VS.StartPage.HowDoI"
  - "vs.ToolsOptionsPages.Startup"
helpviewer_keywords: 
  - "personnaliser la page de démarrage (Visual Studio)"
  - "page de démarrage (Visual Studio)"
  - "page de démarrage de Visual Studio"
ms.assetid: 925d42eb-ec34-426e-ad81-19db8630e536
caps.latest.revision: 45
caps.handback.revision: 45
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Personnalisation de la page de d&#233;marrage pour Visual Studio
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Vous pouvez personnaliser la page de démarrage de Visual Studio de plusieurs façons standard, par exemple en affichant la boîte de dialogue **Ouvrir un projet** ou en ouvrant la solution chargée en dernier.  Vous pouvez également afficher une page de démarrage personnalisée, qui est une page WAML WPF \(Windows Presentation Foundation\) qui s'exécute dans une fenêtre d'outil et peut exécuter des commandes internes à Visual Studio.  
  
## Personnalisation de la page de démarrage par défaut  
  
1.  Dans la barre de menus, sélectionnez **Outils**, **Options**.  
  
2.  Développez **Environnement**, puis choisissez **Démarrage**.  
  
3.  Dans la liste **Au démarrage**, choisissez l'élément de personnalisation souhaité.  
  
## Afficher une page de démarrage personnalisée  
  
1.  Installez une page de démarrage personnalisée en procédant d'une des manières suivantes :  
  
    -   Procédez à l'installation à partir de la [galerie Visual Studio](http://visualstudiogallery.msdn.microsoft.com/site/search?f%5B0%5D.Type=SearchText&f%5B0%5D.Value=start%20page), d'un autre site web ou d'une page de votre intranet local.  
  
        > [!NOTE]
        >  Si vous aimez une page ciblée pour une version antérieure de Visual Studio, vous pouvez mettre à niveau cette page à l'aide du Kit de développement logiciel Visual Studio.  Consultez [Procédure : mise à niveau d’une page de démarrage personnalisée Visual Studio](../Topic/How%20to:%20Upgrade%20a%20Visual%20Studio%20Custom%20Start%20Page.md).  
  
         Ouvrez un fichier .vsix contenant une page de démarrage personnalisée ou effectuez un copier\-coller des fichiers de la page de démarrage dans le dossier %USERPROFILE%\\Mes documents\\Visual Studio 2015\\StartPages sur votre ordinateur.  
  
    -   Créez votre propre page de démarrage si vous avez installé le Kit de développement logiciel Visual Studio.  
  
         Consultez [Création de votre propre page de démarrage](../misc/creating-your-own-start-page.md).  
  
2.  Dans la barre de menus, sélectionnez **Outils**, **Options**.  
  
3.  Développez **Environnement**, puis choisissez **Démarrage**.  
  
4.  Dans la liste **Personnaliser la page de démarrage**, choisissez la page que vous souhaitez.  
  
> [!NOTE]
>  Si une erreur dans une page de démarrage personnalisée provoque le blocage de Visual Studio, vous pouvez démarrer Visual Studio en mode sans erreur, puis le configurer pour utiliser la page de démarrage par défaut.  Consultez [\/SafeMode](../ide/reference/safemode-devenv-exe.md).  
  
## Voir aussi  
 [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/fr-fr/22c4debb-4e31-47a8-8f19-16f328d7dcd3)   
 [Création de votre propre page de démarrage](../misc/creating-your-own-start-page.md)