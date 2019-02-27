---
title: Mettre à jour une application existante vers MSBuild 15 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 39a6316265b6b3747f247890d45a769ef9240387
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56596023"
---
# <a name="update-an-existing-application-for-msbuild-15"></a>Mettre à jour une application existante vers MSBuild 15

Dans les versions de MSBuild antérieures à la version 15.0, MSBuild était chargé à partir du GAC (Global Assembly Cache), et les extensions MSBuild étaient installées dans le Registre. Ainsi, toutes les applications utilisaient la même version de MSBuild et avaient accès aux mêmes ensembles d’outils. Cela empêchait par ailleurs les installations côte à côte de différentes versions de Visual Studio.

Pour permettre la prise en charge d’installations côte à côte, plus rapides et plus petites, Visual Studio 2017 ne place plus MSBuild dans le GAC et ne modifie plus le Registre. Malheureusement, cela signifie que les applications qui souhaitent utiliser l’API MSBuild pour évaluer ou générer des projets ne peuvent pas reposer implicitement sur l’installation de Visual Studio.

## <a name="use-msbuild-from-visual-studio"></a>Utiliser MSBuild à partir de Visual Studio

Pour que les builds programmatiques de votre application correspondent à celles effectuées dans Visual Studio ou *MSBuild.exe*, chargez les assemblys MSBuild à partir de Visual Studio et utilisez les kits SDK disponibles dans Visual Studio. Le package NuGet Microsoft.Build.Locator simplifie ce processus.

## <a name="use-microsoftbuildlocator"></a>Utiliser Microsoft.Build.Locator

Si vous redistribuez *Microsoft.Build.Locator.dll* avec votre application, vous n’aurez pas besoin de distribuer d’autres assemblys MSBuild.

La mise à jour d’un projet pour utiliser MSBuild 15 et l’API de localisateur nécessite l’ajout de quelques changements dans votre projet, comme indiqué ci-dessous. Pour voir un exemple de changements nécessaires à la mise à jour d’un projet, consultez [les validations apportées à un exemple de projet dans le dépôt MSBuildLocator](https://github.com/Microsoft/MSBuildLocator/commits/example-updating-to-msbuild-15).

### <a name="change-msbuild-references"></a>Changer les références à MSBuild

Pour que MSBuild se charge à partir d’un emplacement central, ne distribuez pas ses assemblys avec votre application.

Le mécanisme de modification du projet dans le but d’éviter de charger MSBuild à partir d’un emplacement central dépend de la référence à MSBuild.

#### <a name="use-nuget-packages-preferred"></a>Utiliser des packages NuGet (recommandé)

Ces instructions supposent d’utiliser des [références NuGet de type PackageReference](https://docs.microsoft.com/nuget/consume-packages/package-references-in-project-files).

Changez vos fichiers projet pour référencer les assemblys MSBuild à partir de leurs packages NuGet. Spécifiez `ExcludeAssets=runtime` pour indiquer à NuGet que les assemblys ne sont nécessaires qu’au moment de la génération et qu’ils ne doivent pas être copiés dans le répertoire de sortie.

Les versions majeure et mineure des packages MSBuild doivent être inférieures ou égales à la version minimale de Visual Studio à prendre en charge. Si vous souhaitez assurer la prise en charge d’une version de Visual Studio 2017, référencez la version de package `15.1.548`.

Par exemple, utilisez le code XML suivant :

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.Build" Version="15.1.548" ExcludeAssets="runtime" />
  <PackageReference Include="Microsoft.Build.Utilities" Version="15.1.548" ExcludeAssets="runtime" />
</ItemGroup>
```

#### <a name="use-extension-assemblies"></a>Utiliser des assemblys d’extension

Si vous ne pouvez pas utiliser de packages NuGet, vous pouvez faire référence aux assemblys MSBuild distribués avec Visual Studio. Si vous faites directement référence à MSBuild, vérifiez qu’il n’est pas copié dans votre répertoire de sortie en affectant à `Copy Local` la valeur `False`. Dans le fichier projet, ce paramètre se présentera comme le code suivant :

```xml
    <Reference Include="Microsoft.Build, Version=15.1.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a, processorArchitecture=MSIL">
      <Private>False</Private>
    </Reference>
```

#### <a name="binding-redirects"></a>Redirections de liaison

Faites référence au package Microsoft.Build.Locator pour que votre application utilise automatiquement les redirections de liaison nécessaires de toutes les versions des assemblys MSBuild vers la version `15.1.0.0`.

### <a name="ensure-output-is-clean"></a>Vérifier la propreté de la sortie

Générez votre projet et inspectez le répertoire de sortie pour vérifier qu’il ne contient pas d’assemblys *Microsoft.Build.\*.dll* (à part *Microsoft.Build.Locator.dll*, ajouté à l’étape suivante).

### <a name="add-package-reference"></a>Ajouter une référence de package

Ajoutez une référence de package NuGet à [Microsoft.Build.Locator](https://www.nuget.org/packages/Microsoft.Build.Locator/).

```xml
    <PackageReference Include="Microsoft.Build.Locator">
      <Version>1.1.2</Version>
    </PackageReference>
```

### <a name="register-instance-before-calling-msbuild"></a>Inscrire l’instance avant d’appeler MSBuild

Ajoutez un appel à l’API de localisateur avant d’appeler une méthode qui utilise MSBuild.

Le moyen le plus simple d’ajouter l’appel à l’API Localisateur consiste à ajouter un appel à :

```csharp
MSBuildLocator.RegisterDefaults();
```

dans le code de démarrage de votre application.

Pour contrôler de manière plus précise le chargement de MSBuild, vous pouvez sélectionner un résultat de `MSBuildLocator.QueryVisualStudioInstances()` à passer à `MSBuildLocator.RegisterInstance()` manuellement, mais cela n’est généralement pas nécessaire.
