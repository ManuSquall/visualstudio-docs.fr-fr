---
title: "Visual&#160;C++ pour le d&#233;veloppement mobile multiplateforme | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "tgt-pltfrm-cross-plat"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: 0bb872d6-981b-4c96-9143-fcec5336bf0d
caps.latest.revision: 9
caps.handback.revision: 7
author: "BrianPeek"
ms.author: "brpeek"
manager: "ghogen"
---
# Visual&#160;C++ pour le d&#233;veloppement mobile multiplateforme
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Vous pouvez générer des applications C\+\+ natives pour les appareils Android et Windows et partager le code dans des bibliothèques pour iOS, Android et Windows en Visual C\+\+ pour le développement mobile multiplateforme. Il s’agit d’une option disponible dans Visual Studio 2015 qui permet d’installer les Kit de développement logiciel \(SDK\) et les outils dont vous avez besoin pour le développement multiplateforme de bibliothèques partagées et d’applications natives. Une fois ceux\-ci installés, vous pouvez utiliser Visual C\+\+ pour créer du code qui s’exécute sur les appareils et plateformes iOS et Android, en plus de Windows, Windows Phone et Xbox.  
  
 Écrire du code pour plusieurs plateformes peut être contrariant. Si les principaux langages et outils de développement varient d’une plateforme à une autre \(iOS, Android et Windows\), toutes les plateformes prennent en charge l’écriture de code en C\+\+. Il s’agit du dénominateur commun qui va vous permettre de réutiliser le code de base sur les différentes plateformes. Le code natif écrit en C\+\+ peut s’avérer plus performant et plus résistant à l’ingénierie à rebours. La réutilisation de code peut vous faire gagner du temps et des efforts quand il s’agit de créer des applications pour plusieurs plateformes.  
  
 L’utilisation de Visual C\+\+ pour le développement mobile multiplateforme présente plusieurs avantages :  
  
1.  **Un installation facile** : le programme d’installation de Visual Studio procède à l’acquisition et à l’installation des outils et Kit de développement logiciel \(SDK\) tiers dont vous avez besoin pour créer des applications ou des bibliothèques pour Android et iOS. La configuration et l’installation sont simples et pour l’essentiel automatiques.  
  
2.  **Un environnement de génération puissant et bien connu** : créez des solutions et des projets multiplateformes partageables en toute simplicité à l’aide de modèles Visual Studio. Gérez les propriétés de tous les projets au moyen d’une interface commune. Modifiez l’ensemble de votre code dans l’éditeur Visual Studio et tirez parti de la fonctionnalité IntelliSense multiplateforme intégrée pour finaliser le code et mettre en évidence les erreurs.  
  
3.  **Une expérience de débogage unifiée** : à l’aide des outils de débogage de classe mondiale, vous pouvez examiner et parcourir le code C\+\+ pas à pas sur toutes les plateformes, notamment les appareils et émulateurs Android, les simulateurs et appareils iOS, ainsi que les appareils et simulateurs Windows ou Windows Phone.  
  
## Se procurer les outils  
 Visual C\+\+ pour le développement mobile multiplateforme est une option installable fournie avec Visual Studio 2015. Pour connaître les conditions préalables et obtenir des instructions d’installation, consultez [Installer Visual C\+\+ pour le développement mobile multiplateforme](../cross-platform/install-visual-cpp-for-cross-platform-mobile-development.md). Pour créer du code pour iOS, vous avez aussi besoin d’un Mac et d’un compte développeur Apple iOS. Pour plus d’informations, consultez [Installer et configurer des outils de génération en utilisant iOS](../cross-platform/install-and-configure-tools-to-build-using-ios.md).  
  
## Une acclimatation rapide  
 Si vous êtes habitué aux environnements de développement Android ou iOS, nous tenons à votre disposition des supports qui faciliteront votre prise en main. Visual Studio est un environnement de développement expressif et efficace. Pour apprendre à l’utiliser, consultez [Prise en main pour les développeurs d’applications Android](https://msdn.microsoft.com/en-us/library/windows/apps/dn275875.aspx) ou [Prise en main pour les développeurs d’applications iOS](https://msdn.microsoft.com/en-us/library/windows/apps/xaml/jj657966.aspx). Ces rubriques vous présentent Visual Studio et les concepts nécessaires au développement d’applications multiplateformes pour Windows et Windows Phone. Pour vous lancer dans l’écriture de votre première application multiplateforme pour iOS et Android, consultez [Générer une application OpenGL ES sur Android et iOS](../cross-platform/build-an-opengl-es-application-on-android-and-ios.md).  
  
 Visual C\+\+ pour le développement mobile multiplateforme comprend plusieurs modèles destinés à vous aider à vous lancer dans le développement d’applications :  
  
-   Application Native Activity \(Android\)  
  
     Permet de créer une application OpenGL C\+\+ complète sous forme de projet Android Native Activity.  
  
-   Application OpenGLES \(Android, iOS\)  
  
     Permet de créer une solution avec un jeu de projets pour créer à la fois une application Android Native Activity et une application iOS. Ces applications utilisent des bibliothèques spécifiques à la plateforme créées avec du code OpenGL ES C\+\+ commun pour dessiner le même cube tournant dans chaque application.  
  
-   Bibliothèque partagée \(Android, iOS\)  
  
     Permet de créer une solution avec des projets pour créer un fichier de bibliothèque dynamique Android \(.so\) et un fichier de bibliothèque statique iOS \(.a\) en utilisant du code C\+\+ commun dans un projet partagé.  
  
-   Application de base \(Android\)  
  
     Permet de créer une application Android « Hello, World » qui utilise uniquement du code source Java.  
  
-   Bibliothèque partagée dynamique \(Android\)  
  
     Permet de créer un fichier de bibliothèque dynamique Android \(.so\) avec du code C\+\+.  
  
-   Projet de création de package vide \(iOS\)  
  
     Visual Studio peut héberger un projet d’application iOS à confectionner sur un Mac. Ce projet vide est le point de départ.  
  
-   Bibliothèque statique \(Android\)  
  
     Permet de créer un projet pour confectionner une bibliothèque statique pour Android. Autant vous ne pouvez lier qu’une seule bibliothèque dynamique dans une application Android, autant vous pouvez lier autant de bibliothèques statiques que vous le souhaitez.  
  
-   Bibliothèque statique \(iOS\)  
  
     Permet de créer un projet pour confectionner une bibliothèque statique pour iOS.  
  
-   Projet Makefile \(Android\)  
  
     Permet de créer un wrapper de projets pour vos propres projets Makefile Android.  
  
## Essayer des exemples de code  
 Téléchargez des exemples qui montrent comment créer des bibliothèques de code partagées utilisables dans des applications Windows, Android et iOS et comment créer des applications Native Activity complètes pour Android. Pour commencer, consultez [Exemples de développement mobile multiplateforme](../cross-platform/cross-platform-mobile-development-examples.md).  
  
## Dans cette section  
  
1.  [Installer Visual C\+\+ pour le développement mobile multiplateforme](../cross-platform/install-visual-cpp-for-cross-platform-mobile-development.md)  
  
2.  [Installer et configurer des outils de génération en utilisant iOS](../cross-platform/install-and-configure-tools-to-build-using-ios.md)  
  
3.  [Créer une application Android Native Activity](../cross-platform/create-an-android-native-activity-app.md)  
  
4.  [Générer une application OpenGL ES sur Android et iOS](../cross-platform/build-an-opengl-es-application-on-android-and-ios.md)  
  
5.  [Exemples de développement mobile multiplateforme](../cross-platform/cross-platform-mobile-development-examples.md)