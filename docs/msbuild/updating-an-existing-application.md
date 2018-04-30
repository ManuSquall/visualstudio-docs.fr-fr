# <a name="updating-an-existing-application-for-msbuild-15"></a>Mise à jour d’une application existante pour MSBuild 15

Dans les versions de MSBuild antérieures à la version 15.0, MSBuild était chargé à partir du GAC (Global Assembly Cache), et les extensions MSBuild étaient installées dans le Registre. Ainsi, toutes les applications utilisaient la même version de MSBuild et avaient accès aux mêmes ensembles d’outils. De plus, cela empêchait les installations côte à côte de différentes versions de Visual Studio.

Pour permettre la prise en charge d’installations plus rapides, plus petites et côte à côte, Visual Studio 2017 ne place plus MSBuild dans le GAC et ne modifie plus le Registre. Malheureusement, cela signifie que les applications qui souhaitent utiliser l’API MSBuild pour évaluer ou générer des projets ne peuvent pas reposer implicitement sur l’installation de Visual Studio.

## <a name="using-msbuild-from-visual-studio"></a>Utilisation de MSBuild à partir de Visual Studio

Pour vérifier que les builds programmatiques de votre application correspondent à celles effectuées dans Visual Studio ou MSBuild.exe, chargez les assemblys MSBuild à partir de Visual Studio et utilisez les kits SDK disponibles dans Visual Studio. Utilisez le package NuGet Microsoft.Build.Locator pour vous simplifier la tâche.

## <a name="using-microsoftbuildlocator"></a>Utilisation de Microsoft.Build.Locator

Si vous redistribuez `Microsoft.Build.Locator.dll` avec votre application, vous n’avez pas besoin de distribuer d’autres assemblys MSBuild.

La mise à jour d’un projet pour utiliser MSBuild 15 et l’API de localisateur nécessite l’ajout de quelques changements dans votre projet, comme indiqué ci-dessous. Pour voir un exemple de changements nécessaires à la mise à jour d’un projet, consultez [les validations apportées à un exemple de projet dans le dépôt MSBuildLocator](https://github.com/Microsoft/MSBuildLocator/commits/example-updating-to-msbuild-15).

### <a name="change-msbuild-references"></a>Changer les références à MSBuild

Pour garantir le chargement de MSBuild à partir d’un emplacement central, ne distribuez pas ses assemblys avec votre application.

Le mécanisme permettant de changer votre projet pour éviter de charger MSBuild à partir d’un emplacement central dépend de la façon dont vous référencez MSBuild.

#### <a name="using-nuget-packages-preferred"></a>Utilisation de packages NuGet (recommandée)

Les instructions suivantes supposent que vous utilisez les [références NuGet de type `PackageReference`](https://docs.microsoft.com/en-us/nuget/consume-packages/package-references-in-project-files).

Changez vos fichiers projet pour référencer les assemblys MSBuild à partir de leurs packages NuGet. Spécifiez `ExcludeAssets=runtime` pour indiquer à NuGet que les assemblys sont nécessaires uniquement au moment de la génération, et qu’ils ne doivent pas être copiés dans le répertoire de sortie.

Les versions majeure et mineure des packages MSBuild doivent être inférieures ou égales à la version minimale de Visual Studio à prendre en charge. Si vous souhaitez assurer la prise en charge d’une version de Visual Studio 2017, référencez la version de package `15.1.548`.

Par exemple, utilisez le code XML suivant :

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.Build" Version="15.1.548" ExcludeAssets="runtime" />
  <PackageReference Include="Microsoft.Build.Utilities" Version="15.1.548" ExcludeAssets="runtime" />
</ItemGroup>
```

#### <a name="using-extension-assemblies"></a>Utilisation d’assemblys d’extension

Si vous ne pouvez pas utiliser de packages NuGet, référencez les assemblys MSBuild distribués avec Visual Studio. Si vous référencez MSBuild directement, vérifiez qu’il n’est pas copié dans votre répertoire de sortie en affectant à `Copy Local` la valeur `False`. Dans le fichier projet, cela donne ce qui suit :

```xml
    <Reference Include="Microsoft.Build, Version=15.1.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a, processorArchitecture=MSIL">
      <Private>False</Private>
    </Reference>
```

#### <a name="binding-redirects"></a>Redirections de liaison

En référençant le package Microsoft.Build.Locator, vous avez automatiquement la garantie que votre application utilise les redirections de liaison nécessaires de toutes les versions des assemblys MSBuild vers la version `15.1.0.0`.

### <a name="ensure-output-clean"></a>Vérifier la propreté de la sortie

Générez votre projet et inspectez le répertoire de sortie pour vérifier qu’il ne contient pas d’assemblys `Microsoft.Build.*.dll` (à part `Microsoft.Build.Locator.dll`, ajouté à l’étape suivante).

### <a name="add-package-reference"></a>Ajouter une référence de package

Ajoutez une référence de package NuGet à [Microsoft.Build.Locator](https://www.nuget.org/packages/Microsoft.Build.Locator/).

```xml
    <PackageReference Include="Microsoft.Build.Locator">
      <Version>1.0.7-preview-ge60d679b53</Version>
    </PackageReference>
```

### <a name="register-instance-before-calling-msbuild"></a>Inscrire l’instance avant d’appeler MSBuild

Ajoutez un appel à l’API de localisateur avant d’appeler une méthode qui utilise MSBuild.

Le moyen le plus simple d’y parvenir est d’ajouter un appel à

```c#
MSBuildLocator.RegisterDefaults();
```

dans le code de démarrage de votre application.

Pour contrôler de manière plus précise le chargement de MSBuild, vous pouvez sélectionner un résultat de `MSBuildLocator.QueryVisualStudioInstances()` à passer à `MSBuildLocator.RegisterInstance()` manuellement, mais cela n’est généralement pas nécessaire.
