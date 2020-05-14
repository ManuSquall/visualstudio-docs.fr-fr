---
title: Projets multitargeting
description: Ce document donne un aperçu de la façon d’installer des projets multi-ciblés dans Visual Studio pour Mac.
ms.topic: overview
author: jmatthiesen
ms.author: jomatthi
ms.date: 12/12/2019
ms.assetid: 2a561af4-f1fe-493e-9a53-aa6d77d15498
ms.openlocfilehash: 3d1372ab5bd08ce164352293ec9d341ca567e3d5
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/20/2020
ms.locfileid: "75451439"
---
# <a name="projects-with-multiple-target-frameworks"></a>Projets avec de multiples cadres cibles
Dans Visual Studio pour Mac, vous pouvez configurer un projet Xamarin ou .NET Core pour fonctionner sur l’une des nombreuses versions du cadre .NET, et sur l’une des plates-formes système. Par exemple, vous pouvez cibler un projet à exécuter à la fois sur .NET Framework 4.6 et .NET Core 3.1. 

Pour plus d’informations sur les frameworks cibles, consultez [Frameworks cibles](/dotnet/standard/frameworks).

> [!NOTE] 
> Cette rubrique s’applique à Visual Studio pour Mac. Pour Visual Studio sur Windows, voir [Aperçu du ciblage du Cadre](/visualstudio/ide/visual-studio-multi-targeting-overview).

## <a name="targeting-multiple-frameworks"></a>Cibler plusieurs cadres

Les cadres cibles sont spécifiés dans votre fichier de projet, que vous pouvez modifier en cliquant à droite sur votre projet et en choisissant la commande **Tools > Edit File.** Quand vous spécifiez un framework cible unique, utilisez l’élément TargetFramework. Le fichier de projet d’application de console suivant montre comment cibler .NET Core 3.0 :

```XML
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp3.0</TargetFramework>
  </PropertyGroup>

</Project>
```

Utilisez l’élément Pluriel TargetFrameworks avec plusieurs cadres cibles :

```XML
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TargetFrameworks>netstandard1.4;net40;net45</TargetFrameworks>
  </PropertyGroup>
```

En savoir plus sur la façon de [cibler plusieurs cadres](/dotnet/standard/frameworks#how-to-specify-target-frameworks).

## <a name="working-with-code-in-a-multi-target-project"></a>Travailler avec le code dans un projet multi-cible
Lorsque vous modifiez un fichier Cmd dans un projet doté de plusieurs cadres cibles, vous pouvez spécifier le cadre cible que vous souhaitez utiliser pour guider l’expérience de votre éditeur (par exemple, en montrant des avertissements si vous utilisez une API non prise en charge par ce cadre). Vous pouvez modifier le cadre cible en utilisant le sélecteur **du cadre cible** dans le coin supérieur gauche de la fenêtre de l’éditeur.

![Utilisation du sélecteur de cadre cible pour modifier le cadre cible, situé en haut de la fenêtre de l’éditeur](media/project-multitargeting-framework-selector.png)

Parfois, vous devez appeler différentes API en fonction de la plate-forme que votre application cible. Pour ce faire, vous pouvez écrire du code conditionnel pour compiler du code pour une plate-forme spécifique :

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

Lors de la rédaction du code, vous verrez des avertissements dans les suggestions d’auto-achèvement IntelliSense, vous permettant de savoir si des API spécifiques sont manquants pour l’un des cadres cibles que votre application prend en charge.

![Un message d’avertissement montré dans IntelliSense, une API ne fonctionnera pas pour un cadre cible spécifié. Exemple de texte: namespace System.Buffers, SharedUtils (netstandard2.0) - Non disponible. Vous pouvez utiliser la barre de navigation pour changer de contexte.](media/project-multitargeting-intellisense-warnings.png)

## <a name="see-also"></a>Voir aussi

- [Aperçu du ciblage du cadre (Windows)](/visualstudio/ide/visual-studio-multi-targeting-overview)
- [Cadres cibles dans les projets de type SDK](/dotnet/standard/frameworks#how-to-specify-target-frameworks)
