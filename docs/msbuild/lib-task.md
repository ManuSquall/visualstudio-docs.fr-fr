---
title: Tâche LIB | Microsoft Docs
description: Découvrez comment MSBuild utilise la tâche LIB pour encapsuler l’outil Gestionnaire de bibliothèques Microsoft 32 bits, lib.exe, qui crée et gère une bibliothèque de fichiers objets COFF.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 2141818c13a187b8afddf337aa11677097940f23
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99913735"
---
# <a name="lib-task"></a>LIB (tâche)

Encapsule l’outil Gestionnaire de bibliothèques Microsoft 32 bits, *lib.exe*. Le gestionnaire de bibliothèques crée et gère une bibliothèque de fichiers objets COFF (Common Object File Format). Il peut également créer des fichiers d'exportation et des bibliothèques d'importation pour référencer des définitions exportées. Pour plus d’informations, consultez [référence lib](/cpp/build/reference/lib-reference) et [exécution de lib](/cpp/build/reference/running-lib).

## <a name="parameters"></a>Paramètres

 Le tableau ci-dessous décrit les paramètres de la tâche **LIB**. La plupart des paramètres de tâche correspondent à une option de ligne de commande.

|Paramètre|Description|
|---------------|-----------------|
|**AdditionalDependencies**|Paramètre **String []** facultatif.<br /><br /> Spécifie les éléments supplémentaires à ajouter à la ligne de commande.|
|**AdditionalLibraryDirectories**|Paramètre **String []** facultatif.<br /><br /> Substitue le chemin d’accès de la bibliothèque d’environnement. Spécifiez un nom de répertoire.<br /><br /> Pour plus d’informations, consultez l’article [/LIBPATH (Autre chemin de bibliothèque)](/cpp/build/reference/libpath-additional-libpath).|
|**AdditionalOptions**|Paramètre de **chaîne** facultatif.<br /><br /> Liste des options de *lib.exe* telles qu’elles sont spécifiées sur la ligne de commande. Par exemple,/ \<option1>  / \<option2>  / \<option#> . Utilisez ce paramètre pour spécifier *lib.exe* options qui ne sont pas représentées par un autre paramètre de tâche **lib** .<br /><br /> Pour plus d’informations, consultez [Exécution de LIB](/cpp/build/reference/running-lib).|
|**DisplayLibrary**|Paramètre de **chaîne** facultatif.<br /><br /> Affiche des informations sur la bibliothèque de sortie. Spécifiez un nom de fichier pour rediriger les informations vers un fichier. Spécifiez « CON » ou ne spécifiez rien pour rediriger les informations vers la console.<br /><br /> Ce paramètre correspond à l’option **/List** de *lib.exe*.|
|**Errorreporting (**|Paramètre de **chaîne** facultatif.<br /><br /> Spécifie comment envoyer des informations d’erreur interne à Microsoft si *lib.exe* échoue au moment de l’exécution.<br /><br /> Spécifiez l'une des valeurs suivantes, chacune d'elles correspondant à une option de ligne de commande.<br /><br /> -   **NoErrorReport**  -  **/errorreport : aucun**<br />-   **PromptImmediately**  -  **/errorreport : invite**<br />-   **QueueForNextLogin**  -  **/errorreport : queue**<br />-   **SendErrorReport**  -  **/errorreport : envoyer**<br /><br /> Pour plus d’informations, consultez l’option de ligne de commande **/ERRORREPORT** dans [Exécution de LIB](/cpp/build/reference/running-lib).|
|**ExportNamedFunctions**|Paramètre **String []** facultatif.<br /><br /> Spécifie une ou plusieurs fonctions à exporter.<br /><br /> Ce paramètre correspond à l’option **/Export :** de *lib.exe*.|
|**ForceSymbolReferences**|Paramètre de **chaîne** facultatif.<br /><br /> Force *lib.exe* à inclure une référence au symbole spécifié.<br /><br /> Ce paramètre correspond à l’option **/include :** de *lib.exe*.|
|**IgnoreAllDefaultLibraries**|Paramètre `Boolean` facultatif.<br /><br /> Si `true` la valeur est, supprime toutes les bibliothèques par défaut de la liste des bibliothèques que *lib.exe* recherche lorsqu’elle résout des références externes.<br /><br /> Ce paramètre correspond à la forme sans paramètre de l’option **/NODEFAULTLIB** de *lib.exe*.|
|**IgnoreSpecificDefaultLibraries**|Paramètre **String []** facultatif.<br /><br /> Supprime les bibliothèques spécifiées de la liste des bibliothèques que *lib.exe* recherche lorsqu’il résout des références externes.<br /><br /> Ce paramètre correspond à l’option **/NODEFAULTLIB** de *lib.exe* qui accepte un `library` argument.|
|**LinkLibraryDependencies**|Paramètre `Boolean` facultatif.<br /><br /> Si la valeur est `true`, spécifie que les sorties de bibliothèque émanant des dépendances du projet sont automatiquement liées.|
|**LinkTimeCodeGeneration**|Paramètre `Boolean` facultatif.<br /><br /> Si la valeur est `true`, spécifie la génération du code durant l'édition de liens.<br /><br /> Ce paramètre correspond à l’option **/LCTG** de *lib.exe*.|
|**MinimumRequiredVersion**|Paramètre de **chaîne** facultatif.<br /><br /> Spécifie la version minimale requise du sous-système. Spécifiez la liste, délimitée par des virgules, de nombres décimaux compris entre 0 et 65535.|
|**ModuleDefinitionFile**|Paramètre de **chaîne** facultatif.<br /><br /> Spécifie le nom du fichier de définition de module (*. def*).<br /><br /> Ce paramètre correspond à l’option **/def** de *lib.exe* qui accepte un `filename` argument.|
|**Nom**|Paramètre de **chaîne** facultatif.<br /><br /> Lors de la génération d'une bibliothèque d'importation, spécifie le nom de la DLL pour laquelle la bibliothèque d'importation est générée.<br /><br /> Ce paramètre correspond à l’option **/Name** de *lib.exe* qui accepte un `filename` argument.|
|**OutputFile**|Paramètre de **chaîne** facultatif.<br /><br /> Remplace le nom et l’emplacement par défaut du programme que *lib.exe* crée.<br /><br /> Ce paramètre correspond à l’option **/out** de *lib.exe* qui accepte un `filename` argument.|
|**RemoveObjects**|Paramètre **String []** facultatif.<br /><br /> Omet l'objet spécifié de la bibliothèque de sortie. *Lib.exe* crée une bibliothèque de sortie en combinant tous les objets (que ce soit dans des fichiers objets ou des bibliothèques), puis en supprimant tous les objets spécifiés par cette option.<br /><br /> Ce paramètre correspond à l’option **/Remove** de *lib.exe* qui accepte un `membername` argument.|
|**Sources**|Paramètre `ITaskItem[]` requis.<br /><br /> Spécifie la liste des fichiers sources séparés par des espaces.|
|**Sous-système**|Paramètre de **chaîne** facultatif.<br /><br /> Spécifie l'environnement pour l'exécutable. Le choix du sous-système affecte le symbole de point d'entrée ou la fonction de point d'entrée.<br /><br /> Spécifiez l'une des valeurs suivantes, chacune d'elles correspondant à une option de ligne de commande.<br /><br /> -   **Console**  -  **/SUBSYSTEM : console**<br />-   **Windows**  -  **/SUBSYSTEM : Windows**<br />-   En **mode natif**  -  **/SUBSYSTEM : Native**<br />-   **Application EFI**  -  **/SUBSYSTEM : EFI_APPLICATION**<br />-   Pilote du service de **démarrage EFI**  -  **/SUBSYSTEM : EFI_BOOT_SERVICE_DRIVER**<br />-   **ROM EFI**  -  **/SUBSYSTEM : EFI_ROM**<br />-   **Runtime EFI**  -  **/SUBSYSTEM : EFI_RUNTIME_DRIVER**<br />-   **WindowsCE**  -  **/SUBSYSTEM : WindowsCE**<br />-   **POSIX**  -  **/SUBSYSTEM : POSIX**<br /><br /> Pour plus d’informations, consultez l’article [/SUBSYSTEM (Spécifier le sous-système)](/cpp/build/reference/subsystem-specify-subsystem).|
|**SuppressStartupBanner**|Paramètre **booléen** facultatif.<br /><br /> Si la valeur est `true`, empêche l'affichage du message de copyright et de numéro de version quand la tâche démarre.<br /><br /> Pour plus d’informations, consultez l’option **/NOLOGO** dans [Exécution de LIB](/cpp/build/reference/running-lib).|
|**TargetMachine**|Paramètre de **chaîne** facultatif.<br /><br /> Spécifie la plateforme cible du programme ou de la DLL.<br /><br /> Spécifiez l'une des valeurs suivantes, chacune d'elles correspondant à une option de ligne de commande.<br /><br /> -   **MachineARM**  -  **/machine : ARM**<br />-   **MachineEBC**  -  **/machine : EBC**<br />-   **MachineIA64**  -  **/Machine : ia64**<br />-   **MachineMIPS**  -  **/machine : mips**<br />-   **MachineMIPS16**  -  **/Machine : MIPS16**<br />-   **MachineMIPSFPU**  - **/machine : MIPSFPU**<br />-   **MachineMIPSFPU16**  -  **/Machine : MIPSFPU16**<br />-   **MachineSH4**  -  **/Machine : sh4**<br />-   **MachineTHUMB**  -  **/machine : Thumb**<br />-   **MachineX64**  -  **/Machine : x64**<br />-   **MachineX86**  -  **/Machine : x86**<br /><br /> Pour plus d’informations, consultez [/machine (spécifier la plateforme cible)](/cpp/build/reference/machine-specify-target-platform).|
|**TrackerLogDirectory**|Paramètre de **chaîne** facultatif.<br /><br /> Spécifie le répertoire du journal de Tracker.|
|**TreatLibWarningAsErrors**|Paramètre **booléen** facultatif.<br /><br /> Si `true` la valeur est, la tâche **lib** ne génère pas de fichier de sortie si *lib.exe* génère un avertissement. Si la valeur est `false`, un fichier de sortie est généré.<br /><br /> Pour plus d’informations, consultez l’option **/WX** dans [Exécution de LIB](/cpp/build/reference/running-lib).|
|**UseUnicodeResponseFiles**|Paramètre **booléen** facultatif.<br /><br /> Si la valeur est `true`, indique au système de projet de générer des fichiers réponse UNICODE quand le générateur de bibliothèques est créé dynamiquement. Spécifiez `true` quand les fichiers du projet ont des chemins d'accès UNICODE.|
|**Verbose**|Paramètre **booléen** facultatif.<br /><br /> Si `true` , affiche des détails sur la progression de la session, y compris les noms des fichiers *. obj* en cours d’ajout. Les informations sont envoyées vers la sortie standard et peuvent être redirigées vers un fichier.<br /><br /> Pour plus d’informations, consultez l’option **/VERBOSE** dans [Exécution de LIB](/cpp/build/reference/running-lib).|

## <a name="see-also"></a>Voir aussi

- [Informations de référence sur les tâches](../msbuild/msbuild-task-reference.md)