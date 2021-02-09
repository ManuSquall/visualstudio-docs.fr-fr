---
title: Informations de référence sur les tâches MSBuild | Microsoft Docs
description: En savoir plus sur les tâches incluses dans MSBuild, qui fournissent le code qui s’exécute pendant le processus de génération.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f26c3c1b8256597c795fa8bcd815fd605f895fa5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99878381"
---
# <a name="msbuild-task-reference"></a>Informations de référence sur les tâches MSBuild

Les tâches fournissent le code exécuté pendant le processus de génération. Les tâches de la liste suivante sont incluses dans MSBuild. Lorsque la charge de travail C++ est installée, des tâches supplémentaires qui sont utilisées pour générer des projets C++ sont disponibles. Pour plus d’informations, consultez [tâches C++](../msbuild/msbuild-tasks-specific-to-visual-cpp.md).

Outre les paramètres répertoriés dans les rubriques de cette section, chaque tâche comprend les paramètres suivants :

| Paramètre | Description |
|-------------------| - |
| `Condition` | Paramètre `String` facultatif.<br /><br /> `Boolean`Expression utilisée par le moteur MSBuild pour déterminer si cette tâche sera exécutée. Pour plus d’informations sur les conditions prises en charge par MSBuild, consultez [conditions](../msbuild/msbuild-conditions.md). |
| `ContinueOnError` | Paramètre facultatif. Peut contenir l’une des valeurs suivantes :<br /><br /> -   **WarnAndContinue** ou **true**. En cas d’échec d’une tâche, les tâches suivantes dans l’élément [cible](../msbuild/target-element-msbuild.md) et la build continuent à s’exécuter, et toutes les erreurs de la tâche sont traitées comme des avertissements.<br />-   **ErrorAndContinue**. En cas d’échec d’une tâche, l’exécution des tâches suivantes de l’élément `Target` et de la génération se poursuit, et toutes les erreurs de la tâche sont considérées comme des erreurs.<br />-   **ErrorAndStop** ou **false** (valeur par défaut). En cas d’échec d’une tâche, les tâches restantes de l’élément `Target` et de la génération ne sont pas exécutées, et tout l’élément `Target` ainsi que la génération sont considérés comme étant en échec.<br /><br /> Les versions de .NET Framework antérieures à 4.5 prenaient en charge uniquement les valeurs `true` et `false`.<br /><br /> Pour plus d’informations, consultez [Comment : ignorer les erreurs dans les tâches](../msbuild/how-to-ignore-errors-in-tasks.md). |

## <a name="in-this-section"></a>Dans cette section

- [Classe de base Task](../msbuild/task-base-class.md)

 Ajoute plusieurs paramètres aux tâches qui dérivent de la classe <xref:Microsoft.Build.Utilities.Task>. Non destiné à être utilisé directement.

- [Classe de base TaskExtension](../msbuild/taskextension-base-class.md)

 Ajoute plusieurs paramètres aux tâches qui dérivent de la classe <xref:Microsoft.Build.Tasks.TaskExtension>. Non destiné à être utilisé directement.

- [Classe de base ToolTaskExtension](../msbuild/tooltaskextension-base-class.md)

 Ajoute plusieurs paramètres aux tâches qui dérivent de la classe <xref:Microsoft.Build.Tasks.ToolTaskExtension>. Non destiné à être utilisé directement.

- [AL (Assembly Linker), tâche](../msbuild/al-assembly-linker-task.md)

 Crée un assembly avec un manifeste à partir d’un ou de plusieurs fichiers qui sont soit des modules, soit des fichiers de ressources.

- [AspNetCompiler (tâche)](../msbuild/aspnetcompiler-task.md)

 Encapsule *aspnet_compiler.exe*, un utilitaire permettant de précompiler des applications ASP.net.

- [AssignCulture (tâche)](../msbuild/assignculture-task.md)

 Assigne des identificateurs de culture aux éléments.

- [AssignProjectConfiguration, tâche](../msbuild/assignprojectconfiguration-task.md)

 Accepte une liste de chaînes de configuration et les assigne aux projets spécifiés.

- [AssignTargetPath, tâche](../msbuild/assigntargetpath-task.md)

 Accepte une liste des fichiers et ajoute des attributs `<TargetPath>` s’ils ne sont pas déjà spécifiés.

- [CallTarget (tâche)](../msbuild/calltarget-task.md)

 Appelle une cible dans le fichier projet.

- [CombinePath (tâche)](../msbuild/combinepath-task.md)

 Combine les chemins spécifiés en un chemin unique.

- [ConvertToAbsolutePath (tâche)](../msbuild/converttoabsolutepath-task.md)

 Convertit une référence ou un chemin relatif en chemin absolu.

- [Copy (tâche)](../msbuild/copy-task.md)

 Copie les fichiers dans un nouvel emplacement.

