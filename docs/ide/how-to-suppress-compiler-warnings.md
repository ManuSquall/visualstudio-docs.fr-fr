---
title: Supprimer les avertissements pour les projets et les packages NuGet
description: Découvrez comment vous pouvez utiliser Visual Studio pour nettoyer un journal de génération en filtrant un ou plusieurs types d’avertissements du compilateur.
ms.custom: SEO-VS-2020
ms.date: 01/24/2018
ms.technology: vs-ide-compile
ms.topic: how-to
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: ab79521cfd4cc122fa398f88b56ca37e2f2673a1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99869178"
---
# <a name="how-to-suppress-compiler-warnings"></a>Guide pratique pour supprimer des avertissements du compilateur

Vous pouvez nettoyer un journal de génération en filtrant un ou plusieurs types d’avertissements du compilateur. Par exemple, vous souhaiterez peut-être passer en revue uniquement une partie de la sortie générée lorsque vous définissez le niveau de détail du journal de génération sur **normal**, **détaillé** ou **diagnostic**. Pour plus d’informations sur le niveau de détail, consultez [Guide pratique pour afficher, enregistrer et configurer des fichiers journaux de génération](../ide/how-to-view-save-and-configure-build-log-files.md).

## <a name="suppress-specific-warnings-for-visual-c-or-f"></a>Supprimer des avertissements spécifiques pour Visual C# ou F\#

Utilisez la page de propriétés **Générer** pour supprimer des avertissements spécifiques pour les projets C# et F#.

1. Dans l’**Explorateur de solutions**, choisissez le projet dans lequel vous souhaitez supprimer les avertissements.

1. Dans la barre de menus, choisissez **Afficher** les  >  **pages de propriétés**.

1. Choisissez la page **Générer**.

1. Dans la zone **Supprimer les avertissements**, spécifiez les codes d’erreur des avertissements que vous souhaitez supprimer, séparés par des points-virgules.

1. Régénérez la solution.

## <a name="suppress-specific-warnings-for-c"></a>Supprimer des avertissements spécifiques pour C++

Utilisez la page de propriétés **Propriétés de configuration** pour supprimer des avertissements spécifiques pour les projets C++.

1. Dans l’**Explorateur de solutions**, choisissez le projet ou fichier source dans lequel vous souhaitez supprimer les avertissements.

1. Dans la barre de menus, choisissez **Afficher** les  >  **pages de propriétés**.

1. Choisissez la catégorie **Propriétés de configuration**, la catégorie **C/C++**, puis la page **Avancé**.

1. Effectuez l’une des opérations suivantes :

    - Dans la zone **Désactivation des avertissements spécifiques**, spécifiez les codes d’erreur des avertissements que vous souhaitez supprimer, séparés par des points-virgules.

    - Dans la zone **Désactivation des avertissements spécifiques**, choisissez **Edition** pour afficher davantage d’options.

1. Choisissez le bouton **OK**, puis régénérez la solution.

## <a name="suppress-warnings-for-visual-basic"></a>Supprimer des avertissements pour Visual Basic

Vous pouvez masquer des avertissements spécifiques du compilateur pour Visual Basic en modifiant le fichier *. vbproj* du projet. Pour supprimer des avertissements par *catégorie*, vous pouvez utiliser la [page de propriétés Compiler](../ide/reference/compile-page-project-designer-visual-basic.md). Pour plus d’informations, consultez [Configurer des avertissements dans Visual Basic](../ide/configuring-warnings-in-visual-basic.md).

### <a name="to-suppress-specific-warnings-for-visual-basic"></a>Pour supprimer des avertissements spécifiques pour Visual Basic

Cet exemple montre comment modifier le fichier *.vbproj* pour supprimer des avertissements spécifiques du compilateur.

1. Dans l’**Explorateur de solutions**, choisissez le projet dans lequel vous souhaitez supprimer les avertissements.

1. Dans la barre de menus, choisissez **projet**  >  **décharger le projet**.

1. Dans l’**Explorateur de solutions**, ouvrez le menu contextuel (clic droit) du projet, puis choisissez **Modifier \<ProjectName>.vbproj**.

    Le fichier de projet XML s’ouvre dans l’éditeur de code.

