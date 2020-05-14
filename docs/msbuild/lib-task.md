---
title: Tâche LIB | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VC.Project.VCLibrarianTool.Name
- VC.Project.VCLibrarianTool.TreatLibWarningsAsErrors
- VC.Project.VCLibrarianTool.Verbose
- vc.task.lib
- VC.Project.VCLibrarianTool.ErrorReporting
- VC.Project.VCLibrarianTool.LinkLibraryDependencies
- VC.Project.VCLibrarianTool.LinkTimeCodeGeneration
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- MSBuild (C++), LIB task
- LIB task (MSBuild (C++))
ms.assetid: e062c7f9-cc69-4a83-9361-1bb5355e5fe8
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a5794d059a17f39531a7788895b604ae0e9590ce
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633588"
---
# <a name="lib-task"></a>LIB (tâche)

Enveloppe l’outil Microsoft 32-Bit Library Manager, *lib.exe*. Le gestionnaire de bibliothèques crée et gère une bibliothèque de fichiers objets COFF (Common Object File Format). Il peut également créer des fichiers d'exportation et des bibliothèques d'importation pour référencer des définitions exportées. Pour plus d’informations, voir [lib reference](/cpp/build/reference/lib-reference) et [Running LIB](/cpp/build/reference/running-lib).

## <a name="parameters"></a>Paramètres

 Le tableau ci-dessous décrit les paramètres de la tâche **LIB**. La plupart des paramètres de tâche correspondent à une option de ligne de commande.

