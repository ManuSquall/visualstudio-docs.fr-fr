---
title: Csc, tâche | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
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
caps.latest.revision: 30
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e0dd27fe64982e77872e37ec01dbdb71a0a141ae
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65694099"
---
# <a name="csc-task"></a>Csc, tâche
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Encapsule CSC.exe et produit des fichiers exécutables (.exe), des bibliothèques de liens dynamiques (.dll) ou des modules de code (.netmodule). Pour plus d’informations sur CSC.exe, consultez l’article [C# Compiler Options (Options du compilateur C#)](https://msdn.microsoft.com/library/d3403556-1816-4546-a782-e8223a772e44).  
  
## <a name="parameters"></a>Paramètres  
 Le tableau ci-dessous décrit les paramètres de la tâche `Csc` .  
  
|Paramètre|Description|  
|---------------|-----------------|  
|`AdditionalLibPaths`|Paramètre `String[]` facultatif.<br /><br /> Spécifie des répertoires supplémentaires dans lesquels rechercher des références. Pour plus d’informations, consultez l’article [/lib (C# Compiler Options) (/lib [Options du compilateur C#])](https://msdn.microsoft.com/library/b0efcc88-e8aa-4df4-a00b-8bdef70b7673).|  
|`AddModules`|Paramètre `String` facultatif.<br /><br /> Spécifie un ou plusieurs modules à inclure dans cet assembly. Pour plus d’informations, consultez l’article [/addmodule (C# Compiler Options) (/addmodule [Options du compilateur C#])](https://msdn.microsoft.com/library/ed604546-0dc2-4bd4-9a3e-610a8d973e58).|  
|`AllowUnsafeBlocks`|Paramètre `Boolean` facultatif.<br /><br /> Si `true`, compile le code qui utilise le mot clé [unsafe](https://msdn.microsoft.com/library/7e818009-1c6e-4b9e-b769-3728a01586a0). Pour plus d’informations, consultez l’article [/unsafe (C# Compiler Options) (/unsafe [Options du compilateur C#])](https://msdn.microsoft.com/library/fdb77ed9-da03-45bd-bb7f-250704da1bcc).|  
|`ApplicationConfiguration`|Paramètre `String` facultatif.<br /><br /> Spécifie le fichier de configuration de l’application contenant les paramètres de liaison d’assembly.|  
|`BaseAddress`|Paramètre `String` facultatif.<br /><br /> Spécifie l'adresse de base préférée à laquelle charger une DLL. L’adresse de base par défaut d’une DLL est définie par le common language runtime [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]. Pour plus d’informations, consultez l’article [/baseaddress (C# Compiler Options) (/baseaddress [Options du compilateur C#])](https://msdn.microsoft.com/library/ce13c965-dfe4-4433-94f5-63b476e3a608).|  
|`CheckForOverflowUnderflow`|Paramètre `Boolean` facultatif.<br /><br /> Indique si l’arithmétique sur les entiers qui dépasse les limites du type de données entraîne une exception au moment de l’exécution. Pour plus d’informations, consultez l’article [/checked (C# Compiler Options) (/checked [Options du compilateur C#])](https://msdn.microsoft.com/library/fb7475d3-e6a6-4e6d-b86c-69e7a74c854b).|  
|`CodePage`|Paramètre `Int32` facultatif.<br /><br /> Spécifie la page de codes à utiliser pour tous les fichiers de code source inclus dans la compilation. Pour plus d’informations, consultez l’article [/codepage (C# Compiler Options) (/codepage [Options du compilateur C#])](https://msdn.microsoft.com/library/75942989-b69a-4308-90a0-840c73d2c478).|  
|`DebugType`|Paramètre `String` facultatif.<br /><br /> Spécifie le type de débogage. `DebugType` peut avoir la valeur `full` ou `pdbonly`. La valeur par défaut est `full`, ce qui permet d’attacher un débogueur à un programme en cours d’exécution. La spécification de `pdbonly` active le débogage du code source lorsque le programme est démarré dans le débogueur, mais affiche uniquement un assembleur lorsque le programme en cours d’exécution est attaché au débogueur.<br /><br /> Ce paramètre remplace le paramètre `EmitDebugInformation`.<br /><br /> Pour plus d’informations, consultez l’article [/debug (C# Compiler Options) (/debug [Options du compilateur C#])](https://msdn.microsoft.com/library/e2b48c07-01bc-45cc-a52c-92e9085eb969).|  
|`DefineConstants`|Paramètre `String` facultatif.<br /><br /> Définit les symboles du préprocesseur. Pour plus d’informations, consultez l’article [/define (C# Compiler Options) (/define [Options du compilateur C#])](https://msdn.microsoft.com/library/f17d7b4d-82d0-4133-8563-68cced1cac6e).|  
|`DelaySign`|Paramètre `Boolean` facultatif.<br /><br /> Si `true`, indique que vous souhaitez obtenir un assembly complètement signé. Si `false`, indique que vous souhaitez placer uniquement la clé publique dans l’assembly.<br /><br /> Ce paramètre n’a aucun effet, sauf s’il est utilisé avec les paramètres `KeyFile` ou `KeyContainer`.<br /><br /> Pour plus d’informations, consultez l’article [/delaysign (C# Compiler Options) (/delaysign [Options du compilateur C#])](https://msdn.microsoft.com/library/bcb058eb-2933-4e7f-b356-5c941db4de75).|  
|`DisabledWarnings`|Paramètre `String` facultatif.<br /><br /> Spécifie la liste d’avertissements à désactiver. Pour plus d’informations, consultez l’article [/nowarn (C# Compiler Options) (/nowarn [Options du compilateur C#])](https://msdn.microsoft.com/library/6dcbc5e8-ae67-4566-9df3-f63cfdd9c4e4).|  
|`DocumentationFile`|Paramètre `String` facultatif.<br /><br /> Traite les commentaires de documentation pour les diriger vers un fichier XML. Pour plus d’informations, consultez l’article [/doc (C# Compiler Options) (/doc [Options du compilateur C#])](https://msdn.microsoft.com/library/849eea59-c936-4311-bad8-d07404480f2a).|  
|`EmitDebugInformation`|Paramètre `Boolean` facultatif.<br /><br /> Si `true`, la tâche génère des informations de débogage et les place dans un fichier de base de données du programme (.pdb). Si `false`, la tâche n’émet aucune information de débogage. La valeur par défaut est `false`. Pour plus d’informations, consultez [/debug (options du compilateur C#)](https://msdn.microsoft.com/library/e2b48c07-01bc-45cc-a52c-92e9085eb969).|  
|`ErrorReport`|Paramètre `String` facultatif.<br /><br /> Fournit un moyen pratique de signaler une erreur interne C# à Microsoft. Ce paramètre peut avoir la valeur `prompt`, `send` ou `none`. Si le paramètre est défini sur `prompt`, vous recevez une invite lorsqu’une erreur interne du compilateur se produit. Cette invite vous permet d’envoyer un rapport de bogue par voie électronique à Microsoft. Si le paramètre est défini sur `send`, un rapport de bogue est automatiquement envoyé. Si le paramètre est défini sur `none`, l’erreur est signalée uniquement dans la sortie de texte du compilateur. La valeur par défaut est `none`. Pour plus d’informations, consultez l’article [/errorreport (C# Compiler Options) (/errorreport [Options du compilateur C#])](https://msdn.microsoft.com/library/bd0e7493-b79d-4369-9c3f-ba26ebdfbedf).|  
|`FileAlignment`|Paramètre `Int32` facultatif.<br /><br /> Spécifie la taille des sections dans le fichier de sortie. Pour plus d’informations, consultez [/filealign (options du compilateur C#)](https://msdn.microsoft.com/library/15cf1c98-3798-4ced-9f08-60619308a073).|  
|`GenerateFullPaths`|Paramètre `Boolean` facultatif.<br /><br /> Si `true`, spécifie le chemin d’accès absolu au fichier dans la sortie du compilateur. Si `false`, spécifie le nom du fichier. La valeur par défaut est `false`. Pour plus d’informations, consultez l’article [/fullpaths (C# Compiler Options) (/fullpaths [Options du compilateur C#])](https://msdn.microsoft.com/library/d2a5f857-cbb2-430b-879c-d648aaf0b8c4).|  
|`KeyContainer`|Paramètre `String` facultatif.<br /><br /> Spécifie le nom du conteneur de la clé de chiffrement. Pour plus d’informations, consultez l’article [/keycontainer (C# Compiler Options) (/keycontainer [Options du compilateur C#])](https://msdn.microsoft.com/library/b3982b6d-2382-4f7e-bebd-ce98eaa30763).|  
|`KeyFile`|Paramètre `String` facultatif.<br /><br /> Spécifie le nom du fichier contenant la clé de chiffrement. Pour plus d’informations, consultez l’article [/keyfile (C# Compiler Options) (/keyfile [Options du compilateur C#])](https://msdn.microsoft.com/library/0815f9de-ace4-4e98-b4c6-13c55dea40c2).|  
|`LangVersion`|Paramètre `String` facultatif.<br /><br /> Spécifie la version du langage à utiliser. Pour plus d’informations, consultez [/langversion (options du compilateur C#)](https://msdn.microsoft.com/library/3fb00b05-a0ff-4782-b313-13a4c0f62d94).|  
|`LinkResources`|Paramètre <xref:Microsoft.Build.Framework.ITaskItem>`[]` facultatif.<br /><br /> Crée un lien à une ressource [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] dans le fichier de sortie ; le fichier de ressources n’est pas placé dans le fichier de sortie.<br /><br /> Les éléments transmis dans ce paramètre peuvent posséder des entrées de métadonnées facultatives nommées `LogicalName` et `Access`. `LogicalName` correspond au paramètre `identifier` du commutateur `/linkresource`, et `Access` correspond au paramètre `accessibility-modifier`. Pour plus d’informations, consultez l’article [/linkresource (C# Compiler Options) (/linkresource [Options du compilateur C#])](https://msdn.microsoft.com/library/440c26c2-77c1-4811-a0a3-57cce3f5fc96).|  
|`MainEntryPoint`|Paramètre `String` facultatif.<br /><br /> Spécifie l’emplacement de la méthode `Main`. Pour plus d’informations, consultez l’article [/main (C# Compiler Options) (/main [Options du compilateur C#])](https://msdn.microsoft.com/library/975cf4d5-36ac-4530-826c-4aad0c7f2049).|  
|`ModuleAssemblyName`|Paramètre `String` facultatif.<br /><br /> Spécifie le nom de l’assembly dont ce module doit faire partie.|  
|`NoConfig`|Paramètre `Boolean` facultatif.<br /><br /> Si `true`, indique au compilateur de ne pas compiler avec le fichier csc.rsp. Pour plus d’informations, consultez l’article [/noconfig (C# Compiler Options) (/noconfig [Options du compilateur C#])](https://msdn.microsoft.com/library/cd26967e-e494-4c8c-b5c9-af13b2f78b2e).|  
|`NoLogo`|Paramètre `Boolean` facultatif.<br /><br /> Si `true`, supprime l’affichage des informations de bannière du compilateur. Pour plus d’informations, consultez l’article [/nologo (C# Compiler Options) (/nologo [Options du compilateur C#])](https://msdn.microsoft.com/library/426afb36-a8fb-469d-9c45-a35d9512557c).|  
|`NoStandardLib`|Paramètre `Boolean` facultatif.<br /><br /> Si `true`, empêche l’importation du fichier mscorlib.dll, qui définit l’espace de noms système tout entier. Utilisez ce paramètre si vous souhaitez définir ou créer vos propres objets et espace de noms système. Pour plus d’informations, consultez l’article [/nostdlib (C# Compiler Options) (/nostdlib [Options du compilateur C#])](https://msdn.microsoft.com/library/ec197989-fa49-4725-a455-e06b551eb65f).|  
|`NoWin32Manifest`|Paramètre `Boolean` facultatif.<br /><br /> Si `true`, n’inclut pas le manifeste Win32 par défaut.|  
|`Optimize`|Paramètre `Boolean` facultatif.<br /><br /> Si `true`, active les optimisations. Si `false`, désactive les optimisations. Pour plus d’informations, consultez l’article [/optimize (C# Compiler Options) (/optimize [Options du compilateur C#])](https://msdn.microsoft.com/library/6dd5b6f2-cd1d-4593-a9f4-1c2ed9404ca0).|  
|`OutputAssembly`|Paramètre de sortie `String` facultatif.<br /><br /> Spécifie le nom du fichier de sortie. Pour plus d’informations, consultez l’article [/out (C# Compiler Options) (/out [Options du compilateur C#])](https://msdn.microsoft.com/library/70d91d01-7bd2-4aea-ba8b-4e9807e9caa5).|  
|`PdbFile`|Paramètre `String` facultatif.<br /><br /> Spécifie le nom de fichier des informations de débogage. Le nom par défaut est le nom de fichier de sortie pourvu d’une extension .pdb.|  
|`Platform`|Paramètre `String` facultatif.<br /><br /> Spécifie la plateforme de processeur ciblée par le fichier de sortie. Ce paramètre peut avoir la valeur `x86`, `x64` ou `anycpu`. La valeur par défaut est `anycpu`. Pour plus d’informations, consultez [/platform (options du compilateur C#)](https://msdn.microsoft.com/library/c290ff5e-47f4-4a85-9bb3-9c2525b0be04).|  
|`References`|Paramètre <xref:Microsoft.Build.Framework.ITaskItem>`[]` facultatif.<br /><br /> Provoque l’importation par la tâche des informations de type public dans le projet actuel à partir des éléments spécifiés. Pour plus d’informations, consultez l’article [/reference (C# Compiler Options) (/reference [Options du compilateur C#])](https://msdn.microsoft.com/library/8d13e5b0-abf6-4c46-bf71-2daf2cd0a6c4).<br /><br /> Vous pouvez spécifier un alias de référence [!INCLUDE[csprcs](../includes/csprcs-md.md)] dans un fichier [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] en ajoutant les métadonnées `Aliases` à l’élément « Reference » d’origine. Par exemple, pour définir l’alias « LS1 » dans la ligne de commande CSC suivante :<br /><br /> `csc /r:LS1=MyCodeLibrary.dll /r:LS2=MyCodeLibrary2.dll *.cs`<br /><br /> Vous devez utiliser :<br /><br /> `<Reference Include="MyCodeLibrary"> <Aliases>LS1</Aliases> </Reference>`|  
|`Resources`|Paramètre <xref:Microsoft.Build.Framework.ITaskItem>`[]` facultatif.<br /><br /> Incorpore une ressource [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] dans le fichier de sortie.<br /><br /> Les éléments transmis dans ce paramètre peuvent posséder des entrées de métadonnées facultatives nommées `LogicalName` et `Access`. `LogicalName` correspond au paramètre `identifier` du commutateur `/resource`, et `Access` correspond au paramètre `accessibility-modifier`. Pour plus d’informations, consultez l’article [/resource (C# Compiler Options) (/resource [Options du compilateur C#])](https://msdn.microsoft.com/library/5212666e-98ab-47e4-a497-b5545ab15c7f).|  
|`ResponseFiles`|Paramètre `String` facultatif.<br /><br /> Spécifie le fichier réponse qui contient les commandes correspondant à cette tâche. Pour plus d’informations, consultez [@ (Spécifier un fichier réponse)](https://msdn.microsoft.com/library/dda4fa9f-a02c-400f-8b6a-d58834e13d7f).|  
|`Sources`|Paramètre <xref:Microsoft.Build.Framework.ITaskItem>`[]` facultatif.<br /><br /> Spécifie un ou plusieurs fichiers sources [!INCLUDE[csprcs](../includes/csprcs-md.md)].|  
|`TargetType`|Paramètre `String` facultatif.<br /><br /> Spécifie le format de fichier du fichier de sortie. Ce paramètre peut avoir la valeur `library`, qui crée une bibliothèque de codes, `exe`, qui crée une application console, `module`, qui crée un module, ou `winexe`, qui crée un programme Windows. La valeur par défaut est `library`. Pour plus d’informations, consultez l’article [/target (C# Compiler Options) (/target [Options du compilateur C#])](https://msdn.microsoft.com/library/a18bbd8e-bbf7-49e7-992c-717d0eb1f76f).|  
|`TreatWarningsAsErrors`|Paramètre `Boolean` facultatif.<br /><br /> Si `true`, traite tous les avertissements comme des erreurs. Pour plus d’informations, consultez [/warnaserror (options du compilateur C#)](https://msdn.microsoft.com/library/04680ec3-08d6-4e2e-a274-38310e10e33c).|  
|`UseHostCompilerIfAvailable`|Paramètre `Boolean` facultatif.<br /><br /> Demande à la tâche d’utiliser l’objet de compilateur in-process s’il est disponible. Son utilisation est réservée à [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].|  
|`Utf8Output`|Paramètre `Boolean` facultatif.<br /><br /> Enregistre les résultats de la compilation au format d’encodage UTF-8. Pour plus d’informations, consultez l’article [/utf8output (C# Compiler Options) (/utf8output [Options du compilateur C#])](https://msdn.microsoft.com/library/27ff7381-c281-45d7-b2eb-1ad644b1354e).|  
|`WarningLevel`|Paramètre `Int32` facultatif.<br /><br /> Spécifie le niveau d’avertissement que le compilateur doit afficher. Pour plus d’informations, consultez l’article [/warn (C# Compiler Options) (/warn [Options du compilateur C#])](https://msdn.microsoft.com/library/5f80ff59-4991-4382-9f9a-77da18446e71).|  
|`WarningsAsErrors`|Paramètre `String` facultatif.<br /><br /> Spécifie une liste d'avertissements à traiter comme des erreurs. Pour plus d’informations, consultez [/warnaserror (options du compilateur C#)](https://msdn.microsoft.com/library/04680ec3-08d6-4e2e-a274-38310e10e33c).<br /><br /> Ce paramètre remplace le paramètre `TreatWarningsAsErrors`.|  
|`WarningsNotAsErrors`|Paramètre `String` facultatif.<br /><br /> Spécifie une liste d'avertissements à ne pas traiter comme des erreurs. Pour plus d’informations, consultez l’article [/warnaserror (C# Compiler Options) (/warnaserror [Options du compilateur C#])](https://msdn.microsoft.com/library/04680ec3-08d6-4e2e-a274-38310e10e33c).<br /><br /> Ce paramètre est utile uniquement si le paramètre `TreatWarningsAsErrors` est défini sur `true`.|  
|`Win32Icon`|Paramètre `String` facultatif.<br /><br /> Insère un fichier .ico dans l’assembly, ce qui donne au fichier de sortie l’apparence souhaitée dans l’Explorateur de fichiers. Pour plus d’informations, consultez l’article [/win32icon (C# Compiler Options) (/win32icon [Options du compilateur C#])](https://msdn.microsoft.com/library/756d9b6d-ab07-41b7-ba58-5bd88f711138).|  
|`Win32Manifest`|Paramètre `String` facultatif.<br /><br /> Spécifie le manifeste Win32 à inclure.|  
|`Win32Resource`|Paramètre `String` facultatif.<br /><br /> Insère un fichier de ressources Win32 (.res) dans le fichier de sortie. Pour plus d’informations, consultez l’article [/win32res (C# Compiler Options) (/win32res [Options du compilateur C#])](https://msdn.microsoft.com/library/3c33f750-6948-4c7e-a27e-bef98f77255b).|  
  
## <a name="remarks"></a>Remarques  
 En plus des paramètres énumérés ci-dessus, cette tâche hérite des paramètres de la classe `Microsoft.Build.Tasks.ManagedCompiler`, qui hérite de la classe <xref:Microsoft.Build.Tasks.ToolTaskExtension>, qui hérite elle-même de la classe <xref:Microsoft.Build.Utilities.ToolTask>. Pour obtenir la liste de ces paramètres supplémentaires et de leurs descriptions, consultez l’article [ToolTaskExtension Base Class (Classe de base ToolTaskExtension)](../msbuild/tooltaskextension-base-class.md).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant utilise la tâche `Csc` pour compiler un fichier exécutable à partir des fichiers sources de la collection d’éléments `Compile`.  
  
```  
<CSC  
    Sources="@(Compile)"  
    OutputAssembly="$(AppName).exe"  
    EmitDebugInformation="true" />  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Task Reference (Informations de référence sur les tâches MSBuild)](../msbuild/msbuild-task-reference.md)   
 [Tâches](../msbuild/msbuild-tasks.md)
