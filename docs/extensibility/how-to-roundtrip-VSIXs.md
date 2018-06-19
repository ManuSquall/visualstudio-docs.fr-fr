---
title: 'Comment : aller-retour des Extensions pour Visual Studio | Documents Microsoft'
ms.custom: ''
ms.date: 06/25/2017
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 2d6cf53c-011e-4c9e-9935-417edca8c486
author: willbrown
ms.author: willbrown
manager: justinclareburt
ms.workload:
- willbrown
ms.openlocfilehash: 9d8d0dc2e5c8c95b5f2502ef5a48e6f97c26e289
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31133103"
---
# <a name="how-to-make-extensions-compatible-with-visual-studio-2017-and-visual-studio-2015"></a>Comment : créer des Extensions Compatible avec Visual Studio 2017 et Visual Studio 2015

Ce document explique comment créer des projets d’extensibilité aller-retour entre Visual Studio 2015 et Visual Studio 2017. Après avoir effectué cette mise à niveau, un projet est en mesure de les ouvrir, générer, installer et exécuter dans Visual Studio 2015 et Visual Studio 2017.  En tant que référence, vous pouvez trouver les certaines extensions que vous peuvent effectuer un aller-retour entre Visual Studio 2015 et Visual Studio 2017 [ici](https://github.com/Microsoft/VSSDK-Extensibility-Samples) dans les exemples d’extensibilité de Microsoft.

Si vous souhaitez uniquement créer dans Visual Studio 2017, mais la sortie VSIX pour s’exécuter dans Visual Studio 2015 et Visual Studio 2017, puis consultez le [Document de Migration d’Extension](how-to-migrate-extensibility-projects-to-visual-studio-2017.md).

>**Remarque :** en raison de modifications dans Visual Studio entre les versions, les éléments qui fonctionnaient dans une version ne fonctionnera pas une autre. Vérifiez que les fonctionnalités que vous essayez d’accéder sont disponibles dans les deux versions, ou l’extension aura des résultats inattendus.

Voici les étapes que vous effectuerez dans ce document pour effectuer un aller-retour d’une extension VSIX :

1. Importer les packages NuGet corrects.
2. Mise à jour du manifeste d’Extension :
    * Cible d’installation
    * Prérequis
3. CSProj de mise à jour :
    * Mise à jour `<MinimumVisualStudioVersion>`.
    * Ajouter le `<VsixType>` propriété.
    * Ajoutez la propriété débogage `($DevEnvDir)` 3 fois.
    * Ajoutez des conditions pour l’importation des outils de génération et de cibles.

4. Génération et Test

## <a name="environment-setup"></a>Configuration de l'environnement

Ce document suppose que vous avez installé sur votre ordinateur les éléments suivants :

* Visual Studio 2015 avec le Kit de développement logiciel Visual Studio installé
* Visual Studio 2017, la charge de travail d’extensibilité installé

## <a name="recommended-approach"></a>Approche recommandée

Il est fortement recommandé de démarrer cette mise à niveau avec Visual Studio 2015, au lieu de Visual Studio 2017. Le principal avantage du développement dans Visual Studio 2015 est pour vous assurer de ne pas référencer les assemblys qui ne sont pas disponibles dans Visual Studio 2015. Si vous effectuez le développement dans Visual Studio 2017, il est un risque que vous risquez d’introduire une dépendance sur un assembly qui existe uniquement dans Visual Studio 2017.

## <a name="ensure-there-is-no-reference-to-projectjson"></a>Vérifiez qu’il n’existe aucune référence à project.json

Plus loin dans ce document, nous insère les instructions import conditionnelles dans votre fichier *.csproj.  Cela ne fonctionne pas si vos références NuGet sont stockés dans project.json. Par conséquent, il est recommandé de déplacer toutes les références NuGet dans le fichier packages.config.
Si votre projet contient un fichier project.json :

* Notez les références dans project.json.
* À partir de l’Explorateur de solutions, supprimez le fichier project.json à partir du projet.
    * Cela supprime le fichier project.json et supprimer le projet.
* Ajoutez que les références NuGet réintégré dans le projet.
    * Avec le bouton droit sur la Solution et choisissez **gérer les Packages NuGet pour la Solution...**
    * Visual Studio crée automatiquement le fichier packages.config pour vous

>**Remarque :** si votre projet contient les packages EnvDTE, ils peuvent doivent être ajoutés en cliquant avec le bouton droit sur **références** en sélectionnant **ajouter une référence** et l’ajout de la référence appropriée.  À l’aide de packages NuGet peut créer des erreurs lors de la tentative générer votre projet.

## <a name="adding-appropriate-build-tools"></a>Ajout d’outils de génération approprié

Nous devons pour être sûr d’ajouter des outils de génération qui nous permettra de générer et déboguer de manière appropriée. Microsoft a créé un assembly pour cette Microsoft.VisualStudio.Sdk.BuildTasks appelée.

Pour générer et déployer un VSIXv3 dans Visual Studio 2015 et 2017, vous aurez besoin des packages NuGet suivants :

Version | Outils de génération
--- | ---
Visual Studio 2015 | Microsoft.VisualStudio.Sdk.BuildTasks.14.0
Visual Studio 2017 | Microsoft.VSSDK.BuildTool

Pour cela :

* Ajoutez le package NuGet Microsoft.VisualStudio.Sdk.BuildTasks.14.0 à votre projet.
* Si votre projet ne contient pas de Microsoft.VSSDK.BuildTools, ajoutez-le.
* Vérifiez que la version Microsoft.VSSDK.BuildTools est 15.x ou supérieur.

## <a name="update-extension-manifest"></a>Mettre à jour le manifeste d’Extension

### <a name="1-installation-targets"></a>1. Cibles d’installation

Nous devons indiquer quelles versions à cibler pour la création d’une extension VSIX à Visual Studio.  En règle générale, ces références sont à la version 14.0 (Visual Studio 2015) ou version 15.0 (Visual Studio 2017).  Dans notre cas, nous souhaitons générer une extension VSIX qui installe une extension pour les deux, donc cibler les deux versions.  Si vous souhaitez que votre extension VSIX pour générer et installer sur des versions antérieures à 14.0, cela est possible en définissant le numéro de version antérieur ; Toutefois, version 10.0 et versions antérieure ne sont plus prises en charge.

* Ouvrez le fichier source.extension.vsixmanifest dans Visual Studio.
* Ouvrez le **cibles d’installation** onglet.
* Modifier la **la plage de versions** à [14.0, 16.0).  Le ' [' indique à Visual Studio pour inclure 14.0 et toutes les versions au-delà de celle-ci.  Le «) » indique à Visual Studio pour inclure toutes les versions de 15.0 des, mais sans inclure la version 16.0.
* Enregistrer toutes les modifications et fermez toutes les instances de Visual Studio.

