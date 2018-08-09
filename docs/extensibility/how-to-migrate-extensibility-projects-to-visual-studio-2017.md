---
title: 'Comment : migrer des projets d’extensibilité vers Visual Studio 2017 | Microsoft Docs'
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
ms.openlocfilehash: 669f3625827d923a0951caa1bb0137d38c0daacc
ms.sourcegitcommit: 06db1892fff22572f0b0a11994dc547c2b7e2a48
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/08/2018
ms.locfileid: "39637495"
---
# <a name="how-to-migrate-extensibility-projects-to-visual-studio-2017"></a>Comment : migrer des projets d’extensibilité vers Visual Studio 2017

Ce document explique comment mettre à niveau des projets d’extensibilité vers Visual Studio 2017. En plus de décrire comment mettre à jour les fichiers projet, il décrit également comment mettre à niveau à partir de la version de manifeste d’extension 2 (v2 VSIX) vers la nouvelle version 3 format de manifeste VSIX (v3 VSIX).

## <a name="install-visual-studio-2017-with-required-workloads"></a>Installez Visual Studio 2017 avec des charges de travail requis

Vérifiez que votre installation inclut les charges de travail suivantes :

* Développement .NET Desktop
* Développement d’une extension Visual Studio

## <a name="open-vsix-solution-in-visual-studio-2017"></a>Ouvrez la Solution VSIX dans Visual Studio 2017

Tous les projets VSIX nécessitera une mise à niveau définitive de version majeure à Visual Studio 2017.

Le fichier projet (par exemple **.csproj*) sera mis à jour :

* Minimumvisualstudioversion par - maintenant la valeur 15.0
* OldToolsVersion (si précédemment existe)-maintenant la valeur 14.0

## <a name="update-the-microsoftvssdkbuildtools-nuget-package"></a>Mettre à jour le package Microsoft.VSSDK.BuildTools NuGet

>**Remarque :** si votre solution ne référence pas le package Microsoft.VSSDK.BuildTools NuGet, vous pouvez ignorer cette étape.

Pour générer votre extension dans le nouveau v3 VSIX format (version 3), votre solution doit être généré avec la nouvelle extensibilité Visual Studio Build Tools. Le composant sera installé avec Visual Studio 2017, mais votre extension de v2 VSIX peut contenir une référence à une version antérieure par le biais de NuGet. Dans ce cas, vous devez installer manuellement une mise à jour du package Microsoft.VSSDK.BuildTools NuGet pour votre solution.

Pour mettre à jour les références NuGet Microsoft.VSSDK.BuildTools :

* Avec le bouton droit sur la solution et choisissez **gérer les Packages NuGet pour la Solution**.
* Accédez à la **mises à jour** onglet.
* Sélectionnez **Microsoft.VSSDK.BuildTools (dernière version)**.
* Appuyez sur **mise à jour**.

![Outils de génération d’extensibilité Visual Studio](media/vssdk-build-tools.png)

## <a name="make-changes-to-the-vsix-extension-manifest"></a>Apportez des modifications au manifeste de l’extension VSIX

Pour vous assurer que l’installation de l’utilisateur de Visual Studio dispose de tous les assemblys requis pour exécuter l’extension, spécifiez tous les composants requis ou les packages dans le fichier manifeste d’extension. Lorsqu’un utilisateur tente d’installer l’extension, le VSIXInstaller vérifie si tous les composants requis sont installés. Si certaines sont manquantes, l’utilisateur sera invité à installer les composants manquants dans le cadre du processus d’installation de l’extension.

>**Remarque :** au minimum, toutes les extensions doivent spécifier le composant de Visual Studio core editor comme condition préalable.

* Modifiez le fichier de manifeste d’extension (généralement appelé *source.extension.vsixmanifest*).
* Vérifiez `InstallationTarget` inclut 15.0.
* Ajouter des conditions préalables d’installation requis (comme indiqué dans l’exemple ci-dessous).
  * Nous vous recommandons de que spécifier uniquement les ID de composant pour les conditions préalables d’installation.
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

### <a name="option-use-the-designer-to-make-changes-to-the-vsix-extension-manifest"></a>Option : Utiliser le concepteur pour apporter des modifications au manifeste de l’extension VSIX

Au lieu de modifier directement le XML du manifeste, vous pouvez utiliser la nouvelle **conditions préalables** onglet dans le Concepteur de manifeste pour sélectionner les conditions préalables et le code XML sera être mises à jour automatiquement.

>**Remarque :** le Concepteur de manifeste uniquement vous permettra de sélectionner les composants (pas les charges de travail ou les Packages) qui sont installés sur l’instance actuelle de Visual Studio. Si vous devez ajouter une condition préalable pour une charge de travail, un package ou un composant qui n’est pas installé, modifiez directement le code XML du manifeste.

* Ouvrez *source.extension.vsixmanifest [Design]* fichier.
* Sélectionnez **prérequis** onglet, puis appuyez sur **New** bouton.

  ![Concepteur de manifeste VSIX](media/vsix-manifest-designer.png)

