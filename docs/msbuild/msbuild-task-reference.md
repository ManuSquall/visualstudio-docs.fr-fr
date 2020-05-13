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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2020
ms.locfileid: "78865321"
---
# <a name="msbuild-task-reference"></a>Informations de référence sur les tâches MSBuild

Les tâches fournissent le code exécuté pendant le processus de génération. Les tâches de la liste suivante sont incluses avec MSBuild. Lorsque la charge de travail de la C est installée, des tâches supplémentaires sont disponibles pour construire des projets C. Pour plus d’informations, voir [tâches C .](../msbuild/msbuild-tasks-specific-to-visual-cpp.md)

Outre les paramètres répertoriés dans les rubriques de cette section, chaque tâche comprend les paramètres suivants :

| Paramètre | Description |
|-------------------| - |
| `Condition` | Paramètre `String` facultatif.<br /><br /> Une `Boolean` expression que le moteur MSBuild utilise pour déterminer si cette tâche sera exécutée. Pour plus d’informations sur les conditions qui sont prises en charge par MSBuild, voir [Conditions](../msbuild/msbuild-conditions.md). |
| `ContinueOnError` | Paramètre facultatif. Peut contenir l’une des valeurs suivantes :<br /><br /> -   **WarnAndContinue** ou **vrai**. Lorsqu’une tâche échoue, les tâches ultérieures de [l’élément Cible](../msbuild/target-element-msbuild.md) et de la build continuent d’être exécutées, et toutes les erreurs de la tâche sont traitées comme des avertissements.<br />-   **ErreurAndContinue**. En cas d’échec d’une tâche, l’exécution des tâches suivantes de l’élément `Target` et de la génération se poursuit, et toutes les erreurs de la tâche sont considérées comme des erreurs.<br />-   **ErreurAndStop** ou **faux** (par défaut). En cas d’échec d’une tâche, les tâches restantes de l’élément `Target` et de la génération ne sont pas exécutées, et tout l’élément `Target` ainsi que la génération sont considérés comme étant en échec.<br /><br /> Les versions de .NET Framework antérieures à 4.5 prenaient en charge uniquement les valeurs `true` et `false`.<br /><br /> Pour plus d’informations, voir [Comment : Ignorer les erreurs dans les tâches](../msbuild/how-to-ignore-errors-in-tasks.md). |

## <a name="in-this-section"></a>Contenu de cette section

- [Classe de base Task](../msbuild/task-base-class.md)

 Ajoute plusieurs paramètres aux tâches qui dérivent de la classe <xref:Microsoft.Build.Utilities.Task>. Non destiné à être utilisé directement.

- [Classe de base TaskExtension](../msbuild/taskextension-base-class.md)

 Ajoute plusieurs paramètres aux tâches qui dérivent de la classe <xref:Microsoft.Build.Tasks.TaskExtension>. Non destiné à être utilisé directement.

- [ToolTaskExtension classe de base](../msbuild/tooltaskextension-base-class.md)

 Ajoute plusieurs paramètres aux tâches qui dérivent de la classe <xref:Microsoft.Build.Tasks.ToolTaskExtension>. Non destiné à être utilisé directement.

- [AL (Assembly Linker), tâche](../msbuild/al-assembly-linker-task.md)

 Crée un assembly avec un manifeste à partir d’un ou de plusieurs fichiers qui sont soit des modules, soit des fichiers de ressources.

- [Tâche AspNetCompiler](../msbuild/aspnetcompiler-task.md)

 Enveloppe *aspnet_compiler.exe*, un utilitaire pour précompte ASP.NET applications.

- [Tâche AssignCulture](../msbuild/assignculture-task.md)

 Assigne des identificateurs de culture aux éléments.

- [AssignProjectConfiguration tâche](../msbuild/assignprojectconfiguration-task.md)

 Accepte une liste de chaînes de configuration et les assigne aux projets spécifiés.

- [Charge assignTargetPath](../msbuild/assigntargetpath-task.md)

 Accepte une liste des fichiers et ajoute des attributs `<TargetPath>` s’ils ne sont pas déjà spécifiés.

- [CallTarget tâche](../msbuild/calltarget-task.md)

 Appelle une cible dans le fichier projet.

- [Tâche CombinePath](../msbuild/combinepath-task.md)

 Combine les chemins spécifiés en un chemin unique.

- [ConvertirToAbsolutePath tâche](../msbuild/converttoabsolutepath-task.md)

 Convertit une référence ou un chemin relatif en chemin absolu.

- [Copie de la tâche](../msbuild/copy-task.md)

 Copie les fichiers dans un nouvel emplacement.

- [CréerCSharpManifestResourceName tâche](../msbuild/createcsharpmanifestresourcename-task.md)

 Crée un nom manifeste de type C à partir d’un nom de fichier *.resx* donné ou d’une autre ressource.