- [CreateCSharpManifestResourceName (tâche)](../msbuild/createcsharpmanifestresourcename-task.md)

 Crée un nom de manifeste de style C# à partir d’un nom de fichier *. resx* donné ou d’une autre ressource.

- [CreateItem (tâche)](../msbuild/createitem-task.md)

 Remplit des collections d’éléments à partir des éléments d’entrée, en autorisant la copie d’éléments d’une liste dans une autre.

- [CreateProperty (tâche)](../msbuild/createproperty-task.md)

 Remplit des propriétés à partir des valeurs d’entrée, en autorisant la copie de valeurs d’une propriété ou d’une chaîne dans une autre.

- [CreateVisualBasicManifestResourceName (tâche)](../msbuild/createvisualbasicmanifestresourcename-task.md)

 Crée un nom de manifeste de style Visual Basic à partir d’un nom de fichier *. resx* donné ou d’une autre ressource.

- [Csc (tâche)](../msbuild/csc-task.md)

 Appelle le compilateur Visual C# pour produire des exécutables, des bibliothèques de liens dynamiques ou des modules de code.

- [Delete (tâche)](../msbuild/delete-task.md)

 Supprime les fichiers spécifiés.

- [DownloadFile, tâche](../msbuild/downloadfile-task.md)

 Télécharge un fichier à l’emplacement spécifié.

- [Erreur (tâche)](../msbuild/error-task.md)

 Arrête une génération et enregistre une erreur en fonction d’une instruction conditionnelle évaluée.

- [Exec (tâche)](../msbuild/exec-task.md)

 Exécute la commande ou le programme spécifié avec les arguments spécifiés.

- [FindAppConfigFile (tâche)](../msbuild/findappconfigfile-task.md)

 Recherche le fichier *app.config* , le cas échéant, dans les listes fournies.

- [FindInList (tâche)](../msbuild/findinlist-task.md)

 Recherche un élément dans une liste spécifiée associée à la spécification d’éléments (itemspec) correspondante.

- [FindUnderPath (tâche)](../msbuild/findunderpath-task.md)

 Détermine les éléments de la collection spécifiée qui existent dans le dossier spécifié et tous ses sous-dossiers.

- [FormatUrl (tâche)](../msbuild/formaturl-task.md)

 Convertit une URL en URL au format correct.

- [FormatVersion, tâche](../msbuild/formatversion-task.md)

 Ajoute le numéro de révision au numéro de version.

- [GenerateApplicationManifest (tâche)](../msbuild/generateapplicationmanifest-task.md)

 Génère un manifeste d’application ClickOnce ou un manifeste natif.

- [GenerateBootstrapper (tâche)](../msbuild/generatebootstrapper-task.md)

 Fournit un moyen automatisé de détecter, télécharger et installer une application et ses composants requis.

- [GenerateDeploymentManifest (tâche)](../msbuild/generatedeploymentmanifest-task.md)

 Génère un manifeste de déploiement ClickOnce.

- [GenerateResource (tâche)](../msbuild/generateresource-task.md)

 Convertit les fichiers *. txt* et *. resx* Common Language Runtime en fichiers. *Resources* binaires.

- [GenerateTrustInfo (tâche)](../msbuild/generatetrustinfo-task.md)

 Génère le niveau de confiance de l’application à partir du manifeste de base, ainsi que des paramètres `TargetZone` et `ExcludedPermissions`.

- [GetAssemblyIdentity (tâche)](../msbuild/getassemblyidentity-task.md)

 Récupère les identités d’assembly des fichiers spécifiés et génère les informations d’identité.

- [GetFileHash, tâche](../msbuild/getfilehash-task.md)

 Calcule les sommes de contrôle du contenu d’un fichier ou d’un ensemble de fichiers.

- [GetFrameworkPath (tâche)](../msbuild/getframeworkpath-task.md)

 Récupère le chemin vers les assemblys du .NET Framework.

- [GetFrameworkSdkPath (tâche)](../msbuild/getframeworksdkpath-task.md)

 Récupère le chemin d’accès au kit de développement logiciel (SDK) Windows.

- [GetReferenceAssemblyPaths, tâche](../msbuild/getreferenceassemblypaths-task.md)

 Retourne les chemins des assemblys de référence des différents frameworks.

- [LC (tâche)](../msbuild/lc-task.md)

 Génère un fichier *. License* à partir d’un fichier *. licx* .

- [MakeDir (tâche)](../msbuild/makedir-task.md)

 Crée des répertoires et, si nécessaire, des répertoires parents.

- [Message (tâche)](../msbuild/message-task.md)

 Enregistre un message pendant une génération.

- [Move (tâche)](../msbuild/move-task.md)

 Déplace les fichiers vers un nouvel emplacement.

- [MSBuild (tâche)](../msbuild/msbuild-task.md)

 Génère des projets MSBuild à partir d’un autre projet MSBuild.

- [ReadLinesFromFile (tâche)](../msbuild/readlinesfromfile-task.md)

 Lit une liste d’éléments à partir d’un fichier texte.

