---
title: "Comment : migrer les projets d’extensibilité pour Visual Studio 2017 | Documents Microsoft"
ms.custom: 
ms.date: 11/09/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8ca07b00-a3ff-40ab-b647-c0a93b55e86a
caps.latest.revision: 1
author: gregvanl
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 09f14e5b28a506d4f2112f82ee4fd6b0855a8f93
ms.openlocfilehash: 67e143e1b95a0e4d881d7d6bccae0d7445897aa2
ms.lasthandoff: 02/22/2017

---
# <a name="how-to-migrate-extensibility-projects-to-visual-studio-2017"></a>Comment : migrer les projets d’extensibilité pour Visual Studio 2017

>**Remarque :** cette documentation est préliminaire et en fonction de la version de Visual Studio 2017 RC.

Ce document explique comment mettre à niveau des projets d’extensibilité pour Visual Studio 2017. En plus de décrire comment mettre à jour les fichiers de projet, il décrit également la mise à niveau à partir de la version du manifeste extension 2 (v2 VSIX) vers la nouvelle version 3 manifest format VSIX (VSIX v3).

## <a name="install-visual-studio-2017-rc-with-required-workloads"></a>Installer Visual Studio 2017 RC avec les charges de travail requis

Assurez-vous que votre installation inclut les charges de travail suivants :

* Développement bureautique .NET
* Développement d’une extension Visual Studio

## <a name="open-vsix-solution-in-visual-studio-2017"></a>Ouvrez la Solution VSIX dans Visual Studio 2017

Tous les projets VSIX nécessite une mise à niveau définitive version majeure à Visual Studio 2017.

Le fichier projet (*.csproj par exemple) est actualisé :

* MinimumVisualStudioVersion - maintenant la valeur 15.0
* OldToolsVersion (s’il existe déjà)-maintenant la valeur 14.0

## <a name="update-the-microsoftvssdkbuildtools-nuget-package"></a>Mise à jour du package NuGet de Microsoft.VSSDK.BuildTools

>**Remarque :** si votre solution ne référence pas le package NuGet de Microsoft.VSSDK.BuildTools, vous pouvez ignorer cette étape.

Pour générer votre extension dans le nouveau v3 VSIX format (version 3), votre solution doit être créée avec les nouveaux outils de génération de VSSDK. Elle sera installée avec Visual Studio 2017 RC, mais votre extension de v2 VSIX peut contenir une référence à une version plus ancienne via NuGet. Dans ce cas, vous devrez installer manuellement une mise à jour du package NuGet de Microsoft.VSSDK.BuildTools pour votre solution. Au moment de la version RC, ce package sera en état de « Version préliminaire ».

Pour mettre à jour les références NuGet Microsoft.VSSDK.BuildTools :

* Avec le bouton droit sur la Solution et choisissez **gérer les Packages NuGet pour la Solution...**
* Accédez à la **mises à jour** onglet.
* Cochez la case pour **inclure la version préliminaire**.
* Sélectionnez Microsoft.VSSDK.BuildTools (dernière version).
* Appuyez sur **mise à jour**.

![Outils de génération VSSDK](media/vssdk-build-tools.png)

>**Remarque :** la capture d’écran montre une version différente de la BuildTools. Sélectionnez la version RC.

## <a name="make-changes-to-the-vsix-extension-manifest"></a>Apporter des modifications au manifeste de l’extension VSIX

Pour vous assurer que l’installation de l’utilisateur de Visual Studio dispose de tous les assemblys requis pour exécuter l’extension, spécifiez tous les composants requis ou des packages dans le fichier manifeste d’extension. Lorsqu’un utilisateur tente d’installer l’extension, le VSIXInstaller vérifie si tous les composants requis sont installés. Si certains sont manquants, l’utilisateur sera invité à installer les composants manquants dans le cadre du processus d’installation de l’extension.

