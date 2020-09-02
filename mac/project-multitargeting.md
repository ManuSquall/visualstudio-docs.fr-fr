---
title: Projets de MULTICIBLAGE
description: Ce document fournit une vue d’ensemble de la configuration de projets multi-ciblés dans Visual Studio pour Mac.
ms.topic: overview
author: jmatthiesen
ms.author: jomatthi
ms.date: 12/12/2019
ms.assetid: 2a561af4-f1fe-493e-9a53-aa6d77d15498
ms.openlocfilehash: 3d1372ab5bd08ce164352293ec9d341ca567e3d5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75451439"
---
# <a name="projects-with-multiple-target-frameworks"></a>Projets avec plusieurs frameworks cibles
Dans Visual Studio pour Mac, vous pouvez configurer un projet Xamarin ou .NET Core pour qu’il s’exécute sur n’importe quelle version du .NET Framework et sur l’une des différentes plateformes système. Par exemple, vous pouvez cibler un projet pour qu’il s’exécute à la fois .NET Framework 4,6 et .NET Core 3,1. 

Pour plus d’informations sur les frameworks cibles, consultez [Frameworks cibles](/dotnet/standard/frameworks).

> [!NOTE] 
> Cette rubrique s’applique à Visual Studio pour Mac. Pour Visual Studio sur Windows, consultez [vue d’ensemble du ciblage](/visualstudio/ide/visual-studio-multi-targeting-overview)de l’infrastructure.

## <a name="targeting-multiple-frameworks"></a>Ciblage de plusieurs frameworks

Les frameworks cibles sont spécifiés dans votre fichier projet, que vous pouvez modifier en cliquant avec le bouton droit sur votre projet et en choisissant la commande **outils > modifier le fichier** . Quand vous spécifiez un framework cible unique, utilisez l’élément TargetFramework. Le fichier de projet d’application console suivant montre comment cibler .NET Core 3,0 :

```XML
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp3.0</TargetFramework>
  </PropertyGroup>

</Project>
```

Utilisez l’élément TargetFrameworks pluriel avec plusieurs frameworks cibles :

```XML
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TargetFrameworks>netstandard1.4;net40;net45</TargetFrameworks>
  </PropertyGroup>
```

En savoir plus sur la façon de [cibler plusieurs infrastructures](/dotnet/standard/frameworks#how-to-specify-target-frameworks).

## <a name="working-with-code-in-a-multi-target-project"></a>Utilisation du code dans un projet à plusieurs cibles
Lorsque vous modifiez un fichier C# dans un projet avec plusieurs frameworks cibles, vous pouvez spécifier la version cible de .NET Framework que vous souhaitez utiliser pour guider votre éditeur (par exemple, en indiquant des avertissements si vous utilisez une API non prise en charge par cette infrastructure). Vous pouvez modifier la version cible du .NET Framework en utilisant le sélecteur de **Framework cible** dans l’angle supérieur gauche de la fenêtre de l’éditeur.

![Utilisation du sélecteur de Framework cible pour modifier la version cible du .NET Framework, située en haut de la fenêtre de l’éditeur](media/project-multitargeting-framework-selector.png)

Parfois, vous devez appeler différentes API en fonction de la plateforme ciblée par votre application. Pour ce faire, vous pouvez écrire du code conditionnel pour compiler le code pour une plateforme spécifique :

```C#
public class MyClass
{
    static void Main()
    {
#if NET40
        Console.WriteLine("Target framework: .NET Framework 4.0");
#elif NET45  
        Console.WriteLine("Target framework: .NET Framework 4.5");
#else
        Console.WriteLine("Target framework: .NET Standard 1.4");
#endif
    }
}
```

Lors de l’écriture de code, vous verrez des avertissements dans les suggestions de saisie semi-automatique IntelliSense, ce qui vous permet de savoir si des API spécifiques sont manquantes pour l’une des infrastructures cibles prises en charge par votre application.

![Un message d’avertissement s’affiche dans IntelliSense. une API ne fonctionnera pas pour une version cible de .NET Framework spécifiée. Exemple de texte : espace de noms System. buffers, SharedUtils (netstandard 2.0)-non disponible. Vous pouvez utiliser la barre de navigation pour changer de contexte.](media/project-multitargeting-intellisense-warnings.png)

## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble du ciblage du Framework (Windows)](/visualstudio/ide/visual-studio-multi-targeting-overview)
- [Frameworks cibles dans les projets de style SDK](/dotnet/standard/frameworks#how-to-specify-target-frameworks)
