---
title: Compiler et générer du code de machine à écrire à l’aide de NuGet
description: Apprenez à compiler et à créer une machine à écrire dans Visual Studio.
ms.date: 7/23/2020
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jillfra
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: 16ff335fdf8ca76889562cfd94807ec1adc516d2
ms.sourcegitcommit: 754133c68ad841f7d7962e0b7a575e133289d8a8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/09/2020
ms.locfileid: "91927924"
---
# <a name="compile-typescript-code-aspnet-core"></a>Compiler le code de la machine à écrire (ASP.NET Core)

Vous pouvez ajouter la prise en charge de la machine à écrire à vos projets à l’aide de la TypeScript SDK, disponible par défaut dans le programme d’installation de Visual Studio ou à l’aide du package NuGet. Pour les projets développés dans Visual Studio 2019, nous vous encourageons à utiliser NuGet NuGet pour une plus grande portabilité sur différents environnements et plateformes.

Pour les projets ASP.NET Core, une utilisation courante du package NuGet consiste à compiler la machine à écrire à l’aide du CLI .NET Core. À moins que vous ne modifiiez manuellement votre fichier projet pour importer des cibles de génération à partir d’une installation TypeScript SDK, le package NuGet est le seul moyen d’activer la compilation d’une machine à écrire à l’aide des commandes CLI .NET Core telles que `dotnet build` et `dotnet publish` . En outre, pour l' [intégration de MSBuild](https://www.staging-typescript.org/docs/handbook/compiler-options-in-msbuild.html) avec ASP.net Core et la machine à écrire, choisissez le package NuGet sur le package NPM.

## <a name="add-typescript-support-with-nuget"></a>Ajouter la prise en charge de la fonction de machine avec NuGet

