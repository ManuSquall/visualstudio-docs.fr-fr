---
title: 'Comment : Migrate Extensibility Projects à Visual Studio 2017 (fr) Microsoft Docs'
ms.date: 11/09/2016
ms.topic: conceptual
ms.assetid: 8ca07b00-a3ff-40ab-b647-c0a93b55e86a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: b0cae0261b185ee08400e5f3d25735634663f54a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710981"
---
# <a name="how-to-migrate-extensibility-projects-to-visual-studio-2017"></a>Comment : Migrer les projets d’extensibility au Visual Studio 2017

Ce document explique comment mettre à niveau les projets d’extensibility à Visual Studio 2017. En plus de décrire comment mettre à jour les fichiers du projet, il décrit également comment mettre à niveau de la version manifeste d’extension 2 (VSIX v2) à la nouvelle version 3 VSIX format manifeste (VSIX v3).

## <a name="install-visual-studio-2017-with-required-workloads"></a>Installer Visual Studio 2017 avec les charges de travail requises

Assurez-vous que votre installation comprend les charges de travail suivantes :

* Développement .NET Desktop
* Développement d’une extension Visual Studio

## <a name="open-vsix-solution-in-visual-studio-2017"></a>Ouvrez la solution VSIX dans Visual Studio 2017

Tous les projets VSIX nécessiteront une mise à niveau à sens unique de la version majeure vers Visual Studio 2017.

Le dossier du projet (par exemple *.csproj*) sera mis à jour :

* MinimumVisualStudioVersion - maintenant réglé à 15.0
* OldToolsVersion (s’il existe auparavant) - maintenant réglé à 14,0

## <a name="update-the-microsoftvssdkbuildtools-nuget-package"></a>Mettre à jour le paquet Microsoft.VSSDK.BuildTools NuGet

> [!Note]
> Si votre solution ne fait pas référence au forfait NuGet Microsoft.VSSDK.BuildTools, vous pouvez sauter cette étape.

Afin de construire votre extension dans le nouveau format VSIX v3 (version 3), votre solution devra être construite avec les nouveaux outils de construction VSSDK. Ceci sera installé avec Visual Studio 2017, mais votre extension VSIX v2 pourrait être tenue une référence à une version plus ancienne via NuGet. Si c’est le cas, vous devrez installer manuellement une mise à jour du paquet NuGet Microsoft.VSSDK.BuildTools pour votre solution.

Pour mettre à jour les références NuGet à Microsoft.VSSDK.BuildTools:

* Cliquez à droite sur la solution et choisissez **les forfaits Manage NuGet pour la solution**.
* Naviguez vers l’onglet **Mises à jour.**
* Sélectionnez **Microsoft.VSSDK.BuildTools (dernière version)**.
* **Mise à jour de la presse**.

![VSSDK construisez des outils](media/vssdk-build-tools.png)

## <a name="make-changes-to-the-vsix-extension-manifest"></a>Modifier le manifeste d’extension VSIX

Pour s’assurer que l’installation de Visual Studio par l’utilisateur dispose de tous les assemblages nécessaires à l’exécution de l’extension, spécifiez tous les composants ou paquets préalables dans le fichier manifeste d’extension. Lorsqu’un utilisateur tente d’installer l’extension, le VSIXInstaller vérifie si toutes les conditions préalables sont installées. Si certains sont manquants, l’utilisateur sera invité à installer les composants manquants dans le cadre du processus d’installation d’extension.

> [!Note]
> Au minimum, toutes les extensions doivent spécifier le composant de l’éditeur de base Visual Studio comme condition préalable.

