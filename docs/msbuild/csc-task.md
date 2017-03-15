---
title: "Csc, t&#226;che | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/msbuild/2003#Csc"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "Csc (tâche MSBuild)"
  - "MSBuild, CSC, tâche"
ms.assetid: d8c19b36-f5ca-484b-afa6-8ff3b90e103a
caps.latest.revision: 26
caps.handback.revision: 26
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Csc, t&#226;che
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Encapsule CSC.exe et produit des fichiers exécutables (fichiers .exe), des bibliothèques de liens dynamiques (fichiers .dll) ou des modules de code (fichiers .netmodule). Pour plus d’informations sur CSC.exe, consultez [Options du compilateur c#](/dotnet/csharp/language-reference/compiler-options/index).  
  
## <a name="parameters"></a>Paramètres  
 Le tableau ci-dessous décrit les paramètres de la tâche `Csc`.  
  
|Paramètre|Description|  
|---------------|-----------------|  
|`AdditionalLibPaths`|Paramètre `String[]` facultatif.<br /><br /> Spécifie des répertoires supplémentaires dans lesquels rechercher des références. Pour plus d’informations, consultez [/lib (Options du compilateur c#)](/dotnet/csharp/language-reference/compiler-options/lib-compiler-option).|  
|`AddModules`|Paramètre `String` facultatif.<br /><br /> Spécifie un ou plusieurs modules à inclure dans cet assembly. Pour plus d’informations, consultez [/addmodule (Options du compilateur c#)](/dotnet/csharp/language-reference/compiler-options/addmodule-compiler-option).|  
|`AllowUnsafeBlocks`|Paramètre `Boolean` facultatif.<br /><br /> Si `true`, compile le code qui utilise le [unsafe](/dotnet/csharp/language-reference/keywords/unsafe) (mot clé). Pour plus d’informations, consultez [/unsafe (Options du compilateur c#)](/dotnet/csharp/language-reference/compiler-options/unsafe-compiler-option).|  
|`ApplicationConfiguration`|Paramètre `String` facultatif.<br /><br /> Spécifie le fichier de configuration contenant les paramètres de liaison d’assembly.|  
|`BaseAddress`|Paramètre `String` facultatif.<br /><br /> Spécifie l'adresse de base préférée à laquelle charger une DLL. L’adresse de base par défaut pour une DLL est définie par le [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] common language runtime. Pour plus d’informations, consultez [/baseaddress (Options du compilateur c#)](/dotnet/csharp/language-reference/compiler-options/baseaddress-compiler-option).|  
|`CheckForOverflowUnderflow`|Paramètre `Boolean` facultatif.<br /><br /> Spécifie si arithmétique qui dépasse les limites du type de données entier provoque une exception au moment de l’exécution. Pour plus d’informations, consultez [/checked (Options du compilateur c#)](/dotnet/csharp/language-reference/compiler-options/checked-compiler-option).|  
|`CodePage`|Paramètre `Int32` facultatif.<br /><br /> Spécifie la page de codes à utiliser pour tous les fichiers de code source inclus dans la compilation. Pour plus d’informations, consultez [/codepage (Options du compilateur c#)](/dotnet/csharp/language-reference/compiler-options/codepage-compiler-option).|  
|`DebugType`|Paramètre `String` facultatif.<br /><br /> Spécifie le type de débogage. `DebugType` peut être `full` ou `pdbonly`. La valeur par défaut est `full`, ce qui permet à un débogueur à attacher à un programme en cours d’exécution. Spécification de `pdbonly` permet de débogage du code source lorsque le programme est démarré dans le débogueur, mais affiche uniquement assembleur lorsque le programme en cours d’exécution est attaché au débogueur.<br /><br /> Ce paramètre remplace le `EmitDebugInformation` paramètre.<br /><br /> Pour plus d’informations, consultez [/debug (Options du compilateur c#)](/dotnet/csharp/language-reference/compiler-options/debug-compiler-option).|  
|`DefineConstants`|Paramètre `String` facultatif.<br /><br /> Définit les symboles du préprocesseur. Pour plus d’informations, consultez [/define (Options du compilateur c#)](/dotnet/csharp/language-reference/compiler-options/define-compiler-option).|  
|`DelaySign`|Paramètre `Boolean` facultatif.<br /><br /> Si `true`, spécifie que vous souhaitez obtenir un assembly complètement signé. Si `false`, spécifie que vous souhaitez uniquement placer la clé publique dans l’assembly.<br /><br /> Ce paramètre n’a aucun effet, sauf si utilisée avec le `KeyFile` ou `KeyContainer` paramètre.<br /><br /> Pour plus d’informations, consultez [/delaysign (Options du compilateur c#)](/dotnet/csharp/language-reference/compiler-options/delaysign-compiler-option).|  
|`DisabledWarnings`|Paramètre `String` facultatif.<br /><br /> Spécifie la liste d’avertissements à désactiver. Pour plus d’informations, consultez [/nowarn (Options du compilateur c#)](/dotnet/csharp/language-reference/compiler-options/nowarn-compiler-option).|  
|`DocumentationFile`|Paramètre `String` facultatif.<br /><br /> Traite les commentaires de documentation pour les diriger vers un fichier XML. Pour plus d’informations, consultez [/doc (Options du compilateur c#)](/dotnet/csharp/language-reference/compiler-options/doc-compiler-option).|  
|`EmitDebugInformation`|Paramètre `Boolean` facultatif.<br /><br /> Si `true`, la tâche génère des informations de débogage et les place dans un fichier de base de données (.pdb) de programme. Si `false`, la tâche ne génère aucune information de débogage. La valeur par défaut est `false`. Pour plus d’informations, consultez [/debug (Options du compilateur c#)](/dotnet/csharp/language-reference/compiler-options/debug-compiler-option).|  
|`ErrorReport`|Paramètre `String` facultatif.<br /><br /> Offre un moyen pratique de signaler une erreur interne c# à Microsoft. Ce paramètre peut avoir une valeur de `prompt`, `send`, ou `none`. Si le paramètre est défini sur `prompt`, vous recevrez une invite de commandes lorsqu’une erreur interne du compilateur se produit. L’invite vous permet d’envoyer un rapport de bogue par voie électronique à Microsoft. Si le paramètre est défini sur `send`, un rapport de bogue est automatiquement envoyé. Si le paramètre est défini sur `none`, l’erreur est signalée uniquement dans la sortie texte du compilateur. La valeur par défaut est `none`. Pour plus d’informations, consultez [/errorreport (Options du compilateur c#)](/dotnet/csharp/language-reference/compiler-options/errorreport-compiler-option).|  
|`FileAlignment`|Paramètre `Int32` facultatif.<br /><br /> Spécifie la taille des sections dans le fichier de sortie. Pour plus d’informations, consultez [/filealign (Options du compilateur c#)](/dotnet/csharp/language-reference/compiler-options/filealign-compiler-option).|  
|`GenerateFullPaths`|Paramètre `Boolean` facultatif.<br /><br /> Si `true`, spécifie le chemin d’accès absolu au fichier dans la sortie du compilateur. Si `false`, spécifie le nom du fichier. La valeur par défaut est `false`. Pour plus d’informations, consultez [/fullpaths (Options du compilateur c#)](/dotnet/csharp/language-reference/compiler-options/fullpaths-compiler-option).|  
|`KeyContainer`|Paramètre `String` facultatif.<br /><br /> Spécifie le nom du conteneur de la clé de chiffrement. Pour plus d’informations, consultez [/keycontainer (Options du compilateur c#)](/dotnet/csharp/language-reference/compiler-options/keycontainer-compiler-option).|  
|`KeyFile`|Paramètre `String` facultatif.<br /><br /> Spécifie le nom du fichier contenant la clé de chiffrement. Pour plus d’informations, consultez [/keyfile (Options du compilateur c#)](/dotnet/csharp/language-reference/compiler-options/keyfile-compiler-option).|  
|`LangVersion`|Paramètre `String` facultatif.<br /><br /> Spécifie la version du langage à utiliser. Pour plus d’informations, consultez [/langversion (Options du compilateur c#)](/dotnet/csharp/language-reference/compiler-options/langversion-compiler-option).|  
|`LinkResources`|Facultatif <xref:Microsoft.Build.Framework.ITaskItem>`[]` paramètre.<br /><br /> Crée un lien vers une [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] ressource dans le fichier de sortie, le fichier de ressources n’est pas placé dans le fichier de sortie.<br /><br /> Les éléments passés dans ce paramètre peuvent avoir des entrées de métadonnées facultatives nommées `LogicalName` et `Access`. `LogicalName` correspond à la `identifier` paramètre de la `/linkresource` commutateur, et `Access` correspond à `accessibility-modifier` paramètre. Pour plus d’informations, consultez [/linkresource (Options du compilateur c#)](/dotnet/csharp/language-reference/compiler-options/linkresource-compiler-option).|  
|`MainEntryPoint`|Paramètre `String` facultatif.<br /><br /> Spécifie l’emplacement de la `Main` méthode. Pour plus d’informations, consultez [/main (Options du compilateur c#)](/dotnet/csharp/language-reference/compiler-options/main-compiler-option).|  
|`ModuleAssemblyName`|Paramètre `String` facultatif.<br /><br /> Spécifie le nom de ce module fera partie de l’assembly.|  
|`NoConfig`|Paramètre `Boolean` facultatif.<br /><br /> Si `true`, indique au compilateur ne pas de compiler avec le fichier csc.rsp. Pour plus d’informations, consultez [/noconfig (Options du compilateur c#)](/dotnet/csharp/language-reference/compiler-options/noconfig-compiler-option).|  
|`NoLogo`|Paramètre `Boolean` facultatif.<br /><br /> Si `true`, supprime l’affichage des informations de la bannière du compilateur. Pour plus d’informations, consultez [/nologo (Options du compilateur c#)](/dotnet/csharp/language-reference/compiler-options/nologo-compiler-option).|  
|`NoStandardLib`|Paramètre `Boolean` facultatif.<br /><br /> Si `true`, empêche l’importation du fichier mscorlib.dll, qui définit l’espace de noms système entier. Utilisez ce paramètre si vous souhaitez définir ou créer vos propres objets et espace de noms System. Pour plus d’informations, consultez [/nostdlib (Options du compilateur c#)](/dotnet/csharp/language-reference/compiler-options/nostdlib-compiler-option).|  
|`NoWin32Manifest`|Paramètre `Boolean` facultatif.<br /><br /> Si `true`, ne pas inclure le manifeste Win32 par défaut.|  
|`Optimize`|Paramètre `Boolean` facultatif.<br /><br /> Si `true`, Active les optimisations. Si `false`, désactive les optimisations. Pour plus d’informations, consultez [/optimize (Options du compilateur c#)](/dotnet/csharp/language-reference/compiler-options/optimize-compiler-option).|  
|`OutputAssembly`|Facultatif `String` paramètre de sortie.<br /><br /> Spécifie le nom du fichier de sortie. Pour plus d’informations, consultez [/out (Options du compilateur c#)](/dotnet/csharp/language-reference/compiler-options/out-compiler-option).|  
|`PdbFile`|Paramètre `String` facultatif.<br /><br /> Spécifie le nom de fichier des informations de débogage. Le nom par défaut est le nom de fichier de sortie avec une extension .pdb.|  
|`Platform`|Paramètre `String` facultatif.<br /><br /> Spécifie la plateforme de processeur ciblée par le fichier de sortie. Ce paramètre peut avoir une valeur de `x86`, `x64`, ou `anycpu`. La valeur par défaut est `anycpu`. Pour plus d’informations, consultez [/platform (Options du compilateur c#)](/dotnet/csharp/language-reference/compiler-options/platform-compiler-option).|  
|`References`|Facultatif <xref:Microsoft.Build.Framework.ITaskItem>`[]` paramètre.<br /><br /> Force la tâche à importer des informations de type public à partir des éléments spécifiés dans le projet actuel. Pour plus d’informations, consultez [Reference (Options du compilateur c#)](/dotnet/csharp/language-reference/compiler-options/reference-compiler-option).<br /><br /> Vous pouvez spécifier un [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] référence alias dans un [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] fichier en ajoutant les métadonnées `Aliases` pour l’élément d’origine de la « Référence ». Par exemple, pour définir l’alias « LS1 » dans la ligne de commande CSC suivante :<br /><br /> `csc /r:LS1=MyCodeLibrary.dll /r:LS2=MyCodeLibrary2.dll *.cs`<br /><br /> Vous devez utiliser :<br /><br /> `<Reference Include="MyCodeLibrary"> <Aliases>LS1</Aliases> </Reference>`|  
|`Resources`|Facultatif <xref:Microsoft.Build.Framework.ITaskItem>`[]` paramètre.<br /><br /> Incorpore un [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] ressource dans le fichier de sortie.<br /><br /> Les éléments passés dans ce paramètre peuvent avoir des entrées de métadonnées facultatives nommées `LogicalName` et `Access`. `LogicalName` correspond à la `identifier` paramètre de la `/resource` commutateur, et `Access` correspond à `accessibility-modifier` paramètre. Pour plus d’informations, consultez [/resource (Options du compilateur c#)](/dotnet/csharp/language-reference/compiler-options/resource-compiler-option).|  
|`ResponseFiles`|Paramètre `String` facultatif.<br /><br /> Spécifie le fichier de réponse qui contient les commandes pour cette tâche. Pour plus d’informations, consultez [@ (spécifier un fichier réponse)](/dotnet/csharp/language-reference/compiler-options/response-file-compiler-option).|  
|`Sources`|Facultatif <xref:Microsoft.Build.Framework.ITaskItem>`[]` paramètre.<br /><br /> Spécifie un ou plusieurs [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] les fichiers source.|  
|`TargetType`|Paramètre `String` facultatif.<br /><br /> Spécifie le format de fichier du fichier de sortie. Ce paramètre peut avoir une valeur de `library`, ce qui crée une bibliothèque de code, `exe`, ce qui crée une application console, `module`, qui crée un module, ou `winexe`, ce qui crée un programme Windows. La valeur par défaut est `library`. Pour plus d’informations, consultez [/target (Options du compilateur c#)](/dotnet/csharp/language-reference/compiler-options/target-compiler-option).|  
|`TreatWarningsAsErrors`|Paramètre `Boolean` facultatif.<br /><br /> Si `true`, traite tous les avertissements comme des erreurs. Pour plus d’informations, consultez [/warnaserror (Options du compilateur c#)](/dotnet/csharp/language-reference/compiler-options/warnaserror-compiler-option).|  
|`UseHostCompilerIfAvailable`|Paramètre `Boolean` facultatif.<br /><br /> Fait en sorte que la tâche d’utiliser l’objet de compilateur in-process, s’il est disponible. Utilisé uniquement par [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].|  
|`Utf8Output`|Paramètre `Boolean` facultatif.<br /><br /> Enregistre la sortie à l’aide du codage UTF-8 du compilateur. Pour plus d’informations, consultez [/utf8output (Options du compilateur c#)](/dotnet/csharp/language-reference/compiler-options/utf8output-compiler-option).|  
|`WarningLevel`|Paramètre `Int32` facultatif.<br /><br /> Spécifie le niveau d’avertissement à afficher par le compilateur. Pour plus d’informations, consultez [/warn (Options du compilateur c#)](/dotnet/csharp/language-reference/compiler-options/warn-compiler-option).|  
|`WarningsAsErrors`|Paramètre `String` facultatif.<br /><br /> Spécifie une liste d'avertissements à traiter comme des erreurs. Pour plus d’informations, consultez [/warnaserror (Options du compilateur c#)](/dotnet/csharp/language-reference/compiler-options/warnaserror-compiler-option).<br /><br /> Ce paramètre remplace le `TreatWarningsAsErrors` paramètre.|  
|`WarningsNotAsErrors`|Paramètre `String` facultatif.<br /><br /> Spécifie une liste d'avertissements à ne pas traiter comme des erreurs. Pour plus d’informations, consultez [/warnaserror (Options du compilateur c#)](/dotnet/csharp/language-reference/compiler-options/warnaserror-compiler-option).<br /><br /> Ce paramètre est utile uniquement si le `TreatWarningsAsErrors` paramètre est défini sur `true`.|  
|`Win32Icon`|Paramètre `String` facultatif.<br /><br /> Insère un fichier .ico dans l’assembly, ce qui donne au fichier de sortie l’aspect souhaité dans l’Explorateur de fichiers. Pour plus d’informations, consultez [/win32icon (Options du compilateur c#)](/dotnet/csharp/language-reference/compiler-options/win32icon-compiler-option).|  
|`Win32Manifest`|Paramètre `String` facultatif.<br /><br /> Spécifie le manifeste Win32 à inclure.|  
|`Win32Resource`|Paramètre `String` facultatif.<br /><br /> Insère un fichier de ressources (.res) Win32 dans le fichier de sortie. Pour plus d’informations, consultez [/win32res (Options du compilateur c#)](/dotnet/csharp/language-reference/compiler-options/win32res-compiler-option).|  
  
## <a name="remarks"></a>Notes  
 En plus des paramètres énumérés ci-dessus, cette tâche hérite des paramètres de la `Microsoft.Build.Tasks.ManagedCompiler` classe qui hérite de la <xref:Microsoft.Build.Tasks.ToolTaskExtension> (classe), qui elle-même hérite de la <xref:Microsoft.Build.Utilities.ToolTask> classe. Pour obtenir la liste de ces paramètres supplémentaires et leurs descriptions, consultez la page [une classe de Base ToolTaskExtension](../msbuild/tooltaskextension-base-class.md).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant utilise le `Csc` tâche pour compiler un fichier exécutable à partir des fichiers source dans le `Compile` collection d’éléments.  
  
```  
<CSC  
    Sources="@(Compile)"  
    OutputAssembly="$(AppName).exe"  
    EmitDebugInformation="true" />  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Référence des tâches](../msbuild/msbuild-task-reference.md)   
 [Tâches](../msbuild/msbuild-tasks.md)