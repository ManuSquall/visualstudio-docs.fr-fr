---
title: Informations de référence sur les tâches MSBuild | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, tasks
ms.assetid: b3144b27-a426-4259-b8ae-5f7991b202b6
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cbec3c7c020bae0e94bc16bdb1fe9740a36a93ae
ms.sourcegitcommit: 3154387056160bf4c36ac8717a7fdc0cd9faf3f9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/06/2020
ms.locfileid: "78865321"
---
# <a name="msbuild-task-reference"></a>Informations de référence sur les tâches MSBuild

Les tâches fournissent le code exécuté pendant le processus de génération. Les tâches de la liste suivante sont incluses dans MSBuild. Lorsque la C++ charge de travail est installée, des tâches supplémentaires qui sont utilisées pour C++ générer des projets sont disponibles. Pour plus d’informations, consultez [ C++ tâches](../msbuild/msbuild-tasks-specific-to-visual-cpp.md).

Outre les paramètres répertoriés dans les rubriques de cette section, chaque tâche comprend les paramètres suivants :

| Paramètre | Description |
|-------------------| - |
| `Condition` | Paramètre `String` facultatif.<br /><br /> Expression `Boolean` que le moteur MSBuild utilise pour déterminer si cette tâche sera exécutée. Pour plus d’informations sur les conditions prises en charge par MSBuild, consultez [conditions](../msbuild/msbuild-conditions.md). |
| `ContinueOnError` | Paramètre facultatif. Peut contenir l’une des valeurs suivantes :<br /><br /> -   **WarnAndContinue** ou **true**. En cas d’échec d’une tâche, l’exécution des tâches suivantes de l’élément [Target](../msbuild/target-element-msbuild.md) et de la génération se poursuit, et toutes les erreurs de la tâche sont considérées comme des avertissements.<br />-   **ErrorAndContinue**. En cas d’échec d’une tâche, l’exécution des tâches suivantes de l’élément `Target` et de la génération se poursuit, et toutes les erreurs de la tâche sont considérées comme des erreurs.<br />-   **ErrorAndStop** ou **false** (par défaut). En cas d’échec d’une tâche, les tâches restantes de l’élément `Target` et de la génération ne sont pas exécutées, et tout l’élément `Target` ainsi que la génération sont considérés comme étant en échec.<br /><br /> Les versions de .NET Framework antérieures à 4.5 prenaient en charge uniquement les valeurs `true` et `false`.<br /><br /> Pour plus d’informations, voir [Guide pratique : Ignorer les erreurs dans les tâches](../msbuild/how-to-ignore-errors-in-tasks.md). |

## <a name="in-this-section"></a>Contenu de cette section

- [Classe de base Task](../msbuild/task-base-class.md)

 Ajoute plusieurs paramètres aux tâches qui dérivent de la classe <xref:Microsoft.Build.Utilities.Task>. Non destiné à être utilisé directement.

- [Classe de base TaskExtension](../msbuild/taskextension-base-class.md)

 Ajoute plusieurs paramètres aux tâches qui dérivent de la classe <xref:Microsoft.Build.Tasks.TaskExtension>. Non destiné à être utilisé directement.

- [Classe de base ToolTaskExtension](../msbuild/tooltaskextension-base-class.md)

 Ajoute plusieurs paramètres aux tâches qui dérivent de la classe <xref:Microsoft.Build.Tasks.ToolTaskExtension>. Non destiné à être utilisé directement.

- [Tâche AL (Assembly Linker)](../msbuild/al-assembly-linker-task.md)

 Crée un assembly avec un manifeste à partir d’un ou de plusieurs fichiers qui sont soit des modules, soit des fichiers de ressources.

- [Tâche AspNetCompiler](../msbuild/aspnetcompiler-task.md)

 Inclut dans un wrapper *aspnet_compiler.exe*, un utilitaire permettant de précompiler des applications ASP.NET.

- [Tâche AssignCulture](../msbuild/assignculture-task.md)

 Assigne des identificateurs de culture aux éléments.

- [Tâche AssignProjectConfiguration](../msbuild/assignprojectconfiguration-task.md)

 Accepte une liste de chaînes de configuration et les assigne aux projets spécifiés.

- [Tâche AssignTargetPath](../msbuild/assigntargetpath-task.md)

 Accepte une liste des fichiers et ajoute des attributs `<TargetPath>` s’ils ne sont pas déjà spécifiés.

- [Tâche CallTarget](../msbuild/calltarget-task.md)

 Appelle une cible dans le fichier projet.

- [Tâche CombinePath](../msbuild/combinepath-task.md)

 Combine les chemins spécifiés en un chemin unique.

- [Tâche ConvertToAbsolutePath](../msbuild/converttoabsolutepath-task.md)

 Convertit une référence ou un chemin relatif en chemin absolu.

- [Tâche Copy](../msbuild/copy-task.md)

 Copie les fichiers dans un nouvel emplacement.

