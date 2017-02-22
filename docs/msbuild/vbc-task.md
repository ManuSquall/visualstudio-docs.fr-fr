---
title: "Vbc Task | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/msbuild/2003#Vbc"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "Vbc task [MSBuild]"
  - "MSBuild, Vbc task"
ms.assetid: 595278b1-2782-4577-b1ba-b4b5ab5625a3
caps.latest.revision: 19
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 19
---
# Vbc Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Inclut vbc.exe dans un wrapper, ce qui produit des fichiers exécutables \(.exe\), des bibliothèques de liens dynamiques \(.dll\) ou des modules de code \(.  netmodule\).  Pour plus d'informations sur vbc.exe, consultez [Visual Basic Command\-Line Compiler](/dotnet/visual-basic/reference/command-line-compiler/index).  
  
## Paramètres  
 Le tableau suivant décrit les paramètres de la tâche `Vbc`.  
  
|Paramètre|Description|  
|---------------|-----------------|  
|`AdditionalLibPaths`|Paramètre `String[]` facultatif.<br /><br /> Spécifie les dossiers supplémentaires dans lesquels rechercher les assemblys spécifiés dans l'attribut References.|  
|`AddModules`|Paramètre `String[]` facultatif.<br /><br /> Entraîne le compilateur à donner des informations de type dans le ou les fichiers spécifiés disponibles pour le projet en cours de compilation.  Ce paramètre correspond au commutateur [\/addmodule](/dotnet/visual-basic/reference/command-line-compiler/addmodule) du compilateur vbc.exe.|  
|`BaseAddress`|Paramètre `String` facultatif.<br /><br /> Spécifie l'adresse de base de la DLL.  Ce paramètre correspond au commutateur [\/baseaddress](/dotnet/visual-basic/reference/command-line-compiler/baseaddress) du compilateur vbc.exe.|  
|`CodePage`|Paramètre `Int32` facultatif.<br /><br /> Spécifie la page de codes à utiliser pour tous les fichiers de code source inclus dans la compilation.  Ce paramètre correspond au commutateur [\/codepage](/dotnet/visual-basic/reference/command-line-compiler/codepage) du compilateur vbc.exe.|  
|`DebugType`|Paramètre `String[]` facultatif.<br /><br /> Entraîne le compilateur à générer des informations de débogage.  Ce paramètre peut avoir les valeurs suivantes :<br /><br /> -   `full`<br />-   `pdbonly`<br /><br /> La valeur par défaut, `full`, active l'attachement d'un débogueur au programme en cours d'exécution.  La valeur `pdbonly` permet un débogage du code source lorsque le programme est démarré dans le débogueur, mais affiche du code en langage assembleur uniquement lorsque le programme en cours d'exécution est attaché au débogueur.  Pour plus d'informations, consultez [\/debug](/dotnet/visual-basic/reference/command-line-compiler/debug).|  
|`DefineConstants`|Paramètre `String[]` facultatif.<br /><br /> Définit des constantes de compilation conditionnelle.  Les paires symbole\/valeur sont séparées par des points\-virgules et spécifiées avec la syntaxe suivante :<br /><br /> *symbole1* `=` *valeur1* `;` *symbole2* `=` *valeur2*<br /><br /> Ce paramètre correspond au commutateur [\/define](/dotnet/visual-basic/reference/command-line-compiler/define) du compilateur vbc.exe.|  
|`DelaySign`|Paramètre `Boolean` facultatif.<br /><br /> Si la valeur est `true`, la tâche place la clé publique dans l'assembly.  Si la valeur est `false`, la tâche signe complètement l'assembly.  La valeur par défaut est `false`. Ce paramètre n'a aucun effet à moins d'être utilisé avec le paramètre `KeyFile` ou `KeyContainer`.  Ce paramètre correspond au commutateur [\/delaysign](/dotnet/visual-basic/reference/command-line-compiler/delaysign) du compilateur vbc.exe.|  
|`DisabledWarnings`|Paramètre `String` facultatif.<br /><br /> Supprime les avertissements spécifiés.  Il suffit de spécifier la partie numérique de l'identificateur de l'avertissement.  Les différents avertissements sont séparés par des points\-virgules.  Ce paramètre correspond au commutateur [\/nowarn](/dotnet/visual-basic/reference/command-line-compiler/nowarn) du compilateur vbc.exe.|  
|`DocumentationFile`|Paramètre `String` facultatif.<br /><br /> Traite les commentaires de documentation pour les diriger vers le fichier XML spécifié.  Ce paramètre se substitue au paramètre `GenerateDocumentation`.  Pour plus d'informations, consultez [\/doc](/dotnet/visual-basic/reference/command-line-compiler/doc).|  
|`EmitDebugInformation`|Paramètre `Boolean` facultatif.<br /><br /> Si la valeur est `true`, la tâche génère des informations de débogage et les place dans un fichier de base de données de programme \(.pdb\).  Pour plus d'informations, consultez [\/debug](/dotnet/visual-basic/reference/command-line-compiler/debug).|  
|`ErrorReport`|Paramètre `String` facultatif.<br /><br /> Indique comment la tâche doit signaler des erreurs internes du compilateur.  Ce paramètre peut avoir les valeurs suivantes :<br /><br /> -   `prompt`<br />-   `send`<br />-   `none`<br /><br /> Si `prompt` est spécifié et qu'une erreur interne du compilateur se produit, l'utilisateur est invité à choisir d'envoyer ou non les données d'erreur à Microsoft.<br /><br /> Si `send` est spécifié et qu'une erreur interne du compilateur se produit, la tâche envoie les données d'erreur à Microsoft.<br /><br /> La valeur par défaut est `none`, qui signale les erreurs dans une sortie texte uniquement.<br /><br /> Ce paramètre correspond au commutateur [\/errorreport](/dotnet/visual-basic/reference/command-line-compiler/errorreport) du compilateur vbc.exe.|  
|`FileAlignment`|Paramètre `Int32` facultatif.<br /><br /> Spécifie, en octets, où les sections du fichier de sortie doivent être alignées.  Ce paramètre peut avoir les valeurs suivantes :<br /><br /> -   `512`<br />-   `1024`<br />-   `2048`<br />-   `4096`<br />-   `8192`<br /><br /> Ce paramètre correspond au commutateur [\/filealign](/dotnet/visual-basic/reference/command-line-compiler/filealign) du compilateur vbc.exe.|  
|`GenerateDocumentation`|Paramètre `Boolean` facultatif.<br /><br /> Si sa valeur est `true`, il génère des informations de documentation et les place dans un fichier XML avec le nom de la bibliothèque ou du fichier exécutable créé par la tâche.  Pour plus d'informations, consultez [\/doc](/dotnet/visual-basic/reference/command-line-compiler/doc).|  
|`Imports`|Paramètre <xref:Microsoft.Build.Framework.ITaskItem>`[]` optionnel.<br /><br /> Importe des espaces de noms à partir des collections d'éléments spécifiées.  Ce paramètre correspond au commutateur [\/imports](/dotnet/visual-basic/reference/command-line-compiler/imports) du compilateur vbc.exe.|  
|`KeyContainer`|Paramètre `String` facultatif.<br /><br /> Spécifie le nom du conteneur de clé de chiffrement.  Ce paramètre correspond au commutateur [\/keycontainer](/dotnet/visual-basic/reference/command-line-compiler/keycontainer) du compilateur vbc.exe.|  
|`KeyFile`|Paramètre `String` facultatif.<br /><br /> Spécifie le nom de fichier qui contient la clé de chiffrement.  Pour plus d'informations, consultez [\/keyfile](/dotnet/visual-basic/reference/command-line-compiler/keyfile).|  
|`LangVersion`|Paramètre [String](assetId:///String?qualifyHint=False&autoUpgrade=True) facultatif.<br /><br /> Spécifie la version linguistique \(« 9 » ou « 10 »\).|  
|`LinkResources`|Paramètre <xref:Microsoft.Build.Framework.ITaskItem>`[]` optionnel.<br /><br /> Crée un lien avec une ressource du .NET Framework dans le fichier de sortie ; le fichier de ressources n'est pas stocké dans le fichier de sortie.  Ce paramètre correspond au commutateur [\/linkresource](/dotnet/visual-basic/reference/command-line-compiler/linkresource) du compilateur vbc.exe.|  
|`MainEntryPoint`|Paramètre `String` facultatif.<br /><br /> Spécifie la classe ou le module qui contient la procédure `Sub Main`.  Ce paramètre correspond au commutateur [\/main](/dotnet/visual-basic/reference/command-line-compiler/main) du compilateur vbc.exe.|  
|`ModuleAssemblyName`|Paramètre `String` facultatif.<br /><br /> Spécifie l'assembly dont ce module fait partie.|  
|`NoConfig`|Paramètre `Boolean` facultatif.<br /><br /> Indique que le compilateur ne doit pas utiliser le fichier vbc.rsp.  Ce paramètre correspond au commutateur [\/noconfig](/dotnet/visual-basic/reference/command-line-compiler/noconfig) du compilateur vbc.exe.|  
|`NoLogo`|Paramètre `Boolean` facultatif.<br /><br /> Si sa valeur est `true`, il supprime l'affichage d'informations sur la bannière du compilateur.  Ce paramètre correspond au commutateur [\/nologo](/dotnet/visual-basic/reference/command-line-compiler/nologo) du compilateur vbc.exe.|  
|`NoStandardLib`|Paramètre `Boolean` facultatif.<br /><br /> Empêche le compilateur de référencer les bibliothèques standard.  Ce paramètre correspond au commutateur [\/nostdlib](/dotnet/visual-basic/reference/command-line-compiler/nostdlib) du compilateur vbc.exe.|  
|`NoVBRuntimeReference`|Paramètre `Boolean` facultatif.<br /><br /> Usage interne uniquement.  Si la valeur est true, la référence automatique à Microsoft.VisualBasic.dll est impossible.|  
|`NoWarnings`|Paramètre `Boolean` facultatif.<br /><br /> Si la valeur est `true`, la tâche supprime tous les avertissements.  Pour plus d'informations, consultez [\/nowarn](/dotnet/visual-basic/reference/command-line-compiler/nowarn).|  
|`Optimize`|Paramètre `Boolean` facultatif.<br /><br /> Si sa valeur est `true`, il active les optimisations du compilateur.  Ce paramètre correspond au commutateur [\/optimize](/dotnet/visual-basic/reference/command-line-compiler/optimize) du compilateur vbc.exe.|  
|`OptionCompare`|Paramètre `String` facultatif.<br /><br /> Spécifie la façon dont sont effectuées les comparaisons de chaînes.  Ce paramètre peut avoir les valeurs suivantes :<br /><br /> -   `binary`<br />-   `text`<br /><br /> La valeur `binary` spécifie que la tâche utilise des comparaisons de chaînes binaires.  La valeur `text` indique que la tâche utilise des comparaisons de chaînes de texte.  La valeur par défaut de ce paramètre est `binary`.  Ce paramètre correspond au commutateur [\/optioncompare](/dotnet/visual-basic/reference/command-line-compiler/optioncompare) du compilateur vbc.exe.|  
|`OptionExplicit`|Paramètre `Boolean` facultatif.<br /><br /> Si la valeur est `true`, la déclaration explicite de variables est requise.  Ce paramètre correspond au commutateur [\/optionexplicit](/dotnet/visual-basic/reference/command-line-compiler/optionexplicit) du compilateur vbc.exe.|  
|`OptionInfer`|Paramètre `Boolean` facultatif.<br /><br /> Si la valeur est `true`, l'inférence de types de variables est autorisée.|  
|`OptionStrict`|Paramètre `Boolean` facultatif.<br /><br /> Si la valeur est `true`, la tâche applique une sémantique de type stricte pour limiter les conversions de types implicites.  Ce paramètre correspond au commutateur [\/optionstrict](/dotnet/visual-basic/reference/command-line-compiler/optionstrict) du compilateur vbc.exe.|  
|`OptionStrictType`|Paramètre `String` facultatif.<br /><br /> Spécifie quelle sémantique de type stricte génère un avertissement.  Actuellement, seul "custom" est pris en charge.  Ce paramètre correspond au commutateur [\/optionstrict](/dotnet/visual-basic/reference/command-line-compiler/optionstrict) du compilateur vbc.exe.|  
|`OutputAssembly`|Paramètre de sortie `String` facultatif.<br /><br /> Spécifie le nom du fichier de sortie.  Ce paramètre correspond au commutateur [\/out](/dotnet/visual-basic/reference/command-line-compiler/out) du compilateur vbc.exe.|  
|`Platform`|Paramètre `String` facultatif.<br /><br /> Spécifie la plateforme du processeur ciblée par le fichier de sortie.  Ce paramètre peut avoir les valeurs `x86`, `x64`, `Itanium` ou `anycpu`.  La valeur par défaut est `anycpu`.  Ce paramètre correspond au commutateur [\/platform](/dotnet/visual-basic/reference/command-line-compiler/platform) du compilateur vbc.exe.|  
|`References`|Paramètre <xref:Microsoft.Build.Framework.ITaskItem>`[]` optionnel.<br /><br /> Entraîne la tâche à importer des informations de type public à partir des éléments spécifiés dans le projet actif.  Ce paramètre correspond au commutateur [\/reference](/dotnet/visual-basic/reference/command-line-compiler/reference) du compilateur vbc.exe.|  
|`RemoveIntegerChecks`|Paramètre `Boolean` facultatif.<br /><br /> Si la valeur est `true`, il désactive les vérifications d'erreur de dépassement sur les entiers.  La valeur par défaut est `false`.  Ce paramètre correspond au commutateur [\/removeintchecks](/dotnet/visual-basic/reference/command-line-compiler/removeintchecks) du compilateur vbc.exe.|  
|`Resources`|Paramètre <xref:Microsoft.Build.Framework.ITaskItem>`[]` optionnel.<br /><br /> Incorpore une ressource .NET Framework dans le fichier de sortie.  Ce paramètre correspond au commutateur [\/resource](/dotnet/visual-basic/reference/command-line-compiler/resource) du compilateur vbc.exe.|  
|`ResponseFiles`|Paramètre <xref:Microsoft.Build.Framework.ITaskItem>`[]` optionnel.<br /><br /> Spécifie le fichier réponse qui contient les commandes pour cette tâche.  Ce paramètre correspond à l'option [@ \(Specify Response File\)](/dotnet/visual-basic/reference/command-line-compiler/specify-response-file) du compilateur vbc.exe.|  
|`RootNamespace`|Paramètre `String` facultatif.<br /><br /> Spécifie l'espace de noms racine pour toutes les déclarations de type.  Ce paramètre correspond au commutateur [\/rootnamespace](/dotnet/visual-basic/reference/command-line-compiler/rootnamespace) du compilateur vbc.exe.|  
|`SdkPath`|Paramètre `String` facultatif.<br /><br /> Spécifie l'emplacement de mscorlib.dll et de microsoft.visualbasic.dll.  Ce paramètre correspond au commutateur [\/sdkpath](/dotnet/visual-basic/reference/command-line-compiler/sdkpath) du compilateur vbc.exe.|  
|`Sources`|Paramètre <xref:Microsoft.Build.Framework.ITaskItem>`[]` optionnel.<br /><br /> Spécifie un ou plusieurs fichiers sources [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)].|  
|`TargetCompactFramework`|Paramètre `Boolean` facultatif.<br /><br /> Si la valeur est `true`, la tâche cible le [!INCLUDE[Compact](../extensibility/includes/compact_md.md)].  Ce commutateur correspond au commutateur [\/netcf](/dotnet/visual-basic/reference/command-line-compiler/netcf) du compilateur vbc.exe.|  
|`TargetType`|Paramètre `String` facultatif.<br /><br /> Spécifie le format du fichier de sortie.  Ce paramètre peut avoir la valeur `library` pour créer une bibliothèque de code, `exe` pour créer une application console, `module` pour créer un module ou `winexe` pour créer un programme Windows.  La valeur par défaut est `library`.  Ce paramètre correspond au commutateur [\/target](/dotnet/visual-basic/reference/command-line-compiler/target) du compilateur vbc.exe.|  
|`Timeout`|Paramètre `Int32` facultatif.<br /><br /> Spécifie la durée, en millisecondes, après laquelle la tâche exécutable est terminée.  La valeur par défaut est `Int.MaxValue`, indiquant qu'il n'existe aucun délai d'attente.|  
|`ToolPath`|Paramètre `String` facultatif.<br /><br /> Spécifie l'emplacement à partir duquel la tâche charge le fichier exécutable sous\-jacent \(vbc.exe\).  Si ce paramètre n'est pas spécifié, la tâche utilise le chemin d'accès d'installation du Kit de développement logiciel qui correspond à la version de l'infrastructure exécutant [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].|  
|`TreatWarningsAsErrors`|Paramètre `Boolean` facultatif.<br /><br /> Si la valeur est `true`, tous les avertissements sont traités comme des erreurs.  Pour plus d'informations, consultez [\/warnaserror](/dotnet/visual-basic/reference/command-line-compiler/warnaserror).|  
|`UseHostCompilerIfAvailable`|Paramètre `Boolean` facultatif.<br /><br /> Indique à la tâche d'utiliser l'objet compilateur in\-process, s'il est disponible.  Utilisé uniquement par [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].|  
|`Utf8Output`|Paramètre `Boolean` facultatif.<br /><br /> Affiche les résultats de la compilation en encodage UTF\-8.  Ce paramètre correspond au commutateur [\/utf8output](/dotnet/visual-basic/reference/command-line-compiler/utf8output) du compilateur vbc.exe.|  
|`Verbosity`|Paramètre `String` facultatif.<br /><br /> Spécifie le niveau de commentaires de la sortie de compilation.  Le niveau de commentaires peut avoir la valeur `Quiet`, `Normal` \(par défaut\) ou `Verbose`.|  
|`WarningsAsErrors`|Paramètre `String` facultatif.<br /><br /> Spécifie une liste d'avertissements à traiter comme des erreurs.  Pour plus d'informations, consultez [\/warnaserror](/dotnet/visual-basic/reference/command-line-compiler/warnaserror).<br /><br /> Ce paramètre se substitue au paramètre `TreatWarningsAsErrors`.|  
|`WarningsNotAsErrors`|Paramètre `String` facultatif.<br /><br /> Spécifie une liste d'avertissements à ne pas traiter comme des erreurs.  Pour plus d'informations, consultez [\/warnaserror](/dotnet/visual-basic/reference/command-line-compiler/warnaserror).<br /><br /> Ce paramètre n'est utile que lorsque la propriété `TreatWarningsAsErrors` a la valeur `true`.|  
|`Win32Icon`|Paramètre `String` facultatif.<br /><br /> Insère un fichier .ico dans l'assembly, qui donne au fichier de sortie l'apparence souhaitée dans l'Explorateur de fichiers.  Ce paramètre correspond au commutateur [\/win32icon](/dotnet/visual-basic/reference/command-line-compiler/win32icon) du compilateur vbc.exe.|  
|`Win32Resources`|Paramètre `String` facultatif.<br /><br /> Insère un fichier de ressources Win32 \(.res\) dans le fichier de sortie.  Ce paramètre correspond au commutateur [\/win32resource](/dotnet/visual-basic/reference/command-line-compiler/win32resource) du compilateur vbc.exe.|  
  
## Notes  
 En plus des paramètres énumérés ci\-dessus, cette tâche hérite des paramètres de la classe <xref:Microsoft.Build.Tasks.ToolTaskExtension>, qui hérite elle\-même de la classe <xref:Microsoft.Build.Utilities.ToolTask>.  Pour obtenir la liste de ces paramètres supplémentaires et de leurs descriptions, consultez [ToolTaskExtension Base Class](../msbuild/tooltaskextension-base-class.md).  
  
## Exemple  
 L'exemple suivant compile un projet [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)].  
  
```  
<VBC  
   Sources="@(sources)"  
   Resources="strings.resources"  
   Optimize="true"  
   OutputAssembly="out.exe"/>  
```  
  
## Voir aussi  
 [Visual Basic Command\-Line Compiler](/dotnet/visual-basic/reference/command-line-compiler/index)   
 [Tasks](../msbuild/msbuild-tasks.md)   
 [Task Reference](../msbuild/msbuild-task-reference.md)