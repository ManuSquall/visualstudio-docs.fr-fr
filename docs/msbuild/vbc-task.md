---
title: Vbc, tâche | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology: msbuild
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Vbc
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Vbc task [MSBuild]
- MSBuild, Vbc task
ms.assetid: 595278b1-2782-4577-b1ba-b4b5ab5625a3
caps.latest.revision: 19
author: Mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 01b38f523a3a1c97798cdd629290791ab5e480f8
ms.sourcegitcommit: 3b692c9bf332b7b9150901e16daf99a64b599fee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/10/2018
---
# <a name="vbc-task"></a>Vbc, tâche
Encapsule vbc.exe, qui produit des fichiers exécutables (.exe), des bibliothèques de liens dynamiques (.dll) ou des modules de code (.netmodule). Pour plus d’informations sur vbc.exe, consultez [Compilateur de ligne de commande de Visual Basic](/dotnet/visual-basic/reference/command-line-compiler/index).  
  
## <a name="parameters"></a>Paramètres  
 Le tableau ci-dessous décrit les paramètres de la tâche `Vbc` .  
  
|Paramètre|Description|  
|---------------|-----------------|  
|`AdditionalLibPaths`|Paramètre `String[]` facultatif.<br /><br /> Spécifie des dossiers supplémentaires dans lesquels rechercher les assemblys spécifiés dans l’attribut References.|  
|`AddModules`|Paramètre `String[]` facultatif.<br /><br /> Entraîne la mise à disposition par le compilateur de toutes les informations de type à partir du ou des fichiers spécifiés, pour le projet en cours de compilation. Ce paramètre correspond au commutateur [/addmodule](/dotnet/visual-basic/reference/command-line-compiler/addmodule) du compilateur vbc.exe.|  
|`BaseAddress`|Paramètre `String` facultatif.<br /><br /> Spécifie l’adresse de base de la DLL. Ce paramètre correspond au commutateur [/baseaddress](/dotnet/visual-basic/reference/command-line-compiler/baseaddress) du compilateur vbc.exe.|  
|`CodePage`|Paramètre `Int32` facultatif.<br /><br /> Spécifie la page de codes à utiliser pour tous les fichiers de code source inclus dans la compilation. Ce paramètre correspond au commutateur [/codepage](/dotnet/visual-basic/reference/command-line-compiler/codepage) du compilateur vbc.exe.|  
|`DebugType`|Paramètre `String[]` facultatif.<br /><br /> Fait en sorte que le compilateur génère des informations de débogage. Ce paramètre peut avoir les valeurs suivantes :<br /><br /> -   `full`<br />-   `pdbonly`<br /><br /> La valeur par défaut `full`, permet d’attacher un débogueur au programme en cours d’exécution. La valeur `pdbonly` autorise un débogage du code source quand le programme est démarré dans le débogueur, mais affiche du code en langage assembleur uniquement quand le programme en cours d’exécution est attaché au débogueur. Pour plus d’informations, consultez [/debug (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/debug).|  
|`DefineConstants`|Paramètre `String[]` facultatif.<br /><br /> Définit des constantes conditionnelles du compilateur. Les paires symbole/valeur sont séparées par des points-virgules et spécifiées avec la syntaxe suivante :<br /><br /> *symbole1* `=` *valeur1* `;` *symbole2* `=` *valeur2*<br /><br /> Ce paramètre correspond au commutateur [/define](/dotnet/visual-basic/reference/command-line-compiler/define) du compilateur vbc.exe.|  
|`DelaySign`|Paramètre `Boolean` facultatif.<br /><br /> Si la valeur est `true`, la tâche place la clé publique dans l’assembly. Si la valeur est `false`, la tâche signe complètement l’assembly. La valeur par défaut est `false`. Ce paramètre n’a aucun effet sauf s’il est utilisé avec le paramètre `KeyFile` ou `KeyContainer`. Ce paramètre correspond au commutateur [/delaysign](/dotnet/visual-basic/reference/command-line-compiler/delaysign) du compilateur vbc.exe.|  
|`DisabledWarnings`|Paramètre `String` facultatif.<br /><br /> Supprime les avertissements spécifiés. Vous avez besoin de spécifier uniquement la partie numérique de l’identificateur d’avertissement. Les différents avertissements sont séparés par des points-virgules. Ce paramètre correspond au commutateur [/nowarn](/dotnet/visual-basic/reference/command-line-compiler/nowarn) du compilateur vbc.exe.|  
|`DocumentationFile`|Paramètre `String` facultatif.<br /><br /> Traite les commentaires de documentation pour les diriger vers le fichier XML spécifié. Ce paramètre remplace l’attribut `GenerateDocumentation`. Pour plus d’informations, consultez [/doc](/dotnet/visual-basic/reference/command-line-compiler/doc).|  
|`EmitDebugInformation`|Paramètre `Boolean` facultatif.<br /><br /> Si la valeur est `true`, la tâche génère des informations de débogage et les place dans un fichier .pdb. Pour plus d’informations, consultez [/debug (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/debug).|  
|`ErrorReport`|Paramètre `String` facultatif.<br /><br /> Indique comment la tâche doit signaler les erreurs internes du compilateur. Ce paramètre peut avoir les valeurs suivantes :<br /><br /> -   `prompt`<br />-   `send`<br />-   `none`<br /><br /> Si vous spécifiez `prompt` et qu’une erreur interne du compilateur se produit, l’utilisateur est invité à envoyer les données d’erreur à Microsoft.<br /><br /> Si vous spécifiez `send` et qu’une erreur interne du compilateur se produit, la tâche envoie les données d’erreur à Microsoft.<br /><br /> La valeur par défaut est `none`. Elle signale les erreurs dans une sortie texte uniquement.<br /><br /> Ce paramètre correspond au commutateur [/errorreport](/dotnet/visual-basic/reference/command-line-compiler/errorreport) du compilateur vbc.exe.|  
|`FileAlignment`|Paramètre `Int32` facultatif.<br /><br /> Spécifie, en octets, où les sections du fichier de sortie doivent être alignées. Ce paramètre peut avoir les valeurs suivantes :<br /><br /> -   `512`<br />-   `1024`<br />-   `2048`<br />-   `4096`<br />-   `8192`<br /><br /> Ce paramètre correspond au commutateur [/filealign](/dotnet/visual-basic/reference/command-line-compiler/filealign) du compilateur vbc.exe.|  
|`GenerateDocumentation`|Paramètre `Boolean` facultatif.<br /><br /> Si la valeur est `true`, génère des informations de documentation et les place dans un fichier XML avec le nom du fichier exécutable ou de la bibliothèque créé(e) par la tâche. Pour plus d’informations, consultez [/doc](/dotnet/visual-basic/reference/command-line-compiler/doc).|  
|`Imports`|Paramètre <xref:Microsoft.Build.Framework.ITaskItem>`[]` facultatif.<br /><br /> Importe des espaces de noms à partir des collections d’éléments spécifiées. Ce paramètre correspond au commutateur [/imports](/dotnet/visual-basic/reference/command-line-compiler/imports) du compilateur vbc.exe.|  
|`KeyContainer`|Paramètre `String` facultatif.<br /><br /> Spécifie le nom du conteneur de la clé de chiffrement. Ce paramètre correspond au commutateur [/keycontainer](/dotnet/visual-basic/reference/command-line-compiler/keycontainer) du compilateur vbc.exe.|  
|`KeyFile`|Paramètre `String` facultatif.<br /><br /> Spécifie le nom du fichier contenant la clé de chiffrement. Pour plus d’informations, consultez [/keyfile](/dotnet/visual-basic/reference/command-line-compiler/keyfile).|  
|`LangVersion`|Paramètre <xref:System.String?displayProperty=fullName> facultatif.<br /><br /> Spécifie la version du langage, « 9 » ou « 10 ».|  
|`LinkResources`|Paramètre <xref:Microsoft.Build.Framework.ITaskItem>`[]` facultatif.<br /><br /> Crée un lien à une ressource .NET Framework dans le fichier de sortie ; le fichier de ressources n’est pas placé dans le fichier de sortie. Ce paramètre correspond au commutateur [/linkresource](/dotnet/visual-basic/reference/command-line-compiler/linkresource) du compilateur vbc.exe.|  
|`MainEntryPoint`|Paramètre `String` facultatif.<br /><br /> Spécifie la classe ou le module qui contient la procédure `Sub Main`. Ce paramètre correspond au commutateur [/main](/dotnet/visual-basic/reference/command-line-compiler/main) du compilateur vbc.exe.|  
|`ModuleAssemblyName`|Paramètre `String` facultatif.<br /><br /> Spécifie l’assembly dont ce module fait partie.|  
|`NoConfig`|Paramètre `Boolean` facultatif.<br /><br /> Indique que le compilateur ne doit pas utiliser le fichier vbc.rsp. Ce paramètre correspond au commutateur [/noconfig](/dotnet/visual-basic/reference/command-line-compiler/noconfig) du compilateur vbc.exe.|  
|`NoLogo`|Paramètre `Boolean` facultatif.<br /><br /> Si `true`, supprime l’affichage des informations de bannière du compilateur. Ce paramètre correspond au commutateur [/nologo](/dotnet/visual-basic/reference/command-line-compiler/nologo) du compilateur vbc.exe.|  
|`NoStandardLib`|Paramètre `Boolean` facultatif.<br /><br /> Configure le compilateur pour ne pas référencer les bibliothèques standard. Ce paramètre correspond au commutateur [/nostdlib](/dotnet/visual-basic/reference/command-line-compiler/nostdlib) du compilateur vbc.exe.|  
|`NoVBRuntimeReference`|Paramètre `Boolean` facultatif.<br /><br /> Usage interne uniquement. Si la valeur est true, empêche la référence automatique à Microsoft.VisualBasic.dll.|  
|`NoWarnings`|Paramètre `Boolean` facultatif.<br /><br /> Si la valeur est `true`, la tâche supprime tous les avertissements. Pour plus d’informations, consultez [/nowarn](/dotnet/visual-basic/reference/command-line-compiler/nowarn).|  
|`Optimize`|Paramètre `Boolean` facultatif.<br /><br /> Si la valeur est `true`, active les optimisations du compilateur. Ce paramètre correspond au commutateur [/optimize](/dotnet/visual-basic/reference/command-line-compiler/optimize) du compilateur vbc.exe.|  
|`OptionCompare`|Paramètre `String` facultatif.<br /><br /> Spécifie la façon dont sont effectuées les comparaisons de chaînes. Ce paramètre peut avoir les valeurs suivantes :<br /><br /> -   `binary`<br />-   `text`<br /><br /> La valeur `binary` indique que la tâche utilise des comparaisons de chaînes binaires. La valeur `text` indique que la tâche utilise des comparaisons de chaînes de texte. La valeur par défaut de ce paramètre est `binary`. Ce paramètre correspond au commutateur [/optioncompare](/dotnet/visual-basic/reference/command-line-compiler/optioncompare) du compilateur vbc.exe.|  
|`OptionExplicit`|Paramètre `Boolean` facultatif.<br /><br /> Si la valeur est `true`, les variables doivent être déclarées de manière explicite. Ce paramètre correspond au commutateur [/optionexplicit](/dotnet/visual-basic/reference/command-line-compiler/optionexplicit) du compilateur vbc.exe.|  
|`OptionInfer`|Paramètre `Boolean` facultatif.<br /><br /> Si la valeur est `true`, autorise l’inférence de type des variables.|  
|`OptionStrict`|Paramètre `Boolean` facultatif.<br /><br /> Si la valeur est `true`, la tâche applique la sémantique de type stricte pour restreindre les conversions de types implicites. Ce paramètre correspond au commutateur [/optionstrict](/dotnet/visual-basic/reference/command-line-compiler/optionstrict) du compilateur vbc.exe.|  
|`OptionStrictType`|Paramètre `String` facultatif.<br /><br /> Spécifie quelle sémantique de type stricte génère un avertissement. Actuellement, seul « custom » est pris en charge. Ce paramètre correspond au commutateur [/optionstrict](/dotnet/visual-basic/reference/command-line-compiler/optionstrict) du compilateur vbc.exe.|  
|`OutputAssembly`|Paramètre de sortie `String` facultatif.<br /><br /> Spécifie le nom du fichier de sortie. Ce paramètre correspond au commutateur [/out](/dotnet/visual-basic/reference/command-line-compiler/out) du compilateur vbc.exe.|  
|`Platform`|Paramètre `String` facultatif.<br /><br /> Spécifie la plateforme de processeur ciblée par le fichier de sortie. Ce paramètre peut avoir la valeur `x86`, `x64`, `Itanium` ou `anycpu`. La valeur par défaut est `anycpu`. Ce paramètre correspond au commutateur [/platform](/dotnet/visual-basic/reference/command-line-compiler/platform) du compilateur vbc.exe.|  
|`References`|Paramètre <xref:Microsoft.Build.Framework.ITaskItem>`[]` facultatif.<br /><br /> Provoque l’importation par la tâche des informations de type public dans le projet actuel à partir des éléments spécifiés. Ce paramètre correspond au commutateur [/reference](/dotnet/visual-basic/reference/command-line-compiler/reference) du compilateur vbc.exe.|  
|`RemoveIntegerChecks`|Paramètre `Boolean` facultatif.<br /><br /> Si la valeur est `true`, désactive les contrôles d’erreur de dépassement sur les entiers. La valeur par défaut est `false`. Ce paramètre correspond au commutateur [/removeintchecks](/dotnet/visual-basic/reference/command-line-compiler/removeintchecks) du compilateur vbc.exe.|  
|`Resources`|Paramètre <xref:Microsoft.Build.Framework.ITaskItem>`[]` facultatif.<br /><br /> Incorpore une ressource .NET Framework dans le fichier de sortie. Ce paramètre correspond au commutateur [/resource](/dotnet/visual-basic/reference/command-line-compiler/resource) du compilateur vbc.exe.|  
|`ResponseFiles`|Paramètre <xref:Microsoft.Build.Framework.ITaskItem>`[]` facultatif.<br /><br /> Spécifie le fichier réponse qui contient les commandes correspondant à cette tâche. Ce paramètre correspond à l’option [@ (Spécifier un fichier réponse)](/dotnet/visual-basic/reference/command-line-compiler/specify-response-file) du compilateur vbc.exe.|  
|`RootNamespace`|Paramètre `String` facultatif.<br /><br /> Spécifie l’espace de noms racine pour toutes les déclarations de type. Ce paramètre correspond au commutateur [/rootnamespace](/dotnet/visual-basic/reference/command-line-compiler/rootnamespace) du compilateur vbc.exe.|  
|`SdkPath`|Paramètre `String` facultatif.<br /><br /> Spécifie l'emplacement de mscorlib.dll et de microsoft.visualbasic.dll. Ce paramètre correspond au commutateur [/sdkpath](/dotnet/visual-basic/reference/command-line-compiler/sdkpath) du compilateur vbc.exe.|  
|`Sources`|Paramètre <xref:Microsoft.Build.Framework.ITaskItem>`[]` facultatif.<br /><br /> Spécifie un ou plusieurs fichiers sources [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)].|  
|`TargetCompactFramework`|Paramètre `Boolean` facultatif.<br /><br /> Si la valeur est `true`, la tâche cible le [!INCLUDE[Compact](../extensibility/includes/compact_md.md)]. Cette option correspond au commutateur [/netcf](/dotnet/visual-basic/reference/command-line-compiler/netcf) du compilateur vbc.exe.|  
|`TargetType`|Paramètre `String` facultatif.<br /><br /> Spécifie le format de fichier du fichier de sortie. Ce paramètre peut avoir la valeur `library`, qui crée une bibliothèque de codes, `exe`, qui crée une application console, `module`, qui crée un module, ou `winexe`, qui crée un programme Windows. La valeur par défaut est `library`. Ce paramètre correspond au commutateur [/target](/dotnet/visual-basic/reference/command-line-compiler/target) du compilateur vbc.exe.|  
|`Timeout`|Paramètre `Int32` facultatif.<br /><br /> Spécifie le délai, en millisecondes, après lequel l’exécutable de la tâche est arrêté. La valeur par défaut est `Int.MaxValue`, ce qui indique qu’il n’existe aucun délai d’expiration.|  
|`ToolPath`|Paramètre `String` facultatif.<br /><br /> Spécifie l’emplacement à partir duquel la tâche chargera le fichier exécutable sous-jacent (vbc.exe). Si vous ne spécifiez pas ce paramètre, la tâche utilise le chemin d’installation du SDK correspondant à la version du framework qui exécute [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].|  
|`TreatWarningsAsErrors`|Paramètre `Boolean` facultatif.<br /><br /> Si la valeur est `true`, tous les avertissements sont traités comme des erreurs. Pour plus d’informations, consultez [/warnaserror (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/warnaserror).|  
|`UseHostCompilerIfAvailable`|Paramètre `Boolean` facultatif.<br /><br /> Demande à la tâche d’utiliser l’objet de compilateur in-process s’il est disponible. Son utilisation est réservée à [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].|  
|`Utf8Output`|Paramètre `Boolean` facultatif.<br /><br /> Enregistre les résultats de la compilation au format d’encodage UTF-8. Ce paramètre correspond au commutateur [/utf8output](/dotnet/visual-basic/reference/command-line-compiler/utf8output) du compilateur vbc.exe.|  
|`Verbosity`|Paramètre `String` facultatif.<br /><br /> Spécifie le niveau de commentaires de la sortie du compilateur. Le niveau de commentaires peut être `Quiet`, `Normal` (la valeur par défaut) ou `Verbose`.|  
|`WarningsAsErrors`|Paramètre `String` facultatif.<br /><br /> Spécifie une liste d'avertissements à traiter comme des erreurs. Pour plus d’informations, consultez [/warnaserror (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/warnaserror).<br /><br /> Ce paramètre remplace le paramètre `TreatWarningsAsErrors`.|  
|`WarningsNotAsErrors`|Paramètre `String` facultatif.<br /><br /> Spécifie une liste d'avertissements à ne pas traiter comme des erreurs. Pour plus d’informations, consultez [/warnaserror (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/warnaserror).<br /><br /> Ce paramètre est utile uniquement si le paramètre `TreatWarningsAsErrors` est défini sur `true`.|  
|`Win32Icon`|Paramètre `String` facultatif.<br /><br /> Insère un fichier .ico dans l’assembly, ce qui donne au fichier de sortie l’apparence souhaitée dans l’Explorateur de fichiers. Ce paramètre correspond au commutateur [/win32icon](/dotnet/visual-basic/reference/command-line-compiler/win32icon) du compilateur vbc.exe.|  
|`Win32Resources`|Paramètre `String` facultatif.<br /><br /> Insère un fichier de ressources Win32 (.res) dans le fichier de sortie. Ce paramètre correspond au commutateur [/win32resource](/dotnet/visual-basic/reference/command-line-compiler/win32resource) du compilateur vbc.exe.|  
  
## <a name="remarks"></a>Notes  
 En plus des paramètres énumérés ci-dessus, cette tâche hérite des paramètres de la classe <xref:Microsoft.Build.Tasks.ToolTaskExtension>, qui elle-même hérite de la classe <xref:Microsoft.Build.Utilities.ToolTask>. Pour obtenir la liste de ces paramètres supplémentaires et de leurs descriptions, consultez l’article [ToolTaskExtension Base Class (Classe de base ToolTaskExtension)](../msbuild/tooltaskextension-base-class.md).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant compile un projet [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)].  
  
```xml  
<VBC  
   Sources="@(sources)"  
   Resources="strings.resources"  
   Optimize="true"  
   OutputAssembly="out.exe"/>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Compilateur de ligne de commande de Visual Basic](/dotnet/visual-basic/reference/command-line-compiler/index)   
 [Tâches](../msbuild/msbuild-tasks.md)   
 [Task Reference (Informations de référence sur les tâches MSBuild)](../msbuild/msbuild-task-reference.md)