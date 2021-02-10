---
title: Guide pratique pour configurer des projets et cibler des plateformes
description: Découvrez comment Visual Studio vous permet de configurer vos applications pour cibler différentes plateformes, y compris les plateformes 64 bits.
ms.custom: SEO-VS-2020
ms.date: 08/16/2019
ms.technology: vs-ide-compile
ms.topic: how-to
helpviewer_keywords:
- project settings [Visual Studio], targeting platforms
- platforms, targeting specific CPUs
- project properties [Visual Studio], targeting platforms
- projects [Visual Studio], targeting platforms
- 64-bit [Visual Studio]
- 64-bit programming [Visual Studio]
- CPUs, targeting specific
- 64-bit applications [Visual Studio]
ms.assetid: 845302fc-273d-4f81-820a-7296ce91bd76
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f8a298f19f247c45740e87074804755f6ca691ec
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99969865"
---
# <a name="how-to-configure-projects-to-target-platforms"></a>Guide pratique pour configurer des projets et cibler des plateformes

Visual Studio vous permet de configurer vos applications pour cibler différentes plateformes, notamment des plateformes 64 bits. Pour plus d’informations sur la prise en charge de la plateforme 64 bits dans Visual Studio, consultez [applications 64 bits](/dotnet/framework/64-bit-apps).

## <a name="target-platforms-with-the-configuration-manager"></a>Cibler des plateformes avec le Gestionnaire de configurations

Le **Gestionnaire de configurations** vous permet d’ajouter rapidement une nouvelle plateforme à cibler avec votre projet. Si vous sélectionnez l'une des plateformes incluses avec Visual Studio, les propriétés de votre projet sont modifiées afin de générer votre projet pour la plateforme sélectionnée.

### <a name="to-configure-a-project-to-target-a-64-bit-platform"></a>Pour configurer un projet pour cibler une plateforme 64 bits

1. Dans la barre de menus, choisissez **générer**  >  **Configuration Manager**.

2. Dans la liste **Plateforme de la solution active**, choisissez une plateforme 64 bits pour la solution à cibler, puis choisissez le bouton **Fermer**.

    1. Si la plateforme souhaitée ne figure pas dans la liste **plateforme de la solution active** , choisissez **nouveau**.

         La boîte de dialogue **Nouvelle plateforme de solution** s’affiche.

    2. Dans la liste **Tapez ou sélectionnez la nouvelle plateforme**, choisissez **x64**.

        > [!NOTE]
        > Si vous affectez un nouveau nom à votre configuration, vous devrez peut-être modifier les paramètres dans le **Concepteur de projet** pour cibler la plateforme correcte.

    3. Si vous souhaitez copier les paramètres d’une configuration de plateforme actuelle, choisissez-la, puis choisissez le bouton **OK**.

Les propriétés de tous les projets qui ciblent la plateforme 64 bits sont mises à jour et la prochaine génération du projet est optimisée pour les plateformes 64 bits.

> [!NOTE]
> Le nom de la plateforme **Win32** est utilisé pour les projets C++, et cela signifie **x86**. Visual Studio prend en compte les plateformes au niveau du projet et les plateformes de niveau solution, et les plateformes de projet proviennent des systèmes de projet spécifiques au langage. Les projets C++ utilisent **Win32** et **x64**, mais les plateformes de solution utilisent **x86** et **x64**. Quand vous choisissez **x86** comme configuration de solution, Visual Studio sélectionne la plateforme **Win32** pour les projets C++. Pour afficher à la fois les paramètres de plateforme de niveau projet et de plateforme au niveau de la solution, ouvrez **Configuration Manager** et notez les deux paramètres de plateforme. La plateforme au niveau de la solution est présentée dans la liste déroulante plateforme de la **solution active** , et le tableau indique la plateforme au niveau du projet pour chaque projet.
> ![Capture d’écran montrant la plateforme de la solution et la plateforme de projet](media/project-platform-win32.png)

## <a name="target-platforms-in-the-project-designer"></a>Cibler des plateformes dans le Concepteur de projet

Le **Concepteur de projet** permet également de cibler différentes plateformes pour votre projet. Si la sélection de l’une des plateformes incluses dans la liste affichée dans la boîte de dialogue **Nouvelle plateforme de solution** ne fonctionne pas pour votre solution, vous pouvez créer un nom de configuration personnalisée, puis en modifier les paramètres dans le **Concepteur de projet** pour cibler la plateforme appropriée.

