---
title: "Visual C++ pour le développement mobile multiplateforme | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- tgt-pltfrm-cross-plat
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: 0bb872d6-981b-4c96-9143-fcec5336bf0d
caps.latest.revision: 9
author: BrianPeek
ms.author: brpeek
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
translationtype: Human Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 591fc488e2a2801fd6acb6e065038d11aaa13b67
ms.lasthandoff: 02/22/2017

---
# <a name="visual-c-for-cross-platform-mobile-development"></a>Visual C++ pour le développement mobile multiplateforme
Vous pouvez générer des applications C++ natives pour les appareils iOS, Android et Windows et partager du code commun dans des bibliothèques pour iOS, Android et Windows en utilisant Visual C++ pour le développement mobile multiplateforme. Il s’agit d’une option disponible dans Visual Studio 2015 qui permet d’installer les kits SDK et les outils dont vous avez besoin pour le développement multiplateforme de bibliothèques partagées et d’applications natives. Une fois ceux-ci installés, vous pouvez utiliser Visual C++ pour créer du code qui s’exécute sur les appareils et plateformes iOS et Android, en plus de Windows, Windows Phone et Xbox.  
  
 Écrire du code pour plusieurs plateformes peut être contrariant. Si les principaux langages et outils de développement varient d’une plateforme à une autre (iOS, Android et Windows), toutes les plateformes prennent en charge l’écriture de code en C++. Il s’agit du dénominateur commun qui va vous permettre de réutiliser le code de base sur les différentes plateformes. Le code natif écrit en C++ peut s’avérer plus performant et plus résistant à l’ingénierie à rebours. La réutilisation de code peut vous faire gagner du temps et des efforts quand il s’agit de créer des applications pour plusieurs plateformes.  
  
 L’utilisation de Visual C++ pour le développement mobile multiplateforme présente plusieurs avantages :  
  
1.  **Une installation facile.** Le programme d’installation de Visual Studio procède à l’acquisition et à l’installation des outils et des kits SDK tiers dont vous avez besoin pour créer des applications ou des bibliothèques pour Android et iOS. La configuration et l’installation sont simples et pour l’essentiel automatiques.  
  
2.  **Un environnement de build puissant et familier.** : créez des solutions et des projets multiplateformes partageables en toute simplicité à l’aide de modèles Visual Studio. Gérez les propriétés de tous les projets au moyen d’une interface commune. Modifiez l’ensemble de votre code dans l’éditeur Visual Studio et tirez parti de la fonctionnalité IntelliSense multiplateforme intégrée pour finaliser le code et mettre en évidence les erreurs.  
  
3.  **Une expérience de débogage unifiée.** : à l’aide des outils de débogage de classe mondiale, vous pouvez examiner et parcourir le code C++ pas à pas sur toutes les plateformes, notamment les appareils et émulateurs Android, les simulateurs et appareils iOS, ainsi que les appareils et simulateurs Windows ou Windows Phone.  
  
## <a name="get-the-tools"></a>Se procurer les outils  
 Visual C++ pour le développement mobile multiplateforme est une option installable fournie avec Visual Studio 2015. Pour connaître les prérequis et obtenir les instructions d’installation, consultez [Installer Visual C++ pour le développement mobile multiplateforme](../cross-platform/install-visual-cpp-for-cross-platform-mobile-development.md). Pour créer du code pour iOS, vous avez aussi besoin d’un Mac et d’un compte développeur Apple iOS. Pour plus d’informations, consultez [Installer et configurer des outils de génération en utilisant iOS](../cross-platform/install-and-configure-tools-to-build-using-ios.md).  
  
