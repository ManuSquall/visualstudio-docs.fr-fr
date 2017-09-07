---
title: "Avantages de Visual Studio pour Mac par rapport à Xamarin Studio"
author: asb3993
ms.author: amburns
ms.date: 04/14/2017
ms.topic: article
ms.assetid: 6ACF5FD4-D5C1-4050-95E3-467C753F25F1
ms.translationtype: HT
ms.sourcegitcommit: f6c7e290f0abc2c32456e076420a7695ae868ba6
ms.openlocfilehash: 655795fd64958805e0137d7e231391c59f676776
ms.contentlocale: fr-fr
ms.lasthandoff: 09/07/2017

---

# <a name="benefits-of-visual-studio-for-mac-over-xamarin-studio"></a>Avantages de Visual Studio pour Mac par rapport à Xamarin Studio 
 
Visual Studio pour Mac a remplacé Xamarin Studio comme IDE complet sur Mac. Il fournit des fonctionnalités qui vous permettent de développer des applications et des services web, des applications multiplateformes mobiles et pour poste de travail, et des jeux. Il facilite aussi l’intégration à Azure, que ce soit pour publier sur Azure ou créer des fonctions Azure. Il offre tout ce que vous pouvez attendre d’un IDE moderne, notamment un éditeur de code source complet, un débogueur puissant, un espace de travail personnalisable, une intégration de Git et un système d’extensions riche, le tout conçu à l’origine pour le Mac. 

Parmi les autres fonctionnalités disponibles figurent : 

* IntelliSense, refactorisation, analyseurs et correctifs de code C# basés sur Roslyn 
* Gestion de packages NuGet 
* Format de projet compatible avec Visual Studio 
* Moteur de génération MSbuild 
* Tests unitaires intégrés 
* Prise en charge de F# prête à l’emploi 