* Le **ajouter une nouvelle condition préalable** fenêtre s’ouvre.

  ![ajouter la condition préalable vsix](media/add-vsix-prerequisite.png)

* Cliquez sur la liste déroulante pour **nom** et sélectionnez la condition préalable souhaitée.
* Si nécessaire, mettez à jour la version.

  >Remarque : Le champ de version sera prérempli avec la version du composant actuellement installée, avec une plage couvrant jusqu'à (, mais sans inclure) la prochaine version majeure du composant.

  ![ajouter la condition préalable de roslyn](media/add-roslyn-prerequisite.png)

* Appuyez sur **OK**.

## <a name="update-debug-settings-for-the-project"></a>Mettre à jour les paramètres de débogage pour le projet

Si vous souhaitez déboguer votre extension dans une instance expérimentale de Visual Studio, assurez-vous que les paramètres du projet pour **déboguer** > **action de démarrage** a le **Démarrer externe programme :** valeur définie sur le *devenv.exe* fichier de votre installation de Visual Studio 2017.

Cela peut ressembler : *C:\Program Files (x86) \Microsoft Visual Studio\2017\Enterprise\Common7\IDE\devenv.exe*

![Démarrer le programme externe](media/start-external-program.png)

>**Remarque :** l’Action de démarrage de débogage sont généralement stockée dans le *. csproj.user* fichier. Ce fichier est généralement inclus dans le *.gitignore* de fichiers et, par conséquent, n’est pas normalement enregistré avec d’autres fichiers de projet lorsque validées dans le contrôle de code source. Par conséquent, si vous avez extrait votre solution fraîches à partir du contrôle de code source, il est probable que le projet n’aura aucune valeur définie pour l’Action de démarrage. Les nouveaux projets VSIX créés avec Visual Studio 2017 aura un *. csproj.user* fichier créé avec les valeurs par défaut qui pointe vers le répertoire d’installation de Visual Studio en cours. Toutefois si vous migrez une extension de v2 VSIX, il est probable que le *. csproj.user* fichier contiendra des références au répertoire d’installation de la version précédente Visual Studio. Définition de la valeur pour **déboguer** > **action de démarrage** permettra l’instance expérimentale de Visual Studio correcte à lancer lorsque vous essayez de déboguer votre extension.

## <a name="check-that-the-extension-builds-correctly-as-a-vsix-v3"></a>Vérifiez que l’extension se génère correctement (comme un v3 VSIX)

* Générez le projet VSIX.
* Décompressez l’extension VSIX généré.
  * Par défaut, le fichier VSIX réside dans *bin/Debug* ou *bin/Release* comme *[YourCustomExtension] .vsix*.
  * Renommer *.vsix* à *.zip* permettent d’afficher le contenu.
* Vérifier l’existence de trois fichiers :
  * *extension.vsixmanifest*
  * *manifest.JSON*
  * *Catalog.JSON*

## <a name="check-when-all-required-prerequisites-are-installed"></a>Vérification de tous les composants requis sont installés.

Vérifiez que l’extension VSIX s’installe correctement sur un ordinateur avec tous les composants requis installés.

>**Remarque :** avant d’installer n’importe quelle extension, arrêtez toutes les instances de Visual Studio.

Essayez d’installer l’extension :

* Visual Studio 2017

![Programme d’installation VSIX sur Visual Studio 2017](media/vsixinstaller-vs-2017.png)

* Facultatif : Vérifier les versions précédentes de Visual Studio.
  * Prouve la compatibilité descendante.
  * Doit fonctionner avec Visual Studio 2012, Visual Studio 2013, Visual Studio 2015.
* Facultatif : Vérifiez que le vérificateur de Version du programme d’installation VSIX offre un choix de versions.
  * Inclut les versions précédentes de Visual Studio (si installé).
  * Inclut Visual Studio 2017.

Si Visual Studio a été récemment ouvert, vous pouvez voir une boîte de dialogue comme suit :

![processus en cours d’exécution de Visual Studio](media/vs-running-processes.png)

Attendez que les processus à arrêter, ou arrêter manuellement les tâches. Vous trouverez les processus par le nom répertorié, ou avec le PID figure entre parenthèses.

>**Remarque :** ces processus automatiquement éteindra pas pendant l’exécution d’une instance de Visual Studio. Assurez-vous que vous avez arrêté toutes les instances de Visual Studio sur l’ordinateur - y compris ceux d’autres utilisateurs, puis réessayera.

## <a name="check-when-missing-the-required-prerequisites"></a>Vérifier lorsque manque les conditions préalables requises

* Essayez d’installer l’extension sur un ordinateur avec Visual Studio 2017 ne contenant tous les composants définis dans les conditions préalables (ci-dessus).
* Vérifiez que l’installation identifie le composant manquant/s et les affiche comme une condition préalable dans le VSIXInstaller.
* Remarque : Élévation sera nécessaire si les conditions préalables doivent être installés avec l’extension.