[Le package NuGet dactylographié ajoute la](https://www.nuget.org/packages/Microsoft.TypeScript.MSBuild) prise en charge de la méthode de réécrire. lorsque le package NuGet pour TypeScript 3.2 (ou version ultérieure) est installé dans un projet, la version correspondante du service de langage TypeScript est chargée dans l’éditeur.

Si Visual Studio est installé, la node.exe regroupée avec elle est automatiquement récupérée par Visual Studio. Si vous n’avez pas Node.js installé, nous vous recommandons d’installer la version LTS à partir du site Web [Node.js](https://nodejs.org/en/download/) .

1. Ouvrez votre projet ASP.NET Core dans Visual Studio.

1. Dans Explorateur de solutions (volet droit). Cliquez avec le bouton droit sur le nœud du projet et choisissez **gérer les packages NuGet**. Sous l’onglet **Parcourir** , recherchez **Microsoft. dactylographié. MSBuild**, puis cliquez sur **installer** à droite pour installer le package.

   ![Ajouter un package NuGet](../javascript/media/aspnet-core-ts-nuget.png)

   Visual Studio ajoute le package NuGet sous le nœud **dépendances** dans Explorateur de solutions. La référence de package suivante est ajoutée à votre fichier *. csproj.

   ```xml
   <PackageReference Include="Microsoft.TypeScript.MSBuild" Version="3.9.7">
      <PrivateAssets>all</PrivateAssets>
      <IncludeAssets>runtime; build; native; contentfiles; analyzers; buildtransitive</IncludeAssets>
   </PackageReference>
   ```

1. Cliquez avec le bouton droit sur le nœud du projet et choisissez **ajouter > nouvel élément**. Choisissez le **fichier de configuration de la machine à écrire JSON**, puis cliquez sur **Ajouter**.

   Visual Studio ajoute le *tsconfig.jssur* le fichier à la racine du projet. Vous pouvez utiliser ce fichier pour [configurer les options](https://www.typescriptlang.org/docs/handbook/tsconfig-json.html) du compilateur de machine à écrire.

1. Ouvrez *tsconfig.jssur* et mettez à jour pour définir les options du compilateur de votre choix.

   Voici un exemple de *tsconfig.jssimple sur* un fichier.

   ```json
   {
     "compilerOptions": {
       "noImplicitAny": false,
       "noEmitOnError": true,
       "removeComments": false,
       "sourceMap": true,
       "target": "es5",
       "outDir": "wwwroot/js"
     },
     "include": [
       "scripts/**/*"
     ]
   }
   ```

   Dans cet exemple :
   - *include* indique au compilateur où rechercher les fichiers de machine à écrire (*. TS).
   - l’option *outDir* spécifie le dossier de sortie pour les fichiers JavaScript ordinaires qui sont transpiles par le compilateur de machine à écrire.
   - l’option *mappage* indique si le compilateur génère des fichiers *mappage* .

   La configuration précédente fournit uniquement une présentation de base de la configuration de la machine à écrire. Pour plus d’informations sur les autres options, consultez [tsconfig.jssur](https://www.typescriptlang.org/docs/handbook/tsconfig-json.html).

### <a name="build-the-application"></a>Créer l’application

1. Ajoutez des fichiers de machine à écrire (*. TS*) ou de jsx (*. TSX*) à votre projet, puis ajoutez le code de la machine à écrire. Pour obtenir un exemple simple de la méthode de machine à écrire, utilisez ce qui suit :

   ```typescript
   let message: string = 'Hello World';
   console.log(message);
   ```

1. Si vous utilisez un ancien projet de style non SDK, suivez les instructions dans [Supprimer les importations par défaut](#remove-default-imports) avant la génération.

1. Choisissez **générer > générer la solution**.

   Bien que l’application soit générée automatiquement lorsque vous l’exécutez, nous souhaitons examiner un problème qui se produit pendant le processus de génération :

   Si vous avez généré des mappages de sources, ouvrez le dossier spécifié dans l’option *outDir* et recherchez les fichiers *. js générés avec le ou les fichiers * js. map générés.

   Les fichiers de mappage source sont requis pour le débogage.

1. Si vous souhaitez compiler chaque fois que vous enregistrez le projet, utilisez l’option *compileOnSave* dans *. tsconfig.

   ```json
   ```{
      "compileOnSave":  true,
      "compilerOptions": {
      }
   }
   ```

Pour obtenir un exemple d’utilisation de Gulp avec la tâche Runner pour générer votre application, consultez [ASP.net Core et la machine à écrire](https://www.typescriptlang.org/docs/handbook/asp-net-core.html).

Si vous rencontrez des problèmes où Visual Studio utilise une version de Node.js ou un outil tiers différent de la version attendue, vous devrez peut-être définir le chemin d’accès de Visual Studio à utiliser. Choisissez **Outils**  >  **options**. Sous **projets et solutions**, choisissez **Web Package Management**  >  **Outils Web externes**.

### <a name="run-the-application"></a>Exécution de l'application

Pour obtenir des instructions sur l’exécution de l’application après sa compilation, consultez [créer votre première Node.js application](/visualstudio/ide/quickstart-nodejs?toc=%2Fvisualstudio%2Fjavascript%2Ftoc.json#run-the-application).

### <a name="nuget-package-structure-details"></a>Détails de la structure du package NuGet

`Microsoft.TypeScript.MSBuild.nupkg` contient deux dossiers principaux :

- dossier de *Build*

    Deux fichiers se trouvent dans ce dossier.
    Les deux sont des points d’entrée (pour le fichier cible de la base de texte et les fichiers props), respectivement.

    1. *Microsoft. dactylographié. MSBuild. targets*

        Ce fichier définit les variables qui spécifient la plateforme Runtime, comme un chemin d’accès *TypeScript.Tasks.dll*, avant d’importer *Microsoft. dactylographié. targets* à partir du dossier *Tools* .

    2. *Microsoft. dactylographié. MSBuild. props*

        Ce fichier importe *Microsoft. dactylographié. default. props* à partir du dossier *Tools* et définit les propriétés indiquant que la génération a été lancée par le biais de NuGet.

- dossier *Outils*

    Les versions de package antérieures à 2,3 contiennent uniquement un dossier TSC. *Microsoft. dactylographié. targets* et *TypeScript.Tasks.dll* se trouvent au niveau de la racine.

    Dans les versions de package 2,3 et ultérieures, le niveau racine contient `Microsoft.TypeScript.targets` et `Microsoft.TypeScript.Default.props` . Pour plus d’informations sur ces fichiers, consultez [configuration de MSBuild](https://www.typescriptlang.org/docs/handbook/compiler-options-in-msbuild.html).

    En outre, le dossier contient trois sous-dossiers :

    1. *net45*

        Ce dossier contient `TypeScript.Tasks.dll` et d’autres dll dont il dépend.
        Lors de la génération d’un projet sur une plateforme Windows, MSBuild utilise les dll de ce dossier.

    2. *netstandard1.3*

        Ce dossier contient une autre version de `TypeScript.Tasks.dll` , qui est utilisée lors de la génération de projets sur un ordinateur non-Windows.

    3. *TSC*

        Ce dossier contient `tsc.js` , `tsserver.js` ainsi que tous les fichiers de dépendance requis pour les exécuter en tant que scripts de nœud.

        > [!NOTE]
        > Si Visual Studio est installé, la *node.exe* regroupée avec elle est automatiquement sélectionnée. Dans le cas contraire, Node.js doit être installé sur l’ordinateur.

        Les versions antérieures à 3,1 contenaient un `tsc.exe` exécutable pour exécuter la compilation. Dans la version 3,1, elle a été supprimée en faveur de l’utilisation de `node.exe` .

### <a name="remove-default-imports"></a>Supprimer les importations par défaut

Dans les projets de ASP.NET Core plus anciens qui utilisent le [format autre que le kit de développement logiciel (SDK](https://docs.microsoft.com/nuget/resources/check-project-format)), vous devrez peut-être supprimer certains éléments du fichier projet.

Si vous utilisez le package NuGet pour la prise en charge de MSBuild pour un projet, le fichier projet ne doit pas importer `Microsoft.TypeScript.Default.props` ou `Microsoft.TypeScript.targets` . Les fichiers sont importés par le package NuGet. ainsi, les inclure séparément peuvent entraîner un comportement inattendu.

1. Cliquez avec le bouton droit sur le projet et choisissez **décharger le projet**.

1. Cliquez avec le bouton droit sur le projet, puis choisissez **modifier \<*project file name*\> **.

   Le fichier projet s’ouvre.

1. Supprimez les références à `Microsoft.TypeScript.Default.props` et `Microsoft.TypeScript.targets` .

   Les importations à supprimer ressemblent à ce qui suit :

   ```xml
   <Import
      Project="$(MSBuildExtensionsPath32)\Microsoft\VisualStudio\v$(VisualStudioVersion)\TypeScript\Microsoft.TypeScript.Default.props"
      Condition="Exists('$(MSBuildExtensionsPath32)\Microsoft\VisualStudio\v$(VisualStudioVersion)\TypeScript\Microsoft.TypeScript.Default.props')" />

   <Import
      Project="$(MSBuildExtensionsPath32)\Microsoft\VisualStudio\v$(VisualStudioVersion)\TypeScript\Microsoft.TypeScript.targets"
      Condition="Exists('$(MSBuildExtensionsPath32)\Microsoft\VisualStudio\v$(VisualStudioVersion)\TypeScript\Microsoft.TypeScript.targets')" />
   ```
