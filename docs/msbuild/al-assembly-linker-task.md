---
title: AL (Assembly Linker), tâche | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#AL
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- AL task [MSBuild]
- MSBuild, AL task
ms.assetid: 2ddefbf2-5662-4d55-99a6-ac383bf44560
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 39340e268d41207e9b054866ecebe613f7836347
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62951281"
---
# <a name="al-assembly-linker-task"></a>AL (Assembly Linker), tâche
La tâche AL encapsule *AL.exe*, un outil distribué avec le [!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)]. L’outil Assembly Linker sert à créer un assembly avec un manifeste à partir d’un ou plusieurs fichiers qui sont soit des modules, soit des fichiers de ressources. Les compilateurs et les environnements de développement pouvant déjà fournir ces fonctionnalités, il n’est généralement pas nécessaire d’utiliser cette tâche directement. Assembly Linker est très utile aux développeurs ayant besoin de créer un assembly unique à partir de plusieurs fichiers de composant, tels que ceux qui peuvent être générés par le développement en plusieurs langages. Cette tâche ne combine pas les modules dans un fichier d’assembly unique. Les modules individuels doivent toujours être distribués et disponibles pour que l’assembly résultant se charge correctement. Pour plus d’informations sur *AL.exe*, consultez [Al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker).

## <a name="parameters"></a>Paramètres
 Le tableau ci-dessous décrit les paramètres de la tâche `AL` .