* Modifier le fichier manifeste d’extension (généralement appelé *source.extension.vsixmanifest*).
* S’assurer `InstallationTarget` comprend 15.0.
* Ajouter les conditions préalables à l’installation requises (comme le montre l’exemple ci-dessous).
  * Nous vous recommandons de spécifier uniquement les Œd composant pour les conditions préalables à l’installation.
  * Voir la section à la fin de ce document pour [les instructions sur l’identification des identifiants composant](#find-component-ids).

Exemple :

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

### <a name="option-use-the-designer-to-make-changes-to-the-vsix-extension-manifest"></a>Option : Utilisez le concepteur pour apporter des modifications au manifeste d’extension VSIX

Au lieu d’éditer directement le manifeste XML, vous pouvez utiliser le nouvel onglet **Prerequisites** dans le Concepteur Manifeste pour sélectionner les conditions préalables et le XML sera mis à jour pour vous.

> [!Note]
> Le Concepteur Manifeste ne vous permettra de sélectionner que les composants (pas les charges de travail ou les paquets) qui sont installés sur l’instance Visual Studio actuelle. Si vous avez besoin d’ajouter une condition préalable pour une charge de travail, un paquet ou un composant qui n’est pas actuellement installé, modifiez directement le XML manifeste.

* Fichier Open *source.extension.vsixmanifest [Design].*
* Sélectionnez **l’onglet Prerequisites** et appuyez sur **le nouveau** bouton.

   ![CONCEPTEUR manifeste VSIX](media/vsix-manifest-designer.png)

* La **fenêtre Add New Prerequisite** s’ouvrira.

   ![ajouter vsix préalable](media/add-vsix-prerequisite.png)

* Cliquez sur le dropdown pour **le nom** et sélectionnez la condition préalable souhaitée.
* Mettre à jour la version si nécessaire.

   > [!Note]
   > Le champ de version sera pré-peuplé avec la version du composant actuellement installé, avec une gamme couvrant jusqu’à (mais sans inclure) la prochaine version majeure du composant.

   ![ajouter roslyn préalable](media/add-roslyn-prerequisite.png)

* Appuyez sur **OK**.

## <a name="update-debug-settings-for-the-project"></a>Mettre à jour les paramètres de Debug pour le projet

Si vous souhaitez déboiffer votre extension dans une instance expérimentale de Visual Studio, assurez-vous que les paramètres du projet pour**l’action** **Debug** > Start ont le **programme externe Démarrer :** la valeur réglée sur le fichier *devenv.exe* de votre installation Visual Studio 2017.

Il pourrait ressembler à: *C:'Program Files (x86)-Microsoft Visual Studio'2017'Enterprise’Common7'IDE-devenv.exe*

![démarrer un programme externe](media/start-external-program.png)

> [!Note]
> L’action Debug Start est généralement stockée dans le fichier *.csproj.user.* Ce fichier est généralement inclus dans le fichier *.gitignore* et, par conséquent, n’est pas normalement enregistré avec d’autres fichiers de projet lorsqu’il est engagé dans le contrôle source. En tant que tel, si vous avez tiré votre solution fraîchement de contrôle source, il est probable que le projet n’aura pas de valeurs définies pour Démarrer l’action. Les nouveaux projets VSIX créés avec Visual Studio 2017 auront un fichier *.csproj.user* créé avec des défauts pointant vers l’actuel Visual Studio installer répertoire. Toutefois, si vous migrez une extension VSIX v2, il est probable que le fichier *.csproj.user* contiendra des références à l’annuaire d’installation de la version Visual Studio précédente. Définir la valeur de > **l’action** **Debug**Start permettra à l’instance expérimentale Visual Studio correcte de lancer lorsque vous essayez de déboiser votre extension.

## <a name="check-that-the-extension-builds-correctly-as-a-vsix-v3"></a>Vérifiez que l’extension se construit correctement (sous forme de VSIX v3)

* Construire le projet VSIX.
* Décomez le VSIX généré.
  * Par défaut, le fichier VSIX vit à l’intérieur *du bac/Debug* ou *du bac/Release* sous le nom *de [YourCustomExtension].vsix*.
  * Rebaptisez *.vsix* pour *.zip* pour afficher facilement le contenu.
* Vérifiez l’existence de trois fichiers :
  * *extension.vsixmanifest*
  * *manifest.json*
  * *catalog.json*

## <a name="check-when-all-required-prerequisites-are-installed"></a>Vérifiez quand toutes les conditions préalables requises sont installées

Test que le VSIX installe avec succès sur une machine avec toutes les conditions préalables requises installées.

> [!Note]
> Avant d’installer toute extension, veuillez fermer tous les instances de Visual Studio.

Tentative d’installation de l’extension :

* Sur Visual Studio 2017

![INSTALLateur VSIX sur Visual Studio 2017](media/vsixinstaller-vs-2017.png)

* Facultatif: Vérifiez les versions précédentes de Visual Studio.
  * Prouve la compatibilité vers l’arrière.
  * Devrait travailler pour Visual Studio 2012, Visual Studio 2013, Visual Studio 2015.
* Option : Vérifiez que VSIX InstallAteur Version Checker offre un choix de versions.
  * Inclut les versions précédentes de Visual Studio (si elle est installée).
  * Inclut Visual Studio 2017.

Si Visual Studio a été récemment ouvert, vous pourriez voir une boîte de dialogue comme ceci:

![vs processus d’exécution](media/vs-running-processes.png)

Attendez que les processus s’arrêtent ou que les tâches terminent manuellement. Vous pouvez trouver les processus par le nom énuméré, ou avec la MIP énumérée dans la parenthèse.

> [!Note]
> Ces processus ne s’éteignent pas automatiquement pendant qu’une instance de Visual Studio est en cours d’exécution. Assurez-vous que vous avez arrêté toutes les instances de Visual Studio sur la machine - y compris celles d’autres utilisateurs, puis continuer à réessayer.

## <a name="check-when-missing-the-required-prerequisites"></a>Vérifier lorsqu’il manque les conditions préalables requises

* Tentative d’installer l’extension sur une machine avec Visual Studio 2017 qui ne contient PAS tous les composants définis dans les Prérequis (ci-dessus).
* Vérifiez que l’installation identifie le composant/s manquant et les énumère comme condition préalable dans le VSIXInstaller.
* Remarque : L’élévation sera nécessaire si des conditions préalables doivent être installées avec l’extension.

![vsixinstaller manquant la condition préalable](media/vsixinstaller-missing-prerequisite.png)

## <a name="decide-on-components"></a>Décider des composants

Lorsque vous cherchez vos dépendances, vous constaterez qu’une dépendance pourrait cartographier plusieurs composants. Pour déterminer quelles dépendances vous devez spécifier comme votre condition préalable, nous vous suggérons de choisir un composant qui a une fonctionnalité similaire à votre extension et de considérer également vos utilisateurs et quel type de composants auraient-ils très probablement installé ou ne serait pas l’esprit d’installation. Nous vous suggérons également de construire vos extensions d’une manière où les conditions préalables requises ne satisfont qu’au minimum qui permettra à votre extension de fonctionner et pour des fonctionnalités supplémentaires, les faire dormir si certains composants ne sont pas détectés.

Pour fournir des indications supplémentaires, nous avons identifié quelques types communs d’extension et leurs conditions préalables suggérées :

Type d'extension | Nom d’affichage | id
--- | --- | ---
Éditeur | Éditeur de base de Visual Studio | Microsoft.VisualStudio.Component.CoreEditor
Roslyn | C# et Visual Basic | Microsoft.VisualStudio.Component.Roslyn.LanguageServices
WPF | Managed Desktop Workload Core | Microsoft.VisualStudio.Component.ManagedDesktop.Core
Débogueur | Débogueur juste-à-temps | Microsoft.VisualStudio.Component.Debugger.JustInTime

## <a name="find-component-ids"></a>Trouver des ID composant

La liste des composants triés par le produit Visual Studio est à [Visual Studio 2017 charge de travail et les composants ID .](/visualstudio/install/workload-and-component-ids?view=vs-2019) Utilisez ces composants IDs pour vos demandes d’emploi préalables dans votre manifeste.

Si vous n’êtes pas sûr quel composant contient un binaire spécifique, téléchargez la [feuille de calcul de cartographie binaire composant->.](https://aka.ms/vs2017componentid-binaries)

### <a name="vs2017-componentbinarymappingxlsx"></a>vs2017-ComponentBinaryMapping.xlsx

Il ya quatre colonnes dans la feuille Excel: **Nom des composants**, **ComponentId**, **Version**, et Binaire / Noms **de fichiers**.  Vous pouvez utiliser les filtres pour rechercher et trouver des composants et des binaires spécifiques.

Pour toutes vos références, déterminez d’abord celles qui sont dans le composant de base (Microsoft.VisualStudio.Component.CoreEditor).  Au minimum, nous exigeons que le composant de base de l’éditeur soit spécifié comme condition préalable à toutes les extensions. Parmi les références qui restent qui ne sont pas dans l’éditeur de base, ajouter des filtres dans la section **Binaires / Noms de fichiers** pour trouver des composants qui ont l’un des sous-ensembles de ces références.

Exemples :

* Si vous disposez d’une extension de débbugger et que vous savez que votre projet a une référence à *VSDebugEng.dll* et *VSDebug.dll*, cliquez sur le bouton filtre dans **l’en-tête Binaries / Files Names.**  Recherchez "VSDebugEng.dll" et sélectionnez *OK*.  Cliquez ensuite sur le bouton filtre dans l’en-tête **des binaires / fichiers noms** à nouveau et la recherche de "VSDebug.dll".  Sélectionnez la case à cocher **Ajouter la sélection de courant pour filtrer** et sélectionner **OK**.  Maintenant, regardez à travers le **nom de composant** pour trouver un composant qui est le plus lié à votre type d’extension. Dans cet exemple, vous choisiriez le débbuggeur Just-In-Time et l’ajouteriez à votre vsixmanifest.
* Si vous savez que votre projet traite d’éléments débbuggeurs, vous pouvez rechercher sur "debugger" dans la boîte de recherche de filtre pour voir quels composants contiennent de débbugger en son nom.

## <a name="specify-a-visual-studio-2017-release"></a>Spécifier une version Visual Studio 2017

Si votre extension nécessite une version spécifique de Visual Studio 2017, par exemple, cela dépend d’une fonctionnalité sortie en 15.3, vous devez spécifier le numéro de build dans votre **installation VSIXTarget**. Par exemple, la version 15.3 a un nombre de build de '15.0.26730.3'. Vous pouvez voir la cartographie des versions pour construire des nombres [ici](../install/visual-studio-build-numbers-and-release-dates.md). L’utilisation du numéro de version '15.3' ne fonctionnera pas correctement.

Si votre extension nécessite 15,3 ou plus, vous déclareriez la **version InstallationTarget** comme [15.0.26730.3, 16.0):

```xml
<Installation>
  <InstallationTarget Id="Microsoft.VisualStudio.Community" Version="[15.0.26730.3, 16.0)" />
</Installation>
```
