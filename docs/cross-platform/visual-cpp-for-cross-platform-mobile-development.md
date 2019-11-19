---
title: Développement mobile multiplateforme avec C++ | Microsoft Docs
ms.custom: ''
ms.date: 11/14/2019
ms.technology: vs-ide-mobile
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 0bb872d6-981b-4c96-9143-fcec5336bf0d
author: corob-msft
ms.author: corob
manager: jillfra
ms.workload:
- xplat-cplusplus
ms.openlocfilehash: bc4164ec405aed2941e807934ee8d66b7ae72504
ms.sourcegitcommit: ca3bb6db949f5e405f6ffe1afa5f430662c1173f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/15/2019
ms.locfileid: "74098980"
---
# <a name="cross-platform-mobile-development-with-c"></a>Développement mobile multiplateforme avec C++

Vous pouvez créer des C++ applications natives pour les appareils iOS, Android et Windows à l’aide des outils multiplateformes disponibles dans Visual Studio. Le **développement mobile C++ avec** est une charge de travail disponible dans le programme d’installation de Visual Studio. Il installe les kits de développement logiciel (SDK) et les outils dont vous avez besoin pour le développement multiplateforme de bibliothèques partagées et d’applications natives. Une fois l’installation terminée, vous pouvez C++ utiliser pour créer du code qui s’exécute sur les appareils et plateformes iOS et Android, Windows, Windows Store et Xbox.

L’écriture de code pour plusieurs plateformes est souvent frustrante. Si les principaux langages et outils de développement varient d’une plateforme à une autre (iOS, Android et Windows), toutes les plateformes prennent en charge l’écriture de code en C++. Il s’agit du dénominateur commun qui peut permettre la réutilisation du code de base entre les plateformes. Le code natif écrit en C++ peut s’avérer plus performant et plus résistant à l’ingénierie à rebours. La réutilisation de code peut vous faire gagner du temps et des efforts quand il s’agit de créer des applications pour plusieurs plateformes.

Le développement C++ à l’aide de pour le développement mobile multiplateforme présente plusieurs avantages :

- **Un installation facile** : le programme d’installation de Visual Studio procède à l’acquisition et à l’installation des outils et Kit de développement logiciel (SDK) tiers dont vous avez besoin pour créer des applications ou des bibliothèques pour Android et iOS. La configuration et l’installation sont simples et principalement automatiques.

- **Un environnement de génération puissant et bien connu** : créez des solutions et des projets multiplateformes partageables en toute simplicité à l’aide de modèles Visual Studio. Gérez les propriétés de tous les projets au moyen d’une interface commune. Modifiez l’ensemble de votre code dans l’éditeur Visual Studio et tirez parti de la fonctionnalité IntelliSense multiplateforme intégrée pour finaliser le code et mettre en évidence les erreurs.

- **Une expérience de débogage unifiée** Utilisez les outils de débogage de classe mondiale de Visual Studio pour regarder et parcourir C++ le code sur toutes les plateformes : appareils et émulateurs Android, simulateurs et appareils iOS, et appareils et émulateurs Windows ou Windows Store.

## <a name="get-the-tools"></a>Se procurer les outils

Le développement mobile C++ avec est une charge de travail pouvant être installée qui est fournie avec Visual Studio. Pour connaître les conditions préalables et les instructions d’installation, consultez [installer le développement C++mobile multiplateforme avec ](../cross-platform/install-visual-cpp-for-cross-platform-mobile-development.md). Pour créer du code pour iOS, vous avez aussi besoin d’un Mac et d’un compte développeur Apple iOS. Pour plus d’informations, consultez [Installer et configurer des outils de génération en utilisant iOS](../cross-platform/install-and-configure-tools-to-build-using-ios.md).

## <a name="come-up-to-speed"></a>Une acclimatation rapide