## <a name="come-up-to-speed"></a>Une acclimatation rapide  
 Si vous êtes habitué aux environnements de développement Android ou iOS, nous tenons à votre disposition des supports qui faciliteront votre prise en main. Visual Studio est un environnement de développement expressif et efficace. Pour apprendre à l’utiliser, consultez [Prise en main pour les développeurs d’applications Android](https://msdn.microsoft.com/en-us/library/windows/apps/dn275875.aspx) ou [Prise en main pour les développeurs d’applications iOS](https://msdn.microsoft.com/en-us/library/windows/apps/xaml/jj657966.aspx). Ces rubriques vous présentent Visual Studio et les concepts nécessaires au développement d’applications multiplateformes pour Windows et Windows Phone. Pour vous lancer dans l’écriture de votre première application multiplateforme pour iOS et Android, consultez [Générer une application OpenGL ES sur Android et iOS](../cross-platform/build-an-opengl-es-application-on-android-and-ios.md).  
  
 Visual C++ pour le développement mobile multiplateforme comprend plusieurs modèles destinés à vous aider à vous lancer dans le développement d’applications :  
  
-   Application OpenGLES 2 (Android, iOS, Windows universel)  
  
     Crée une solution qui inclut un ensemble de projets pour générer une application Android Native Activity, une application iOS et une application Windows universelle, ainsi qu’une bibliothèque de code C++ partagée. Ces applications utilisent des bibliothèques spécifiques à la plateforme créées avec du code OpenGL ES C++ commun pour dessiner le même cube tournant dans chaque application. Vous devez inclure l’option Outils de développement d’applications Windows universelles quand vous installez Visual Studio pour utiliser ce modèle.  
  
-   Application Native Activity (Android)  
  
     Permet de créer une application OpenGL C++ complète sous forme de projet Android Native Activity.  
  
-   Application OpenGLES (Android, iOS)  
  
     Permet de créer une solution avec un jeu de projets pour créer à la fois une application Android Native Activity et une application iOS. Ces applications utilisent des bibliothèques spécifiques à la plateforme créées avec du code OpenGL ES C++ commun pour dessiner le même cube tournant dans chaque application.  
  
-   Bibliothèque partagée (Android, iOS)  
  
     Permet de créer une solution avec des projets pour créer un fichier de bibliothèque dynamique Android (.so) et un fichier de bibliothèque statique iOS (.a) en utilisant du code C++ commun dans un projet partagé.  
  
-   Application de base (Android, Ant)  
  
     Permet de créer un projet d’application Android « Hello, World » qui utilise uniquement du code source Java et le système de build Ant.  
  
-   Application de base (Android, Gradle)  
  
     Permet de créer un projet d’application Android « Hello, World » qui utilise uniquement du code source Java et le système de build Gradle.  
  
-   Bibliothèque de base (Android, Ant)  
  
     Permet de créer un projet de bibliothèque Android « Hello, World » qui utilise uniquement du code source Java et le système de build Ant.  
  
-   Bibliothèque de base (Android, Gradle)  
  
     Permet de créer un projet de bibliothèque Android « Hello, World » qui utilise uniquement du code source Java et le système de build Gradle.  
  
-   Bibliothèque partagée dynamique (Android)  
  
     Permet de créer un fichier de bibliothèque dynamique Android (.so) avec du code C++.  
  
-   Application OpenGLES 2 (iOS)  
  
     Crée une solution avec un ensemble de projets permettant de générer une application iOS OpenGL ES 2. L’application utilise une bibliothèque de code C++ OpenGL ES pour dessiner un cube en rotation dans une application iOS. Cette application peut être un bon point de départ pour découvrir comment importer des bibliothèques C++ dans votre application iOS.  
  
-   Bibliothèque statique (Android)  
  
     Permet de créer un projet pour confectionner une bibliothèque statique pour Android. Autant vous ne pouvez lier qu’une seule bibliothèque dynamique dans une application Android, autant vous pouvez lier autant de bibliothèques statiques que vous le souhaitez.  
  
-   Bibliothèque statique (iOS)  
  
     Permet de créer un projet pour confectionner une bibliothèque statique pour iOS.  
  
-   Projet Makefile (Android)  
  
     Permet de créer un wrapper de projets pour vos propres projets Makefile Android.  
  
## <a name="try-out-sample-code"></a>Essayer des exemples de code  
 Téléchargez des exemples qui montrent comment créer des bibliothèques de code partagées utilisables dans des applications Windows, Android et iOS et comment créer des applications Native Activity complètes pour Android. Pour démarrer, consultez [Exemples de développement mobile multiplateforme](../cross-platform/cross-platform-mobile-development-examples.md).  
  
## <a name="in-this-section"></a>Dans cette section  
  
1.  [Installer Visual C++ pour le développement mobile multiplateforme](../cross-platform/install-visual-cpp-for-cross-platform-mobile-development.md)  
  
2.  [Installer et configurer des outils de génération en utilisant iOS](../cross-platform/install-and-configure-tools-to-build-using-ios.md)  
  
3.  [Créer une application Android Native Activity](../cross-platform/create-an-android-native-activity-app.md)  
  
4.  [Générer une application OpenGL ES sur Android et iOS](../cross-platform/build-an-opengl-es-application-on-android-and-ios.md)  
  
5.  [Exemples de développement mobile multiplateforme](../cross-platform/cross-platform-mobile-development-examples.md)