L’exécution de cette tâche varie suivant le langage de programmation que vous utilisez. Pour plus d’informations, consultez les liens suivants :

- Pour les projets [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)], consultez [/platform (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/platform).

- Pour les projets [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)], consultez [Build, page du Concepteur de projet (C#)](../ide/reference/build-page-project-designer-csharp.md).

- Pour les projets [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)], consultez [/clr (compilation pour le Common Language Runtime)](/cpp/build/reference/clr-common-language-runtime-compilation).

## <a name="manually-editing-the-project-file"></a>Modification manuelle du fichier projet

Parfois, vous devez modifier manuellement le fichier projet pour une configuration personnalisée. C’est le cas quand vous avez des conditions qui ne peuvent pas être spécifiées dans l’IDE, comme dans l’exemple suivant comprenant deux références pour deux plateformes différentes.

### <a name="example-referencing-x86-and-x64-assemblies-and-dlls"></a>Exemple : référencement d’assemblys et de dll x86 et x64

Vous pouvez avoir les versions x86 et x64 d’un assembly ou d’une DLL .NET. Pour configurer votre projet de manière à utiliser ces références, ajoutez d’abord la référence, puis ouvrez le fichier projet et modifiez-le pour ajouter un `ItemGroup` avec une condition qui fait référence à la fois à la configuration et à la plateforme cible.  Par exemple, supposons que le binaire que vous référencez est ClassLibrary1 et qu’il existe des chemins différents pour les configurations Debug et Release, ainsi que des versions x86 et x64.  Ensuite, utilisez quatre éléments `ItemGroup` avec toutes les combinaisons de paramètres, comme suit :

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp2.0</TargetFramework>
    <Platforms>AnyCPU;x64;x86</Platforms>
  </PropertyGroup>

  <ItemGroup Condition=" '$(Configuration)|$(Platform)' == 'Debug|x64'">
    <Reference Include="ClassLibrary1">
      <HintPath>..\..\ClassLibrary1\ClassLibrary1\bin\x64\Debug\netstandard2.0\ClassLibrary1.dll</HintPath>
    </Reference>
  </ItemGroup>

  <ItemGroup Condition=" '$(Configuration)|$(Platform)' == 'Release|x64'">
    <Reference Include="ClassLibrary1">
      <HintPath>..\..\ClassLibrary1\ClassLibrary1\bin\x64\Release\netstandard2.0\ClassLibrary1.dll</HintPath>
    </Reference>
  </ItemGroup>

  <ItemGroup Condition=" '$(Configuration)|$(Platform)' == 'Debug|x86'">
    <Reference Include="ClassLibrary1">
      <HintPath>..\..\ClassLibrary1\ClassLibrary1\bin\x86\Debug\netstandard2.0\ClassLibrary1.dll</HintPath>
    </Reference>
  </ItemGroup>
  
  <ItemGroup Condition=" '$(Configuration)|$(Platform)' == 'Release|x86'">
    <Reference Include="ClassLibrary1">
      <HintPath>..\..\ClassLibrary1\ClassLibrary1\bin\x86\Release\netstandard2.0\ClassLibrary1.dll</HintPath>
    </Reference>
  </ItemGroup>
</Project>
```

::: moniker range="vs-2017"
> [!NOTE]
> Dans Visual Studio 2017, vous devez décharger le projet avant de pouvoir modifier le fichier projet. Pour décharger le projet, cliquez avec le bouton droit sur le nœud du projet, puis choisissez **Décharger le projet**. Quand vous avez terminé, enregistrez vos changements et rechargez le projet en cliquant avec le bouton droit sur le nœud du projet et en choisissant **Recharger le projet**.
::: moniker-end

Pour plus d’informations sur le fichier projet, consultez [Informations de référence sur le schéma de fichier de projet MSBuild](../msbuild/msbuild-project-file-schema-reference.md).

## <a name="see-also"></a>Voir aussi

- [Présentation des plateformes de build](../ide/understanding-build-platforms.md)
- [/platform (options du compilateur C#)](/dotnet/csharp/language-reference/compiler-options/platform-compiler-option)
- [Applications 64 bits](/dotnet/framework/64-bit-apps)
- [Prise en charge de l’IDE Visual Studio 64 bits](../ide/visual-studio-ide-64-bit-support.md)
- [Fonctionnement du fichier projet](/aspnet/web-forms/overview/deployment/web-deployment-in-the-enterprise/understanding-the-project-file)