- [Tâche CreateCSharpManifestResourceName](../msbuild/createcsharpmanifestresourcename-task.md)

 Crée un C#nom de manifeste de style à partir d’un nom de fichier *. resx* donné ou d’une autre ressource.

- [Tâche CreateItem](../msbuild/createitem-task.md)

 Remplit des collections d’éléments à partir des éléments d’entrée, en autorisant la copie d’éléments d’une liste dans une autre.

- [Tâche CreateProperty](../msbuild/createproperty-task.md)

 Remplit des propriétés à partir des valeurs d’entrée, en autorisant la copie de valeurs d’une propriété ou d’une chaîne dans une autre.

- [Tâche CreateVisualBasicManifestResourceName](../msbuild/createvisualbasicmanifestresourcename-task.md)

 Crée un nom de manifeste de style Visual Basic à partir d’un nom de fichier *. resx* donné ou d’une autre ressource.

- [Tâche Csc](../msbuild/csc-task.md)

 Appelle le compilateur Visual C# pour produire des exécutables, des bibliothèques de liens dynamiques ou des modules de code.

- [Tâche Delete](../msbuild/delete-task.md)

 Supprime les fichiers spécifiés.

- [Tâche DownloadFile](../msbuild/downloadfile-task.md)

 Télécharge un fichier à l’emplacement spécifié.

- [Tâche Error](../msbuild/error-task.md)

 Arrête une génération et enregistre une erreur en fonction d’une instruction conditionnelle évaluée.

- [Tâche Exec](../msbuild/exec-task.md)

 Exécute la commande ou le programme spécifié avec les arguments spécifiés.

- [Tâche FindAppConfigFile](../msbuild/findappconfigfile-task.md)

 Recherche le fichier *app.config*, le cas échéant, dans les listes fournies.

- [Tâche FindInList](../msbuild/findinlist-task.md)

 Recherche un élément dans une liste spécifiée associée à la spécification d’éléments (itemspec) correspondante.

- [Tâche FindUnderPath](../msbuild/findunderpath-task.md)

 Détermine les éléments de la collection spécifiée qui existent dans le dossier spécifié et tous ses sous-dossiers.

- [Tâche FormatUrl](../msbuild/formaturl-task.md)

 Convertit une URL en URL au format correct.

- [Tâche FormatVersion](../msbuild/formatversion-task.md)

 Ajoute le numéro de révision au numéro de version.

- [GenerateApplicationManifest, tâche](../msbuild/generateapplicationmanifest-task.md)

 Génère un manifeste d’application ClickOnce ou un manifeste natif.

- [Tâche GenerateBootstrapper](../msbuild/generatebootstrapper-task.md)

 Fournit un moyen automatisé de détecter, télécharger et installer une application et ses composants requis.

- [Tâche GenerateDeploymentManifest](../msbuild/generatedeploymentmanifest-task.md)

 Génère un manifeste de déploiement ClickOnce.

- [Tâche GenerateResource](../msbuild/generateresource-task.md)

 Convertit les fichiers *.txt* et *.resx* en fichiers *.resources* binaires du common language runtime.

- [Tâche GenerateTrustInfo](../msbuild/generatetrustinfo-task.md)

 Génère le niveau de confiance de l’application à partir du manifeste de base, ainsi que des paramètres `TargetZone` et `ExcludedPermissions`.

- [Tâche GetAssemblyIdentity](../msbuild/getassemblyidentity-task.md)

 Récupère les identités d’assembly des fichiers spécifiés et génère les informations d’identité.

- [GetFileHash, tâche](../msbuild/getfilehash-task.md)

 Calcule les sommes de contrôle du contenu d’un fichier ou d’un ensemble de fichiers.

- [Tâche GetFrameworkPath](../msbuild/getframeworkpath-task.md)

 Récupère le chemin vers les assemblys du .NET Framework.

- [Tâche GetFrameworkSdkPath](../msbuild/getframeworksdkpath-task.md)

 Récupère le chemin d’accès au kit de développement logiciel (SDK) Windows.

- [Tâche GetReferenceAssemblyPaths](../msbuild/getreferenceassemblypaths-task.md)

 Retourne les chemins des assemblys de référence des différentes infrastructures.

- [Tâche LC](../msbuild/lc-task.md)

 Génère un fichier *.license* à partir d’un fichier *.licx*.

- [Tâche MakeDir](../msbuild/makedir-task.md)

 Crée des répertoires et, si nécessaire, des répertoires parents.

- [Tâche Message](../msbuild/message-task.md)

 Enregistre un message pendant une génération.

- [Tâche Move](../msbuild/move-task.md)

 Déplace les fichiers vers un nouvel emplacement.

- [Tâche MSBuild](../msbuild/msbuild-task.md)

 Génère des projets MSBuild à partir d’un autre projet MSBuild.

