---
title: Comment les Extensions aller-retour
ms.date: 06/25/2017
ms.topic: conceptual
ms.assetid: 2d6cf53c-011e-4c9e-9935-417edca8c486
author: willbrown
ms.author: gregvanl
manager: justinclareburt
ms.workload:
- willbrown
ms.openlocfilehash: 0b70d8f1692eed8dcd1ba339dc9bcbb361e60db0
ms.sourcegitcommit: 11337745c1aaef450fd33e150664656d45fe5bc5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57323813"
---
# <a name="how-to-make-extensions-compatible-with-visual-studio-2017-and-visual-studio-2015"></a>Procédure : Créer des extensions compatible avec Visual Studio 2017 et Visual Studio 2015

Ce document explique comment créer des projets d’extensibilité aller-retour entre Visual Studio 2015 et Visual Studio 2017. À l’issue de cette mise à niveau, un projet seront en mesure d’ouvrir, générer, installer et exécuter dans Visual Studio 2015 et Visual Studio 2017. En tant que référence, certaines extensions que vous peuvent effectuer un aller-retour entre Visual Studio 2015 et Visual Studio 2017 se trouve dans le [exemples d’extensibilité de Visual Studio SDK](https://github.com/Microsoft/VSSDK-Extensibility-Samples).

Si vous souhaitez uniquement créer dans Visual Studio 2017, mais la sortie VSIX à exécuter dans Visual Studio 2015 et Visual Studio 2017, puis vous référer à la [document de migration d’Extension](how-to-migrate-extensibility-projects-to-visual-studio-2017.md).

> [!NOTE]
> En raison de modifications dans Visual Studio entre les versions, certaines choses qui fonctionnait dans une version ne fonctionnent pas dans un autre. Assurez-vous que les fonctionnalités que vous essayez d’accéder sont disponibles dans les deux versions ou l’extension aura des résultats inattendus.

Voici une brève présentation des étapes que vous effectuerez dans ce document pour effectuer un aller-retour d’une extension VSIX :

1. Importer les packages NuGet corrects.
2. Mettre à jour du manifeste d’Extension :
    * Cible d’installation
    * Prérequis
3. Mise à jour CSProj :
    * Mise à jour `<MinimumVisualStudioVersion>`.
    * Ajouter le `<VsixType>` propriété.
    * Ajoutez la propriété débogage `($DevEnvDir)` 3 fois.
    * Ajouter des conditions pour l’importation des outils de génération et de cibles.

4. Générer et tester

## <a name="environment-setup"></a>Configuration de l’environnement

Ce document suppose que vous avez installé sur votre ordinateur les éléments suivants :

* Visual Studio 2015 avec le SDK de Visual Studio installé
* Visual Studio 2017 avec la charge de travail d’extensibilité installé

## <a name="recommended-approach"></a>Approche recommandée

Il est vivement recommandé de démarrer cette mise à niveau avec Visual Studio 2015, au lieu de Visual Studio 2017. Le principal avantage du développement dans Visual Studio 2015 est pour vous assurer de ne pas référencer les assemblys qui ne sont pas disponibles dans Visual Studio 2015. Si vous effectuez le développement dans Visual Studio 2017, il existe un risque que vous risquez d’introduire une dépendance sur un assembly qui existe uniquement dans Visual Studio 2017.

## <a name="ensure-there-is-no-reference-to-projectjson"></a>Garantir qu'aucune référence au fichier project.json

Plus loin dans ce document, nous insérera dans les instructions import conditionnelles à votre **.csproj* fichier. Cela ne fonctionne pas si vos références NuGet sont stockés dans *project.json*. Par conséquent, nous vous recommandons de déplacer toutes les références NuGet à la *packages.config* fichier.
Si votre projet contient un *project.json* fichier :

* Prenez note des références dans *project.json*.
* À partir de la **l’Explorateur de solutions**, supprimez le *project.json* fichier à partir du projet. Cette opération supprime le *project.json* de fichiers et supprime du projet.
* Ajoutez que les références NuGet de nouveau dans le projet :
    * Avec le bouton droit sur le **Solution** et choisissez **gérer les Packages NuGet pour la Solution**.
    * Visual Studio crée automatiquement le *packages.config* fichier pour vous.

> [!NOTE]
> Si votre projet contient les packages EnvDTE, ils peuvent avoir à être ajoutés en cliquant avec le bouton droit sur **références** en sélectionnant **ajouter une référence** et l’ajout de la référence appropriée. À l’aide de packages NuGet peut créer des erreurs lors de la tentative générer votre projet.

## <a name="add-appropriate-build-tools"></a>Ajouter des outils de génération approprié

Nous avons besoin pour être sûr qu’ajouter des outils de génération qui nous permettra de créer et déboguer de manière appropriée. Microsoft a créé un assembly pour cette Microsoft.VisualStudio.Sdk.BuildTasks appelée.

Pour générer et déployer un VSIXv3 dans Visual Studio 2015 et 2017, vous aurez besoin des packages NuGet suivants :

Version | Outils de génération
--- | ---
Visual Studio 2015 | Microsoft.VisualStudio.Sdk.BuildTasks.14.0
Visual Studio 2017 | Microsoft.VSSDK.BuildTool

Pour ce faire :

* Ajoutez le package NuGet Microsoft.VisualStudio.Sdk.BuildTasks.14.0 à votre projet.
* Si votre projet ne contient pas de Microsoft.VSSDK.BuildTools, ajoutez-le.
* Vérifiez la version de Microsoft.VSSDK.BuildTools est 15.x ou supérieur.

## <a name="update-extension-manifest"></a>Mettre à jour le manifeste d’extension

### <a name="1-installation-targets"></a>1. Cibles d’installation

Nous devons indiquer à Visual Studio quelles versions à cibler pour la création d’une extension VSIX. En règle générale, ces références sont dans la version 14.0 (Visual Studio 2015), version 15.0 (Visual Studio 2017) ou version 16.0 (Visual Studio 2019). Dans notre cas, nous voulons créer une extension VSIX qui installe une extension pour les deux, donc nous avons besoin cibler les deux versions. Si vous souhaitez que votre projet VSIX pour générer et installer sur les versions antérieures à 14.0, cela est possible en définissant le numéro de version antérieur ; Toutefois, version 10.0 et versions antérieures ne sont plus prises en charge.

* Ouvrez le *source.extension.vsixmanifest* fichier dans Visual Studio.
* Ouvrez le **cibles d’installation** onglet.
* Modifier le **plage de versions** à [14.0, 17.0). Le ' [' indique à Visual Studio pour inclure 14.0 et toutes les versions au-delà de celle-ci. Le «) » indique à Visual Studio pour inclure toutes les versions jusqu'à, mais non compris, version 17.0.
* Enregistrer toutes les modifications et fermez toutes les instances de Visual Studio.

