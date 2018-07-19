---
title: 'Comment : migrer des projets d’extensibilité pour Visual Studio 2017 | Documents Microsoft'
ms.custom: ''
ms.date: 11/09/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 8ca07b00-a3ff-40ab-b647-c0a93b55e86a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 93f5d663a31d43dc7a52cbd11261ca78134c682a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31133528"
---
# <a name="how-to-migrate-extensibility-projects-to-visual-studio-2017"></a>Comment : migrer des projets d’extensibilité pour Visual Studio 2017

Ce document explique comment mettre à niveau des projets d’extensibilité pour Visual Studio 2017. En plus de décrire comment mettre à jour les fichiers de projet, il décrit également comment mettre à niveau à partir de la version du manifeste extension 2 (v2 VSIX) vers la nouvelle version 3 format de manifeste VSIX (v3 VSIX).

## <a name="install-visual-studio-2017-with-required-workloads"></a>Installer Visual Studio 2017 avec des charges de travail requis

Assurez-vous que votre installation inclut les charges de travail suivants :

* Développement .NET Desktop
* Développement d’une extension Visual Studio

## <a name="open-vsix-solution-in-visual-studio-2017"></a>Ouvrez la Solution VSIX dans Visual Studio 2017

Tous les projets VSIX nécessite une mise à niveau définitive de version majeure à Visual Studio 2017.

Le fichier projet (par exemple, *.csproj) sera mise à jour :

* Minimumvisualstudioversion par - maintenant la valeur 15.0
* OldToolsVersion (s’il existe déjà)-maintenant la valeur 14.0

## <a name="update-the-microsoftvssdkbuildtools-nuget-package"></a>Mettre à jour le package NuGet de Microsoft.VSSDK.BuildTools

>**Remarque :** si votre solution ne référence pas le package NuGet de Microsoft.VSSDK.BuildTools, vous pouvez ignorer cette étape.

Pour générer votre extension dans la nouvelle v3 VSIX (version 3), format, votre solution doit être généré avec les nouveaux outils de Build extensibilité Visual Studio. Le composant sera installé avec Visual Studio 2017, mais votre extension de v2 VSIX peut contenir une référence à une version plus ancienne via NuGet. Dans ce cas, vous devez installer manuellement une mise à jour du package NuGet de Microsoft.VSSDK.BuildTools pour votre solution.

Pour mettre à jour les références NuGet pour Microsoft.VSSDK.BuildTools :

* Avec le bouton droit sur la Solution et choisissez **gérer les Packages NuGet pour la Solution...**
* Accédez à la **mises à jour** onglet.
* Sélectionnez Microsoft.VSSDK.BuildTools (dernière version).
* Appuyez sur **mise à jour**.

![Outils de génération d’extensibilité Visual Studio](media/vssdk-build-tools.png)

## <a name="make-changes-to-the-vsix-extension-manifest"></a>Modifier le manifeste d’extension VSIX

Pour vous assurer que l’installation de l’utilisateur de Visual Studio dispose de tous les assemblys nécessaires pour exécuter l’extension, spécifiez tous les composants requis ou les packages dans le fichier manifeste d’extension. Lorsqu’un utilisateur tente d’installer l’extension, le VSIXInstaller vérifie si tous les composants requis sont installés. Si certains sont manquants, l’utilisateur sera invité à installer les composants manquants dans le cadre du processus d’installation de l’extension.

>**Remarque :** au minimum, toutes les extensions doivent spécifier le composant de l’éditeur Visual Studio core comme condition préalable.