- [Tâche ReadLinesFromFile](../msbuild/readlinesfromfile-task.md)

 Lit une liste d’éléments à partir d’un fichier texte.

- [Tâche RegisterAssembly](../msbuild/registerassembly-task.md)

 Lit les métadonnées dans l’assembly spécifié et ajoute les entrées nécessaires au Registre.

- [Tâche RemoveDir](../msbuild/removedir-task.md)

 Supprime les répertoires spécifiés ainsi que tous leurs fichiers et sous-répertoires.

- [Tâche RemoveDuplicates](../msbuild/removeduplicates-task.md)

 Supprime les éléments en double de la collection d’éléments spécifiée.

- [Tâche RequiresFramework35SP1Assembly](../msbuild/requiresframework35sp1assembly-task.md)

 Détermine si l’application nécessite le .NET Framework 3.5 SP1.

- ResGen, tâche

 Obsolète. Utilisez la [tâche GenerateResource](../msbuild/generateresource-task.md) pour convertir des fichiers *.txt* et *.resx* en fichiers *.resources* binaires du common language runtime, et vice versa.

- [Tâche ResolveAssemblyReference](../msbuild/resolveassemblyreference-task.md)

 Détermine tous les assemblys qui dépendent des assemblys spécifiés.

- [Tâche ResolveComReference](../msbuild/resolvecomreference-task.md)

 Prend une liste d’un ou plusieurs noms de bibliothèques de types ou de fichiers *.tlb* et résout ces bibliothèques de types sous forme d’emplacements sur le disque.

- [Tâche ResolveKeySource](../msbuild/resolvekeysource-task.md)

 Détermine la source des clés à nom fort.

- [Tâche ResolveManifestFiles](../msbuild/resolvemanifestfiles-task.md)

 Résout les éléments suivants dans le processus de génération en fichiers pour la génération de manifeste : éléments générés, dépendances, satellites, contenu, symboles de débogage et documentation.

- [Tâche ResolveNativeReference](../msbuild/resolvenativereference-task.md)

 Résout les références natives.

- [Tâche ResolveNonMSBuildProjectOutput](../msbuild/resolvenonmsbuildprojectoutput-task.md)

 Détermine les fichiers de sortie des références de projet non-MSBuild.

- [Tâche SGen](../msbuild/sgen-task.md)

 Crée un assembly de sérialisation XML pour les types dans l’assembly spécifié.

- [SignFile, tâche](../msbuild/signfile-task.md)

 Signe le fichier spécifié à l'aide du certificat spécifié.

- [Tâche Touch](../msbuild/touch-task.md)

 Définit les heures d’accès et de modification des fichiers.

- [Tâche UnregisterAssembly](../msbuild/unregisterassembly-task.md)

 Désinscrit les assemblys spécifiés dans le cadre de COM Interop.

- [Tâche Unzip](../msbuild/unzip-task.md)

 Décompresse une archive *.zip* à l’emplacement spécifié.

- [Tâche UpdateManifest](../msbuild/updatemanifest-task.md)

 Met à jour les propriétés sélectionnées dans un manifeste et signe à nouveau.

- [Vbc, tâche](../msbuild/vbc-task.md)

 Appelle le compilateur Visual Basic pour produire des exécutables, des bibliothèques de liens dynamiques ou des modules de code.

- [VerifyFileHash, tâche](../msbuild/verifyfilehash-task.md)

 Vérifie qu’un fichier correspond au hachage de fichier attendu.

- [Tâche Warning](../msbuild/warning-task.md)

 Enregistre un avertissement durant une génération en fonction d’une instruction conditionnelle évaluée.

- [Tâche WriteCodeFragment](../msbuild/writecodefragment-task.md)

 Génère un fichier de code temporaire à l’aide du fragment de code généré spécifié. Ne supprime pas le fichier.

- [Tâche WriteLinesToFile](../msbuild/writelinestofile-task.md)

 Écrit les éléments spécifiés dans le fichier texte spécifié.

- [Tâche XmlPeek](../msbuild/xmlpeek-task.md)

 Retourne des valeurs comme spécifié par la requête XPath à partir d’un fichier XML.

- [Tâche XmlPoke](../msbuild/xmlpoke-task.md)

 Définit les valeurs comme spécifié par une requête XPath dans un fichier XML.

- [Tâche XslTransformation](../msbuild/xsltransformation-task.md)

 Transforme une entrée XML à l’aide d’une *transformation XLS* (XSLT) ou d’un XSLT compilé et envoie la sortie vers un fichier ou un périphérique de sortie.

- [Tâche ZipDirectory](../msbuild/zipdirectory-task.md)

 Crée une archive *.zip* à partir du contenu d’un répertoire.

## <a name="see-also"></a>Voir aussi

- [Informations de référence sur MSBuild](../msbuild/msbuild-reference.md)
- [Écriture de tâches](../msbuild/task-writing.md)
- [Tâches :](../msbuild/msbuild-tasks.md)