Les avantages listés dans ce guide qui sont marqués en **Préversion** sont disponibles seulement dans le [canal Alpha](https://docs.microsoft.com/en-us/visualstudio/mac/update#Changing_the_Updater_channel). 

## <a name="language-support"></a>Prise en charge linguistique 

L’écriture de code C# 7 sur votre Mac est proposée seulement dans Visual Studio pour Mac.

## <a name="net-core"></a>.NET Core  

[.NET Core](https://www.microsoft.com/net/core#macos) est une plateforme de création d’applications qui s’exécutent sur Windows, Linux et Mac. Visual Studio pour Mac prend en charge le chargement, la création, l’exécution et le débogage de projets .NET Core. 

.NET Core est installé avec Visual Studio pour Mac et prêt à l’emploi.

La prise en charge de .NET Core inclut : 

* IntelliSense C# et F#. 
* Modèles de projet .NET Core pour applications console, bibliothèque et web. 
* Prise en charge complète du débogage, notamment des points d’arrêt, de la pile d’appels, de la fenêtre Espion, etc. 
* Références de package NuGet et restauration MSBuild. 
* Prise en charge des tests unitaires intégrés pour l’exécution et le débogage de tests avec la plateforme de test Visual Studio fournie avec le SDK .NET Core. 
* Migration depuis l’ancien format project.json. 
* Prise en charge des projets standard .NET.

## <a name="web-development"></a>Développement web  

### <a name="aspnet-core"></a>ASP.NET Core 

Visual Studio pour Mac comprend des modèles ASP.NET Core prêts à l’emploi pour les projets MVC et d’API web.
 
![IntelliSense HTML](media/benefits-vsmac-over-xs-image3.png)

Visual Studio pour Mac ajoute également la prise en charge de nouveaux outils web pour les fichiers HTML, CSS et JSON. 

### <a name="html"></a>HTML 

* Nouveau modèle HTML. 
* Amélioration du retrait intelligent et de la mise en forme. 
* Amélioration de la colorisation. 
* Amélioration d’IntelliSense. 
* Pliage de code (doit être activé). 
* Commande Unminify. 
* Amélioration des modèles de code (extraits). 
* Entourer la sélection avec `<div>`. 
* Option haut/bas déplaçant le texte vers le haut/bas. 

### <a name="css"></a>CSS 

* Amélioration du retrait intelligent et de la mise en forme. 
* Amélioration de la colorisation. 
* Amélioration d’IntelliSense. 
* Pliage de code. 
* Divers modèles de code (extraits). 
* Option haut/bas déplaçant le texte vers le haut/bas. 

### <a name="json"></a>JSON 
* Sélecteur de schéma avec accès à schemastore.org. 
* Validation à partir du schéma. 
* IntelliSense à partir du schéma. 
* Amélioration du retrait intelligent et de la mise en forme. 
* Amélioration de la colorisation. 
* Création/suppression de marques de commentaire. 
* Injection de guillemets et correspondance d’accolade. 
* Option haut/bas déplaçant le texte vers le haut/bas. 

## <a name="publishing-to-azure"></a>Publication sur Azure

Avec Visual Studio pour Mac, il est possible de publier vos applications et services web ASP.NET Core sur Azure App Service. 

![Publier sur Azure](media/benefits-vsmac-over-xs-image1.png)

### <a name="azure-functions-preview"></a>Azure Functions (**Préversion**)

Azure Functions est une solution qui vous permet d’exécuter facilement de petits blocs de code, ou « fonctions », dans le cloud. Visual Studio pour Mac vous permet de coder et de déboguer localement vos fonctions Azure. Pour démarrer, recherchez Azure Functions en dessous de Cloud dans la boîte de dialogue Nouveau projet. 

### <a name="docker-support-preview"></a>Prise en charge de Docker (**Préversion**)

Vous pouvez désormais publier des applications ASP.NET Core sur des conteneurs Docker et les exécuter à partir d’Azure App Service. 

Pour activer la prise en charge de Docker dans votre projet, cliquez avec le bouton droit sur votre application web ASP.NET Core et sélectionnez **Ajouter > Ajouter la prise en charge de Docker**. 

Pour publier votre application web sur un conteneur Docker, utilisez le workflow **Publier > Publier sur Azure** introduit dans Visual Studio pour Mac.

## <a name="source-editor-improvements"></a>Autres améliorations de l’éditeur de code source 

En plus d’IntelliSense, de la refactorisation, des analyseurs et des correctifs de code C# basés sur Roslyn, l’éditeur de code source de Visual Studio pour Mac offre les améliorations suivantes par rapport à Xamarin Studio : 

### <a name="language-bundles"></a>Bundles de langage 

Visual Studio pour Mac prend en charge les bundles de langage TextMate (`.tmBundle`) et Sublime Text 3 (`.sublime`), que vous pouvez utiliser pour ajouter les éléments suivants : 

* Thèmes de couleurs de l’éditeur 
* Extraits de code 
* Grammaires de nouveaux langages, avec la mise en surbrillance et des fonctionnalités IntelliSense de base. 

Vous pouvez ajouter des bundles de langage dans **Préférences > Éditeur de texte > Bundles de langage**. 

### <a name="color-theme-support"></a>Prise en charge des thèmes de couleurs 

Les formats des thèmes de couleurs suivants sont pris en charge dans Visual Studio pour Mac : 

* Visual Studio (`.vssettings`) 
* Xamarin Studio (`.json`) 
* TextMate (`tmTheme`) 

## <a name="unity"></a>Unity 

[Unity](https://unity3d.com/) est un outil de création de jeux que vous pouvez utiliser pour créer des jeux multiplateformes 2D et 3D de qualité pour toutes les plateformes principales : appareils mobiles, postes de travail, consoles, appareils de réalité augmentée et de réalité virtuelle, et même le web. 

À compter de Unity 5.6.1, vous pouvez utiliser Visual Studio pour Mac pour écrire et déboguer votre jeu Unity. Pour commencer, définissez Visual Studio comme éditeur de script de Unity 5.6.1. 

Les outils pour Unity incluent : 

* Prise en charge des scripts écrits en C#. 
* Panneau de solutions Unity. 
* Débogage en un clic de l’éditeur Unity. 
* IntelliSense pour les messages Unity. 
* Colorisation du code pour les nuanceurs de Unity. 
* Accès à la documentation Unity. 

## <a name="xamarin"></a>Xamarin 

Bien que les fonctionnalités multiplateformes de Xamarin aient toujours été un atout majeur de Xamarin Studio, certaines fonctionnalités de Xamarin sont disponibles uniquement dans Visual Studio pour Mac. 

### <a name="android"></a>Android 

* [Android SDK manager](https://developer.xamarin.com/guides/android/application_fundamentals/using-the-sdk-manager/)  
* Android O est pris en charge seulement dans Visual Studio pour Mac, pas dans Xamarin Studio 

### <a name="ios-and-mac"></a>iOS et Mac 

* [Mises à jour du flux de travail de signature iOS](https://developer.xamarin.com/guides/cross-platform/macios/apple-account-management/) 
    * Création d’identités de signature et installation de celles-ci dans le trousseau local. 
    * Création de profils d’approvisionnement. 
    * Ajout d’une identité de signature à un profil existant.
    *  Approvisionnement d’appareils : inscrivez un appareil dans le portail des développeurs Apple et ajoutez-le à un profil d’approvisionnement.
* iOS 11, watchOS 4 et tvOS 2 seront pris en charge seulement dans Visual Studio pour Mac, pas dans Xamarin Studio 
* MacOS High Sierra sera pris en charge seulement dans Visual Studio pour Mac, pas dans Xamarin Studio 

### <a name="cross-platform"></a>Multiplateforme 

* [Xamarin Live Player](https://developer.xamarin.com/guides/cross-platform/live/) (**Préversion**) 
* [Xamarin IoT](https://developer.xamarin.com/guides/cross-platform/iot/) (**Préversion**) 
 
