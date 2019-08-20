---
title: Application web ASP.NET Core avec Entity Framework et Visual Studio 2019
titleSuffix: ''
description: Avant de créer une application web ASP.NET Core, découvrez comment installer Visual Studio 2019 avec ce tutoriel vidéo et des instructions détaillées.
ms.custom: get-started
ms.date: 03/31/2019
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
monikerRange: vs-2019
ms.topic: tutorial
ms.devlang: CSharp
author: ardalis
ms.author: tglee
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- aspnet
- dotnetcore
ms.openlocfilehash: 6668648668ab71e033d1341d71ecf5c7c2a47554
ms.sourcegitcommit: 117ece52507e86c957a5fd4f28d48a0057e1f581
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/28/2019
ms.locfileid: "66261721"
---
# <a name="tutorial-create-your-first-aspnet-core-app-using-entity-framework-with-visual-studio-2019"></a>Tutoriel : Créer une application ASP.NET Core à l’aide d’Entity Framework avec Visual Studio 2019

Ce tutoriel explique comment créer une application web ASP.NET Core qui utilise des données et la déployer sur Azure. Il se compose des étapes suivantes :

- [Étape 1 : Installer Visual Studio 2019](#step-1-install-visual-studio-2019)
- [Étape 2 : Créer une application web ASP.NET Core](tutorial-aspnet-core-ef-step-02.md)
- [Étape 3 : Travailler avec des données à l’aide d’Entity Framework](tutorial-aspnet-core-ef-step-03.md)
- [Étape 4 : Exposer une API web à partir d’une application ASP.NET Core](tutorial-aspnet-core-ef-step-04.md)
- [Étape 5 : Déployer une application ASP.NET Core sur Azure](tutorial-aspnet-core-ef-step-05.md)

## <a name="step-1-install-visual-studio-2019"></a>Étape 1 : Installer Visual Studio 2019

Découvrez comment installer Visual Studio 2019 avec ce tutoriel vidéo et des instructions détaillées. Si vous avez déjà installé Visual Studio, passez directement à [Étape 2 : Créer une application web ASP.NET Core](tutorial-aspnet-core-ef-step-02.md).

_Regardez cette vidéo et suivez les instructions pour installer Visual Studio et créer votre première application ASP.NET Core._

> [!VIDEO https://www.youtube.com/embed/Fz_HAqQGLtY]

## <a name="download-the-installer"></a>Télécharger le programme d’installation

Accédez à [visualstudio.com](https://visualstudio.com) pour trouver le programme d’installation. Recherchez le lien de Visual Studio 2019 et cliquez dessus pour lancer le téléchargement. Si vous souhaitez une version gratuite de Visual Studio, choisissez Visual Studio Community.

## <a name="start-the-installer"></a>Lancer le programme d’installation

Une fois le téléchargement terminé, cliquez sur **Exécuter** pour lancer le programme d’installation.

![Visual Studio 2019 Installer](media/vs-2019/vs2019-installer.png)

## <a name="choose-workloads"></a>Choisir les charges de travail

Visual Studio peut être utilisé dans différents contextes de développement ; les charges de travail permettent de télécharger facilement tout ce qu’il faut pour le type d’applications souhaité. Choisissez pour le moment les charges de travail **Développement ASP.NET et web** et **Développement multiplateforme .NET Core**. Vous pourrez toujours relancer le programme d’installation pour installer des composants et des charges de travail supplémentaires.

![Visual Studio 2019 – Choisir les charges de travail](media/vs-2019/vs2019-choose-workloads.png)

## <a name="install"></a>Installez

Cliquez sur **Installer** et laissez le programme d’installation télécharger et installer Visual Studio.

## <a name="run-visual-studio-for-the-first-time"></a>Exécuter Visual Studio la première fois

Visual Studio devrait se lancer automatiquement une fois l’installation terminée. Il peut vous être demandé de vous connecter, ce qui donne accès à quelques fonctionnalités intéressantes ; vous pouvez choisir de le faire plus tard. Ensuite, vous pouvez choisir vos paramètres de thème et de développement. Vous pourrez alors commencer votre premier projet. Cliquez sur **Créer un projet**, puis choisissez **Application web ASP.NET Core**.

![Visual Studio 2019 – Créer un projet d’application web ASP.NET Core](media/vs-2019/vs2019-create-new-project.png)

## <a name="explore-aspnet-core-project-types"></a>Explorer les types de projets ASP.NET Core

Vous pouvez choisir le nom et l’emplacement de votre projet, puis sélectionner **Créer**. Sélectionnez le modèle à utiliser pour votre application ASP.NET Core. Vous pouvez choisir parmi les options suivantes :

- Vide : modèle de projet vide permettant de partir de zéro.
- API : modèle idéal pour les API web.
- Application web : application web ASP.NET Core standard conçue avec Razor Pages.
- Application web (modèle-vue-contrôleur) : application web ASP.NET Core standard suivant le modèle modèle-vue-contrôleur.
- Angular.
- React.js.
- React.js/Redux.
- Bibliothèque de classes Razor : modèle utilisé pour partager des ressources Razor entre projets.

Notez que, pour la plupart des modèles de projet, vous pouvez également choisir d’activer la prise en charge de Docker en cochant une case. Il est également possible d’ajouter la prise en charge de l’authentification en cliquant sur la bouton Modifier l’authentification. Plusieurs options sont disponibles :

- Aucune authentification.
- Comptes d’utilisateur individuels : comptes stockés dans une base de données locale ou Azure.
- Comptes professionnels ou scolaires : authentification avec Active Directory, Azure AD ou Office 365.
- Authentification Windows : authentification adaptée aux applications intranet.

Sélectionnez le modèle d’application web standard avec Aucune authentification et cliquez sur **OK**.

![Visual Studio 2019 – Choisir les options de projet ASP.NET Core](media/vs-2019/vs2019-choose-aspnetcore-project.png)

## <a name="next-steps"></a>Étapes suivantes

Dans la vidéo suivante, vous aborderez votre premier projet ASP.NET Core.

[Tutoriel : Créer une application web ASP.NET Core](tutorial-aspnet-core-ef-step-02.md)

## <a name="see-also"></a>Voir aussi

- [Tutoriel : Bien démarrer avec C# et ASP.NET Core](tutorial-aspnet-core.md) : tutoriel plus détaillé sans procédure pas à pas vidéo
