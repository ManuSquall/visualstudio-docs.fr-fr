---
title: Csc, tâche | Microsoft Docs
description: Cet article décrit la tâche du CSC MSBuild, qui encapsule le compilateur C#, csc.exe et produit des fichiers .exe, .dll ou. netmodule.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Csc
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Csc task [MSBuild]
- MSBuild, Csc task
ms.assetid: d8c19b36-f5ca-484b-afa6-8ff3b90e103a
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 10a63b114379f56ca5f253f853a1ff6bdd6c60dc
ms.sourcegitcommit: 3fe04d5b931ae459a802a1b965f84186757cbc08
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2021
ms.locfileid: "111588473"
---
# <a name="csc-task"></a>Csc (tâche)

Encapsule *csc.exe* et produit des fichiers exécutables (*.exe*), des bibliothèques de liens dynamiques (*.dll*) ou des modules de code (*.netmodule*). Pour plus d’informations sur *csc.exe*, consultez [Options du compilateur C#](/dotnet/csharp/language-reference/compiler-options/index).

## <a name="parameters"></a>Paramètres

Le tableau ci-dessous décrit les paramètres de la tâche `Csc` .

| Paramètre | Description |
|------------------------------| - |
| `AdditionalLibPaths` | Paramètre `String[]` facultatif.<br /><br /> Spécifie des répertoires supplémentaires dans lesquels rechercher des références. Pour plus d’informations, consultez [-lib (options du compilateur C#)](/dotnet/csharp/language-reference/compiler-options/lib-compiler-option). |
| `AddModules` | Paramètre `String` facultatif.<br /><br /> Spécifie un ou plusieurs modules à inclure dans cet assembly. Pour plus d’informations, consultez [-addmodule (options du compilateur C#)](/dotnet/csharp/language-reference/compiler-options/addmodule-compiler-option). |
| `AllowUnsafeBlocks` | Paramètre `Boolean` facultatif.<br /><br /> Si `true`, compile le code qui utilise le mot clé [unsafe](/dotnet/csharp/language-reference/keywords/unsafe). Pour plus d’informations, consultez [-unsafe (options du compilateur C#)](/dotnet/csharp/language-reference/compiler-options/unsafe-compiler-option). |
| `ApplicationConfiguration` | Paramètre `String` facultatif.<br /><br /> Spécifie le fichier de configuration de l’application contenant les paramètres de liaison d’assembly. |
| `BaseAddress` | Paramètre `String` facultatif.<br /><br /> Spécifie l'adresse de base préférée à laquelle charger une DLL. L’adresse de base par défaut d’une DLL est définie par le Common Language Runtime (CLR) .NET Framework. Pour plus d’informations, consultez [-baseaddress (options du compilateur C#)](/dotnet/csharp/language-reference/compiler-options/baseaddress-compiler-option). |
| `CheckForOverflowUnderflow` | Paramètre `Boolean` facultatif.<br /><br /> Indique si l’arithmétique sur les entiers qui dépasse les limites du type de données entraîne une exception au moment de l’exécution. Pour plus d’informations, consultez [-checked (options du compilateur C#)](/dotnet/csharp/language-reference/compiler-options/checked-compiler-option). |
| `CodePage` | Paramètre `Int32` facultatif.<br /><br /> Spécifie la page de codes à utiliser pour tous les fichiers de code source inclus dans la compilation. Pour plus d’informations, consultez [-codepage (options du compilateur C#)](/dotnet/csharp/language-reference/compiler-options/codepage-compiler-option). |
| `DebugType` | Paramètre `String` facultatif.<br /><br /> Spécifie le type de débogage. `DebugType` peut avoir la valeur `full` ou `pdbonly`. La valeur par défaut est `full`, ce qui permet d’attacher un débogueur à un programme en cours d’exécution. La spécification de `pdbonly` active le débogage du code source lorsque le programme est démarré dans le débogueur, mais affiche uniquement un assembleur lorsque le programme en cours d’exécution est attaché au débogueur.<br /><br /> Ce paramètre remplace le paramètre `EmitDebugInformation`.<br /><br /> Pour plus d’informations, consultez [-debug (options du compilateur C#)](/dotnet/csharp/language-reference/compiler-options/debug-compiler-option). |
| `DefineConstants` | Paramètre `String` facultatif.<br /><br /> Définit les symboles du préprocesseur. Pour plus d’informations, consultez [-define (options du compilateur C#)](/dotnet/csharp/language-reference/compiler-options/define-compiler-option). |
| `DelaySign` | Paramètre `Boolean` facultatif.<br /><br /> Si `true`, indique que vous souhaitez placer uniquement la clé publique dans l’assembly. Si `false` , spécifie que vous souhaitez un assembly complètement signé<br /><br /> Ce paramètre n’a aucun effet, sauf s’il est utilisé avec les paramètres `KeyFile` ou `KeyContainer`.<br /><br /> Pour plus d’informations, consultez [-delaysign (options du compilateur C#)](/dotnet/csharp/language-reference/compiler-options/delaysign-compiler-option). |
| `Deterministic` | Paramètre `Boolean` facultatif.<br/><br/> Quand la valeur est `true`, indique au compilateur de générer un assembly dont le contenu binaire est identique dans les compilations si les entrées sont identiques.<br/><br/>Pour plus d’informations, consultez [-deterministic (options du compilateur C#)](/dotnet/csharp/language-reference/compiler-options/deterministic-compiler-option). |
| `DisabledWarnings` | Paramètre `String` facultatif.<br /><br /> Spécifie la liste d’avertissements à désactiver. Pour plus d’informations, consultez [-nowarn (options du compilateur C#)](/dotnet/csharp/language-reference/compiler-options/nowarn-compiler-option). |
| `DocumentationFile` | Paramètre `String` facultatif.<br /><br /> Traite les commentaires de documentation pour les diriger vers un fichier XML. Pour plus d’informations, consultez [-doc (options du compilateur C#)](/dotnet/csharp/language-reference/compiler-options/doc-compiler-option). |
| `EmbedAllSources` | Paramètre `Boolean` facultatif.<br /><br /> Incorporer tous les fichiers sources du PDB. Pour plus d’informations, consultez [-embed (options du compilateur C#)](/dotnet/csharp/language-reference/compiler-options/listed-alphabetically) |
| `EmitDebugInformation` | Paramètre `Boolean` facultatif.<br /><br /> Si `true`, la tâche génère des informations de débogage et les place dans un fichier de base de données du programme (.pdb). Si `false`, la tâche n’émet aucune information de débogage. La valeur par défaut est `false`. Pour plus d’informations, consultez [-debug (options du compilateur C#)](/dotnet/csharp/language-reference/compiler-options/debug-compiler-option). |
| `ErrorReport` | Paramètre `String` facultatif.<br /><br /> Fournit un moyen pratique de signaler une erreur interne C# à Microsoft. Ce paramètre peut avoir la valeur `prompt`, `send` ou `none`. Si le paramètre est défini sur `prompt`, vous recevez une invite lorsqu’une erreur interne du compilateur se produit. Cette invite vous permet d’envoyer un rapport de bogue par voie électronique à Microsoft. Si le paramètre est défini sur `send`, un rapport de bogue est automatiquement envoyé. Si le paramètre est défini sur `none`, l’erreur est signalée uniquement dans la sortie de texte du compilateur. La valeur par défaut est `none`. Pour plus d’informations, consultez [-errorreport (options du compilateur C#)](/dotnet/csharp/language-reference/compiler-options/errorreport-compiler-option). |
| `FileAlignment` | Paramètre `Int32` facultatif.<br /><br /> Spécifie la taille des sections dans le fichier de sortie. Pour plus d’informations, consultez [-filealign (options du compilateur C#)](/dotnet/csharp/language-reference/compiler-options/filealign-compiler-option). |
| `GenerateFullPaths` | Paramètre `Boolean` facultatif.<br /><br /> Si `true`, spécifie le chemin d’accès absolu au fichier dans la sortie du compilateur. Si `false`, spécifie le nom du fichier. La valeur par défaut est `false`. Pour plus d’informations, consultez [-fullpaths (options du compilateur C#)](/dotnet/csharp/language-reference/compiler-options/fullpaths-compiler-option). |
| `KeyContainer` | Paramètre `String` facultatif.<br /><br /> Spécifie le nom du conteneur de la clé de chiffrement. Pour plus d’informations, consultez [-keycontainer (options du compilateur C#)](/dotnet/csharp/language-reference/compiler-options/keycontainer-compiler-option). |
| `KeyFile` | Paramètre `String` facultatif.<br /><br /> Spécifie le nom du fichier contenant la clé de chiffrement. Pour plus d’informations, consultez [-keyfile (options du compilateur C#)](/dotnet/csharp/language-reference/compiler-options/keyfile-compiler-option). |
| `LangVersion` | Paramètre `String` facultatif.<br /><br /> Spécifie la version du langage à utiliser. Pour plus d’informations, consultez [-langversion (options du compilateur C#)](/dotnet/csharp/language-reference/compiler-options/langversion-compiler-option). |
| `LinkResources` | Paramètre <xref:Microsoft.Build.Framework.ITaskItem>`[]` facultatif.<br /><br /> Crée un lien à une ressource .NET Framework dans le fichier de sortie ; le fichier de ressources n’est pas placé dans le fichier de sortie.<br /><br /> Les éléments transmis dans ce paramètre peuvent posséder des entrées de métadonnées facultatives nommées `LogicalName` et `Access`. `LogicalName` correspond au paramètre `identifier` du commutateur `/linkresource`, et `Access` correspond au paramètre `accessibility-modifier`. Pour plus d’informations, consultez [-linkresource (options du compilateur C#)](/dotnet/csharp/language-reference/compiler-options/linkresource-compiler-option). |
| `MainEntryPoint` | Paramètre `String` facultatif.<br /><br /> Spécifie l’emplacement de la méthode `Main`. Pour plus d’informations, consultez [-main (options du compilateur C#)](/dotnet/csharp/language-reference/compiler-options/main-compiler-option). |
| `ModuleAssemblyName` | Paramètre `String` facultatif.<br /><br /> Spécifie le nom de l’assembly dont ce module doit faire partie. |
| `NoConfig` | Paramètre `Boolean` facultatif.<br /><br /> Si la valeur est `true`, indique au compilateur de ne pas compiler avec le fichier *csc.rsp*. Pour plus d’informations, consultez [-noconfig (options du compilateur C#)](/dotnet/csharp/language-reference/compiler-options/noconfig-compiler-option). |
| `NoLogo` | Paramètre `Boolean` facultatif.<br /><br /> Si `true`, supprime l’affichage des informations de bannière du compilateur. Pour plus d’informations, consultez [-nologo (options du compilateur C#)](/dotnet/csharp/language-reference/compiler-options/nologo-compiler-option). |
| `NoStandardLib` | Paramètre `Boolean` facultatif.<br /><br /> Si sa valeur est `true`, empêche l’importation de *mscorlib.dll*, qui définit la totalité de l’espace de noms système. Utilisez ce paramètre si vous souhaitez définir ou créer vos propres objets et espace de noms système. Pour plus d’informations, consultez [-nostdlib (options du compilateur C#)](/dotnet/csharp/language-reference/compiler-options/nostdlib-compiler-option). |
| `NoWin32Manifest` | Paramètre `Boolean` facultatif.<br /><br /> Si `true`, n’inclut pas le manifeste Win32 par défaut. |
| `Optimize` | Paramètre `Boolean` facultatif.<br /><br /> Si `true`, active les optimisations. Si `false`, désactive les optimisations. Pour plus d’informations, consultez [-optimize (options du compilateur C#)](/dotnet/csharp/language-reference/compiler-options/optimize-compiler-option). |
| `OutputAssembly` | Paramètre de sortie `String` facultatif.<br /><br /> Spécifie le nom du fichier de sortie. Pour plus d’informations, consultez [-out (options du compilateur C#)](/dotnet/csharp/language-reference/compiler-options/out-compiler-option). |
| `OutputRefAssembly` | Paramètre `String` facultatif.<br /><br /> Spécifie le nom du fichier d’assembly de la référence de sortie. Pour plus d’informations, consultez [-refout (options du compilateur C#)](/dotnet/csharp/language-reference/compiler-options/refout-compiler-option). |
| `PdbFile` | Paramètre `String` facultatif.<br /><br /> Spécifie le nom de fichier des informations de débogage. Le nom par défaut est le nom du fichier de sortie avec l’extension *.pdb*. |
| `Platform` | Paramètre `String` facultatif.<br /><br /> Spécifie la plateforme de processeur ciblée par le fichier de sortie. Ce paramètre peut avoir la valeur `x86`, `x64` ou `anycpu`. La valeur par défaut est `anycpu`. Pour plus d’informations, consultez [-Platform (options du compilateur C#)](/dotnet/csharp/language-reference/compiler-options/platform-compiler-option). |
| `References` | Paramètre <xref:Microsoft.Build.Framework.ITaskItem>`[]` facultatif.<br /><br /> Provoque l’importation par la tâche des informations de type public dans le projet actuel à partir des éléments spécifiés. Pour plus d’informations, consultez [-reference (options du compilateur C#)](/dotnet/csharp/language-reference/compiler-options/reference-compiler-option).<br /><br /> Vous pouvez spécifier un alias de référence C# dans un fichier MSBuild en ajoutant les métadonnées `Aliases` à l’élément « référence » d’origine. Par exemple, pour définir l’alias « LS1 » dans la ligne de commande CSC suivante :<br /><br /> `CSC /r:LS1=MyCodeLibrary.dll /r:LS2=MyCodeLibrary2.dll *.cs`<br /><br /> Vous devez utiliser :<br /><br /> `<Reference Include="MyCodeLibrary"> <Aliases>LS1</Aliases> </Reference>` |
| `Resources` | Paramètre <xref:Microsoft.Build.Framework.ITaskItem>`[]` facultatif.<br /><br /> Incorpore une ressource .NET Framework dans le fichier de sortie.<br /><br /> Les éléments transmis dans ce paramètre peuvent posséder des entrées de métadonnées facultatives nommées `LogicalName` et `Access`. `LogicalName` correspond au paramètre `identifier` du commutateur `/resource`, et `Access` correspond au paramètre `accessibility-modifier`. Pour plus d’informations, consultez [-resource (options du compilateur C#)](/dotnet/csharp/language-reference/compiler-options/resource-compiler-option). |
| `ResponseFiles` | Paramètre `String` facultatif.<br /><br /> Spécifie le fichier réponse qui contient les commandes correspondant à cette tâche. Pour plus d’informations, consultez [@ (Spécifier un fichier réponse)](/dotnet/csharp/language-reference/compiler-options/response-file-compiler-option). |
| `Sources` | Paramètre <xref:Microsoft.Build.Framework.ITaskItem>`[]` facultatif.<br /><br /> Spécifie un ou plusieurs fichiers sources C#. |
| `TargetType` | Paramètre `String` facultatif.<br /><br /> Spécifie le format de fichier du fichier de sortie. Ce paramètre peut avoir la valeur `library`, qui crée une bibliothèque de codes, `exe`, qui crée une application console, `module`, qui crée un module, ou `winexe`, qui crée un programme Windows. La valeur par défaut est `library`. Pour plus d’informations, consultez [-target (options du compilateur C#)](/dotnet/csharp/language-reference/compiler-options/target-compiler-option). |
| `TreatWarningsAsErrors` | Paramètre `Boolean` facultatif.<br /><br /> Si `true`, traite tous les avertissements comme des erreurs. Pour plus d’informations, consultez [-warnaserror (options du compilateur C#)](/dotnet/csharp/language-reference/compiler-options/warnaserror-compiler-option). |
| `UseHostCompilerIfAvailable` | Paramètre `Boolean` facultatif.<br /><br /> Demande à la tâche d’utiliser l’objet de compilateur in-process s’il est disponible. Utilisé uniquement par Visual Studio. |
| `Utf8Output` | Paramètre `Boolean` facultatif.<br /><br /> Enregistre les résultats de la compilation au format d’encodage UTF-8. Pour plus d’informations, consultez [-utf8output (options du compilateur C#)](/dotnet/csharp/language-reference/compiler-options/utf8output-compiler-option). |
| `WarningLevel` | Paramètre `Int32` facultatif.<br /><br /> Spécifie le niveau d’avertissement que le compilateur doit afficher. Pour plus d’informations, consultez [-Warn (options du compilateur C#)](/dotnet/csharp/language-reference/compiler-options/warn-compiler-option). |
| `WarningsAsErrors` | Paramètre `String` facultatif.<br /><br /> Spécifie une liste d'avertissements à traiter comme des erreurs. Pour plus d’informations, consultez [-warnaserror (options du compilateur C#)](/dotnet/csharp/language-reference/compiler-options/warnaserror-compiler-option).<br /><br /> Ce paramètre remplace le paramètre `TreatWarningsAsErrors`. |
| `WarningsNotAsErrors` | Paramètre `String` facultatif.<br /><br /> Spécifie une liste d'avertissements à ne pas traiter comme des erreurs. Pour plus d’informations, consultez [-warnaserror (options du compilateur C#)](/dotnet/csharp/language-reference/compiler-options/warnaserror-compiler-option).<br /><br /> Ce paramètre est utile uniquement si le paramètre `TreatWarningsAsErrors` est défini sur `true`. |
| `Win32Icon` | Paramètre `String` facultatif.<br /><br /> Insère un fichier *. ico* dans l’assembly, qui donne au fichier de sortie l’apparence souhaitée dans l' **Explorateur de fichiers**. Pour plus d’informations, consultez [-win32icon (options du compilateur C#)](/dotnet/csharp/language-reference/compiler-options/win32icon-compiler-option). |
| `Win32Manifest` | Paramètre `String` facultatif.<br /><br /> Spécifie le manifeste Win32 à inclure. |
| `Win32Resource` | Paramètre `String` facultatif.<br /><br /> Insère un fichier de ressources Win32 (*. res*) dans le fichier de sortie. Pour plus d’informations, consultez [-win32res (options du compilateur C#)](/dotnet/csharp/language-reference/compiler-options/win32res-compiler-option). |

[!INCLUDE [ToolTaskExtension arguments](includes/tooltaskextension-base-params.md)]

## <a name="example"></a>Exemple

L’exemple suivant utilise la tâche `Csc` pour compiler un fichier exécutable à partir des fichiers sources de la collection d’éléments `Compile`.

```xml
<CSC
    Sources="@(Compile)"
    OutputAssembly="$(AppName).exe"
    EmitDebugInformation="true" />
```

## <a name="see-also"></a>Voir aussi

- [Informations de référence sur les tâches](../msbuild/msbuild-task-reference.md)
- [Tâches](../msbuild/msbuild-tasks.md)