![Image de cibles d’installation](media/visual-studio-installation-targets-example.png)

### <a name="2-adding-prerequisites-to-the-extensionvsixmanifest-file"></a>2. Ajout de conditions préalables pour le fichier extension.vsixmanifest

Conditions préalables sont une nouvelle fonctionnalité avec Visual Studio 2017.  Dans ce cas, nous devons l’éditeur Visual Studio Core comme condition préalable. Étant donné que le concepteur Visual Studio 2015 VSIX ne gère pas la nouvelle `Prerequisites` section, vous devez modifier cette partie manuellement dans le code XML.  Vous pouvez également ouvrir Visual Studio 2017 et utiliser le Concepteur de manifeste mis à jour pour insérer les conditions préalables.

Pour ce faire manuellement :

* Accédez au répertoire du projet dans l’Explorateur de fichiers.
* Ouvrez le `extension.vsixmanifest` fichier avec un éditeur de texte.
* Ajoutez la balise suivante :

```xml
<Prerequisites>
    <Prerequisite Id="Microsoft.VisualStudio.Component.CoreEditor" Version="[15.0,16.0)" DisplayName="Visual Studio core editor" />
</Prerequisites>
```

* Enregistrez et fermez le fichier.

>**Remarque :** si vous choisissez d’effectuer cette opération avec le concepteur VSIX dans Visual Studio 2017, vous devez modifier manuellement la version de configuration requise pour vous assurer qu’il est compatible avec toutes les versions de Visual Studio 2017.  Il s’agit, car le concepteur insère la version minimale que votre version actuelle de Visual Studio (par exemple, 15.0.26208.0).  Toutefois, étant donné que les autres utilisateurs ont peut-être une version antérieure, vous devez modifier manuellement ce à 15.0.

À ce stade, votre fichier manifeste doit ressembler à ceci :

![Exemple de configuration requise](media/visual-studio-prerequisites-example.png)

## <a name="modify-the-project-file-myprojectcsproj"></a>Modifier le fichier projet (myproject.csproj)