- [RegisterAssembly (tâche)](../msbuild/registerassembly-task.md)

 Lit les métadonnées dans l’assembly spécifié et ajoute les entrées nécessaires au Registre.

- [RemoveDir (tâche)](../msbuild/removedir-task.md)

 Supprime les répertoires spécifiés ainsi que tous leurs fichiers et sous-répertoires.

- [RemoveDuplicates (tâche)](../msbuild/removeduplicates-task.md)

 Supprime les éléments en double de la collection d’éléments spécifiée.

- [RequiresFramework35SP1Assembly (tâche)](../msbuild/requiresframework35sp1assembly-task.md)

 Détermine si l’application nécessite le .NET Framework 3.5 SP1.

- ResGen, tâche

 Obsolète. Utilisez la tâche [GenerateResource](../msbuild/generateresource-task.md) pour convertir des fichiers *. txt* et *. resx* vers et à partir de Common Language Runtime fichiers *. Resources* binaires.

- [ResolveAssemblyReference (tâche)](../msbuild/resolveassemblyreference-task.md)

 Détermine tous les assemblys qui dépendent des assemblys spécifiés.

- [ResolveComReference, tâche](../msbuild/resolvecomreference-task.md)

 Prend une liste d’un ou plusieurs noms de bibliothèques de types ou de fichiers *.tlb* et résout ces bibliothèques de types aux emplacements sur le disque.

- [ResolveKeySource (tâche)](../msbuild/resolvekeysource-task.md)

 Détermine la source des clés à nom fort.

- [ResolveManifestFiles (tâche)](../msbuild/resolvemanifestfiles-task.md)

 Résout les éléments suivants dans le processus de génération en fichiers pour la génération de manifeste : éléments générés, dépendances, satellites, contenu, symboles de débogage et documentation.

- [ResolveNativeReference (tâche)](../msbuild/resolvenativereference-task.md)

 Résout des références natives.

- [ResolveNonMSBuildProjectOutput (tâche)](../msbuild/resolvenonmsbuildprojectoutput-task.md)

 Détermine les fichiers de sortie des références de projet non-MSBuild.

- [SGen (tâche)](../msbuild/sgen-task.md)

 Crée un assembly de sérialisation XML pour les types dans l’assembly spécifié.

- [SignFile (tâche)](../msbuild/signfile-task.md)

 Signe le fichier spécifié à l'aide du certificat spécifié.

- [Touch (tâche)](../msbuild/touch-task.md)

 Définit les heures d’accès et de modification des fichiers.

- [UnregisterAssembly (tâche)](../msbuild/unregisterassembly-task.md)

 Désinscrit les assemblys spécifiés dans le cadre de COM Interop.

- [Tâche Unzip](../msbuild/unzip-task.md)

 Décompresse une archive *.zip* à l’emplacement spécifié.

- [UpdateManifest (tâche)](../msbuild/updatemanifest-task.md)

 Met à jour les propriétés sélectionnées dans un manifeste et signe à nouveau.

- [Vbc (tâche)](../msbuild/vbc-task.md)

 Appelle le compilateur Visual Basic pour produire des exécutables, des bibliothèques de liens dynamiques ou des modules de code.

- [VerifyFileHash, tâche](../msbuild/verifyfilehash-task.md)

 Vérifie qu’un fichier correspond au hachage de fichier attendu.

- [Avertissement (tâche)](../msbuild/warning-task.md)

 Enregistre un avertissement durant une génération en fonction d’une instruction conditionnelle évaluée.

- [WriteCodeFragment (tâche)](../msbuild/writecodefragment-task.md)

 Génère un fichier de code temporaire à l’aide du fragment de code généré spécifié. Ne supprime pas le fichier.

- [WriteLinesToFile (tâche)](../msbuild/writelinestofile-task.md)

 Écrit les éléments spécifiés dans le fichier texte spécifié.

- [XmlPeek (tâche)](../msbuild/xmlpeek-task.md)

 Retourne des valeurs comme spécifié par la requête XPath à partir d’un fichier XML.

- [XmlPoke (tâche)](../msbuild/xmlpoke-task.md)

 Définit les valeurs comme spécifié par une requête XPath dans un fichier XML.

- [XslTransformation (tâche)](../msbuild/xsltransformation-task.md)

 Transforme une entrée XML à l’aide d’une *transformation XLS* (XSLT) ou d’un XSLT compilé et envoie la sortie vers un fichier ou un périphérique de sortie.

- [Tâche ZipDirectory](../msbuild/zipdirectory-task.md)

 Crée une archive *.zip* à partir du contenu d’un répertoire.

## <a name="see-also"></a>Voir aussi

- [Informations de référence sur MSBuild](../msbuild/msbuild-reference.md)
- [Écriture de tâches](../msbuild/task-writing.md)
- [Tâches](../msbuild/msbuild-tasks.md)
