---
title: Informations de référence sur les tâches MSBuild | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, tasks
ms.assetid: b3144b27-a426-4259-b8ae-5f7991b202b6
caps.latest.revision: 35
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5bd6df873bf1aadbec4b12763369c60f127819c0
ms.sourcegitcommit: c496a77add807ba4a29ee6a424b44a5de89025ea
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2019
ms.locfileid: "54834421"
---
# <a name="msbuild-task-reference"></a>Informations de référence sur les tâches MSBuild
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Les tâches fournissent le code exécuté pendant le processus de génération. Les tâches de la liste suivante sont incluses dans [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]. Quand [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] est installé, des tâches supplémentaires sont disponibles pour générer des projets [!INCLUDE[vcprvc](../includes/vcprvc-md.md)]. Pour plus d’informations, consultez [Tâches Visual C++](../msbuild/msbuild-tasks-specific-to-visual-cpp.md).  
  
 Outre les paramètres répertoriés dans les rubriques de cette section, chaque tâche comprend les paramètres suivants :  
  
|Paramètre|Description|  
|---------------|-----------------|  
|`Condition`|Paramètre `String` facultatif.<br /><br /> Expression `Boolean` utilisée par le moteur [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] pour déterminer si cette tâche va être exécutée. Pour plus d’informations sur les conditions prises en charge par [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)], consultez [Conditions](../msbuild/msbuild-conditions.md).|  
|`ContinueOnError`|Paramètre facultatif. Peut contenir l’une des valeurs suivantes :<br /><br /> -   **WarnAndContinue** ou **true**. En cas d’échec d’une tâche, l’exécution des tâches suivantes de l’élément [Target](../msbuild/target-element-msbuild.md) et de la génération se poursuit, et toutes les erreurs de la tâche sont considérées comme des avertissements.<br />-   **ErrorAndContinue**. En cas d’échec d’une tâche, l’exécution des tâches suivantes de l’élément `Target` et de la génération se poursuit, et toutes les erreurs de la tâche sont considérées comme des erreurs.<br />-   **ErrorAndStop** ou **false** (par défaut). En cas d’échec d’une tâche, les tâches restantes de l’élément `Target` et de la génération ne sont pas exécutées, et tout l’élément `Target` ainsi que la génération sont considérés comme étant en échec.<br /><br /> Les versions de .NET Framework antérieures à 4.5 prenaient en charge uniquement les valeurs `true` et `false`.<br /><br /> Pour plus d’informations, consultez [Guide pratique pour ignorer des erreurs dans des tâches](../msbuild/how-to-ignore-errors-in-tasks.md).|  
  