1. Recherchez l’élément `<NoWarn>` pour la configuration de build utilisée pour la génération, et ajoutez un ou plusieurs numéros d’avertissement comme valeur de l’élément `<NoWarn>`. Si vous spécifiez plusieurs numéros d’avertissement, séparez-les par des virgules.

     L’exemple suivant montre l’élément `<NoWarn>` en gras pour la configuration de build *Debug* sur une plateforme x86, avec deux avertissements du compilateur supprimés :

    ```xml
    <PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Debug|x86' ">
        <PlatformTarget>x86</PlatformTarget>
        <DebugSymbols>true</DebugSymbols>
        <DebugType>full</DebugType>
        <Optimize>false</Optimize>
        <OutputPath>bin\Debug\</OutputPath>
        <DefineDebug>true</DefineDebug>
        <DefineTrace>true</DefineTrace>
        <ErrorReport>prompt</ErrorReport>
        <NoWarn>40059,42024</NoWarn>
        <WarningLevel>1</WarningLevel>
      </PropertyGroup>
    ```

   > [!NOTE]
   > Les projets .NET Core ne contiennent pas de groupes de propriétés de configuration de build par défaut. Pour supprimer des avertissements d’un projet .NET Core, ajoutez manuellement la section de configuration de build au fichier. Par exemple :
   >
   > ```xml
   > <Project Sdk="Microsoft.NET.Sdk">
   >   <PropertyGroup>
   >     <OutputType>Exe</OutputType>
   >     <TargetFramework>netcoreapp2.0</TargetFramework>
   >     <RootNamespace>VBDotNetCore_1</RootNamespace>
   >   </PropertyGroup>
   >   <PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Debug|AnyCPU' ">
   >     <NoWarn>42016,41999,42017</NoWarn>
   >   </PropertyGroup>
   > </Project>
   > ```

1. Enregistrez les modifications apportées au fichier *.vbproj*.

1. Dans la barre de menus, **Choisissez projet**  >  **recharger le projet**.

1. Dans la barre de menus, choisissez **générer générer** la  >  **solution**.

    La fenêtre **Sortie** n’affiche plus les avertissements que vous avez spécifiés.

Pour plus d’informations, consultez l’[option du compilateur /nowarn](/dotnet/visual-basic/reference/command-line-compiler/nowarn) pour le compilateur de ligne de commande Visual Basic.

## <a name="suppress-warnings-for-nuget-packages"></a>Supprimer des avertissements pour les packages NuGet

Dans certains cas, il se peut que vous souhaitiez supprimer des avertissements du compilateur NuGet pour un seul package NuGet, et non pour un projet entier. L’avertissement a un objectif précis. Vous ne souhaitez donc pas le supprimer au niveau du projet. Par exemple, l’un des avertissements NuGet vous informe que le package peut ne pas être entièrement compatible avec votre projet. Si vous le supprimez au niveau du projet, puis ajoutez par la suite un autre package NuGet, vous ne saurez jamais si c’est ce dernier qui a généré l’avertissement de compatibilité.

### <a name="to-suppress-a-specific-warning-for-a-single-nuget-package"></a>Pour supprimer un avertissement spécifique pour un seul package NuGet

1. Dans **l’Explorateur de solutions**, sélectionnez le package NuGet pour lequel vous souhaitez supprimer les avertissements du compilateur.

   ![Package NuGet dans l’Explorateur de solutions](media/nuget-package-with-warning.png)

1. Dans le menu contextuel (clic droit), sélectionnez **Propriétés**.

1. Dans la zone **NoWarn** des propriétés du package, entrez le numéro d’avertissement à supprimer pour ce package. Si vous souhaitez supprimer plusieurs avertissements, utilisez une virgule pour séparer les numéros d’avertissement.

   ![Propriétés du package NuGet](media/nuget-properties-nowarn.png)

   L’avertissement disparaît de l’**Explorateur de solutions** et de la **liste d’erreurs**.

## <a name="see-also"></a>Voir aussi

- [Procédure pas à pas : Générer une application](../ide/walkthrough-building-an-application.md)
- [Comment : afficher, enregistrer et configurer des fichiers journaux de génération](../ide/how-to-view-save-and-configure-build-log-files.md)
- [Compiler et générer](../ide/compiling-and-building-in-visual-studio.md)