| Paramètre | Description |
|---------------------| - |
| `AlgorithmID` | Paramètre `String` facultatif.<br /><br /> Spécifie un algorithme de hachage de tous les fichiers dans un assembly multifichier, à l'exception du fichier qui contient le manifeste d'assembly. Pour plus d’informations, consultez la documentation relative à l’option `/algid` dans [Al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `BaseAddress` | Paramètre `String` facultatif.<br /><br /> Spécifie l'adresse de chargement d'une DLL sur l'ordinateur de l'utilisateur au moment de l'exécution. Le chargement des applications est plus rapide si vous spécifiez l’adresse de base des DLL au lieu de laisser le système d’exploitation déplacer les DLL dans l’espace de processus. Ce paramètre correspond à l’option /base[address](/dotnet/framework/tools/al-exe-assembly-linker). |
| `CompanyName` | Paramètre `String` facultatif.<br /><br /> Spécifie une chaîne pour le champ `Company` de l'assembly. Pour plus d’informations, consultez la documentation relative à l’option `/comp[any]` dans [Al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `Configuration` | Paramètre `String` facultatif.<br /><br /> Spécifie une chaîne pour le champ `Configuration` de l'assembly. Pour plus d’informations, consultez la documentation relative à l’option `/config[uration]` dans [Al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `Copyright` | Paramètre `String` facultatif.<br /><br /> Spécifie une chaîne pour le champ `Copyright` de l'assembly. Pour plus d’informations, consultez la documentation relative à l’option `/copy[right]` dans [Al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `Culture` | Paramètre `String` facultatif.<br /><br /> Spécifie la chaîne de culture à associer à l'assembly. Pour plus d’informations, consultez la documentation relative à l’option `/c[ulture]` dans [Al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `DelaySign` | Paramètre `Boolean` facultatif.<br /><br /> `true` pour placer uniquement la clé publique dans l’assembly ; `false` pour signer complètement l’assembly. Pour plus d’informations, consultez la documentation relative à l’option `/delay[sign]` dans [Al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `Description` | Paramètre `String` facultatif.<br /><br /> Spécifie une chaîne pour le champ `Description` de l'assembly. Pour plus d’informations, consultez la documentation relative à l’option `/descr[iption]` dans [Al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `EmbedResources` | Paramètre <xref:Microsoft.Build.Framework.ITaskItem>`[]` facultatif.<br /><br /> Incorpore les ressources spécifiées dans l’image qui contient le manifeste d’assembly. Cette tâche copie le contenu du fichier de ressources dans l’image. Les éléments passés dans ce paramètre peuvent avoir des métadonnées facultatives associées appelées `LogicalName` et `Access`. Les métadonnées `LogicalName` sont utilisées pour spécifier l’identificateur interne de la ressource.  Vous pouvez affecter la valeur `private` aux métadonnées `Access` pour rendre la ressource invisible à d’autres assemblys. Pour plus d’informations, consultez la documentation relative à l’option `/embed[resource]` dans [Al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `EvidenceFile` | Paramètre `String` facultatif.<br /><br /> Incorpore le fichier spécifié dans l’assembly avec le nom de ressource `Security.Evidence`.<br /><br /> Vous ne pouvez pas utiliser `Security.Evidence` pour ses ressources standard. Ce paramètre correspond à l’option `/e[vidence]` dans [Al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `ExitCode` | Paramètre en lecture seule de sortie `Int32` facultatif.<br /><br /> Spécifie le code de sortie fourni par la commande exécutée. |
| `FileVersion` | Paramètre `String` facultatif.<br /><br /> Spécifie une chaîne pour le champ `File Version` de l'assembly. Pour plus d’informations, consultez la documentation relative à l’option `/fileversion` dans [Al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `Flags` | Paramètre `String` facultatif.<br /><br /> Spécifie une valeur pour le champ `Flags` de l'assembly. Pour plus d’informations, consultez la documentation relative à l’option `/flags` dans [Al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `GenerateFullPaths` | Paramètre `Boolean` facultatif.<br /><br /> Force la tâche à utiliser le chemin absolu de tout fichier signalé dans un message d’erreur. Ce paramètre correspond à l’option `/fullpaths` dans [Al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `KeyContainer` | Paramètre `String` facultatif.<br /><br /> Spécifie un conteneur qui contient une paire de clés. Cela signe l'assembly (lui donne un nom fort) en insérant une clé publique dans le manifeste d'assembly. La tâche signe ensuite l’assembly définitif à l’aide de la clé privée. Pour plus d’informations, consultez la documentation relative à l’option `/keyn[ame]` dans [Al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `KeyFile` | Paramètre `String` facultatif.<br /><br /> Spécifie un fichier qui contient une paire de clés ou juste une clé publique pour signer un assembly. Le compilateur insère la clé publique dans le manifeste d'assembly, puis signe l'assembly final avec la clé privée. Pour plus d’informations, consultez la documentation relative à l’option `/keyf[ile]` dans [Al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `LinkResources` | Paramètre <xref:Microsoft.Build.Framework.ITaskItem>`[]` facultatif.<br /><br /> Lie les fichiers de ressources spécifiés à un assembly. La ressource est intégrée à l’assembly, mais le fichier n’est pas copié. Les éléments passés dans ce paramètre peuvent avoir des métadonnées facultatives associées appelées `LogicalName`, `Target` et `Access`. Les métadonnées `LogicalName` sont utilisées pour spécifier l’identificateur interne de la ressource. Les métadonnées `Target` peuvent spécifier le chemin et le nom de fichier où la tâche copie le fichier, avant de compiler ce nouveau fichier dans l’assembly. Vous pouvez affecter la valeur `private` aux métadonnées `Access` pour rendre la ressource invisible à d’autres assemblys. Pour plus d’informations, consultez la documentation relative à l’option `/link[resource]` dans [Al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `MainEntryPoint` | Paramètre `String` facultatif.<br /><br /> Spécifie le nom complet (*class.method*) de la méthode à utiliser comme point d’entrée lors de la conversion d’un module en fichier exécutable. Ce paramètre correspond à l’option `/main` dans [Al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `OutputAssembly` | Paramètre de sortie <xref:Microsoft.Build.Framework.ITaskItem> obligatoire.<br /><br /> Spécifie le nom du fichier généré par cette tâche. Ce paramètre correspond à l’option `/out` dans [Al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `Platform` | Paramètre `String` facultatif.<br /><br /> Limite la plateforme sur laquelle ce code peut s’exécuter. Doit correspondre à l’une des valeurs suivantes : `x86`, `Itanium`, `x64` ou `anycpu`. La valeur par défaut est `anycpu`. Ce paramètre correspond à l’option `/platform` dans [Al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `ProductName` | Paramètre `String` facultatif.<br /><br /> Spécifie une chaîne pour le champ `Product` de l'assembly. Pour plus d’informations, consultez la documentation relative à l’option `/prod[uct]` dans [Al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `ProductVersion` | Paramètre `String` facultatif.<br /><br /> Spécifie une chaîne pour le champ `ProductVersion` de l'assembly. Pour plus d’informations, consultez la documentation relative à l’option `/productv[ersion]` dans [Al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `ResponseFiles` | Paramètre `String[]` facultatif.<br /><br /> Spécifie les fichiers réponse qui contiennent des options supplémentaires à passer à Assembly Linker. |
| `SdkToolsPath` | Paramètre `String` facultatif.<br /><br /> Spécifie le chemin des outils du SDK, comme resgen.exe. |
| `SourceModules` | Paramètre <xref:Microsoft.Build.Framework.ITaskItem>`[]` facultatif.<br /><br /> Un ou plusieurs modules à compiler dans un assembly. Les modules seront répertoriés dans le manifeste de l’assembly résultant, et devront toujours être distribués et disponibles pour que l’assembly se charge. Les éléments passés dans ce paramètre peuvent avoir des métadonnées supplémentaires appelées `Target`, qui spécifient le chemin et le nom de fichier où la tâche copie le fichier, avant de compiler ce nouveau fichier dans l’assembly. Pour plus d’informations, consultez la documentation relative [Al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). Ce paramètre correspond à la liste des modules transmis à *Al.exe* sans commutateur spécifique. |
| `TargetType` | Paramètre `String` facultatif.<br /><br /> Spécifie le format du fichier de sortie : `library` (bibliothèque de codes), `exe` (application console) ou `win` (application Windows). La valeur par défaut est `library`. Ce paramètre correspond à l’option `/t[arget]` dans [Al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `TemplateFile` | Paramètre `String` facultatif.<br /><br /> Spécifie l’assembly à partir duquel hériter de toutes les métadonnées d’assembly, à l’exception du champ Culture. L’assembly spécifié doit avoir un nom fort.<br /><br /> Un assembly créé avec le paramètre `TemplateFile` est un assembly satellite. Ce paramètre correspond à l’option `/template` dans [Al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `Timeout` | Paramètre `Int32` facultatif.<br /><br /> Spécifie le délai, en millisecondes, après lequel l’exécutable de la tâche est arrêté. La valeur par défaut est `Int.MaxValue`, ce qui indique qu’il n’existe aucun délai d’expiration. |
| `Title` | Paramètre `String` facultatif.<br /><br /> Spécifie une chaîne pour le champ `Title` de l'assembly. Pour plus d’informations, consultez la documentation relative à l’option `/title` dans [Al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `ToolPath` | Paramètre `String` facultatif.<br /><br /> Spécifie l’emplacement à partir duquel la tâche chargera le fichier exécutable sous-jacent (Al.exe). Si vous ne spécifiez pas ce paramètre, la tâche utilise le chemin d’installation du SDK correspondant à la version du framework qui exécute [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]. |
| `Trademark` | Paramètre `String` facultatif.<br /><br /> Spécifie une chaîne pour le champ `Trademark` de l'assembly. Pour plus d’informations, consultez la documentation relative à l’option `/trade[mark]` dans [Al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `Version` | Paramètre `String` facultatif.<br /><br /> Spécifie les informations de version pour cet assembly. Le format de la chaîne est *principale.mineure.build.révision*. La valeur par défaut est 0. Pour plus d’informations, consultez la documentation relative à l’option `/v[ersion]` dans [Al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `Win32Icon` | Paramètre `String` facultatif.<br /><br /> Insère un fichier *.ico* dans l’assembly. Le fichier *.ico* donne au fichier de sortie l’aspect souhaité dans l’Explorateur de fichiers. Ce paramètre correspond à l’option `/win32icon` dans [Al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `Win32Resource` | Paramètre `String` facultatif.<br /><br /> Insère une ressource Win32 (fichier *.res*) dans le fichier de sortie. Pour plus d’informations, consultez la documentation relative à l’option `/win32res` dans [Al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). |

## <a name="remarks"></a>Remarques
 En plus des paramètres énumérés ci-dessus, cette tâche hérite des paramètres de la classe <xref:Microsoft.Build.Tasks.ToolTaskExtension>, qui elle-même hérite de la classe <xref:Microsoft.Build.Utilities.ToolTask>. Pour obtenir la liste de ces paramètres supplémentaires et leurs descriptions, consultez [Classe de base ToolTaskExtension](../msbuild/tooltaskextension-base-class.md).

## <a name="example"></a>Exemple
 L’exemple suivant crée un assembly avec les options spécifiées.

```xml
<AL
    EmbedResources="@(EmbeddedResource)"
    Culture="%(EmbeddedResource.Culture)"
    TemplateFile="@(IntermediateAssembly)"
    KeyContainer="$(KeyContainerName)"
    KeyFile="$(KeyOriginatorFile)"
    DelaySign="$(DelaySign)"

    OutputAssembly=
       "%(EmbeddedResource.Culture)\$(TargetName).resources.dll">

    <Output TaskParameter="OutputAssembly"
        ItemName="SatelliteAssemblies"/>
</AL>
```

## <a name="see-also"></a>Voir aussi
* [Informations de référence sur les tâches](../msbuild/msbuild-task-reference.md)
* [Tâches](../msbuild/msbuild-tasks.md)