![Image de cibles d’installation](media/visual-studio-installation-targets-example.png)

### <a name="2-adding-prerequisites-to-the-extensionvsixmanifest-file"></a>2. Ajout de conditions préalables à la *extension.vsixmanifest* fichier

Conditions préalables sont une nouvelle fonctionnalité avec Visual Studio 2017. Dans ce cas, nous devons l’éditeur Visual Studio Core comme condition préalable. Étant donné que le concepteur Visual Studio 2015 VSIX ne gère pas la nouvelle `Prerequisites` section, vous devrez modifier cette partie manuellement dans le code XML. Vous pouvez également ouvrir Visual Studio 2017 et utiliser le Concepteur de manifeste mis à jour pour insérer les conditions préalables.

Pour effectuer cette opération manuellement :

* Accédez au répertoire du projet dans l’Explorateur de fichiers.
* Ouvrez le *extension.vsixmanifest* fichier avec un éditeur de texte.
* Ajoutez la balise suivante :

```xml
<Prerequisites>
    <Prerequisite Id="Microsoft.VisualStudio.Component.CoreEditor" Version="[15.0,16.0)" DisplayName="Visual Studio core editor" />
</Prerequisites>
```

* Enregistrez et fermez le fichier.

> [!NOTE]
> Si vous choisissez d’y parvenir avec le concepteur VSIX dans Visual Studio 2017, vous devez modifier manuellement la version prérequise pour vous assurer qu’il est compatible avec toutes les versions de Visual Studio 2017. Il s’agit, car le concepteur insère la version minimale que votre version actuelle de Visual Studio (par exemple, 15.0.26208.0). Toutefois, étant donné que les autres utilisateurs devront peut-être une version antérieure, vous devez modifier manuellement ce 15.0.

À ce stade, votre fichier manifeste doit ressembler à ceci :

![Exemple de configuration requise](media/visual-studio-prerequisites-example.png)

## <a name="modify-the-project-file-myprojectcsproj"></a>Modifiez le fichier projet (myproject.csproj)