- [CréerItem tâche](../msbuild/createitem-task.md)

 Remplit des collections d’éléments à partir des éléments d’entrée, en autorisant la copie d’éléments d’une liste dans une autre.

- [CreateProperty (tâche)](../msbuild/createproperty-task.md)

 Remplit des propriétés à partir des valeurs d’entrée, en autorisant la copie de valeurs d’une propriété ou d’une chaîne dans une autre.

- [CreateVisualBasicManifestResourceName tâche](../msbuild/createvisualbasicmanifestresourcename-task.md)

 Crée un nom manifeste de style Visual Basic à partir d’un nom de fichier *.resx* donné ou d’une autre ressource.

- [Tâche Csc](../msbuild/csc-task.md)

 Appelle le compilateur Visual C# pour produire des exécutables, des bibliothèques de liens dynamiques ou des modules de code.

- [Supprimer la tâche](../msbuild/delete-task.md)

 Supprime les fichiers spécifiés.

- [TéléchargerFile tâche](../msbuild/downloadfile-task.md)

 Télécharge un fichier à l’emplacement spécifié.

- [Erreur (tâche)](../msbuild/error-task.md)

 Arrête une génération et enregistre une erreur en fonction d’une instruction conditionnelle évaluée.

- [Tâche Exec](../msbuild/exec-task.md)

 Exécute la commande ou le programme spécifié avec les arguments spécifiés.

- [Trouver La tâche d’AppConfigFile](../msbuild/findappconfigfile-task.md)

 Recherche le fichier *app.config*, le cas échéant, dans les listes fournies.

- [Tâche FindInList](../msbuild/findinlist-task.md)

 Recherche un élément dans une liste spécifiée associée à la spécification d’éléments (itemspec) correspondante.

- [FindUnderPath tâche](../msbuild/findunderpath-task.md)

 Détermine les éléments de la collection spécifiée qui existent dans le dossier spécifié et tous ses sous-dossiers.

- [Tâche FormatUrl](../msbuild/formaturl-task.md)

 Convertit une URL en URL au format correct.

- [Tâche FormatVersion](../msbuild/formatversion-task.md)

 Ajoute le numéro de révision au numéro de version.

- [GénérerApplicationManifest tâche](../msbuild/generateapplicationmanifest-task.md)

 Génère un manifeste d’application ClickOnce ou un manifeste indigène.

- [GenerateBootstrapper (tâche)](../msbuild/generatebootstrapper-task.md)

 Fournit un moyen automatisé de détecter, télécharger et installer une application et ses composants requis.

- [GénérerdeploymentManifest tâche](../msbuild/generatedeploymentmanifest-task.md)

 Génère un manifeste de déploiement ClickOnce.

- [GenerateResource (tâche)](../msbuild/generateresource-task.md)

 Convertit les fichiers *.txt* et *.resx* en fichiers .ressources binaires *.resources.*

- [Tâche GenerateTrustInfo](../msbuild/generatetrustinfo-task.md)

 Génère le niveau de confiance de l’application à partir du manifeste de base, ainsi que des paramètres `TargetZone` et `ExcludedPermissions`.

- [Obtenir La tâche d’identification d’assemblage](../msbuild/getassemblyidentity-task.md)

 Récupère les identités d’assembly des fichiers spécifiés et génère les informations d’identité.

- [GetFileHash, tâche](../msbuild/getfilehash-task.md)

 Calcule les sommes de contrôle du contenu d’un fichier ou d’un ensemble de fichiers.

- [GetFrameworkPath tâche](../msbuild/getframeworkpath-task.md)

 Récupère le chemin vers les assemblys du .NET Framework.

- [GetFrameworkSdk Tâche](../msbuild/getframeworksdkpath-task.md)

 Récupère le chemin vers le kit de développement logiciel Windows (SDK).

- [GetReferenceAssemblyPaths tâche](../msbuild/getreferenceassemblypaths-task.md)

 Retourne les chemins des assemblys de référence des différents frameworks.

- [Tâche LC](../msbuild/lc-task.md)

 Génère un fichier *.licence* à partir d’un fichier *.licx.*

- [MakeDir, tâche](../msbuild/makedir-task.md)

 Crée des répertoires et, si nécessaire, des répertoires parents.

- [Tâche de message](../msbuild/message-task.md)

 Enregistre un message pendant une génération.

- [Déplacer la tâche](../msbuild/move-task.md)

 Déplace les fichiers vers un nouvel emplacement.

- [Tâche MSBuild](../msbuild/msbuild-task.md)

 Construit des projets MSBuild à partir d’un autre projet MSBuild.

- [LireLinesDefile tâche](../msbuild/readlinesfromfile-task.md)

 Lit une liste d’éléments à partir d’un fichier texte.