* Modifiez le fichier manifeste d’extension (généralement appelé source.extension.vsixmanifest).
* Vérifiez `InstallationTarget` inclut 15.0.
* Ajouter des conditions préalables d’installation requis (comme indiqué dans l’exemple ci-dessous).
  * Nous vous recommandons de que vous spécifiez uniquement les ID de composant Configuration requise pour l’installation.
  * Consultez la section à la fin de ce document pour [obtenir des instructions sur l’identification des identificateurs de composant](#finding-component-ids).

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

### <a name="option-use-the-designer-to-make-changes-to-the-vsix-extension-manifest"></a>Option : Utilisez le concepteur pour apporter des modifications au manifeste de l’extension VSIX

Au lieu de modifier directement le manifeste XML, vous pouvez utiliser la nouvelle **conditions préalables** onglet dans le Concepteur de manifeste pour sélectionner les composants requis et le code XML sera actualisée pour vous.

>**Remarque :** le Concepteur de manifestes vous autorisera uniquement sélectionner les composants (pas les charges de travail ou les Packages) qui sont installés sur l’instance actuelle de Visual Studio. Si vous devez ajouter une condition préalable pour une charge de travail, le package ou le composant n’est pas installé, modifiez directement le manifeste XML.

* Ouvrez le fichier source.extension.vsixmanifest [Design].
* Sélectionnez **conditions préalables** onglet et appuyez sur **nouveau** bouton.

  ![Concepteur de manifeste VSIX](media/vsix-manifest-designer.png)

* Le **ajouter nouvelle vérification** fenêtre s’ouvre.

  ![ajouter la condition préalable vsix](media/add-vsix-prerequisite.png)

* Cliquez sur la liste déroulante pour **nom** et sélectionnez la configuration requise de votre choix.
* Si nécessaire, mettez à jour la version.

  >Remarque : La version de champ sera préremplie avec la version du composant actuellement installé, avec une plage couvrant jusqu'à (mais ne contient ne pas les) la prochaine version majeure du composant.

  ![ajouter la condition préalable roslyn](media/add-roslyn-prerequisite.png)

* Press **OK**.

## <a name="if-migrating-from-preview-4-or-preview-5"></a>Si une migration à partir de la version préliminaire 4 ou 5 de la version préliminaire

* Remplacez `SetupDependencies` avec `Prerequisites` et déplacer les éléments de la `Installer` élément. `Prerequisites`maintenant les pagination directement dans le `PackageManifest` élément.
* [Facultatif] Supprimer le `GenerateVsixV3` élément. (Cela était requis dans les 5 en version préliminaire uniquement.) Le `GenerateVsixV3` élément sera ignoré dans les versions supérieures à 5 de la version préliminaire.

## <a name="update-debug-settings-for-project"></a>Mettre à jour les paramètres de débogage pour le projet

Si vous souhaitez déboguer votre extension dans une instance expérimentale de Visual Studio, assurez-vous que les paramètres du projet pour **Debug** > **action de démarrage** a le **démarrer le programme externe :** valeur définie dans le fichier devenv.exe de votre installation Visual Studio 2017.

Cela peut ressembler :

```
C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\devenv.exe
```

![Démarrer le programme externe](media/start-external-program.png)

>**Remarque :** l’Action de démarrage de débogage est généralement stockée dans la. csproj.user fichier. Ce fichier est généralement inclus dans le fichier .gitignore et, par conséquent, est normalement pas enregistré avec d’autres fichiers de projet lorsque engagé à contrôle de code source. Par conséquent, si vous avez extrait votre solution immédiate à partir du contrôle de code source, il est probablement que le projet n’aura aucune valeur définie pour l’Action de démarrage. Nouveaux projets VSIX créés avec Visual Studio 2017 aura une. csproj.user les fichiers créés avec les valeurs par défaut qui pointe vers le répertoire d’installation de Visual Studio en cours. Toutefois si vous effectuez une migration d’une extension VSIX v2, il est probable que le. csproj.user fichier contiendra des références au répertoire d’installation de la version précédente Visual Studio. Configurez la valeur de **Debug** > **action de démarrage** permettra l’instance expérimentale de Visual Studio correcte à lancer lorsque vous essayez de déboguer votre extension.

## <a name="check-that-the-extension-builds-correctly-as-a-vsix-v3"></a>Vérifiez que l’extension se génère correctement (comme un v3 VSIX)

* Générez le projet VSIX.
* Décompressez le projet VSIX généré.
  * Par défaut, la vie du fichier VSIX dans bin/Debug ou bin/Release en tant que fichier .vsix [YourCustomExtension].
  * Renommez .vsix .zip pour afficher facilement le contenu.
* Vérifier l’existence de trois fichiers :
  * extension.vsixmanifest
  * manifest.JSON
  * Catalog.JSON

## <a name="check-when-all-required-prerequisites-are-installed"></a>Vérification de tous les composants requis sont installés.

Vérifiez que l’extension VSIX s’installe correctement sur un ordinateur avec tous les composants requis installés.

>**Remarque :** avant d’installer n’importe quelle extension, arrêtez toutes les instances de Visual Studio.

Essayez d’installer l’extension :

* Dans Visual Studio 2017 RC

![Programme d’installation de l’extension VSIX dans Visual Studio 2017](media/vsixinstaller-vs-2017.png)

* Facultatif : Vérifier les versions précédentes de Visual Studio.
  * Afin de garantir la compatibilité descendante.
  * Doit fonctionner pour Visual Studio 2012, Visual Studio 2013, Visual Studio 2015.
* Facultatif : Vérifiez que le vérificateur de Version du programme d’installation VSIX propose un choix des versions.
  * Comprend des versions antérieures de Visual Studio (si installé).
  * Inclut Visual Studio 2017 RC.

Si Visual Studio a été récemment ouvert, vous pouvez voir une boîte de dialogue comme suit :

![processus en cours d’exécution de Visual Studio](media/vs-running-processes.png)

Attendez que les processus s’est arrêté ou arrêtez manuellement les tâches. Vous trouverez les processus par le nom répertorié, ou avec le PID figure entre parenthèses.

>**Remarque :** ces processus automatiquement éteindra pas pendant l’exécution d’une instance de Visual Studio. Assurez-vous que vous avez arrêtez toutes les instances de Visual Studio sur l’ordinateur, y compris celles des autres utilisateurs, puis réessayera.

## <a name="check-when-missing-the-required-prerequisites"></a>Contrôle lorsqu’il manque les composants requis

* Essayez d’installer l’extension sur un ordinateur avec Visual Studio 2017 RC ne contenant tous les composants définis dans les conditions préalables (ci-dessus).
* Vérifiez que l’installation identifie le composant manquant/s et les affiche comme une condition préalable dans la VSIXInstaller.
* Remarque : Une élévation sera nécessaire si les conditions préalables doivent être installés avec l’extension.

![élément requis manquant vsixinstaller](media/vsixinstaller-missing-prerequisite.png)

## <a name="deciding-on-components"></a>Décidez de composants

Recherche de vos dépendances, vous constaterez qu’une dépendance peut être mappé à plusieurs composants. Pour déterminer quelles sont les dépendances vous devez spécifier en tant que votre condition préalable, nous vous recommandons que vous choisissez un composant qui a une fonctionnalité similaire à votre extension et à également prendre en compte vos utilisateurs et le type de composants est très probablement avoir installée ou n’aurait pas à l’esprit l’installation. Il est conseillé de créer vos extensions de façon où les conditions préalables requises répondent aux seuls minimales qui permettra à votre extension s’exécute et des fonctionnalités supplémentaires sont dormantes si certains composants ne sont pas détectés.

Pour obtenir des conseils complémentaires, nous avons identifié quelques types d’extension communs et leurs connaissances préalables requises :

Type d’extension | Nom complet |    Id
--- | --- | ---
Éditeur | Éditeur principal de Visual Studio    | Microsoft.VisualStudio.CoreEditor
Roslyn | C# et Visual Basic | Microsoft.VisualStudio.Component.Roslyn.LanguageServices
WPF | Cœur de la charge de travail de bureau géré | Microsoft.VisualStudio.Component.ManagedDesktop.Core
Débogueur | Débogueur juste-à-temps | Microsoft.VisualStudio.Component.Debugger.JustInTime

## <a name="finding-component-ids"></a>Recherche d’ID de composant

La liste des composants, triées par produit Visual Studio se trouve [ID de composant et de charge de travail de Visual Studio 2017](https://aka.ms/vs2017componentIDs). Utiliser ces ID de composant pour votre ID requis dans votre manifeste.

Si vous ne savez pas quel composant contient un téléchargement spécifique binaire, le [composant-> Feuille de calcul de mappage binaire](https://aka.ms/vs2017componentid-binaries).

### <a name="vs2017-componentbinarymappingxlsx"></a>vs2017-ComponentBinaryMapping.xlsx

Il existe quatre colonnes dans la feuille Excel : **nom du composant**, **ComponentId**, **Version**, et **binaire / noms de fichiers**.  Vous pouvez utiliser les filtres pour rechercher les fichiers binaires et des composants spécifiques.

Pour toutes les références, vous devez d’abord déterminer celles qui sont dans le composant éditeur (Microsoft.VisualStudio.Component.CoreEditor) de base.  Au minimum, nous demandons le composant éditeur principal d’être spécifiés comme un composant requis pour toutes les extensions. Des références restantes qui ne sont pas dans l’éditeur de base, ajouter des filtres dans les **binaires / noms de fichiers** section trouver les composants qui ont le sous-ensemble de ces références.

Exemples :

* Si vous disposez d’une extension de débogueur et que vous savez que votre projet a une référence à VSDebugEng.dll et VSDebug.dll, cliquez sur le bouton de filtre dans le **binaires / noms de fichiers** en-tête.  Recherchez « VSDebugEng.dll » et sélectionnez OK.  Ensuite, cliquez sur le bouton de filtrage dans le **binaires / noms de fichiers** en-tête à nouveau et recherchez « VSDebug.dll ».  Sélectionnez la case à cocher « Sélection actuelle ajouter au filtre » et sélectionnez OK.  Examinez maintenant la **nom du composant** pour rechercher un composant qui est le plus liées à votre type d’extension. Dans cet exemple, serait choisie juste-à-temps du débogueur et l’ajouter à votre vsixmanifest.
* Si vous savez que votre projet traite des éléments du débogueur, vous pouvez rechercher « débogueur » dans la zone de filtre de recherche pour voir quels sont les composants contiennent le débogueur dans son nom.
