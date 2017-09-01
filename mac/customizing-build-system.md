---
title: "Personnalisation du système de génération"
description: 
author: asb3993
ms.author: amburns
ms.date: 04/14/2017
ms.topic: article
ms.assetid: 6958B102-8527-4B40-BC65-3505DB63F9D3
ms.translationtype: HT
ms.sourcegitcommit: e2b7ff9126e1cc38ac2e58d6be339b656a024e7f
ms.openlocfilehash: c261dbc285da6f488e6a328c997e2a9563c1c73a
ms.contentlocale: fr-fr
ms.lasthandoff: 08/11/2017

---

# <a name="customizing-the-build-system"></a>Personnalisation du système de génération

MSBuild est un moteur de génération, développé par Microsoft, qui permet de générer principalement des applications .NET. Le framework Mono a également sa propre implémentation du moteur de génération de Microsoft, appelée **xbuild**. Cependant, xbuild a été supprimé en faveur de l’utilisation de MSBuild sur tous les systèmes d’exploitation.

**MSbuild** est principalement utilisé comme système de génération des projets dans Visual Studio pour Mac. 

MSBuild fonctionne en prenant un ensemble d’entrées, comme des fichiers sources, et les transforme en sorties, comme des fichiers exécutables, et réalise ces sorties en appelant des outils, comme le compilateur. 


## <a name="msbuild-file"></a>Fichier MSBuild

MSBuild utilise un fichier XML, appelé fichier projet, qui définit les *éléments* qui font partie de votre projet (par exemple des ressources d’image) et les *propriétés* nécessaires pour générer votre projet. Ce fichier projet a toujours une extension de fichier se terminant par `proj`, par exemple `.csproj` pour les projets C#. 

### <a name="viewing-the-msbuild-file"></a>Affichage du fichier MSBuild
Vous pouvez rechercher ce fichier en cliquant sur le nom de votre projet et en sélectionnant **Afficher dans le Finder**. Ceci affiche tous les fichiers et dossiers associés à votre projet, notamment le fichier `.csproj`, comme illustré ci-dessous :

![](media/customizing-build-system-image1.png)

Vous pouvez également afficher le fichier `.csproj` dans un nouvel onglet de Visual Studio pour Mac en cliquant sur le nom de votre projet et en accédant à **Outils > Modifier le fichier** :

![](media/customizing-build-system-image2.png)

### <a name="composition-of-the-msbuild-file"></a>Composition du fichier MSBuild

Tous les fichiers MSBuild contiennent un élément racine `Project` obligatoire, comme indiqué ci-dessous :

```
<?xml version="1.0" encoding="utf-8"?>
<Project ToolsVersion="14.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
</Project>
```

En général, le projet importe aussi un fichier `.targets`, qui contient la plupart des règles qui décrivent comment traiter et générer les différents fichiers. Cela figure généralement dans le bas de votre fichier `proj` et ressemble à ceci pour les projets C# :

```
<Import Project="$(MSBuildBinPath)\Microsoft.CSharp.targets" />
```

Le fichier .targets est un autre fichier MSBuild. Ce fichier contient le code MSBuild qui est réutilisable par plusieurs projets. Par exemple, le fichier `Microsoft.CSharp.targets`, qui se trouve dans un répertoire représenté par la propriété (ou variable) `MSBuildBinPath`, contient la logique de création des assemblys C# à partir des fichiers sources C#.

### <a name="items-and-properties"></a>Éléments et propriétés

Il existe deux types de données fondamentaux dans MSBuild : les *éléments* et les *propriétés*, qui sont expliqués plus en détail ci-dessous.

#### <a name="properties"></a>Propriétés

Les propriétés sont des paires clé/valeur, qui sont utilisées pour stocker les paramètres qui affectent la compilation, comme les options du compilateur.

Elles sont définies à l’aide d’un PropertyGroup et peuvent contenir un nombre quelconque de PropertiesGroups, qui peuvent eux-mêmes contenir un nombre quelconque de propriétés. 

Par exemple, le PropertyGroup pour une pour une application de console simple peut se présenter comme suit :

```
<PropertyGroup>
        <Configuration Condition=" '$(Configuration)' == '' ">Debug</Configuration>
        <Platform Condition=" '$(Platform)' == '' ">x86</Platform>
        <ProjectGuid>{E248730E-1393-43CC-9183-FFA42F63BE81}</ProjectGuid>
        <OutputType>Exe</OutputType>
        <RootNamespace>refactoring</RootNamespace>
        <AssemblyName>refactoring</AssemblyName>
        <TargetFrameworkVersion>v4.5</TargetFrameworkVersion>
    </PropertyGroup>
```

Les propriétés peuvent être référencées dans des expressions avec la syntaxe `$()`. Par exemple, `$(Foo)` sera évalué comme valeur de la propriété `Foo`. Si la propriété n’a pas été définie, elle est évaluée comme chaîne vide, sans provoquer d’erreur.

#### <a name="items"></a>Éléments

Les éléments offrent un moyen de traiter les entrées dans le système de génération sous formes de listes ou d’ensembles, et représentent en général des fichiers. Chaque élément a un *type*d’élément, une *spécification* d’élément et des *métadonnées* arbitraires facultatives. Notez que MSBuild ne travaille pas sur des éléments individuels, il prend tous les éléments d’un type donné, appelé un *ensemble* d’éléments.

Les éléments sont créés en déclarant un `ItemGroup`. Il peut y avoir un nombre quelconque d’ItemGroups, qui peuvent contenir un nombre quelconque d’éléments. 

Par exemple, l’extrait de code ci-dessous crée les écrans de lancement d’iOS. Ils sont du type `BundleResource`, avec comme spécification le chemin de l’image :

```
 <ItemGroup>
    <BundleResource Include="Resources\Default-568h%402x.png" />
    <BundleResource Include="Resources\Default%402x.png" />
    <BundleResource Include="Resources\Default.png" />
    <BundleResource Include="Resources\Default-Portrait.png" />
    <BundleResource Include="Resources\Default-Portrait%402x.png" />
    <BundleResource Include="Resources\Default-Landscape%402x.png" />
  </ItemGroup>
 ```
 
 Les ensembles d’éléments peuvent être référencés dans des expressions avec la syntaxe `@()`. Par exemple, `@(BundleResource)` sera évalué comme étant l’ensemble d’éléments BundleResource, ce qui signifie tous les éléments BundleResource. S’il n’existe aucun élément de ce type, il sera vide, sans provoquer d’erreur.

## <a name="resources-for-learning-msbuild"></a>Ressources pour l’apprentissage de MSBuild

Les ressources suivantes peuvent être utilisées pour obtenir plus d’informations sur MSBuild :

* [MSDN - Vue d’ensemble](https://msdn.microsoft.com/en-us/library/dd393574.aspx)
* [MSDN - Concepts](https://msdn.microsoft.com/en-us/library/dd637714.aspx)