- [Enregistrer La tâche d’assemblage](../msbuild/registerassembly-task.md)

 Lit les métadonnées dans l’assembly spécifié et ajoute les entrées nécessaires au Registre.

- [Supprimer la tâcheDir](../msbuild/removedir-task.md)

 Supprime les répertoires spécifiés ainsi que tous leurs fichiers et sous-répertoires.

- [SuppressionDuplicates tâche](../msbuild/removeduplicates-task.md)

 Supprime les éléments en double de la collection d’éléments spécifiée.

- [NécessiteFramework35SP1Assembly tâche](../msbuild/requiresframework35sp1assembly-task.md)

 Détermine si l’application nécessite le .NET Framework 3.5 SP1.

- ResGen, tâche

 Obsolète. Utilisez la tâche [de tâche GenerateResource](../msbuild/generateresource-task.md) pour convertir les fichiers *.txt* et *.resx* vers et depuis les fichiers *.ressources* binaires .resources binaires de langage courant.

- [RésoudreAssemblyReference tâche](../msbuild/resolveassemblyreference-task.md)

 Détermine tous les assemblys qui dépendent des assemblys spécifiés.

- [RésoudreComReference tâche](../msbuild/resolvecomreference-task.md)

 Prend une liste d’un ou plusieurs noms de bibliothèques de types ou de fichiers *.tlb* et résout ces bibliothèques de types aux emplacements sur le disque.

- [Tâche ResolveKeySource](../msbuild/resolvekeysource-task.md)

 Détermine la source des clés à nom fort.

- [RésoudreManifestFiles tâche](../msbuild/resolvemanifestfiles-task.md)

 Résout les éléments suivants dans le processus de génération en fichiers pour la génération de manifeste : éléments générés, dépendances, satellites, contenu, symboles de débogage et documentation.

- [ResolveNativeReference (tâche)](../msbuild/resolvenativereference-task.md)

 Résout des références natives.

- [Tâche ResolveNonMSBuildProjectOutput](../msbuild/resolvenonmsbuildprojectoutput-task.md)

 Détermine les fichiers de sortie des références de projet non-MSBuild.

- [Tâche SGen](../msbuild/sgen-task.md)

 Crée un assembly de sérialisation XML pour les types dans l’assembly spécifié.

- [Tâche SignFile](../msbuild/signfile-task.md)

 Signe le fichier spécifié à l'aide du certificat spécifié.

- [Tâche tactile](../msbuild/touch-task.md)

 Définit les heures d’accès et de modification des fichiers.

- [Tâche non enregistrée](../msbuild/unregisterassembly-task.md)

 Désinscrit les assemblys spécifiés dans le cadre de COM Interop.

- [Tâche Unzip](../msbuild/unzip-task.md)

 Décompresse une archive *.zip* à l’emplacement spécifié.

- [Mise à jourLa tâche duManifest](../msbuild/updatemanifest-task.md)

 Met à jour les propriétés sélectionnées dans un manifeste et signe à nouveau.

- [Tâche Vbc](../msbuild/vbc-task.md)

 Appelle le compilateur Visual Basic pour produire des exécutables, des bibliothèques de liens dynamiques ou des modules de code.

- [VerifyFileHash, tâche](../msbuild/verifyfilehash-task.md)

 Vérifie qu’un fichier correspond au hachage de fichier attendu.

- [Tâche d’avertissement](../msbuild/warning-task.md)

 Enregistre un avertissement durant une génération en fonction d’une instruction conditionnelle évaluée.

- [Écrire La tâche Defragment](../msbuild/writecodefragment-task.md)

 Génère un fichier de code temporaire à l’aide du fragment de code généré spécifié. Ne supprime pas le fichier.

- [Tâche WriteLinesToFile](../msbuild/writelinestofile-task.md)

 Écrit les éléments spécifiés dans le fichier texte spécifié.

- [XmlPeek (tâche)](../msbuild/xmlpeek-task.md)

 Retourne des valeurs comme spécifié par la requête XPath à partir d’un fichier XML.

- [Tâche XmlPoke](../msbuild/xmlpoke-task.md)

 Définit les valeurs comme spécifié par une requête XPath dans un fichier XML.

- [Tâche XslTransformation](../msbuild/xsltransformation-task.md)

 Transforme une entrée XML à l’aide d’une *transformation XLS* (XSLT) ou d’un XSLT compilé et envoie la sortie vers un fichier ou un périphérique de sortie.

- [Tâche ZipDirectory](../msbuild/zipdirectory-task.md)

 Crée une archive *.zip* à partir du contenu d’un répertoire.

## <a name="see-also"></a>Voir aussi

- [Référence MSBuild](../msbuild/msbuild-reference.md)
- [Rédaction de tâches](../msbuild/task-writing.md)
- [Tâches](../msbuild/msbuild-tasks.md)