* Modifier le fichier manifeste d’extension (généralement appelé source.extension.vsixmanifest).
* Vérifiez `InstallationTarget` inclut 15.0.
* Ajouter des conditions préalables d’installation requis (comme indiqué dans l’exemple ci-dessous).
  * Nous vous recommandons de que vous spécifiez uniquement les ID de composant pour les conditions préalables d’installation.
  * Consultez la section à la fin de ce document pour [obtenir des instructions sur l’identification des ID de composant](#finding-component-ids).

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

### <a name="option-use-the-designer-to-make-changes-to-the-vsix-extension-manifest"></a>Option : Utilisez le concepteur pour modifier le manifeste d’extension VSIX

Au lieu de modifier directement le XML du manifeste, vous pouvez utiliser la nouvelle **conditions préalables** onglet dans le Concepteur de manifeste pour sélectionner les composants requis et le code XML sera mise à jour pour vous.

>**Remarque :** le Concepteur de manifeste uniquement vous permettra de sélectionner les composants (pas les charges de travail ou les Packages) qui sont installés sur l’instance actuelle de Visual Studio. Si vous devez ajouter une condition préalable pour une charge de travail, un package ou un composant qui n’est pas installé, modifier directement le XML du manifeste.

* Ouvrez le fichier source.extension.vsixmanifest [Design].
* Sélectionnez **conditions préalables** onglet, puis appuyez sur **nouveau** bouton.

  ![Concepteur de manifeste VSIX](media/vsix-manifest-designer.png)

* Le **ajouter la nouvelle configuration requise** fenêtre s’ouvre.

  ![ajouter le composant requis de vsix](media/add-vsix-prerequisite.png)

* Cliquez sur la liste déroulante pour **nom** et sélectionnez la condition préalable de votre choix.
* Si nécessaire, mettez à jour la version.

  >Remarque : Le champ de version sera prérempli avec la version du composant actuellement installé, avec une plage de fractionnement jusqu'à (sans toutefois l’inclure) la prochaine version principale du composant.

  ![ajouter le composant requis de roslyn](media/add-roslyn-prerequisite.png)

* Press **OK**.

## <a name="update-debug-settings-for-project"></a>Mettre à jour les paramètres de débogage pour le projet

Si vous souhaitez déboguer votre extension dans une instance expérimentale de Visual Studio, assurez-vous que les paramètres du projet pour **déboguer** > **action de démarrage** a le **Démarrer externe programme :** valeur définie dans le fichier devenv.exe de votre installation de Visual Studio 2017.

Il peut ressembler à :

```
C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\devenv.exe
```

![Démarrer le programme externe](media/start-external-program.png)

>**Remarque :** l’Action de démarrage de débogage est généralement stockée dans le. csproj.user fichier. Ce fichier est généralement inclus dans le fichier .gitignore et, par conséquent, est normalement pas enregistré avec d’autres fichiers de projet lors de la validation pour le contrôle de code source. Par conséquent, si vous avez extraite votre solution actualisée à partir du contrôle de code source, il est probable que le projet n’aura aucune valeur définie pour l’Action de démarrage. Nouveaux projets VSIX créées avec Visual Studio 2017 aura un. csproj.user les fichiers créés avec des valeurs par défaut pointant vers le répertoire d’installation de Visual Studio en cours. Toutefois si vous migrez une extension VSIX v2, il est probable que le. csproj.user fichier contiendra des références au répertoire d’installation de la version précédente Visual Studio. Définition de la valeur de **déboguer** > **action de démarrage** autorisera l’instance expérimentale de Visual Studio correct à lancer lorsque vous essayez de déboguer votre extension.

## <a name="check-that-the-extension-builds-correctly-as-a-vsix-v3"></a>Vérifiez que l’extension se génère correctement (comme un v3 VSIX)

* Générez le projet VSIX.
* Décompressez le VSIX généré.
  * Par défaut, la qualité de vie du fichier VSIX dans bin/Debug ou bin/Release en tant que [YourCustomExtension] .vsix.
  * Renommez .vsix .zip permet d’afficher facilement le contenu.
* Vérifier l’existence de trois fichiers :
  * extension.vsixmanifest
  * manifest.JSON
  * Catalog.JSON

## <a name="check-when-all-required-prerequisites-are-installed"></a>Vérification de tous les composants requis sont installés.

Vérifiez que l’extension VSIX est installé correctement sur un ordinateur avec tous les composants requis installés.

>**Remarque :** avant d’installer n’importe quelle extension, arrêtez toutes les instances de Visual Studio.

Essayez d’installer l’extension :

* Dans Visual Studio 2017

![Programme d’installation VSIX dans Visual Studio 2017](media/vsixinstaller-vs-2017.png)

* Facultatif : Vérifiez sur les versions antérieures de Visual Studio.
  * Afin de garantir la compatibilité descendante.
  * Doit fonctionner pour Visual Studio 2012, Visual Studio 2013, Visual Studio 2015.
* Facultatif : Vérifiez que le vérificateur de Version du programme d’installation VSIX offre un choix de versions.
  * Inclut les versions précédentes de Visual Studio (si installé).
  * Inclut Visual Studio 2017.

Si Visual Studio a été récemment ouvert, vous pouvez voir une boîte de dialogue comme suit :

![processus en cours d’exécution de VS](media/vs-running-processes.png)

Attendez que les processus pour l’arrêter ou arrêter manuellement les tâches. Vous trouverez les processus par le nom de liste, ou avec le PID figure entre parenthèses.

>**Remarque :** ces processus pas automatiquement s’arrêtent pendant l’exécution d’une instance de Visual Studio. Assurez-vous que vous avez arrêté à toutes les instances de Visual Studio sur l’ordinateur - y compris ceux d’autres utilisateurs, puis réessayera.

## <a name="check-when-missing-the-required-prerequisites"></a>Vérification de manquant de la configuration requise

* Essayez d’installer l’extension sur un ordinateur avec Visual Studio 2017 est pas contenant tous les composants définis dans les conditions préalables (ci-dessus).
* Vérifiez que l’installation identifie le composant manquant/s et les affiche comme une condition préalable dans la VSIXInstaller.
* Remarque : Élévation sera requise si les composants requis doivent être installés avec l’extension.

![élément requis manquant de vsixinstaller](media/vsixinstaller-missing-prerequisite.png)

## <a name="deciding-on-components"></a>Vous décidez de composants

Recherche de vos dépendances, vous constaterez qu’une dépendance peut mapper à plusieurs composants. Pour déterminer les dépendances dont vous devez spécifier comme votre condition préalable, nous vous suggérons de choisir un composant qui contient une fonctionnalité semblable à votre extension et de considérer également vos utilisateurs et le type de composants est très probablement ont installées ou ne pas, n’oubliez pas l’installation. Il est conseillé de construction de vos extensions d’une manière où les conditions préalables requises satisfont uniquement le minimum qui permettre à votre extension s’exécute et des fonctionnalités supplémentaires sont dormantes si certains composants ne sont pas détectés.

Pour fournir davantage d’aide, nous avons identifié des quelques types courants d’extension et de leurs connaissances préalables requises :

Type d’extension | Nom complet | Id
--- | --- | ---
Éditeur | Éditeur de base de Visual Studio  | Microsoft.VisualStudio.Component.CoreEditor
Roslyn | C# et Visual Basic | Microsoft.VisualStudio.Component.Roslyn.LanguageServices
WPF | Managed Desktop Workload Core | Microsoft.VisualStudio.Component.ManagedDesktop.Core
Débogueur | Débogueur juste-à-temps | Microsoft.VisualStudio.Component.Debugger.JustInTime

## <a name="finding-component-ids"></a>ID de composant de recherche

La liste des composants de triés par produit de Visual Studio se trouve [ID de composant et de charge de travail de Visual Studio 2017](https://aka.ms/vs2017componentIDs). Utiliser ces ID de composant pour votre ID requis dans votre manifeste.

Si vous ne savez pas quel composant contient un téléchargement binaire, spécifique du [composant -> feuille de calcul de mappage de types binaires](https://aka.ms/vs2017componentid-binaries).

### <a name="vs2017-componentbinarymappingxlsx"></a>vs2017-ComponentBinaryMapping.xlsx

Il existe quatre colonnes dans la feuille Excel : **nom du composant**, **ComponentId**, **Version**, et **binaire / noms de fichiers**.  Vous pouvez utiliser les filtres pour rechercher et trouver les fichiers binaires et les composants spécifiques.

Pour toutes les références, vous devez d’abord déterminer celles qui sont dans le composant éditeur (Microsoft.VisualStudio.Component.CoreEditor) de base.  Au minimum, nous avons besoin du composant éditeur principal en tant qu’une condition préalable pour toutes les extensions. Des références restantes qui ne sont pas dans l’éditeur de base, ajoutez des filtres dans les **binaires / noms de fichiers** section pour trouver les composants qui ont du sous-ensemble de ces références.

Exemples :

* Si vous disposez d’une extension de débogueur et que vous savez que votre projet contient une référence à VSDebugEng.dll et VSDebug.dll, cliquez sur le bouton de filtre dans le **binaires / noms de fichiers** en-tête.  Recherchez « VSDebugEng.dll » et sélectionnez OK.  Ensuite, cliquez sur le bouton de filtre dans le **binaires / noms de fichiers** en-tête à nouveau et recherchez « VSDebug.dll ».  Sélectionnez la case à cocher « Sélection actuelle ajouter au filtre », puis sélectionnez OK.  Maintenant ressembler la **nom du composant** pour rechercher un composant qui est le plus liées à votre type d’extension. Dans cet exemple, serait choisis juste-à-temps du débogueur et l’ajouter à votre vsixmanifest.
* Si vous savez que votre projet porte sur les éléments de débogueur, vous pouvez rechercher « débogueur » dans la zone de filtre de recherche pour voir quels composants contiennent le débogueur dans son nom.

## <a name="specifying-a-visual-studio-2017-release"></a>Spécification d’une version de Visual Studio 2017

Si votre extension nécessite une version spécifique de Visual Studio 2017, par exemple, elle dépend d’une fonctionnalité intégrée à 15.3, vous devez spécifier le numéro de build dans votre projet VSIX **le InstallationTarget**. Par exemple, release 15.3 a un numéro de build de '15.0.26730.3'. Vous pouvez voir le mappage des versions à des numéros de build [ici](../install/visual-studio-build-numbers-and-release-dates.md). À l’aide du numéro de version '15.3' ne fonctionnera pas correctement.

Si votre extension requiert 15.3 ou une version ultérieure, vous déclarez le **le InstallationTarget Version** comme [15.0.26730.3, 16.0) :

```xml
<Installation>
  <InstallationTarget Id="Microsoft.VisualStudio.Community" Version="[15.0.26730.3, 16.0)" />
</Installation>
```