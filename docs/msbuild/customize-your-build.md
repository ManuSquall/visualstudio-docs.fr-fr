---
title: Personnaliser votre build | Microsoft Docs
description: Découvrez plusieurs hooks d’extensibilité que vous pouvez utiliser pour personnaliser des projets MSBuild qui utilisent le processus de génération standard.
ms.custom: SEO-VS-2020
ms.date: 06/13/2019
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, transforms
- transforms [MSBuild]
ms.assetid: d0bceb3b-14fb-455c-805a-63acefa4b3ed
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 19dafcbb956634eeea5fa0ed967e93a8a8d5e546
ms.sourcegitcommit: 3fe04d5b931ae459a802a1b965f84186757cbc08
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2021
ms.locfileid: "111588447"
---
# <a name="customize-your-build"></a>Personnaliser votre build

Les projets MSBuild qui utilisent le processus de génération standard (importation de *Microsoft.Common.props* et *Microsoft.Common.targets*) ont plusieurs crochets d’extensibilité qui permettent de personnaliser le processus.

## <a name="add-arguments-to-command-line-msbuild-invocations-for-your-project"></a>Ajouter des arguments aux appels MSBuild en ligne de commande pour un projet

Un fichier *Directory.Build.rsp* dans ou au-dessus de votre répertoire source est appliqué aux générations à partir de la ligne de commande de votre projet. Pour plus d’informations, consultez [Fichiers réponse MSBuild](../msbuild/msbuild-response-files.md#directorybuildrsp).

## <a name="directorybuildprops-and-directorybuildtargets"></a>Directory.Build.props et Directory.Build.targets

Avant MSBuild version 15, si vous souhaitiez fournir une nouvelle propriété personnalisée aux projets de votre solution, vous deviez ajouter manuellement une référence à cette propriété pour chaque fichier projet de la solution. Ou bien, vous deviez définir la propriété dans un fichier *. props* , puis importer explicitement le fichier *. props* dans chaque projet de la solution, entre autres choses.

Maintenant, vous pouvez ajouter une nouvelle propriété à chaque projet en une seule étape en la définissant dans un seul fichier appelé *Directory.Build.props* dans le dossier racine contenant votre source. Lorsque MSBuild s’exécute, *Microsoft. Common. props* recherche le fichier *Directory. Build. props* dans votre structure de répertoires (et *Microsoft. Common. targets* recherche *Directory. Build. targets*). S’il en trouve un, il importe la propriété. *Directory. Build. props* est un fichier défini par l’utilisateur qui fournit des personnalisations aux projets situés dans un répertoire.

> [!NOTE]
> Les systèmes de fichiers Linux respectent la casse. Veillez à ce que la casse du nom de fichier Directory.Build.props corresponde exactement ; sinon, il ne sera pas détecté pendant le processus de build.
>
> Pour plus d’informations, voir [ce problème GitHub](https://github.com/dotnet/core/issues/1991#issue-368441031).

### <a name="directorybuildprops-example"></a>Exemple avec Directory.Build.props

Par exemple, si vous souhaitez permettre à l’ensemble de vos projets d’accéder à la nouvelle fonctionnalité Roslyn **/deterministic** (qui est exposée dans la cible `CoreCompile` de Roslyn par la propriété `$(Deterministic)`), vous pouvez procéder comme suit.

1. Créez un nouveau fichier à la racine de votre référentiel appelé *Directory.Build.props*.
2. Ajoutez le code XML suivant au fichier.

   ```xml
   <Project>
    <PropertyGroup>
      <Deterministic>true</Deterministic>
    </PropertyGroup>
   </Project>
   ```

3. Exécutez MSBuild. Les importations existantes de votre projet de *Microsoft.Common.props* et *Microsoft.Common.targets* trouvent le fichier et l’importent.

### <a name="search-scope"></a>Étendue de la recherche

Lorsque vous recherchez un fichier *Directory.Build.props*, MSBuild remonte dans la structure de répertoire par rapport à l’emplacement de votre projet (`$(MSBuildProjectFullPath)`) et s’arrête après avoir localisé un fichier *Directory.Build.props*. Par exemple, si votre `$(MSBuildProjectFullPath)` était *c:\users\username\code\test\case1*, MSBuild commencerait à rechercher ici, puis remonterait dans la structure de répertoire jusqu’à ce qu’il trouve un fichier *Directory.Build.props*, comme dans la structure de répertoire suivante.

```
c:\users\username\code\test\case1
c:\users\username\code\test
c:\users\username\code
c:\users\username
c:\users
c:\
```

L’emplacement du fichier solution est sans importance pour *Directory.Build.props*.

### <a name="import-order"></a>Ordre d’importation

*Directory.Build.props* est importé très tôt dans *Microsoft.Common.props* et les propriétés définies ultérieurement ne sont pas disponibles pour ce dernier. Par conséquent, évitez de faire référence aux propriétés qui ne sont pas encore définies (et qui seront évaluées comme vides).

Les propriétés définies dans *Directory. Build. props* peuvent être remplacées ailleurs dans le fichier projet ou dans les fichiers importés. vous devez donc considérer les paramètres dans *Directory. Build. props* comme en spécifiant les valeurs par défaut pour vos projets.

*Directory. Build. targets* est importé à partir de *Microsoft. Common. targets* après l’importation des fichiers *. targets* à partir des packages NuGet. Par conséquent, il peut substituer les propriétés et les cibles définies dans la plupart de la logique de génération, ou définir des propriétés pour tous vos projets, quel que soit l’ensemble des projets.

Lorsque vous devez définir une propriété ou définir une cible pour un projet individuel qui remplace les paramètres antérieurs, placez cette logique dans le fichier projet après l’importation finale. Pour effectuer cette opération dans un projet de type SDK, vous devez d’abord remplacer l’attribut de style SDK par les importations équivalentes. Consultez Guide pratique [pour utiliser des kits de développement logiciel (SDK) de projet MSBuild](how-to-use-project-sdk.md).

> [!NOTE]
> Le moteur MSBuild lit tous les fichiers importés pendant l’évaluation, avant de commencer l’exécution de la génération pour n’importe quel projet (y compris tout `PreBuildEvent` ), de sorte que ces fichiers ne sont pas censés être modifiés par le `PreBuildEvent` ou par une autre partie du processus de génération. Toutes les modifications ne prennent pas effet tant que l’appel suivant de *MSBuild.exe* ou la génération suivante de Visual Studio n’est pas effectué.

### <a name="use-case-multi-level-merging"></a>Cas d’utilisation : Fusion à plusieurs niveaux

Supposons que vous ayez la structure de solution standard suivante :

```
\
  MySolution.sln
  Directory.Build.props     (1)
  \src
    Directory.Build.props   (2-src)
    \Project1
    \Project2
  \test
    Directory.Build.props   (2-test)
    \Project1Tests
    \Project2Tests
```

Il peut être souhaitable d’avoir des propriétés communes pour tous les projets *(1)*, des propriétés communes pour les projets *src**(2-src)* et des propriétés communes pour les projets *test**(2-test)*.

Pour que MSBuild fusionne correctement les fichiers « internes » (*2-src* et *2-test*) avec le fichier « externe » (*1*), vous devez prendre en compte le fait qu’une fois que MSBuild a trouvé un fichier *Directory.Build.props*, il arrête l’analyse. Pour poursuivre l’analyse et fusionner les fichiers internes avec le fichier externe, placez ce code dans les deux fichiers internes :

`<Import Project="$([MSBuild]::GetPathOfFileAbove('Directory.Build.props', '$(MSBuildThisFileDirectory)../'))" />`

Voici un résumé de l’approche générale MSBuild :

- Pour un projet donné, MSBuild recherche le premier *Directory.Build.props* vers le haut de la structure de la solution, le fusionne avec les valeurs par défaut et arrête la recherche
- Si vous souhaitez que plusieurs niveaux soient recherchés et fusionnés, [`<Import...>`](../msbuild/property-functions.md#msbuild-getpathoffileabove) (voir ci-dessus) le fichier « externe » à partir du fichier « interne »
- Si le fichier « externe » n’importe pas également un élément situé au-dessus, la recherche s’arrête.
- Pour contrôler le processus de recherche et de fusion, utilisez `$(DirectoryBuildPropsPath)` et `$(ImportDirectoryBuildProps)`.

Ou plus simplement : MSBuild s’arrête au premier *Directory.Build.props* qui n’importe aucun élément.

### <a name="choose-between-adding-properties-to-a-props-or-targets-file"></a>Choisir entre l’ajout de propriétés dans un fichier .props ou .targets

MSBuild est dépend de l’ordre d’importation, et la dernière définition d’une propriété (ou d’une `UsingTask` ou d’une cible) est la définition utilisée.

Lorsque vous utilisez des importations explicites, vous pouvez importer à partir d’un fichier *.props* ou *.targets* à tout moment. Voici la convention la plus utilisée :

- Les fichiers *.props* sont importés au début de l’ordre d’importation.

- Les fichiers *.targets* sont importés à la fin de l’ordre de build.

Cette convention est appliquée par les importations `<Project Sdk="SdkName">` (autrement dit, l’importation de *Sdk.props* passe d’abord, avant tout le contenu du fichier, puis *Sdk.targets* vient en dernier, après tout le contenu du fichier).

Lorsque vous choisissez où placer les propriétés, utilisez les directives générales suivantes :

- Pour de nombreuses propriétés, peu importe où elles sont définies, elles ne sont pas remplacées et sont en lecture seule au moment de l’exécution.

- Pour un comportement qui peut être personnalisé dans un projet individuel, définissez des valeurs par défaut dans le fichier *.props*.

- Évitez de définir des propriétés dépendantes dans les fichiers *.props* en lisant la valeur d’une propriété éventuellement personnalisée, car la personnalisation ne se produira qu’une fois que MSBuild aura lu le projet de l’utilisateur.

- Définissez les propriétés dépendantes dans les fichiers *.targets*, car ils récupèrent les personnalisations à partir de projets individuels.

- Si vous avez besoin de remplacer les propriétés, faites-le dans un fichier *.targets*, une fois que toutes les personnalisations de projet de l’utilisateur ont eu l’occasion de prendre effet. Faites attention lors de l’utilisation de propriétés dérivées, car elles peuvent également être remplacées.

- Ajoutez des éléments dans les fichiers *.props* (conditionnés sur une propriété). Toutes les propriétés sont prises en compte avant n’importe quel élément, afin que les personnalisations de propriétés du projet de l’utilisateur soient récupérées, et cela donne au projet de l’utilisateur la possibilité de `Remove` ou `Update` n’importe quel élément introduit par l’importation.

- Définissez des cibles dans les fichiers *.targets*. Toutefois, si le fichier *.targets* est importé par un kit de développement logiciel (SDK), n’oubliez pas que ce scénario rend la substitution de la cible plus difficile, car le projet de l’utilisateur n’a pas un emplacement pour le remplacer par défaut.

- Si possible, préférez la personnalisation des propriétés au moment de l’évaluation à la modification des propriétés à l’intérieur d’une cible. Cette recommandation vous permettra de charger un projet et comprendre ce qu’il fait plus facilement.

## <a name="msbuildprojectextensionspath"></a>MSBuildProjectExtensionsPath

Par défaut, *Microsoft.Common.props* importe `$(MSBuildProjectExtensionsPath)$(MSBuildProjectFile).*.props` et *Microsoft.Common.targets* importe `$(MSBuildProjectExtensionsPath)$(MSBuildProjectFile).*.targets`. La valeur par défaut de `MSBuildProjectExtensionsPath` est `$(BaseIntermediateOutputPath)`, `obj/`. NuGet utilise ce mécanisme pour faire référence à la logique de génération fournie avec les packages ; autrement dit, au moment de la restauration, il crée les fichiers `{project}.nuget.g.props` qui font référence au contenu des packages.

Vous pouvez désactiver ce mécanisme d’extensibilité en définissant la propriété `ImportProjectExtensionProps` sur `false` dans un fichier *Directory.Build.props* ou avant d’importer *Microsoft.Common.props*.

> [!NOTE]
> La désactivation de MSBuildProjectExtensionsPath empêche d’appliquer à votre projet la logique de génération fournie dans les packages NuGet. Certains packages NuGet nécessitent la logique de génération pour effectuer leur fonction et sont rendus inutiles quand ce mécanisme est désactivé.

## <a name="user-file"></a>Fichier .user

*Microsoft.Common.CurrentVersion.targets* importe `$(MSBuildProjectFullPath).user` s’il existe, afin que vous puissiez créer un fichier à côté de votre projet avec cette extension supplémentaire. Pour les changements à long terme que vous envisagez d’archiver dans le contrôle de code source, préférez la modification du projet proprement dit, afin que les futurs responsables de la maintenance n’aient pas à connaître ce mécanisme d’extension.

## <a name="msbuildextensionspath-and-msbuilduserextensionspath"></a>MSBuildExtensionsPath et MSBuildUserExtensionsPath

> [!WARNING]
> L’utilisation de ces mécanismes d’extension rend très difficile la répétition de générations d’une machine à l’autre. Essayez d’utiliser une configuration qui puisse être archivée dans votre système de contrôle de code source et partagée entre tous les développeurs de votre code base.

Par convention, de nombreux fichiers de logique de génération de base importent

```xml
$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\{TargetFileName}\ImportBefore\*.targets
```

avant leur contenu, et

```xml
$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\{TargetFileName}\ImportAfter\*.targets
```

après. Avec cette convention, les kits SDK installés peuvent renforcer la logique de génération des types de projets courants.

La même structure de répertoires fait l’objet d’une recherche dans `$(MSBuildUserExtensionsPath)`, qui est le dossier par utilisateur *%LOCALAPPDATA%\Microsoft\MSBuild*. Les fichiers placés dans ce dossier sont importés pour toutes les générations du type de projet correspondant exécutées sous les informations d’identification de l’utilisateur concerné. Vous pouvez désactiver les extensions utilisateur en définissant les propriétés nommées d’après le fichier d’importation selon le modèle `ImportUserLocationsByWildcardBefore{ImportingFileNameWithNoDots}`. Par exemple, si vous définissez `ImportUserLocationsByWildcardBeforeMicrosoftCommonProps` avec la valeur `false`, vous empêchez l’importation de `$(MSBuildUserExtensionsPath)\$(MSBuildToolsVersion)\Imports\Microsoft.Common.props\ImportBefore\*`.

## <a name="customize-the-solution-build"></a>Personnaliser la génération de la solution

> [!IMPORTANT]
> La personnalisation de la génération de la solution de cette façon s’applique uniquement aux générations de ligne de commande avec *MSBuild.exe*. Elle **ne s’applique pas** aux générations à l’intérieur de Visual Studio. Pour cette raison, il n’est pas recommandé de mettre en place la personnalisation au niveau de la solution. Une meilleure solution pour personnaliser tous les projets dans une solution consiste à utiliser les fichiers *Directory. Build. props* et *Directory. Build. targets* dans le dossier de solution, comme indiqué ailleurs dans cet article.

Quand MSBuild génère un fichier solution, il le convertit en interne en fichier projet, puis génère ce dernier. Le fichier projet généré importe `before.{solutionname}.sln.targets` avant de définir des cibles et `after.{solutionname}.sln.targets` après avoir importé les cibles, notamment les cibles installées dans les répertoires `$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\SolutionFile\ImportBefore` et `$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\SolutionFile\ImportAfter`.

Par exemple, vous pouvez définir une nouvelle cible pour écrire un message de journal personnalisé après avoir généré *MyCustomizedSolution.sln* en créant un fichier dans le même répertoire que celui nommé *after.MyCustomizedSolution.sln.targets* qui contient

```xml
<Project>
 <Target Name="EmitCustomMessage" AfterTargets="Build">
   <Message Importance="High" Text="The solution has completed the Build target" />
 </Target>
</Project>
```

La génération de solution est distincte des générations de projet. les paramètres ici n’affectent donc pas les générations de projet.

## <a name="customize-all-net-builds"></a>Personnaliser toutes les builds .NET

Lors de la maintenance d’un serveur de builds, vous devrez peut-être configurer les paramètres MSBuild globalement pour toutes les builds sur le serveur.  En principe, vous pouvez modifier les fichiers globaux *Microsoft. Common. targets* ou *Microsoft. Common. props* , mais il existe un meilleur moyen de le faire. Vous pouvez affecter toutes les builds d’un certain type de projet (par exemple, tous les projets C#) en utilisant certaines propriétés MSBuild et en ajoutant certains `.targets` fichiers et personnalisés `.props` .

Pour affecter toutes les builds C# ou Visual Basic régies par une installation de MSBuild ou Visual Studio, créez un fichier *personnalisé. Before. Microsoft. Common. targets* ou *Custom. after. Microsoft. Common. targets* avec des cibles qui s’exécutent avant ou après *Microsoft. Common. targets*, ou un fichier *Custom. Before. Microsoft. Common. props* ou *Custom. after. Microsoft. Common. props* avec les propriétés qui seront traitées avant ou après *Microsoft. Common*

Vous pouvez spécifier les emplacements de ces fichiers à l’aide des propriétés MSBuild suivantes :

- CustomBeforeMicrosoftCommonProps
- CustomBeforeMicrosoftCommonTargets
- CustomAfterMicrosoftCommonProps
- CustomAfterMicrosoftCommonTargets
- CustomBeforeMicrosoftCSharpTargets
- CustomBeforeMicrosoftVisualBasicTargets
- CustomAfterMicrosoftCSharpTargets
- CustomAfterMicrosoftVisualBasicTargets

Les versions *courantes* de ces propriétés affectent à la fois les projets C# et Visual Basic. Vous pouvez définir ces propriétés dans la ligne de commande MSBuild.

```cmd
msbuild /p:CustomBeforeMicrosoftCommonTargets="C:\build\config\Custom.Before.Microsoft.Common.Targets" MyProject.csproj
```

La meilleure approche dépend de votre scénario. À l’aide de l’extensibilité Visual Studio, vous pouvez personnaliser le système de génération et fournir un mécanisme pour l’installation et la gestion des personnalisations.

Si vous disposez d’un serveur de builds dédié et que vous souhaitez vous assurer que certaines cibles s’exécutent toujours sur toutes les builds du type de projet approprié qui s’exécutent sur ce serveur, l’utilisation d’un fichier ou d’un fichier personnalisé global `.targets` `.props` est logique.  Si vous souhaitez que les cibles personnalisées s’exécutent uniquement lorsque certaines conditions s’appliquent, utilisez un autre emplacement de fichier et définissez le chemin d’accès à ce fichier en définissant la propriété MSBuild appropriée dans la ligne de commande MSBuild uniquement lorsque cela est nécessaire.

> [!WARNING]
> Visual Studio utilise le `.targets` ou les `.props` fichiers personnalisés s’il les trouve dans le dossier MSBuild chaque fois qu’il génère un projet du type correspondant. Cela peut avoir des conséquences inattendues et, si elle est effectuée de manière incorrecte, peut désactiver la génération de Visual Studio sur votre ordinateur.

## <a name="customize-c-builds"></a>Personnaliser les builds C++

Pour les projets C++, les fichiers *. targets* et *. props* personnalisés mentionnés précédemment ne peuvent pas être utilisés de la même manière pour remplacer les paramètres par défaut. *Directory. Build. props* est importé par *Microsoft. Common. props*, qui est importé dans, `Microsoft.Cpp.Default.props` tandis que la plupart des valeurs par défaut sont définies dans *Microsoft. cpp. props* et pour un certain nombre de propriétés, une condition « si pas encore défini » ne peut pas être utilisée, car la propriété est déjà définie, mais la valeur par défaut doit être différente pour les propriétés de projet spécifiques définies dans `PropertyGroup` avec `Label="Configuration"` (consultez [.](/cpp/build/reference/vcxproj-file-structure)

Toutefois, vous pouvez utiliser les propriétés suivantes pour spécifier le ou les fichiers *. props* à importer automatiquement avant/après *\* Microsoft. cpp.* Files :

- ForceImportAfterCppDefaultProps
- ForceImportBeforeCppProps
- ForceImportAfterCppProps
- ForceImportBeforeCppTargets
- ForceImportAfterCppTargets

Pour personnaliser les valeurs par défaut des propriétés pour toutes les builds C++, créez un autre fichier *. props* (par exemple, *MyProps. props*) et définissez la `ForceImportAfterCppProps` propriété en `Directory.Build.props` pointant sur celle-ci :

<PropertyGroup><ForceImportAfterCppProps>$ (MsbuildThisFileDirectory) \MyProps.props<ForceImportAfterCppProps>
</PropertyGroup>

*MyProps. props* sera automatiquement importé à la fin de *Microsoft. cpp. props*.

## <a name="customize-all-c-builds"></a>Personnaliser toutes les builds C++

La personnalisation de l’installation de Visual Studio n’est pas recommandée, car il n’est pas facile d’effectuer le suivi de ces personnalisations, mais si vous étendez Visual Studio pour personnaliser les builds C++ pour une plateforme particulière, vous pouvez créer `.targets` des fichiers pour chaque plateforme et les placer dans les dossiers d’importation appropriés pour ces plateformes dans le cadre d’une extension Visual Studio.

Le `.targets` fichier pour la plateforme Win32, *Microsoft. cpp. Win32. targets*, contient l' `Import` élément suivant :

```xml
<Import Project="$(VCTargetsPath)\Platforms\Win32\ImportBefore\*.targets"
        Condition="Exists('$(VCTargetsPath)\Platforms\Win32\ImportBefore')"
/>
```

Il y a un élément similaire près de la fin du même fichier :

```xml
<Import Project="$(VCTargetsPath)\Platforms\Win32\ImportAfter\*.targets"
        Condition="Exists('$(VCTargetsPath)\Platforms\Win32\ImportAfter')"
/>
```

Des éléments d’importation similaires existent pour d’autres plateformes cibles dans *%ProgramFiles32%\MSBuild\Microsoft.Cpp\v {version} \ plateformes \* .

Une fois que vous avez placé le `.targets` fichier dans le `ImportAfter` dossier approprié en fonction de la plateforme, MSBuild importe votre fichier dans chaque Build C++ pour cette plateforme. Vous pouvez y placer plusieurs `.targets` fichiers, si nécessaire. 

À l’aide de l’extensibilité Visual Studio, d’autres personnalisations sont possibles, telles que la définition d’une nouvelle plateforme. Pour plus d’informations, consultez [extensibilité de projet C++](../extensibility/visual-cpp-project-extensibility.md).

### <a name="specify-a-custom-import-on-the-command-line"></a>Spécifier une importation personnalisée sur la ligne de commande

Pour les `.targets` éléments personnalisés que vous souhaitez inclure pour une build spécifique d’un projet C++, définissez l’une des propriétés, ou les deux, `ForceImportBeforeCppTargets` et `ForceImportAfterCppTargets` sur la ligne de commande.

```cmd
msbuild /p:ForceImportBeforeCppTargets="C:\build\config\Custom.Before.Microsoft.Cpp.Targets" MyCppProject.vcxproj
```

Pour un paramètre global (pour affecter, par exemple, toutes les builds C++ pour une plateforme sur un serveur de builds), il existe deux méthodes. Tout d’abord, vous pouvez définir ces propriétés à l’aide d’une variable d’environnement système qui est toujours définie. Cela fonctionne parce que MSBuild lit toujours l’environnement et crée (ou remplace) des propriétés pour toutes les variables d’environnement.

## <a name="see-also"></a>Voir aussi

- [Concepts MSBuild](../msbuild/msbuild-concepts.md)

- [Informations de référence sur MSBuild](../msbuild/msbuild-reference.md)
