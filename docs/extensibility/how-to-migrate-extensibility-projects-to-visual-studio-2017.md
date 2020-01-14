---
title: 'Comment : migrer des projets d’extensibilité vers Visual Studio 2017 | Microsoft Docs'
ms.date: 11/09/2016
ms.topic: conceptual
ms.assetid: 8ca07b00-a3ff-40ab-b647-c0a93b55e86a
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: 01c0c8613ec2e4fe72613867d623d510d9734e45
ms.sourcegitcommit: 939407118f978162a590379997cb33076c57a707
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/13/2020
ms.locfileid: "75917656"
---
# <a name="how-to-migrate-extensibility-projects-to-visual-studio-2017"></a>Comment : migrer des projets d’extensibilité vers Visual Studio 2017

Ce document explique comment mettre à niveau des projets d’extensibilité vers Visual Studio 2017. Outre la description de la mise à jour des fichiers projet, elle explique également comment effectuer une mise à niveau à partir du manifeste d’extension version 2 (VSIX v2) vers le nouveau format de manifeste VSIX de la version 3 (VSIX v3).

## <a name="install-visual-studio-2017-with-required-workloads"></a>Installer Visual Studio 2017 avec les charges de travail requises

Assurez-vous que votre installation comprend les charges de travail suivantes :

* Développement .NET Desktop
* Développement d’une extension Visual Studio

## <a name="open-vsix-solution-in-visual-studio-2017"></a>Ouvrir une solution VSIX dans Visual Studio 2017

Tous les projets VSIX requièrent une mise à niveau unidirectionnelle de la version majeure vers Visual Studio 2017.

Le fichier projet (par exemple * *. csproj*) sera mis à jour :

* MinimumVisualStudioVersion-maintenant défini sur 15,0
* OldToolsVersion (le cas échéant)-maintenant défini sur 14,0

## <a name="update-the-microsoftvssdkbuildtools-nuget-package"></a>Mettre à jour le package NuGet Microsoft. VSSDK. BuildTools

> [!Note]
> Si votre solution ne fait pas référence au package NuGet Microsoft. VSSDK. BuildTools, vous pouvez ignorer cette étape.

Pour générer votre extension dans le nouveau format VSIX v3 (version 3), votre solution doit être générée avec les nouveaux outils de génération VSSDK. Ce sera installé avec Visual Studio 2017, mais votre extension VSIX v2 peut contenir une référence à une version antérieure via NuGet. Si c’est le cas, vous devez installer manuellement une mise à jour du package NuGet Microsoft. VSSDK. BuildTools pour votre solution.

Pour mettre à jour les références NuGet à Microsoft. VSSDK. BuildTools :

* Cliquez avec le bouton droit sur la solution et choisissez **gérer les packages NuGet pour la solution**.
* Accédez à l’onglet **mises à jour** .
* Sélectionnez **Microsoft. VSSDK. BuildTools (dernière version)** .
* Appuyez sur **mettre à jour**.

![Outils de génération VSSDK](media/vssdk-build-tools.png)

## <a name="make-changes-to-the-vsix-extension-manifest"></a>Apporter des modifications au manifeste de l’extension VSIX

Pour vous assurer que l’installation de Visual Studio de l’utilisateur a tous les assemblys requis pour exécuter l’extension, spécifiez tous les packages ou composants requis dans le fichier manifeste de l’extension. Quand un utilisateur tente d’installer l’extension, VSIXInstaller vérifie si tous les composants requis sont installés. Si certaines d’entre elles sont manquantes, l’utilisateur est invité à installer les composants manquants dans le cadre du processus d’installation de l’extension.

> [!Note]
> Au minimum, toutes les extensions doivent spécifier le composant éditeur principal de Visual Studio comme condition préalable.