|Paramètre|Description|
|---------------|-----------------|
|**AdditionalDependencies**|Paramètre **de chaîne en** option.<br /><br /> Spécifie les éléments supplémentaires à ajouter à la ligne de commande.|
|**AdditionalLibraryDirectories**|Paramètre **de chaîne en** option.<br /><br /> Substitue le chemin d’accès de la bibliothèque d’environnement. Spécifiez un nom de répertoire.<br /><br /> Pour plus d’informations, consultez l’article [/LIBPATH (Autre chemin de bibliothèque)](/cpp/build/reference/libpath-additional-libpath).|
|**Options supplémentaires**|Paramètre **de chaîne** facultatif.<br /><br /> Une liste d’options *lib.exe* comme spécifié sur la ligne de commande. Par exemple, /\<option1> /\<option2> /\<option#>. Utilisez ce paramètre pour spécifier les options *lib.exe* qui ne sont pas représentées par un autre paramètre de tâche **LIB.**<br /><br /> Pour plus d’informations, consultez [Exécution de LIB](/cpp/build/reference/running-lib).|
|**DisplayLibrary**|Paramètre **de chaîne** facultatif.<br /><br /> Affiche des informations sur la bibliothèque de sortie. Spécifiez un nom de fichier pour rediriger les informations vers un fichier. Spécifiez « CON » ou ne spécifiez rien pour rediriger les informations vers la console.<br /><br /> Ce paramètre correspond à l’option **/LIST** de *lib.exe*.|
|**ErreurReporting**|Paramètre **de chaîne** facultatif.<br /><br /> Specifie comment envoyer des informations d’erreur interne à Microsoft si *lib.exe* échoue au moment de l’exécution.<br /><br /> Spécifiez l'une des valeurs suivantes, chacune d'elles correspondant à une option de ligne de commande.<br /><br /> -   **NoErrorReport** - **/ERRORREPORT:NONE**<br />-   **PromptImmediately** - **/ERRORREPORT:PROMPT**<br />-   **File d’attenteForNextLogin** - **/ERRORREPORT:QUEUE**<br />-   **SendErrorReport** - **/ERRORREPORT:SEND**<br /><br /> Pour plus d’informations, consultez l’option de ligne de commande **/ERRORREPORT** dans [Exécution de LIB](/cpp/build/reference/running-lib).|
|**ExportNamedFunctions**|Paramètre **de chaîne en** option.<br /><br /> Spécifie une ou plusieurs fonctions à exporter.<br /><br /> Ce paramètre correspond à **l’option /EXPORT:** de *lib.exe*.|
|**ForceSymbolReferences**|Paramètre **de chaîne** facultatif.<br /><br /> Forces *lib.exe* d’inclure une référence au symbole spécifié.<br /><br /> Ce paramètre correspond à la **/INCLUDE:** option de *lib.exe*.|
|**IgnoreAllDefaultLibraries**|Paramètre `Boolean` facultatif.<br /><br /> Si `true`, supprime toutes les bibliothèques par défaut de la liste des bibliothèques que *lib.exe* recherche quand il résout les références externes.<br /><br /> Ce paramètre correspond à la forme sans paramètres de l’option **/NODEFAULTLIB** de *lib.exe*.|
|**IgnoreSpecificDefaultLibraries**|Paramètre **de chaîne en** option.<br /><br /> Supprime les bibliothèques spécifiées de la liste des bibliothèques que *lib.exe* recherche lorsqu’elle résout les références externes.<br /><br /> Ce paramètre correspond à l’option **/NODEFAULTLIB** de `library` *lib.exe* qui prend un argument.|
|**LinkLibraryDependencies**|Paramètre `Boolean` facultatif.<br /><br /> Si la valeur est `true`, spécifie que les sorties de bibliothèque émanant des dépendances du projet sont automatiquement liées.|
|**LinkTimeCodeGeneration**|Paramètre `Boolean` facultatif.<br /><br /> Si la valeur est `true`, spécifie la génération du code durant l'édition de liens.<br /><br /> Ce paramètre correspond à l’option **/LCTG** de *lib.exe*.|
|**MinimumRequiredVersion**|Paramètre **de chaîne** facultatif.<br /><br /> Spécifie la version minimale requise du sous-système. Spécifiez la liste, délimitée par des virgules, de nombres décimaux compris entre 0 et 65535.|
|**ModuleDefinitionFile**|Paramètre **de chaîne** facultatif.<br /><br /> Spécifie le nom du fichier module-définition (*.def*).<br /><br /> Ce paramètre correspond à l’option **/DEF** de `filename` *lib.exe* qui prend un argument.|
|**Nom   **|Paramètre **de chaîne** facultatif.<br /><br /> Lors de la génération d'une bibliothèque d'importation, spécifie le nom de la DLL pour laquelle la bibliothèque d'importation est générée.<br /><br /> Ce paramètre correspond à l’option **/NAME** de `filename` *lib.exe* qui prend un argument.|
|**Outputfile**|Paramètre **de chaîne** facultatif.<br /><br /> Remplace le nom par défaut et l’emplacement du programme que *lib.exe* crée.<br /><br /> Ce paramètre correspond à l’option **/OUT** de `filename` *lib.exe* qui prend un argument.|
|**RemoveObjects**|Paramètre **de chaîne en** option.<br /><br /> Omet l'objet spécifié de la bibliothèque de sortie. *Lib.exe* crée une bibliothèque de sortie en combinant tous les objets (que ce soit dans les fichiers d’objets ou les bibliothèques), puis en supprimant tous les objets spécifiés par cette option.<br /><br /> Ce paramètre correspond à l’option **/REMOVE** de `membername` *lib.exe* qui prend un argument.|
|**récentes**|Paramètre `ITaskItem[]` requis.<br /><br /> Spécifie la liste des fichiers sources séparés par des espaces.|
|**Sous-système**|Paramètre **de chaîne** facultatif.<br /><br /> Spécifie l'environnement pour l'exécutable. Le choix du sous-système affecte le symbole de point d'entrée ou la fonction de point d'entrée.<br /><br /> Spécifiez l'une des valeurs suivantes, chacune d'elles correspondant à une option de ligne de commande.<br /><br /> -   **Console** - **/SUBSYSTEM:CONSOLE**<br />-   **Windows** - **/SUBSYSTEM:WINDOWS**<br />-   **Native** - **/SUBSYSTEM:NATIVE**<br />-   **Demande EFI** - **/SUBSYSTEM:EFI_APPLICATION**<br />-   **EFI Boot Service Driver** - **/SUBSYSTEM:EFI_BOOT_SERVICE_DRIVER**<br />-   **EFI ROM** - **/SUBSYSTEM:EFI_ROM**<br />-   **EFI Runtime** - **/SUBSYSTEM:EFI_RUNTIME_DRIVER**<br />-   **WindowsCE** - **/SUBSYSTEM:WINDOWSCE**<br />-   **POSIX** - **/SOUS-SYSTÈME:POSIX**<br /><br /> Pour plus d’informations, consultez l’article [/SUBSYSTEM (Spécifier le sous-système)](/cpp/build/reference/subsystem-specify-subsystem).|
|**SuppressStartupBanner**|Paramètre **Boolean** optionnel.<br /><br /> Si la valeur est `true`, empêche l'affichage du message de copyright et de numéro de version quand la tâche démarre.<br /><br /> Pour plus d’informations, consultez l’option **/NOLOGO** dans [Exécution de LIB](/cpp/build/reference/running-lib).|
|**TargetMachine**|Paramètre **de chaîne** facultatif.<br /><br /> Spécifie la plateforme cible du programme ou de la DLL.<br /><br /> Spécifiez l'une des valeurs suivantes, chacune d'elles correspondant à une option de ligne de commande.<br /><br /> -   **MachineARM** - **/MACHINE:ARM**<br />-   **MachineEBC** - **/MACHINE:EBC**<br />-   **MachineIA64** - **/MACHINE:IA64**<br />-   **MachineMIPS** - **/MACHINE:MIPS**<br />-   **MachineMIPS16** - **/MACHINE:MIPS16**<br />-   **MachineMIPSFPU** -**/MACHINE:MIPSFPU**<br />-   **MachineMIPSFPU16** - **/MACHINE:MIPSFPU16**<br />-   **MachineSH4** - **/MACHINE:SH4**<br />-   **MachineTHUMB** - **/MACHINE:THUMB**<br />-   **MachineX64** - **/MACHINE:X64**<br />-   **MachineX86** - **/MACHINE:X86**<br /><br /> Pour plus d’informations, voir [/MACHINE (Specify target platform)](/cpp/build/reference/machine-specify-target-platform).|
|**TrackerLogDirectory**|Paramètre **de chaîne** facultatif.<br /><br /> Spécifie le répertoire du journal de Tracker.|
|**TreatLibWarningAsErrors**|Paramètre **Boolean** optionnel.<br /><br /> Si `true`, provoque la tâche **LIB** de ne pas générer un fichier de sortie si *lib.exe* génère un avertissement. Si la valeur est `false`, un fichier de sortie est généré.<br /><br /> Pour plus d’informations, consultez l’option **/WX** dans [Exécution de LIB](/cpp/build/reference/running-lib).|
|**UseUnicodeResponseFiles**|Paramètre **Boolean** optionnel.<br /><br /> Si la valeur est `true`, indique au système de projet de générer des fichiers réponse UNICODE quand le générateur de bibliothèques est créé dynamiquement. Spécifiez `true` quand les fichiers du projet ont des chemins d'accès UNICODE.|
|**Verbose**|Paramètre **Boolean** optionnel.<br /><br /> Si `true`, affiche des détails sur l’avancement de la session; cela inclut les noms des fichiers *.obj* ajoutés. Les informations sont envoyées vers la sortie standard et peuvent être redirigées vers un fichier.<br /><br /> Pour plus d’informations, consultez l’option **/VERBOSE** dans [Exécution de LIB](/cpp/build/reference/running-lib).|

## <a name="see-also"></a>Voir aussi

- [Informations de référence sur les tâches](../msbuild/msbuild-task-reference.md)