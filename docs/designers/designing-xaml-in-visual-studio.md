---
title: "Conception XAML dans Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 288e2415-9fcf-408e-bc35-9848315e14fd
caps.latest.revision: 4
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Human Translation
ms.sourcegitcommit: 47057e9611b824c17077b9127f8d2f8b192d6eb8
ms.openlocfilehash: e832941dd00fa81bea1566f17504fe7e27c41a48
ms.contentlocale: fr-fr
ms.lasthandoff: 05/13/2017

---
# <a name="designing-xaml-in-visual-studio"></a>Conception XAML dans Visual Studio
Visual Studio et Blend pour Visual Studio fournissent tous deux des outils visuels conçus pour générer des interfaces utilisateur attrayantes et des expériences multimédias élaborées pour les applications de bureau Windows, web, [Windows Phone](http://msdn.microsoft.com/library/windowsphone/develop/jj683071.aspx)et [Windows Store](http://msdn.microsoft.com/library/windows/apps/jj129478.aspx) en XAML. Ils partagent tous les deux en commun des fenêtres de conception, des fenêtres Outil et un éditeur XAML. Toutefois, Blend pour Visual Studio propose des outils de conception supplémentaires conçus pour des tâches plus avancées telles que l'animation et les comportements.  
  
## <a name="choosing-the-right-tool"></a>Sélection de l'outil approprié  
 Votre sélection des outils de conception dépend en grande partie de vos compétences. Si vous êtes davantage orienté code, vous pouvez écrire du code XAML dans Visual Studio même pour accomplir des tâches de conception avancées. Si vous êtes plus orientée conception, Blend pour Visual Studio vous permet d'effectuer des tâches avancées sans écrire de code.  
  
 Vous pouvez basculer entre Visual Studio et Blend pour Visual Studio, et vous pouvez même ouvrir le même projet simultanément dans les deux environnements. Les modifications apportées aux fichiers XAML dans un environnement IDE peuvent être appliquées via le rechargement automatique quand vous basculez vers l'autre environnement IDE. Vous pouvez contrôler le comportement de rechargement via les options disponibles dans la boîte de dialogue **Outils**, **Options** de l'un ou l'autre environnement IDE.  
  
### <a name="shared-capabilities"></a>Fonctionnalités partagées  
 Pour la plupart des tâches de base, l'IDE de Visual Studio et l'IDE de Blend pour Visual Studio partagent le même ensemble de fenêtres et de fonctionnalités, avec quelques différences subtiles. Voici quelques points clés :  
  
-   **Une interface utilisateur cohérente :** vous pouvez concevoir vos applications dans le contexte familier de l'interface utilisateur de Visual Studio, ce qui rend le passage d'un IDE à un autre plus agréable et plus productif. Blend pour Visual Studio utilise le thème sombre de Visual Studio qui vous permet de vous concentrer sur le contenu que vous créez en améliorant le contraste entre le contenu et l'interface utilisateur. Consultez [Création d’une interface utilisateur à l’aide du concepteur XAML](../designers/creating-a-ui-by-using-xaml-designer-in-visual-studio.md).  
  
     ![Environnement IDE Blend pour Visual Studio](~/designers/media/blendide.png "BlendIDE")  
  
-   **XAML IntelliSense :** les deux IDE prennent en charge toutes les fonctionnalités courantes que vous pouvez attendre d'IntelliSense, notamment la saisie semi-automatique des instructions, la prise en charge des opérations courantes de l'éditeur telles que l'ajout de commentaires et la mise en forme de code, ainsi que la navigation des ressources, la liaison et le code.  
  
-   **Fonctionnalités de débogage de base :** vous pouvez maintenant déboguer dans Blend, notamment en définissant des points d'arrêt dans votre code afin de déboguer votre application en cours d'exécution. Pour maintenir une expérience de débogage cohérente avec Visual Studio, Blend pour Visual Studio inclut la plupart des fenêtres de débogage et barres d’outils de Visual Studio. Certaines fonctionnalités de débogage avancées, telles que les diagnostics et l'analyse du code, sont disponibles uniquement dans Visual Studio. Consultez [Debugging in Visual Studio](../debugger/debugging-in-visual-studio.md).  
  
-   **Expérience de rechargement de fichier :** vous pouvez modifier vos fichiers XAML dans Blend pour Visual Studio ou dans Visual Studio. Vos fichiers modifiés sont alors rechargés automatiquement quand vous passez de l'un à l'autre. Pour minimiser les interruptions de flux de travail, vous pouvez maintenant définir vos préférences de rechargement des fichiers dans la boîte de dialogue correspondante.  
  
     ![Expérience de rechargement de fichiers](~/designers/media/blendfilereload.png "BlendFileReload")  
  
-   **Dispositions et paramètres synchronisés :** les dispositions personnalisées vous permettent d'enregistrer et d'appliquer des personnalisations de disposition de fenêtre Outil. Visual Studio synchronise ces personnalisations et ces préférences à la fois pour Visual Studio et pour Blend pour Visual Studio sur différents ordinateurs lorsque vous vous connectez avec le même compte Microsoft. Consultez [Personnalisation des paramètres de développement dans Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
-   **Un Explorateur de solutions commun :** l'Explorateur de solutions vous offre une vue organisée de vos projets et de leurs fichiers, ainsi qu'un accès aux commandes qui s'y rapportent. Avec l'Explorateur de solutions, il est plus facile de travailler avec des grands projets d'entreprise. Consultez [Projets et solutions](../ide/solutions-and-projects-in-visual-studio.md).  
  
-   **Team Explorer :** Team Explorer vous permet de gérer vos projets avec les référentiels GIT ou TFS afin de faciliter la collaboration d'équipe. Consultez [Travailler dans Team Explorer](http://msdn.microsoft.com/Library/fd7a5cf7-7916-4fa0-b5e6-5a83cf377a02).  
  
-   **NuGet :** vous pouvez gérer les packages NuGet aussi bien dans Visual Studio que dans Blend pour Visual Studio. NuGet est un gestionnaire de package pour le .NET Framework qui simplifie l'installation et la suppression de packages d'une solution.  
  
## <a name="advanced-capabilities-in-blend-for-visual-studio"></a>Fonctionnalités avancées dans Blend pour Visual Studio  
 Pour accroître votre productivité, utilisez Blend pour Visual Studio pour les tâches suivantes. Il s'agit des domaines où Blend pur Visual Studio s'avère plus rapide et plus riche en fonctionnalités que le concepteur Visual Studio ou le code seul.  
  
|À|Visual Studio|Blend pour Visual Studio|Complément d'information|  
|--------|-------------------|-----------------------------|----------------------|  
|**Créer des animations**|Il n'existe aucun outil de conception d'animations ; vous devez les créer par programmation. Cela nécessite une bonne connaissance du système d'animation et de minutage de WPF, ainsi que des compétences étendues en matière de codage.|Vous créez les animations de manière visuelle et pouvez en afficher un aperçu dans Blend pour Visual Studio. Il s'agit d'une méthode plus rapide et plus précise que celle qui consiste à créer des animations dans le code. Vous pouvez ajouter des déclencheurs pour gérer l'interaction des utilisateurs et basculer vers le code pour ajouter des gestionnaires d'événements et d'autres fonctionnalités.|[Animer des objets](../designers/animate-objects-in-xaml-designer.md)|  
|**Transformer des formes et du texte en tracés pour une manipulation plus facile**|Non prise en charge.|Vous pouvez modifier les formes (telles que des rectangles et des ellipses) de manière subtile ou radicale en les convertissant en tracés, ce qui confère un meilleur contrôle d'édition.  Vous pouvez remodeler ou combiner des tracés et créer des tracés composites à partir de plusieurs formes.<br /><br /> Vous pouvez aussi convertir des blocs de texte en tracés pour les manipuler en tant qu'images vectorielles.|[Dessiner des formes et des tracés](../designers/draw-shapes-and-paths.md)|  
|**Ajouter de l’interactivité à vos conceptions d’interface utilisateur**|Nécessite du code C#, Visual Basic ou C++.|Glissez-déplacez des comportements vers des contrôles pour ajouter de l'interactivité à vos conceptions statiques. Les comportements sont des extraits de code prêts à l'emploi qui encapsulent des fonctionnalités, telles que le glisser-déplacer, le zoom et les changements d'état visuel. Vous avez le choix entre un ensemble croissant de comportements, et vous pouvez créer les vôtres.<br /><br /> Vous pouvez ensuite personnaliser chaque comportement en modifiant ses propriétés dans Blend pour Visual Studio ou en ajoutant des gestionnaires d'événements dans le code.|[Insérer des contrôles et modifier leur comportement](../designers/insert-controls-and-modify-their-behavior-in-xaml-designer.md)|  
|**Utiliser une illustration Adobe**|Non prise en charge.|Importez une conception graphique Adobe FXG, PhotoShop ou Illustrator, puis implémentez l'interface utilisateur dans Blend pour Visual Studio.|[Insérer des images, des vidéos et des clips audio](../designers/insert-images-videos-and-audio-clips-in-xaml-designer.md)|  
|**Modifier des contrôles, des modèles et des styles**|Nécessite du codage et une connaissance des styles et modèles WPF.|Transformez une image en contrôle.<br /><br /> Utilisez les outils d'édition de modèle pour apporter des modifications à des contrôles, styles et modèles en quelques clics de souris.<br /><br /> Par exemple, vous pouvez utiliser les ressources de style Blend pour Visual Studio pour implémenter des contrôles WPF courants (tels que des boutons, zones de liste, barres de défilement, menus, etc.) et modifier leur couleur, style ou modèle sous-jacent directement dans Blend pour Visual Studio. Vous pouvez ensuite basculer vers le code pour apporter des touches finales, le cas échéant.|[Modifier le style des objets](../designers/modify-the-style-of-objects-in-blend.md)|  
|**Connecter votre interface utilisateur à des données**|Vous pouvez créer une source de données à partir de ressources, telles que des bases de données SQL Server, des services WCF ou web, des objets ou des listes SharePoint, et lier la source de données aux contrôles de votre interface utilisateur.<br /><br /> Des données doivent être créées manuellement au moment de la conception pour une expérience de conception interactive.|Créez des exemples de données en toute simplicité à des fins de prototypage et de test. Passez à des données en direct dès que vous êtes prêt.<br /><br /> Les capacités de génération de données de Blend pour Visual Studio sont remarquables (vous pouvez facilement ajouter noms, nombres, URL et photos à la volée) et peuvent vous faire gagner beaucoup de temps.<br /><br /> Pour les données en direct, vous pouvez lier les contrôles de votre interface utilisateur à un fichier XML ou à une source de données CLR.|[Afficher des données](../designers/display-data-in-blend.md)|  
  
 Pour plus d'informations sur la conception XAML avancée, consultez [Création d’une interface utilisateur à l’aide de Blend pour Visual Studio](../designers/creating-a-ui-by-using-blend-for-visual-studio.md)