* Modifiez le fichier manifeste d’extension (généralement appelé *source. extension. vsixmanifest*).
* Assurez-vous `InstallationTarget` comprend 15,0.
* Ajoutez les composants requis pour l’installation (comme indiqué dans l’exemple ci-dessous).
  * Nous vous recommandons de spécifier uniquement des ID de composant pour les conditions préalables à l’installation.
  * Pour [obtenir des instructions sur l’identification des ID de composant](#find-component-ids), consultez la section à la fin de ce document.

Exemple :

```xml
<PackageManifest>
 ...
    <Prerequisites>
        <Prerequisite Id="Microsoft.VisualStudio.Component.CoreEditor" Version="[15.0,16.0)" />
        <Prerequisite Id="Microsoft.VisualStudio.Component.DiagnosticTools" Version="[15.0.25814.0,16.0)" />
        <Prerequisite Id="Microsoft.VisualStudio.Shell.12.0" Version="[12.0]" />
    </Prerequisites>
 ...
</PackageManifest>
```

### <a name="option-use-the-designer-to-make-changes-to-the-vsix-extension-manifest"></a>Option : utiliser le concepteur pour apporter des modifications au manifeste de l’extension VSIX

Au lieu de modifier directement le manifeste XML, vous pouvez utiliser l’onglet nouveaux **composants requis** du concepteur de manifeste pour sélectionner les composants requis et le code XML sera mis à jour pour vous.

> [!Note]
> Le concepteur de manifeste vous permet uniquement de sélectionner des composants (et non des charges de travail ou des packages) qui sont installés sur l’instance actuelle de Visual Studio. Si vous devez ajouter un composant requis pour une charge de travail, un package ou un composant qui n’est pas actuellement installé, modifiez directement le fichier XML du manifeste.

* Fichier Open *source. extension. vsixmanifest [Design]* .
* Sélectionnez l’onglet **composants requis** et appuyez sur **nouveau** bouton.

   ![Concepteur de manifeste VSIX](media/vsix-manifest-designer.png)

* La fenêtre **Ajouter une nouvelle prérequis** s’ouvre.

   ![Ajouter la condition préalable VSIX](media/add-vsix-prerequisite.png)

* Cliquez sur le menu déroulant **nom** , puis sélectionnez le composant requis.
* Mettez à jour la version si nécessaire.

   > [!Note]
   > Le champ version est pré-rempli avec la version du composant actuellement installé, avec une plage découvrante (mais sans inclure) la version majeure suivante du composant.

   ![Ajouter le composant requis Roslyn](media/add-roslyn-prerequisite.png)

* Cliquez sur **OK**.

## <a name="update-debug-settings-for-the-project"></a>Mettre à jour les paramètres de débogage du projet

Si vous souhaitez déboguer votre extension dans une instance expérimentale de Visual Studio, assurez-vous que la valeur de l’action démarrer le **programme externe** est définie sur le fichier *devenv. exe* de votre installation Visual Studio 2017 dans les paramètres du projet pour le **débogage** > **action de démarrage** .

Il peut ressembler à ceci : *C:\Program Files (x86) \Microsoft Visual Studio\2017\Enterprise\Common7\IDE\devenv.exe*

![démarrer le programme externe](media/start-external-program.png)

> [!Note]
> L’action de démarrage du débogage est généralement stockée dans le fichier *. csproj. User* . Ce fichier est généralement inclus dans le fichier *. gitignore* et, par conséquent, il n’est normalement pas enregistré avec d’autres fichiers projet lorsqu’il est validé dans le contrôle de code source. Par conséquent, si vous avez extrait votre solution du contrôle de code source, il est probable que le projet n’aura pas de valeurs définies pour l’action de démarrage. Les nouveaux projets VSIX créés avec Visual Studio 2017 auront un fichier *. csproj. User* créé avec des valeurs par défaut pointant vers le répertoire d’installation de Visual Studio actuel. Toutefois, si vous migrez une extension VSIX v2, il est probable que le fichier *. csproj. User* contiendra des références au répertoire d’installation de la version précédente de Visual Studio. La définition de la valeur pour **Déboguer** l' **action de démarrage** > permet l’exécution correcte de l’instance expérimentale de Visual Studio lorsque vous essayez de déboguer votre extension.

## <a name="check-that-the-extension-builds-correctly-as-a-vsix-v3"></a>Vérifier que l’extension est correctement générée (en tant que VSIX v3)

* Générez le projet VSIX.
* Décompressez l’extension VSIX générée.
  * Par défaut, le fichier VSIX se trouve dans *bin/debug* ou *bin/Release* en tant que *[YourCustomExtension]. vsix*.
  * Renommez *. vsix* en *. zip* pour afficher facilement le contenu.
* Vérifiez l’existence de trois fichiers :
  * *extension.vsixmanifest*
  * *manifest.json*
  * *catalog.json*

## <a name="check-when-all-required-prerequisites-are-installed"></a>Vérifier que tous les composants requis sont installés

Vérifiez que le VSIX s’installe correctement sur un ordinateur où tous les composants requis sont installés.

> [!Note]
> Avant d’installer une extension, fermez toutes les instances de Visual Studio.

Essayez d’installer l’extension :

* Sur Visual Studio 2017

![Programme d’installation VSIX sur Visual Studio 2017](media/vsixinstaller-vs-2017.png)

* Facultatif : Vérifiez les versions précédentes de Visual Studio.
  * Prouve la compatibilité descendante.
  * Doit fonctionner pour Visual Studio 2012, Visual Studio 2013, Visual Studio 2015.
* Facultatif : Vérifiez que l’outil de vérification de version du programme d’installation VSIX propose un choix de versions.
  * Contient les versions précédentes de Visual Studio (si installé).
  * Comprend Visual Studio 2017.

Si Visual Studio a été récemment ouvert, une boîte de dialogue semblable à celle-ci peut s’afficher :

![processus vs en cours d’exécution](media/vs-running-processes.png)

Attendez que les processus s’arrêtent ou terminez manuellement les tâches. Vous pouvez trouver les processus en fonction du nom de la liste ou du PID indiqué entre parenthèses.

> [!Note]
> Ces processus ne s’arrêtent pas automatiquement lorsqu’une instance de Visual Studio est en cours d’exécution. Veillez à arrêter toutes les instances de Visual Studio sur l’ordinateur, y compris celles des autres utilisateurs, puis continuez à réessayer.

## <a name="check-when-missing-the-required-prerequisites"></a>Vérifier le moment où les conditions préalables requises sont manquantes

* Essayez d’installer l’extension sur un ordinateur avec Visual Studio 2017 qui ne contient pas tous les composants définis dans les conditions préalables (ci-dessus).
* Vérifiez que l’installation identifie le ou les composants manquants et répertorie les composants requis dans le VSIXInstaller.
* Remarque : l’élévation est requise si des composants requis doivent être installés avec l’extension.

![Configuration requise manquante pour vsixinstaller](media/vsixinstaller-missing-prerequisite.png)

## <a name="decide-on-components"></a>Décider des composants

Lorsque vous recherchez vos dépendances, vous constaterez qu’une dépendance peut être mappée à plusieurs composants. Pour déterminer les dépendances que vous devez spécifier comme condition préalable, nous vous suggérons de choisir un composant qui a une fonctionnalité similaire à celle de votre extension et de prendre en compte les utilisateurs et les types de composants les plus susceptibles d’être installés ou n’envisagez pas d’installer. Nous vous suggérons également de créer vos extensions de manière à ce que les conditions préalables requises répondent uniquement à la valeur minimale permettant à votre extension de s’exécuter et que des fonctionnalités supplémentaires soient dormantes si certains composants ne sont pas détectés.

Pour obtenir de l’aide, nous avons identifié quelques types d’extension courants et leurs conditions préalables recommandées :

Type d'extension | Display Name | Id
--- | --- | ---
Éditeur | Éditeur de base de Visual Studio | Microsoft.VisualStudio.Component.CoreEditor
Roslyn | C# et Visual Basic | Microsoft.VisualStudio.Component.Roslyn.LanguageServices
WPF | Managed Desktop Workload Core | Microsoft.VisualStudio.Component.ManagedDesktop.Core
Débogueur | Débogueur juste-à-temps | Microsoft.VisualStudio.Component.Debugger.JustInTime

## <a name="find-component-ids"></a>Rechercher des ID de composant

La liste des composants triés par produit Visual Studio est celle des [ID de composant et de charge de travail de Visual studio 2017](/visualstudio/install/workload-and-component-ids?view=vs-2019). Utilisez ces ID de composant pour vos ID de composants requis dans votre manifeste.

Si vous ne savez pas quel composant contient un fichier binaire spécifique, téléchargez la [feuille de calcul Component-> binaire Mapping](https://aka.ms/vs2017componentid-binaries).

### <a name="vs2017-componentbinarymappingxlsx"></a>vs2017-ComponentBinaryMapping.xlsx

Il y a quatre colonnes dans la feuille Excel **: nom du composant**, **ID**de version, **version**et **noms binaires/fichiers**.  Vous pouvez utiliser les filtres pour rechercher et Rechercher des composants et des binaires spécifiques.

Pour toutes vos références, commencez par déterminer celles qui se trouvent dans le composant éditeur principal (Microsoft. VisualStudio. Component. CoreEditor).  Au minimum, nous avons besoin que le composant principal de l’éditeur soit spécifié comme condition préalable pour toutes les extensions. Parmi les références laissées qui ne sont pas dans l’éditeur principal, ajoutez des filtres dans la section **noms binaires/fichiers** pour rechercher les composants qui ont l’un des sous-ensembles de ces références.

Exemples :

* Si vous disposez d’une extension de débogueur et que vous savez que votre projet a une référence à *VSDebugEng. dll* et *VSDebug. dll*, cliquez sur le bouton de filtre dans l’en-tête des **noms de fichiers binaires/fichiers** .  Recherchez « VSDebugEng. dll », puis sélectionnez *OK*.  Ensuite, cliquez à nouveau sur le bouton de filtre dans l’en-tête des **noms de fichiers binaires/fichiers** et recherchez « VSDebug. dll ».  Cochez la case **Ajouter la sélection actuelle pour filtrer** et sélectionnez **OK**.  Examinez maintenant le **nom du composant** pour rechercher un composant qui est le plus lié à votre type d’extension. Dans cet exemple, vous devez choisir le débogueur juste-à-temps et l’ajouter à votre vsixmanifest.
* Si vous savez que votre projet gère les éléments du débogueur, vous pouvez effectuer une recherche sur « débogueur » dans la zone de recherche de filtre pour voir quels composants contiennent le débogueur dans son nom.

## <a name="specify-a-visual-studio-2017-release"></a>Spécifier une version de Visual Studio 2017

Si votre extension nécessite une version spécifique de Visual Studio 2017, par exemple, elle dépend d’une fonctionnalité publiée dans 15,3, vous devez spécifier le numéro de build dans votre **le INSTALLATIONTARGET**VSIX. Par exemple, la version 15,3 a un numéro de Build « 15.0.26730.3 ». Vous pouvez voir [ici](../install/visual-studio-build-numbers-and-release-dates.md)le mappage des mises en production aux numéros de Build. L’utilisation du numéro de version « 15,3 » ne fonctionne pas correctement.

Si votre extension requiert 15,3 ou une version ultérieure, vous devez déclarer la **version de le installationtarget** en tant que [15.0.26730.3, 16,0) :

```xml
<Installation>
  <InstallationTarget Id="Microsoft.VisualStudio.Community" Version="[15.0.26730.3, 16.0)" />
</Installation>
```