## <a name="in-this-section"></a>Dans cette section  
 [Classe de base de tâche](../msbuild/task-base-class.md)  
 Ajoute plusieurs paramètres aux tâches qui dérivent de la classe <xref:Microsoft.Build.Utilities.Task>.  
  
 [Classe de base TaskExtension](../msbuild/taskextension-base-class.md)  
 Ajoute plusieurs paramètres aux tâches qui dérivent de la classe <xref:Microsoft.Build.Tasks.TaskExtension>.  
  
 [Classe de base ToolTaskExtension](../msbuild/tooltaskextension-base-class.md)  
 Ajoute plusieurs paramètres aux tâches qui dérivent de la classe <xref:Microsoft.Build.Tasks.ToolTaskExtension>.  
  
 [AL (Assembly Linker), tâche](../msbuild/al-assembly-linker-task.md)  
 Crée un assembly avec un manifeste à partir d’un ou de plusieurs fichiers qui sont soit des modules, soit des fichiers de ressources.  
  
 [AspNetCompiler, tâche](../msbuild/aspnetcompiler-task.md)  
 Inclut dans un wrapper aspnet_compiler.exe, un utilitaire permettant de précompiler des applications ASP.NET.  
  
 [AssignCulture, tâche](../msbuild/assignculture-task.md)  
 Assigne des identificateurs de culture aux éléments.  
  
 [AssignProjectConfiguration, tâche](../msbuild/assignprojectconfiguration-task.md)  
 Accepte une liste de chaînes de configuration et les assigne aux projets spécifiés.  
  
 [AssignTargetPath, tâche](../msbuild/assigntargetpath-task.md)  
 Accepte une liste des fichiers et ajoute des attributs `<TargetPath>` s’ils ne sont pas déjà spécifiés.  
  
 [CallTarget, tâche](../msbuild/calltarget-task.md)  
 Appelle une cible dans le fichier projet.  
  
 [CombinePath, tâche](../msbuild/combinepath-task.md)  
 Combine les chemins spécifiés en un chemin unique.  
  
 [ConvertToAbsolutePath, tâche](../msbuild/converttoabsolutepath-task.md)  
 Convertit une référence ou un chemin relatif en chemin absolu.  
  
 [Copy, tâche](../msbuild/copy-task.md)  
 Copie les fichiers dans un nouvel emplacement.  
  
 [CreateCSharpManifestResourceName, tâche](../msbuild/createcsharpmanifestresourcename-task.md)  
 Crée un nom de manifeste de style [!INCLUDE[csprcs](../includes/csprcs-md.md)] à partir d’un nom de fichier .resx donné ou d’une autre ressource.  
  
 [CreateItem, tâche](../msbuild/createitem-task.md)  
 Remplit des collections d’éléments à partir des éléments d’entrée, en autorisant la copie d’éléments d’une liste dans une autre.  
  
 [CreateProperty, tâche](../msbuild/createproperty-task.md)  
 Remplit des propriétés à partir des valeurs d’entrée, en autorisant la copie de valeurs d’une propriété ou d’une chaîne dans une autre.  
  
 [CreateVisualBasicManifestResourceName, tâche](../msbuild/createvisualbasicmanifestresourcename-task.md)  
 Crée un nom de manifeste de style [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] à partir d’un nom de fichier .resx donné ou d’une autre ressource.  
  
 [Csc, tâche](../msbuild/csc-task.md)  
 Appelle le compilateur Visual C# pour produire des exécutables, des bibliothèques de liens dynamiques ou des modules de code.  
  
 [Delete, tâche](../msbuild/delete-task.md)  
 Supprime les fichiers spécifiés.  
  
 [Error, tâche](../msbuild/error-task.md)  
 Arrête une génération et enregistre une erreur en fonction d’une instruction conditionnelle évaluée.  
  
 [Exec, tâche](../msbuild/exec-task.md)  
 Exécute la commande ou le programme spécifié avec les arguments spécifiés.  
  
 [FindAppConfigFile, tâche](../msbuild/findappconfigfile-task.md)  
 Recherche le fichier app.config, le cas échéant, dans les listes fournies.  
  
 [FindInList, tâche](../msbuild/findinlist-task.md)  
 Recherche un élément dans une liste spécifiée associée à la spécification d’éléments (itemspec) correspondante.  
  
 [FindUnderPath, tâche](../msbuild/findunderpath-task.md)  
 Détermine les éléments de la collection spécifiée qui existent dans le dossier spécifié et tous ses sous-dossiers.  
  
 [FormatUrl, tâche](../msbuild/formaturl-task.md)  
 Convertit une URL en URL au format correct.  
  
 [FormatVersion, tâche](../msbuild/formatversion-task.md)  
 Ajoute le numéro de révision au numéro de version.  
  
 [GenerateApplicationManifest, tâche](../msbuild/generateapplicationmanifest-task.md)  
 Génère un manifeste d’application [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] ou un manifeste natif.  
  
 [GenerateBootstrapper, tâche](../msbuild/generatebootstrapper-task.md)  
 Fournit un moyen automatisé de détecter, télécharger et installer une application et ses composants requis.  
  
 [GenerateDeploymentManifest, tâche](../msbuild/generatedeploymentmanifest-task.md)  
 Génère un manifeste de déploiement [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)].  
  
 [GenerateResource, tâche](../msbuild/generateresource-task.md)  
 Convertit les fichiers .txt et .resx en fichiers .resources binaires du Common Language Runtime.  
  
 [GenerateTrustInfo, tâche](../msbuild/generatetrustinfo-task.md)  
 Génère le niveau de confiance de l’application à partir du manifeste de base, ainsi que des paramètres `TargetZone` et `ExcludedPermissions`.  
  
 [GetAssemblyIdentity, tâche](../msbuild/getassemblyidentity-task.md)  
 Récupère les identités d’assembly des fichiers spécifiés et génère les informations d’identité.  
  
 [GetFrameworkPath, tâche](../msbuild/getframeworkpath-task.md)  
 Récupère le chemin aux assemblys [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)].  
  
 [GetFrameworkSdkPath, tâche](../msbuild/getframeworksdkpath-task.md)  
 Récupère le chemin au [!INCLUDE[winsdklong](../includes/winsdklong-md.md)].  
  
 [GetReferenceAssemblyPaths, tâche](../msbuild/getreferenceassemblypaths-task.md)  
 Retourne les chemins des assemblys de référence des différentes infrastructures.  
  
 [LC, tâche](../msbuild/lc-task.md)  
 Génère un fichier .license à partir d’un fichier .licx.  
  
 [MakeDir, tâche](../msbuild/makedir-task.md)  
 Crée des répertoires et, si nécessaire, des répertoires parents.  
  
 [Message, tâche](../msbuild/message-task.md)  
 Enregistre un message pendant une génération.  
  
 [Move, tâche](../msbuild/move-task.md)  
 Déplace les fichiers vers un nouvel emplacement.  
  
 [MSBuild, tâche](../msbuild/msbuild-task.md)  
 Génère des projets [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] à partir d’un autre projet [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)].  
  
 [ReadLinesFromFile, tâche](../msbuild/readlinesfromfile-task.md)  
 Lit une liste d’éléments à partir d’un fichier texte.  
  
 [RegisterAssembly, tâche](../msbuild/registerassembly-task.md)  
 Lit les métadonnées dans l’assembly spécifié et ajoute les entrées nécessaires au Registre.  
  
 [RemoveDir, tâche](../msbuild/removedir-task.md)  
 Supprime les répertoires spécifiés ainsi que tous leurs fichiers et sous-répertoires.  
  
 [RemoveDuplicates, tâche](../msbuild/removeduplicates-task.md)  
 Supprime les éléments en double de la collection d’éléments spécifiée.  
  
 [RequiresFramework35SP1Assembly, tâche](../msbuild/requiresframework35sp1assembly-task.md)  
 Détermine si l’application nécessite le .NET Framework 3.5 SP1.  
  
 ResGen, tâche  
 Obsolète. Utilisez la tâche [GenerateResource Task](../msbuild/generateresource-task.md) pour convertir des fichiers .txt et .resx en fichiers .resources binaires du Common Language Runtime, et vice versa.  
  
 [ResolveAssemblyReference, tâche](../msbuild/resolveassemblyreference-task.md)  
 Détermine tous les assemblys qui dépendent des assemblys spécifiés.  
  
 [ResolveCOMReference, tâche](../msbuild/resolvecomreference-task.md)  
 Prend une liste d’un ou plusieurs noms de bibliothèques de types ou de fichiers .tlb et résout ces bibliothèques de types aux emplacements sur le disque.  
  
 [ResolveKeySource, tâche](../msbuild/resolvekeysource-task.md)  
 Détermine la source des clés à nom fort.  
  
 [ResolveManifestFiles, tâche](../msbuild/resolvemanifestfiles-task.md)  
 Résout les éléments suivants dans le processus de génération en fichiers pour la génération de manifeste : éléments générés, dépendances, satellites, contenu, symboles de débogage et documentation.  
  
 [ResolveNativeReference, tâche](../msbuild/resolvenativereference-task.md)  
 Résout les références natives.  
  
 [ResolveNonMSBuildProjectOutput, tâche](../msbuild/resolvenonmsbuildprojectoutput-task.md)  
 Détermine les fichiers de sortie des références de projet non-MSBuild.  
  
 [SGen, tâche](../msbuild/sgen-task.md)  
 Crée un assembly de sérialisation XML pour les types dans l’assembly spécifié.  
  
 [SignFile, tâche](../msbuild/signfile-task.md)  
 Signe le fichier spécifié à l'aide du certificat spécifié.  
  
 [Touch, tâche](../msbuild/touch-task.md)  
 Définit les heures d’accès et de modification des fichiers.  
  
 [UnregisterAssembly, tâche](../msbuild/unregisterassembly-task.md)  
 Désinscrit les assemblys spécifiés dans le cadre de COM Interop.  
  
 [UpdateManifest, tâche](../msbuild/updatemanifest-task.md)  
 Met à jour les propriétés sélectionnées dans un manifeste et signe à nouveau.  
  
 [Vbc, tâche](../msbuild/vbc-task.md)  
 Appelle le compilateur Visual Basic pour produire des exécutables, des bibliothèques de liens dynamiques ou des modules de code.  
  
 [Avertissement, tâche](../msbuild/warning-task.md)  
 Enregistre un avertissement durant une génération en fonction d’une instruction conditionnelle évaluée.  
  
 [WriteCodeFragment, tâche](../msbuild/writecodefragment-task.md)  
 Génère un fichier de code temporaire à l’aide du fragment de code généré spécifié. Ne supprime pas le fichier.  
  
 [WriteLinesToFile, tâche](../msbuild/writelinestofile-task.md)  
 Écrit les éléments spécifiés dans le fichier texte spécifié.  
  
 [XmlPeek, tâche](../msbuild/xmlpeek-task.md)  
 Retourne des valeurs comme spécifié par la requête XPath à partir d’un fichier XML.  
  
 [XmlPoke, tâche](../msbuild/xmlpoke-task.md)  
 Définit les valeurs comme spécifié par une requête XPath dans un fichier XML.  
  
 [XslTransformation, tâche](../msbuild/xsltransformation-task.md)  
 Transforme une entrée XML à l’aide d’une *transformation XLS* (XSLT) ou d’un XSLT compilé et envoie la sortie vers un fichier ou un périphérique de sortie.  
  
## <a name="see-also"></a>Voir aussi  
 [Référence MSBuild](../msbuild/msbuild-reference.md)   
 [Task Writing (Écriture de tâches)](../msbuild/task-writing.md)   
 [Tâches MSBuild](../msbuild/msbuild-tasks.md)
