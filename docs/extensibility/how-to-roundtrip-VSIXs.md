---
title: Comment aller-retour des extensions
ms.date: 06/25/2017
ms.topic: how-to
ms.assetid: 2d6cf53c-011e-4c9e-9935-417edca8c486
author: willbrown
ms.author: madsk
manager: justinclareburt
ms.workload:
- willbrown
ms.openlocfilehash: ca1f367510aa9730c1b3b212438579a8eaeb0e8f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "86387276"
---
# <a name="how-to-make-extensions-compatible-with-visual-studio-20192017-and-visual-studio-2015"></a>Comment : rendre des extensions compatibles avec Visual Studio 2019/2017 et Visual Studio 2015

Ce document explique comment faire des allers-retours entre Visual Studio 2015 et Visual Studio 2019 ou Visual Studio 2017 pour les projets d’extensibilité. À l’issue de cette mise à niveau, un projet pourra ouvrir, générer, installer et exécuter dans Visual Studio 2015 et Visual Studio 2019 ou 2017. À titre de référence, certaines extensions qui peuvent aller-retour entre Visual Studio 2015 et Visual Studio 2019 ou 2017 sont disponibles dans les [exemples d’extensibilité du kit de développement logiciel (SDK) vs](https://github.com/Microsoft/VSSDK-Extensibility-Samples).

Si vous envisagez de générer uniquement dans Visual Studio 2019/2017, mais que vous souhaitez que le VSIX de sortie s’exécute à la fois dans Visual Studio 2015 et dans Visual Studio 2019/2017, reportez-vous au document sur la [migration des extensions](how-to-migrate-extensibility-projects-to-visual-studio-2017.md).

> [!NOTE]
> En raison des modifications apportées à Visual Studio entre les versions, certaines choses qui fonctionnaient dans une version ne fonctionnent pas dans une autre. Assurez-vous que les fonctionnalités auxquelles vous essayez d’accéder sont disponibles dans les deux versions ou que l’extension aura des résultats inattendus.

Voici un aperçu des étapes que vous allez effectuer dans ce document pour effectuer un aller-retour d’une extension VSIX :

1. Importez les packages NuGet appropriés.
2. Mettre à jour le manifeste d’extension :
    * Cible d’installation
    * Prérequis
3. Mettre à jour CSProj :
    * Mettez à jour `<MinimumVisualStudioVersion>`.
    * Ajouter la propriété `<VsixType>`
    * Ajoutez la propriété de débogage `($DevEnvDir)` 3 fois.
    * Ajoutez des conditions pour importer les outils de génération et les cibles.

4. Générer et tester

## <a name="environment-setup"></a>Configuration de l’environnement

Ce document suppose que les éléments suivants sont installés sur votre ordinateur :

* Visual Studio 2015 avec le kit de développement logiciel (SDK) VS installé
* Visual Studio 2019 ou 2017 avec la charge de travail d’extensibilité installée

## <a name="recommended-approach"></a>Approche recommandée

Il est vivement recommandé de démarrer cette mise à niveau avec Visual Studio 2015 au lieu de Visual Studio 2019 ou 2017. Le principal avantage du développement dans Visual Studio 2015 est de vous assurer que vous ne référencez pas les assemblys qui ne sont pas disponibles dans Visual Studio 2015. Si vous effectuez un développement dans Visual Studio 2019 ou 2017, vous risquez d’introduire une dépendance sur un assembly qui existe uniquement dans Visual Studio 2019 ou 2017.

## <a name="ensure-there-is-no-reference-to-projectjson"></a>Assurez-vous qu’il n’existe aucune référence à project.js

Plus loin dans ce document, nous allons insérer des instructions Import conditionnelles dans votre fichier **. csproj* . Cela ne fonctionnera pas si vos références NuGet sont stockées dans *project.jssur*. Par conséquent, il est recommandé de déplacer toutes les références NuGet vers le fichier *packages.config* .
Si votre projet contient un *project.jssur* le fichier :

* Prenez note des références dans *project.jssur*.
* À partir de la **Explorateur de solutions**, supprimez le *project.jssur* le fichier du projet. Cela supprime le *project.jsdans* le fichier et le supprime du projet.
* Rajoutez les références NuGet dans le projet :
  * Cliquez avec le bouton droit sur la **solution** et choisissez **gérer les packages NuGet pour la solution**.
  * Visual Studio crée automatiquement le fichier *packages.config* pour vous.

> [!NOTE]
> Si votre projet contenait des packages EnvDTE, vous devrez peut-être les ajouter en cliquant avec le bouton droit sur **références** , en sélectionnant **Ajouter une référence** et en ajoutant la référence appropriée. L’utilisation de packages NuGet peut créer des erreurs lors de la tentative de génération de votre projet.

## <a name="add-appropriate-build-tools"></a>Ajouter les outils de génération appropriés

Nous devons veiller à ajouter des outils de génération qui nous permettront de générer et déboguer correctement. Microsoft a créé un assembly pour ce appelé Microsoft. VisualStudio. Sdk. BuildTasks.

Pour créer et déployer un VSIXv3 dans Visual Studio 2015 et 2019/2017, vous aurez besoin des packages NuGet suivants :

Version | Outils intégrés
--- | ---
Visual Studio 2015 | Microsoft. VisualStudio. Sdk. BuildTasks. 14.0
Visual Studio 2019 ou 2017 | Microsoft. VSSDK. BuildTool

Pour ce faire :

* Ajoutez le package NuGet Microsoft. VisualStudio. Sdk. BuildTasks. 14.0 à votre projet.
* Si votre projet ne contient pas Microsoft. VSSDK. BuildTools, ajoutez-le.
* Assurez-vous que la version de Microsoft. VSSDK. BuildTools est 15. x ou supérieure.

## <a name="update-extension-manifest"></a>Mettre à jour le manifeste d’extension

### <a name="1-installation-targets"></a>1. cibles d’installation

Nous devons indiquer à Visual Studio les versions à cibler pour la création d’une extension VSIX. En règle générale, ces références sont soit vers la version 14,0 (Visual Studio 2015), version 15,0 (Visual Studio 2017), soit vers la version 16,0 (Visual Studio 2019). Dans notre cas, nous voulons créer un VSIX qui installe une extension pour les deux, donc nous devons cibler les deux versions. Si vous souhaitez que votre extension VSIX soit générée et installée sur des versions antérieures à 14,0, vous pouvez effectuer cette opération en définissant le numéro de version antérieure. Toutefois, la version 10,0 et les versions antérieures ne sont plus prises en charge.

* Ouvrez le fichier *source. extension. vsixmanifest* dans Visual Studio.
* Ouvrez l’onglet **installer les cibles** .
* Remplacez la **plage de versions** par [14,0, 17,0). « [ » Indique à Visual Studio d’inclure 14,0 et toutes les versions qui le dépassent. Le') 'indique à Visual Studio d’inclure toutes les versions jusqu’à la version 17,0, mais pas l’inclusion.
* Enregistrez toutes les modifications et fermez toutes les instances de Visual Studio.

![Image de cibles d’installation](media/visual-studio-installation-targets-example.png)

### <a name="2-adding-prerequisites-to-the-extensionvsixmanifest-file"></a>2. Ajout des composants requis au fichier *extension. vsixmanifest*

Nous avons besoin de l’éditeur principal de Visual Studio comme condition préalable. Ouvrez Visual Studio et utilisez le concepteur de manifeste mis à jour pour insérer les composants requis.

Pour effectuer cette opération manuellement :

* Accédez au répertoire du projet dans l’Explorateur de fichiers.
* Ouvrez le fichier *extension. vsixmanifest* à l’aide d’un éditeur de texte.
* Ajoutez la balise suivante :

```xml
<Prerequisites>
    <Prerequisite Id="Microsoft.VisualStudio.Component.CoreEditor" Version="[15.0,16.0)" DisplayName="Visual Studio core editor" />
</Prerequisites>
```

* Enregistrez et fermez le fichier.

> [!NOTE]
> Vous devrez peut-être modifier manuellement la version requise pour vous assurer qu’elle est compatible avec toutes les versions de Visual Studio 2019 ou 2017. Cela est dû au fait que le concepteur insère la version minimale comme version actuelle de Visual Studio (par exemple, 15.0.26208.0). Toutefois, étant donné que les autres utilisateurs peuvent avoir une version antérieure, vous devez modifier manuellement cette valeur sur 15,0.

À ce stade, votre fichier manifeste devrait ressembler à ceci :

![Exemple de conditions préalables](media/visual-studio-prerequisites-example.png)

## <a name="modify-the-project-file-myprojectcsproj"></a>Modifier le fichier projet (MyProject. csproj)

Il est fortement recommandé d’utiliser une référence à un. csproj modifié au cours de cette étape. Vous trouverez plusieurs exemples [ici](https://github.com/Microsoft/VSSDK-Extensibility-Samples). Sélectionnez un exemple d’extensibilité, recherchez le fichier *. csproj* pour référence et exécutez les étapes suivantes :

* Accédez au répertoire du projet dans l' **Explorateur de fichiers**.
* Ouvrez le fichier *MyProject. csproj* à l’aide d’un éditeur de texte.

### <a name="1-update-the-minimumvisualstudioversion"></a>1. Mettez à jour le MinimumVisualStudioVersion

* Définissez la version minimale de Visual Studio sur `$(VisualStudioVersion)` et ajoutez une instruction conditionnelle pour celle-ci. Ajoutez ces balises si elles n’existent pas. Vérifiez que les balises sont définies comme suit :

```xml
<VisualStudioVersion Condition="'$(VisualStudioVersion)' == ''">14.0</VisualStudioVersion>
<MinimumVisualStudioVersion>$(VisualStudioVersion)</MinimumVisualStudioVersion>
```

### <a name="2-add-the-vsixtype-property"></a>2. Ajoutez la propriété VsixType.

* Ajoutez la balise suivante `<VsixType>v3</VsixType>` à un groupe de propriétés.

> [!NOTE]
> Il est recommandé de l’ajouter sous la `<OutputType></OutputType>` balise.

### <a name="3-add-the-debugging-properties"></a>3. ajouter les propriétés de débogage

* Ajoutez le groupe de propriétés suivant :

```xml
<PropertyGroup>
    <StartAction>Program</StartAction>
    <StartProgram>$(DevEnvDir)devenv.exe</StartProgram>
    <StartArguments>/rootsuffix Exp</StartArguments>
</PropertyGroup>
```

* Supprimez toutes les instances de l’exemple de code suivant à partir du fichier *. csproj* et de tous les fichiers *. csproj. User* :

```xml
<StartAction>Program</StartAction>
<StartProgram>$(ProgramFiles)\Microsoft Visual Studio 14.0\Common7\IDE\devenv.exe</StartProgram>
<StartArguments>/rootsuffix Exp</StartArguments>
```

### <a name="4-add-conditions-to-the-build-tools-imports"></a>4. ajouter des conditions aux importations des outils de génération

* Ajoutez des instructions conditionnelles supplémentaires aux `<import>` balises qui ont une référence Microsoft. VSSDK. BuildTools. Insérez `'$(VisualStudioVersion)' != '14.0' And` au début de l’instruction de condition. Ces instructions s’affichent dans l’en-tête et le pied de page du fichier csproj.

Par exemple :

```xml
<Import Project="packages\Microsoft.VSSDK.BuildTools.15.0.26201…" Condition="'$(VisualStudioVersion)' != '14.0' And Exists(…" />
```

* Ajoutez des instructions conditionnelles supplémentaires aux `<import>` balises qui ont un Microsoft. VisualStudio. Sdk. BuildTasks. 14.0. Insérez `'$(VisualStudioVersion)' == '14.0' And` au début de l’instruction de condition. Ces instructions s’affichent dans l’en-tête et le pied de page du fichier csproj.

Par exemple :

```xml
<Import Project="packages\Microsoft.VisualStudio.Sdk.BuildTasks.14.0.14.0…" Condition="'$(VisualStudioVersion)' == '14.0' And Exists(…" />
```

* Ajoutez des instructions conditionnelles supplémentaires aux `<Error>` balises qui ont une référence Microsoft. VSSDK. BuildTools. Pour ce faire, insérez `'$(VisualStudioVersion)' != '14.0' And` au début de l’instruction de condition. Ces instructions s’affichent dans le pied de page du fichier csproj.

Par exemple :

```xml
<Error Condition="'$(VisualStudioVersion)' != '14.0' And Exists('packages\Microsoft.VSSDK.BuildTools.15.0.26201…" />
```

* Ajoutez des instructions conditionnelles supplémentaires aux `<Error>` balises qui ont un Microsoft. VisualStudio. Sdk. BuildTasks. 14.0. Insérez `'$(VisualStudioVersion)' == '14.0' And` au début de l’instruction de condition. Ces instructions s’affichent dans le pied de page du fichier csproj.

Par exemple :

```xml
<Error Condition="'$(VisualStudioVersion)' == '14.0' And Exists('packages\Microsoft.VisualStudio.Sdk.BuildTasks.14.0.14.0…" />
```

* Enregistrez le fichier csproj et fermez-le. 
  * Notez que si vous utilisez plusieurs projets dans la solution, définissez ce projet en tant que projet de démarrage à l’aide de l’option « définir comme projet de démarrage » dans le menu contextuel du projet. Cela permet de s’assurer que Visual Studio ouvre à nouveau ce projet après l’avoir déchargé.

## <a name="test-the-extension-installs-in-visual-studio-2015-and-visual-studio-2019-or-2017"></a>Tester les installations d’extension dans Visual Studio 2015 et Visual Studio 2019 ou 2017

À ce stade, votre projet doit être prêt à créer un VSIXv3 qui peut être installé sur Visual Studio 2015 et Visual Studio 2017.

* Ouvrez votre projet dans Visual Studio 2015.
* Générez votre projet et confirmez dans la sortie qu’une extension VSIX est correctement générée.
* Accédez au répertoire de votre projet.
* Ouvrez le dossier *\bin\Debug* .
* Double-cliquez sur le fichier VSIX et installez votre extension sur Visual Studio 2015 et Visual Studio 2019/2017.
* Assurez-vous que vous pouvez voir l’extension dans **Outils**  >  **extensions et mises à jour** dans la section **installé** .
* Essayez d’exécuter/d’utiliser l’extension pour vérifier qu’elle fonctionne.

![Rechercher une extension VSIX](media/finding-a-VSIX-example.png)

> [!NOTE]
> Si votre projet ne répond plus avec le message **ouvrant le fichier**, forcez l’arrêt de Visual Studio, accédez au répertoire de votre projet, affichez les dossiers masqués, puis supprimez le dossier *. vs* .