Il est recommandé d’avoir une référence à un .csproj modifiés ouverts lors de cette étape.  Vous trouverez plusieurs exemples [ici](https://github.com/Microsoft/VSSDK-Extensibility-Samples).  Sélectionnez tous les échantillons d’extensibilité, de trouver le fichier .csproj pour référence et exécuter les étapes suivantes :

* Accédez au répertoire du projet dans l’Explorateur de fichiers.
* Ouvrez le fichier myproject.csproj avec un éditeur de texte.

### <a name="1-update-the-minimumvisualstudioversion"></a>1. Mettre à jour la minimumvisualstudioversion par

* Définir la version minimale de visual studio `$(VisualStudioVersion)` et ajoutez une instruction conditionnelle pour celle-ci.  Ajoutez ces balises si elles n’existent pas.  Vérifiez que les balises sont définies comme indiqué ci-dessous :

```xml
<VisualStudioVersion Condition="'$(VisualStudioVersion)' == ''">14.0</VisualStudioVersion>
<MinimumVisualStudioVersion>$(VisualStudioVersion)</MinimumVisualStudioVersion>
```

### <a name="2-add-the-vsixtype-property"></a>2. Ajoutez la propriété VsixType

* Ajoutez la balise suivante `<VsixType>v3</VsixType>` à un groupe de propriétés.

>**Remarque :** il est recommandé d’ajouter ce ci-dessous le `<OutputType></OutputType>` balise.

### <a name="3-add-the-debugging-properties"></a>3. Ajouter les propriétés de débogage

* Ajoutez le groupe de propriétés suivantes :

```xml
<PropertyGroup>
    <StartAction>Program</StartAction>
    <StartPrograms>$(DevEnvDir)devenv.exe</StartPrograms>
    <StartArguments>/rootsuffix Exp</StartArguments>
</PropertyGroup>
```

* Supprimer toutes les instances de la commande suivante à partir du fichier .csproj et tout. csproj.user fichiers :

```xml
<StartAction>Program</StartAction>
<StartPrograms>$(ProgramFiles)\Microsoft Visual Studio 14.0\Common7\IDE\devenv.exe</StartPrograms>
<StartArguments>/rootsuffix Exp</StartArguments>
```

### <a name="4-add-conditions-to-the-build-tools-imports"></a>4. Ajouter des conditions pour les importations d’outils de génération

* Ajouter des instructions conditionnelles supplémentaires pour le `<import>` balises qui contiennent une référence Microsoft.VSSDK.BuildTools.  Cela en insérant `'$(VisualStudioVersion)' != '14.0' And` au début de l’instruction de condition.  Ces instructions seront affiche dans l’en-tête et le pied de page du fichier csproj.

Par exemple :

```xml
<Import Project="packages\Microsoft.VSSDK.BuildTools.15.0.26201…" Condition="'$(VisualStudioVersion)' != '14.0' And Exists(…" />
```

* Ajouter des instructions conditionnelles supplémentaires pour le `<import>` balises qui ont un Microsoft.VisualStudio.Sdk.BuildTasks.14.0.  Cela en insérant `'$(VisualStudioVersion)' == '14.0' And` au début de l’instruction de condition. Ces instructions seront affiche dans l’en-tête et le pied de page du fichier csproj.

Par exemple :

```xml
<Import Project="packages\Microsoft.VisualStudio.Sdk.BuildTasks.14.0.14.0…" Condition="'$(VisualStudioVersion)' == '14.0' And Exists(…" />
```

* Ajouter des instructions conditionnelles supplémentaires pour le `<Error>` balises qui contiennent une référence Microsoft.VSSDK.BuildTools.  Cela en insérant `'$(VisualStudioVersion)' != '14.0' And` au début de l’instruction de condition. Ces instructions seront affichent dans le pied de page du fichier csproj.

Par exemple :

```xml
<Error Condition="'$(VisualStudioVersion)' != '14.0' And Exists('packages\Microsoft.VSSDK.BuildTools.15.0.26201…" />
```

* Ajouter des instructions conditionnelles supplémentaires pour le `<Error>` balises qui ont un Microsoft.VisualStudio.Sdk.BuildTasks.14.0.  Cela en insérant `'$(VisualStudioVersion)' == '14.0' And` au début de l’instruction de condition. Ces instructions seront affichent dans le pied de page du fichier csproj.

Par exemple :

```xml
<Error Condition="'$(VisualStudioVersion)' == '14.0' And Exists('packages\Microsoft.VisualStudio.Sdk.BuildTasks.14.0.14.0…" />
```

* Enregistrez le fichier csproj et fermez-le.

## <a name="test-the-extension-installs-in-visual-studio-2015-and-visual-studio-2017"></a>L’installation de l’extension de test dans Visual Studio 2015 et Visual Studio 2017

À ce stade, votre projet doit être prêt à générer un VSIXv3 qui peut installer sur Visual Studio 2015 et Visual Studio 2017.

* Ouvrez votre projet dans Visual Studio 2015
* Générer votre projet et vous assurer de la sortie d’une extension VSIX est correctement générée
* Accédez à votre répertoire de projet
* Ouvrez l’emplacement -> dossier de débogage
* Double-cliquez sur le fichier VSIX et installer votre extension de Visual Studio 2015 et Visual Studio 2017
* Vérifiez que vous pouvez voir l’extension dans Outils -> Extensions et mises à jour dans la section « Installer ».
* Tentative d’exécution/utiliser l’extension pour vérifier qu’il fonctionne

![Recherche d’une extension VSIX](media/finding-a-VSIX-example.png)

>**Remarque :** si votre projet se bloque avec le message « ouverture du fichier » forcée arrêtez Visual Studio, accédez à votre répertoire de projet, afficher les dossiers cachés et supprimez le dossier .vs.