Il est fortement recommandé d’avoir une référence à une modification .csproj ouvert pendant cette étape. Vous trouverez plusieurs exemples [ici](https://github.com/Microsoft/VSSDK-Extensibility-Samples). Sélectionnez n’importe quel exemple d’extensibilité, recherchez le *.csproj* pour la référence de fichier et exécutez les étapes suivantes :

* Accédez au répertoire du projet dans **Explorateur de fichiers**.
* Ouvrez le *myproject.csproj* fichier avec un éditeur de texte.

### <a name="1-update-the-minimumvisualstudioversion"></a>1. Mettre à jour la minimumvisualstudioversion par

* La valeur est la version minimale de visual studio `$(VisualStudioVersion)` et ajouter une instruction conditionnelle pour celle-ci. Ajoutez ces balises si elles n’existent pas. Vérifiez que les balises sont définies comme indiqué ci-dessous :

```xml
<VisualStudioVersion Condition="'$(VisualStudioVersion)' == ''">14.0</VisualStudioVersion>
<MinimumVisualStudioVersion>$(VisualStudioVersion)</MinimumVisualStudioVersion>
```

### <a name="2-add-the-vsixtype-property"></a>2. Ajoutez la propriété VsixType.

* Ajoutez la balise suivante `<VsixType>v3</VsixType>` à un groupe de propriétés.

> [!NOTE]
> Il est recommandé d’ajouter ce ci-dessous le `<OutputType></OutputType>` balise.

### <a name="3-add-the-debugging-properties"></a>3. Ajoutez les propriétés de débogage

* Ajoutez le groupe de propriétés suivantes :

```xml
<PropertyGroup>
    <StartAction>Program</StartAction>
    <StartPrograms>$(DevEnvDir)devenv.exe</StartPrograms>
    <StartArguments>/rootsuffix Exp</StartArguments>
</PropertyGroup>
```

* Supprimer toutes les instances de l’exemple de code suivant à partir de la *.csproj* fichier et tout *. csproj.user* fichiers :

```xml
<StartAction>Program</StartAction>
<StartPrograms>$(ProgramFiles)\Microsoft Visual Studio 14.0\Common7\IDE\devenv.exe</StartPrograms>
<StartArguments>/rootsuffix Exp</StartArguments>
```

### <a name="4-add-conditions-to-the-build-tools-imports"></a>4. Ajouter des conditions pour les importations d’outils de génération

* Ajouter des instructions conditionnelles supplémentaires pour le `<import>` balises ayant une référence Microsoft.VSSDK.BuildTools. Insérer `'$(VisualStudioVersion)' != '14.0' And` au début de l’instruction de condition. Ces instructions seront affiche dans l’en-tête et le pied de page du fichier csproj.

Exemple :

```xml
<Import Project="packages\Microsoft.VSSDK.BuildTools.15.0.26201…" Condition="'$(VisualStudioVersion)' != '14.0' And Exists(…" />
```

* Ajouter des instructions conditionnelles supplémentaires pour le `<import>` balises ayant un Microsoft.VisualStudio.Sdk.BuildTasks.14.0. Insérer `'$(VisualStudioVersion)' == '14.0' And` au début de l’instruction de condition. Ces instructions seront affiche dans l’en-tête et le pied de page du fichier csproj.

Exemple :

```xml
<Import Project="packages\Microsoft.VisualStudio.Sdk.BuildTasks.14.0.14.0…" Condition="'$(VisualStudioVersion)' == '14.0' And Exists(…" />
```

* Ajouter des instructions conditionnelles supplémentaires pour le `<Error>` balises ayant une référence Microsoft.VSSDK.BuildTools. Cela en insérant `'$(VisualStudioVersion)' != '14.0' And` au début de l’instruction de condition. Ces instructions seront affiche dans le pied de page du fichier csproj.

Exemple :

```xml
<Error Condition="'$(VisualStudioVersion)' != '14.0' And Exists('packages\Microsoft.VSSDK.BuildTools.15.0.26201…" />
```

* Ajouter des instructions conditionnelles supplémentaires pour le `<Error>` balises ayant un Microsoft.VisualStudio.Sdk.BuildTasks.14.0. Insérer `'$(VisualStudioVersion)' == '14.0' And` au début de l’instruction de condition. Ces instructions seront affiche dans le pied de page du fichier csproj.

Exemple :

```xml
<Error Condition="'$(VisualStudioVersion)' == '14.0' And Exists('packages\Microsoft.VisualStudio.Sdk.BuildTasks.14.0.14.0…" />
```

* Enregistrez le fichier csproj, puis fermez-le.

## <a name="test-the-extension-installs-in-visual-studio-2015-and-visual-studio-2017"></a>Tester l’extension d’installer dans Visual Studio 2015 et Visual Studio 2017

À ce stade, votre projet doit être prêt à générer un VSIXv3 qui peut installer sur Visual Studio 2015 et Visual Studio 2017.

* Ouvrez votre projet dans Visual Studio 2015.
* Générez votre projet et confirmez dans la sortie qu’une extension VSIX est généré correctement.
* Accédez au répertoire de votre projet.
* Ouvrez le *\bin\Debug* dossier.
* Double-cliquez sur le fichier VSIX et installer votre extension sur Visual Studio 2015 et Visual Studio 2017.
* Assurez-vous que vous pouvez voir l’extension dans **outils** > **Extensions et mises à jour** dans le **installé** section.
* Tentative d’exécution/utiliser l’extension pour vérifier qu’elle fonctionne.

![Rechercher une extension VSIX](media/finding-a-VSIX-example.png)

> [!NOTE]
> Si votre projet se bloque avec le message **l’ouverture du fichier**, forcer l’arrêt Visual Studio, accédez à votre répertoire de projet, afficher les dossiers cachés et supprimez le *.vs* dossier.