Si vous êtes habitué aux environnements de développement Android ou iOS, nous tenons à votre disposition des supports qui faciliteront votre prise en main. Visual Studio est un environnement de développement expressif et efficace. Pour apprendre à l’utiliser, consultez [Get started for Android developers](/previous-versions/windows/apps/dn275875\(v=win.10\)) ou [Get started for iOS developers](/previous-versions/windows/apps/jj657966\(v=win.10\)). Ces articles vous présentent Visual Studio et les concepts dont vous aurez besoin pour développer des applications multiplateformes pour Windows et Windows Store. Pour commencer à écrire votre première application multiplateforme pour iOS et Android, consultez [créer une application OpenGL es sur Android et iOS](../cross-platform/build-an-opengl-es-application-on-android-and-ios.md).

Le développement mobile avec C++ une charge de travail comprend plusieurs modèles pour vous aider à commencer à utiliser vos applications :

- Application Native Activity (Android)

  Permet de créer une application OpenGL C++ complète sous forme de projet Android Native Activity.

- Application OpenGLES (Android, iOS)

  Permet de créer une solution avec un jeu de projets pour créer à la fois une application Android Native Activity et une application iOS. Ces applications utilisent des bibliothèques spécifiques à la plateforme créées avec du code OpenGL ES C++ commun pour dessiner le même cube tournant dans chaque application.

- Bibliothèque partagée (Android, iOS)

  Permet de créer une solution avec des projets pour créer un fichier de bibliothèque dynamique Android (.so) et un fichier de bibliothèque statique iOS (.a) en utilisant du code C++ commun dans un projet partagé.

- Application de base (Android, Ant)

  Permet de créer un projet d’application Android « Hello, World » qui utilise uniquement du code source Java et le système de build Ant.

- Application de base (Android, Gradle)

  Permet de créer un projet d’application Android « Hello, World » qui utilise uniquement du code source Java et le système de build Gradle.

- Bibliothèque de base (Android, Ant)

  Permet de créer un projet de bibliothèque Android « Hello, World » qui utilise uniquement du code source Java et le système de build Ant.

- Bibliothèque de base (Android, Gradle)

  Permet de créer un projet de bibliothèque Android « Hello, World » qui utilise uniquement du code source Java et le système de build Gradle.

- Bibliothèque partagée dynamique (Android)

  Permet de créer un fichier de bibliothèque dynamique Android (.so) avec du code C++.

- Application OpenGLES 2 (iOS)

  Crée une solution avec un ensemble de projets permettant de générer une application iOS OpenGL ES 2. L’application utilise une bibliothèque de code C++ OpenGL ES pour dessiner un cube en rotation dans une application iOS. Cette application peut être un bon point de départ pour découvrir comment importer des bibliothèques C++ dans votre application iOS.

- Bibliothèque statique (Android)

  Permet de créer un projet pour confectionner une bibliothèque statique pour Android. Autant vous ne pouvez lier qu’une seule bibliothèque dynamique dans une application Android, autant vous pouvez lier autant de bibliothèques statiques que vous le souhaitez.

- Bibliothèque statique (iOS)

  Permet de créer un projet pour confectionner une bibliothèque statique pour iOS.

- Projet Makefile (Android)

  Permet de créer un wrapper de projets pour vos propres projets Makefile Android.

## <a name="try-out-sample-code"></a>Essayer des exemples de code

Téléchargez des exemples qui montrent comment créer des bibliothèques de code partagées que vous pouvez utiliser dans des applications Windows, Android et iOS. Et consultez des exemples de création d’applications Native Activity complètes pour Android. Pour démarrer, consultez [Exemples de développement mobile multiplateforme](../cross-platform/cross-platform-mobile-development-examples.md).

## <a name="see-also"></a>Voir aussi

[Installez le développement mobile multiplateforme avec C++ ](../cross-platform/install-visual-cpp-for-cross-platform-mobile-development.md) \
[Installer et configurer des outils de génération à l’aide d’iOS](../cross-platform/install-and-configure-tools-to-build-using-ios.md) \
[Créer une application Android Native activity](../cross-platform/create-an-android-native-activity-app.md) \
[Créer une application OpenGL es sur Android et iOS](../cross-platform/build-an-opengl-es-application-on-android-and-ios.md) \
[Exemples de développement mobile multiplateforme](../cross-platform/cross-platform-mobile-development-examples.md)