![composant requis manquant vsixinstaller](media/vsixinstaller-missing-prerequisite.png)

## <a name="decide-on-components"></a>Choisir des composants

Lorsque vous recherchez vos dépendances, vous trouverez qu’une dépendance peut correspondre à plusieurs composants. Pour déterminer quelles sont les dépendances que vous devez spécifier comme votre condition préalable, nous vous suggérons de choisir un composant qui a une fonctionnalité semblable à votre extension et également prendre en compte vos utilisateurs et quel type de composants est qu’ils très probablement ont installé ou n’oubliez pas l’installation. Nous suggérons également de création de vos extensions d’une manière où les conditions préalables requises satisfont uniquement la valeur minimale qui permettre à votre extension s’exécute et pour des fonctionnalités supplémentaires sont dormantes si certains composants ne sont pas détectés.

Pour donner davantage d’instructions, nous avons identifié quelques types d’extension courants et leurs connaissances préalables requises :

Type d’extension | Nom complet | Id
--- | --- | ---
Éditeur | Éditeur de base de Visual Studio  | Microsoft.VisualStudio.Component.CoreEditor
Roslyn | C# et Visual Basic | Microsoft.VisualStudio.Component.Roslyn.LanguageServices
WPF | Managed Desktop Workload Core | Microsoft.VisualStudio.Component.ManagedDesktop.Core
Débogueur | Débogueur juste-à-temps | Microsoft.VisualStudio.Component.Debugger.JustInTime

## <a name="find-component-ids"></a>Rechercher l’ID de composant

La liste des composants de triés par produit Visual Studio se trouve [ID de composant et de la charge de travail de Visual Studio 2017](https://aka.ms/vs2017componentIDs). Utiliser ces ID de composant pour votre ID requis dans votre manifeste.

Si vous ne savez pas quel composant contient un fichier binaire spécifique, téléchargez le [composant -> feuille de calcul de mappage de types binaires](https://aka.ms/vs2017componentid-binaries).

### <a name="vs2017-componentbinarymappingxlsx"></a>Visual Studio 2017-ComponentBinaryMapping.xlsx

Il existe quatre colonnes dans la feuille Excel : **nom du composant**, **ComponentId**, **Version**, et **binaire / noms de fichiers**.  Vous pouvez utiliser les filtres pour rechercher et trouver les fichiers binaires et des composants spécifiques.

Pour toutes les références, vous devez d’abord déterminer celles qui sont dans le composant d’éditeur (Microsoft.VisualStudio.Component.CoreEditor) core.  Au minimum, nous demandons le composant de l’éditeur principal d’être spécifiés comme un composant requis pour toutes les extensions. Des références restantes qui ne sont pas dans l’éditeur principal, ajoutez des filtres dans les **binaires / noms de fichiers** section Rechercher des composants qui ont le sous-ensemble de ces références.

Exemples :

* Si vous disposez d’une extension de débogage et que vous savez que votre projet a une référence à *VSDebugEng.dll* et *VSDebug.dll*, cliquez sur le bouton de filtre dans le **binaires / noms de fichiers**en-tête.  Recherchez « VSDebugEng.dll » et sélectionnez *OK*.  Cliquez ensuite sur le bouton de filtre dans le **binaires / noms de fichiers** en-tête à nouveau et recherchez « VSDebug.dll ».  Activez la case à cocher **ajouter la sélection actuelle au filtre** et sélectionnez **OK**.  Examinez maintenant le **nom du composant** pour rechercher un composant qui est le plus liées à votre type d’extension. Dans cet exemple, serait choisie juste-à-temps du débogueur et l’ajouter à votre vsixmanifest.
* Si vous savez que votre projet porte sur les éléments de débogueur, vous pouvez rechercher sur « débogueur » dans la zone de recherche de filtre pour voir quels composants contiennent le débogueur dans son nom.

## <a name="specify-a-visual-studio-2017-release"></a>Spécifiez une version de Visual Studio 2017

Si votre extension nécessite une version spécifique de Visual Studio 2017, par exemple, elle dépend d’une fonctionnalité introduite dans la version 15.3, vous devez spécifier le numéro de build dans votre projet VSIX **le InstallationTarget**. Par exemple, la version 15.3 a un numéro de build de '15.0.26730.3'. Vous pouvez voir le mappage des versions pour les numéros de build [ici](../install/visual-studio-build-numbers-and-release-dates.md). À l’aide du numéro de version '15.3' ne fonctionnera pas correctement.

Si votre extension requiert 15.3 ou version ultérieure, vous déclarez le **le InstallationTarget Version** comme [15.0.26730.3, 16.0) :

```xml
<Installation>
  <InstallationTarget Id="Microsoft.VisualStudio.Community" Version="[15.0.26730.3, 16.0)" />
</Installation>
```