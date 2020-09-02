---
title: Vbc, tâche | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
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
caps.latest.revision: 22
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6edc8b246055dcd8efdb32f4118f81a535635d55
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65683832"
---
# <a name="vbc-task"></a>Vbc, tâche
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Encapsule vbc.exe, qui produit des fichiers exécutables (.exe), des bibliothèques de liens dynamiques (.dll) ou des modules de code (.netmodule). Pour plus d’informations sur vbc.exe, consultez [Compilateur de ligne de commande de Visual Basic](https://msdn.microsoft.com/library/6b57c444-50c7-4b88-8f59-ed65cff5e05c).  
  
## <a name="parameters"></a>Paramètres  
 Le tableau ci-dessous décrit les paramètres de la tâche `Vbc` .  
  
|Paramètre|Description|  
|---------------|-----------------|  
|`AdditionalLibPaths`|Paramètre `String[]` facultatif.<br /><br /> Spécifie des dossiers supplémentaires dans lesquels rechercher les assemblys spécifiés dans l’attribut References.|  
|`AddModules`|Paramètre `String[]` facultatif.<br /><br /> Entraîne la mise à disposition par le compilateur de toutes les informations de type à partir du ou des fichiers spécifiés, pour le projet en cours de compilation. Ce paramètre correspond au commutateur [/addmodule](https://msdn.microsoft.com/library/fb4b89d4-4926-4f20-868d-427fa28497b2) du compilateur vbc.exe.|  
|`BaseAddress`|Paramètre `String` facultatif.<br /><br /> Spécifie l’adresse de base de la DLL. Ce paramètre correspond au commutateur [/baseaddress](https://msdn.microsoft.com/library/c982bcf2-46e5-47a2-bc8f-a5cc32b7dc47) du compilateur vbc.exe.|  
|`CodePage`|Paramètre `Int32` facultatif.<br /><br /> Spécifie la page de codes à utiliser pour tous les fichiers de code source inclus dans la compilation. Ce paramètre correspond au commutateur [/codepage](https://msdn.microsoft.com/library/be36ec33-6800-4505-838c-4124564f5cc9) du compilateur vbc.exe.|  
|`DebugType`|Paramètre `String[]` facultatif.<br /><br /> Fait en sorte que le compilateur génère des informations de débogage. Ce paramètre peut avoir les valeurs suivantes :<br /><br /> -   `full`<br />-   `pdbonly`<br /><br /> La valeur par défaut `full`, permet d’attacher un débogueur au programme en cours d’exécution. La valeur `pdbonly` autorise un débogage du code source quand le programme est démarré dans le débogueur, mais affiche du code en langage assembleur uniquement quand le programme en cours d’exécution est attaché au débogueur. Pour plus d’informations, consultez [/debug (Visual Basic)](https://msdn.microsoft.com/library/c2b0bea5-1d5e-499f-9bd5-4f6c6b715ea2).|  
|`DefineConstants`|Paramètre `String[]` facultatif.<br /><br /> Définit des constantes conditionnelles du compilateur. Les paires symbole/valeur sont séparées par des points-virgules et spécifiées avec la syntaxe suivante :<br /><br /> *symbole1* `=` *valeur1* `;` *symbole2* `=` *valeur2*<br /><br /> Ce paramètre correspond au commutateur [/define](https://msdn.microsoft.com/library/f735c57d-1cf9-4f2f-a26f-0de630fd4077) du compilateur vbc.exe.|  
|`DelaySign`|Paramètre `Boolean` facultatif.<br /><br /> Si la valeur est `true`, la tâche place la clé publique dans l’assembly. Si la valeur est `false`, la tâche signe complètement l’assembly. La valeur par défaut est `false`. Ce paramètre n’a aucun effet sauf s’il est utilisé avec le paramètre `KeyFile` ou `KeyContainer`. Ce paramètre correspond au commutateur [/delaysign](https://msdn.microsoft.com/library/c76e61a4-1884-4252-9fb2-377f99caa690) du compilateur vbc.exe.|  
|`DisabledWarnings`|Paramètre `String` facultatif.<br /><br /> Supprime les avertissements spécifiés. Vous avez besoin de spécifier uniquement la partie numérique de l’identificateur d’avertissement. Les différents avertissements sont séparés par des points-virgules. Ce paramètre correspond au commutateur [/nowarn](https://msdn.microsoft.com/library/7ebf2106-0652-4fdc-bf60-70fc86465d83) du compilateur vbc.exe.|  
|`DocumentationFile`|Paramètre `String` facultatif.<br /><br /> Traite les commentaires de documentation pour les diriger vers le fichier XML spécifié. Ce paramètre remplace l’attribut `GenerateDocumentation`. Pour plus d’informations, consultez [/doc](https://msdn.microsoft.com/library/5fc32ec9-a149-4648-994c-a8d0cccd0a65).|  
|`EmitDebugInformation`|Paramètre `Boolean` facultatif.<br /><br /> Si la valeur est `true`, la tâche génère des informations de débogage et les place dans un fichier .pdb. Pour plus d’informations, consultez [/debug (Visual Basic)](https://msdn.microsoft.com/library/c2b0bea5-1d5e-499f-9bd5-4f6c6b715ea2).|  
|`ErrorReport`|Paramètre `String` facultatif.<br /><br /> Indique comment la tâche doit signaler les erreurs internes du compilateur. Ce paramètre peut avoir les valeurs suivantes :<br /><br /> -   `prompt`<br />-   `send`<br />-   `none`<br /><br /> Si vous spécifiez `prompt` et qu’une erreur interne du compilateur se produit, l’utilisateur est invité à envoyer les données d’erreur à Microsoft.<br /><br /> Si vous spécifiez `send` et qu’une erreur interne du compilateur se produit, la tâche envoie les données d’erreur à Microsoft.<br /><br /> La valeur par défaut est `none`. Elle signale les erreurs dans une sortie texte uniquement.<br /><br /> Ce paramètre correspond au commutateur [/errorreport](https://msdn.microsoft.com/library/a7fe83a2-a6d8-460c-8dad-79a8f433f501) du compilateur vbc.exe.|  
|`FileAlignment`|Paramètre `Int32` facultatif.<br /><br /> Spécifie, en octets, où les sections du fichier de sortie doivent être alignées. Ce paramètre peut avoir les valeurs suivantes :<br /><br /> -   `512`<br />-   `1024`<br />-   `2048`<br />-   `4096`<br />-   `8192`<br /><br /> Ce paramètre correspond au commutateur [/filealign](https://msdn.microsoft.com/library/cc61ec3d-ad38-4b28-9659-099d73cad099) du compilateur vbc.exe.|  
|`GenerateDocumentation`|Paramètre `Boolean` facultatif.<br /><br /> Si la valeur est `true`, génère des informations de documentation et les place dans un fichier XML avec le nom du fichier exécutable ou de la bibliothèque créé(e) par la tâche. Pour plus d’informations, consultez [/doc](https://msdn.microsoft.com/library/5fc32ec9-a149-4648-994c-a8d0cccd0a65).|  
|`Imports`|Paramètre <xref:Microsoft.Build.Framework.ITaskItem>`[]` facultatif.<br /><br /> Importe des espaces de noms à partir des collections d’éléments spécifiées. Ce paramètre correspond au commutateur [/imports](https://msdn.microsoft.com/library/9a93fb53-c080-497b-bf9b-441022dbbc39) du compilateur vbc.exe.|  
|`KeyContainer`|Paramètre `String` facultatif.<br /><br /> Spécifie le nom du conteneur de la clé de chiffrement. Ce paramètre correspond au commutateur [/keycontainer](https://msdn.microsoft.com/library/6a9bc861-1752-4db1-9f64-b5252f0482cc) du compilateur vbc.exe.|  
|`KeyFile`|Paramètre `String` facultatif.<br /><br /> Spécifie le nom du fichier contenant la clé de chiffrement. Pour plus d’informations, consultez [/keyfile](https://msdn.microsoft.com/library/ffa82a4b-517a-4c6c-9889-5bae7b534bb8).|  
|`LangVersion`|Paramètre [String](<!-- TODO: review code entity reference <xref:assetId:///String?qualifyHint=False&amp;autoUpgrade=True>  -->) facultatif.<br /><br /> Spécifie la version du langage, « 9 » ou « 10 ».|  
|`LinkResources`|Paramètre <xref:Microsoft.Build.Framework.ITaskItem>`[]` facultatif.<br /><br /> Crée un lien à une ressource .NET Framework dans le fichier de sortie ; le fichier de ressources n’est pas placé dans le fichier de sortie. Ce paramètre correspond au commutateur [/linkresource](https://msdn.microsoft.com/library/cf4dcad8-17b7-404c-9184-29358aa05b15) du compilateur vbc.exe.|  
|`MainEntryPoint`|Paramètre `String` facultatif.<br /><br /> Spécifie la classe ou le module qui contient la procédure `Sub Main`. Ce paramètre correspond au commutateur [/main](https://msdn.microsoft.com/library/83fc339d-6652-415d-b205-b5133319b5b0) du compilateur vbc.exe.|  
|`ModuleAssemblyName`|Paramètre `String` facultatif.<br /><br /> Spécifie l’assembly dont ce module fait partie.|  
|`NoConfig`|Paramètre `Boolean` facultatif.<br /><br /> Indique que le compilateur ne doit pas utiliser le fichier vbc.rsp. Ce paramètre correspond au commutateur [/noconfig](https://msdn.microsoft.com/library/a7405067-bd21-4171-adf4-a126fa3ad6c3) du compilateur vbc.exe.|  
|`NoLogo`|Paramètre `Boolean` facultatif.<br /><br /> Si `true`, supprime l’affichage des informations de bannière du compilateur. Ce paramètre correspond au commutateur [/nologo](https://msdn.microsoft.com/library/25ef54b6-d676-4639-a2d2-a747a158bc07) du compilateur vbc.exe.|  
|`NoStandardLib`|Paramètre `Boolean` facultatif.<br /><br /> Configure le compilateur pour ne pas référencer les bibliothèques standard. Ce paramètre correspond au commutateur [/nostdlib](https://msdn.microsoft.com/library/140381b8-dc96-4ad5-ae11-792c9ed0be4d) du compilateur vbc.exe.|  
|`NoVBRuntimeReference`|Paramètre `Boolean` facultatif.<br /><br /> À usage interne uniquement Si la valeur est true, empêche la référence automatique à Microsoft.VisualBasic.dll.|  
|`NoWarnings`|Paramètre `Boolean` facultatif.<br /><br /> Si la valeur est `true`, la tâche supprime tous les avertissements. Pour plus d’informations, consultez [/nowarn](https://msdn.microsoft.com/library/7ebf2106-0652-4fdc-bf60-70fc86465d83).|  
|`Optimize`|Paramètre `Boolean` facultatif.<br /><br /> Si la valeur est `true`, active les optimisations du compilateur. Ce paramètre correspond au commutateur [/optimize](https://msdn.microsoft.com/library/fcba4a97-3622-4b87-a891-0f77deab4998) du compilateur vbc.exe.|  
|`OptionCompare`|Paramètre `String` facultatif.<br /><br /> Spécifie la façon dont sont effectuées les comparaisons de chaînes. Ce paramètre peut avoir les valeurs suivantes :<br /><br /> -   `binary`<br />-   `text`<br /><br /> La valeur `binary` indique que la tâche utilise des comparaisons de chaînes binaires. La valeur `text` indique que la tâche utilise des comparaisons de chaînes de texte. La valeur par défaut de ce paramètre est `binary`. Ce paramètre correspond au commutateur [/optioncompare](https://msdn.microsoft.com/library/7237b766-b44d-4cc5-9a3c-885348a7d9e4) du compilateur vbc.exe.|  
|`OptionExplicit`|Paramètre `Boolean` facultatif.<br /><br /> Si la valeur est `true`, les variables doivent être déclarées de manière explicite. Ce paramètre correspond au commutateur [/optionexplicit](https://msdn.microsoft.com/library/5d296ab3-bafe-4c4d-9887-78f162ed86c7) du compilateur vbc.exe.|  
|`OptionInfer`|Paramètre `Boolean` facultatif.<br /><br /> Si la valeur est `true`, autorise l’inférence de type des variables.|  
|`OptionStrict`|Paramètre `Boolean` facultatif.<br /><br /> Si la valeur est `true`, la tâche applique la sémantique de type stricte pour restreindre les conversions de types implicites. Ce paramètre correspond au commutateur [/optionstrict](https://msdn.microsoft.com/library/c7b10086-0fa4-49db-b3c8-4ae0db5957da) du compilateur vbc.exe.|  
|`OptionStrictType`|Paramètre `String` facultatif.<br /><br /> Spécifie quelle sémantique de type stricte génère un avertissement. Actuellement, seul « custom » est pris en charge. Ce paramètre correspond au commutateur [/optionstrict](https://msdn.microsoft.com/library/c7b10086-0fa4-49db-b3c8-4ae0db5957da) du compilateur vbc.exe.|  
|`OutputAssembly`|Paramètre de sortie `String` facultatif.<br /><br /> Spécifie le nom du fichier de sortie. Ce paramètre correspond au commutateur [/out](https://msdn.microsoft.com/library/9f148c15-0909-4cb8-a2db-777f8a8b45ae) du compilateur vbc.exe.|  
|`Platform`|Paramètre `String` facultatif.<br /><br /> Spécifie la plateforme de processeur ciblée par le fichier de sortie. Ce paramètre peut avoir la valeur `x86`, `x64`, `Itanium` ou `anycpu`. La valeur par défaut est `anycpu`. Ce paramètre correspond au commutateur [/platform](https://msdn.microsoft.com/library/f9bc61e6-e854-4ae1-87b9-d6244de23fd1) du compilateur vbc.exe.|  
|`References`|Paramètre <xref:Microsoft.Build.Framework.ITaskItem>`[]` facultatif.<br /><br /> Provoque l’importation par la tâche des informations de type public dans le projet actuel à partir des éléments spécifiés. Ce paramètre correspond au commutateur [/reference](https://msdn.microsoft.com/library/66bdfced-bbf6-43d1-a554-bc0990315737) du compilateur vbc.exe.|  
|`RemoveIntegerChecks`|Paramètre `Boolean` facultatif.<br /><br /> Si la valeur est `true`, désactive les contrôles d’erreur de dépassement sur les entiers. La valeur par défaut est `false`. Ce paramètre correspond au commutateur [/removeintchecks](https://msdn.microsoft.com/library/c1835bd5-1e38-4fba-bd2f-6984774765d4) du compilateur vbc.exe.|  
|`Resources`|Paramètre <xref:Microsoft.Build.Framework.ITaskItem>`[]` facultatif.<br /><br /> Incorpore une ressource .NET Framework dans le fichier de sortie. Ce paramètre correspond au commutateur [/resource](https://msdn.microsoft.com/library/eee2f227-91f2-4f2b-a9d6-1c51c5320858) du compilateur vbc.exe.|  
|`ResponseFiles`|Paramètre <xref:Microsoft.Build.Framework.ITaskItem>`[]` facultatif.<br /><br /> Spécifie le fichier réponse qui contient les commandes correspondant à cette tâche. Ce paramètre correspond à l’option [@ (Spécifier un fichier réponse)](https://msdn.microsoft.com/library/a6847eaa-e5f9-4303-9421-45b55484b9ca) du compilateur vbc.exe.|  
|`RootNamespace`|Paramètre `String` facultatif.<br /><br /> Spécifie l’espace de noms racine pour toutes les déclarations de type. Ce paramètre correspond au commutateur [/rootnamespace](https://msdn.microsoft.com/library/e9245edf-6bef-420d-a7c7-324117752783) du compilateur vbc.exe.|  
|`SdkPath`|Paramètre `String` facultatif.<br /><br /> Spécifie l'emplacement de mscorlib.dll et de microsoft.visualbasic.dll. Ce paramètre correspond au commutateur [/sdkpath](https://msdn.microsoft.com/library/fec8a3f1-b791-4a37-8af7-344859f8212d) du compilateur vbc.exe.|  
|`Sources`|Paramètre <xref:Microsoft.Build.Framework.ITaskItem>`[]` facultatif.<br /><br /> Spécifie un ou plusieurs fichiers sources [!INCLUDE[vbprvb](../includes/vbprvb-md.md)].|  
|`TargetCompactFramework`|Paramètre `Boolean` facultatif.<br /><br /> Si la valeur est `true`, la tâche cible le [!INCLUDE[Compact](../includes/compact-md.md)]. Cette option correspond au commutateur [/netcf](https://msdn.microsoft.com/library/db7cfa59-c315-401c-a59b-0daf355343d6) du compilateur vbc.exe.|  
|`TargetType`|Paramètre `String` facultatif.<br /><br /> Spécifie le format de fichier du fichier de sortie. Ce paramètre peut avoir la valeur `library`, qui crée une bibliothèque de codes, `exe`, qui crée une application console, `module`, qui crée un module, ou `winexe`, qui crée un programme Windows. La valeur par défaut est `library`. Ce paramètre correspond au commutateur [/target](https://msdn.microsoft.com/library/e0954147-548b-461f-9c4b-a8f88845616c) du compilateur vbc.exe.|  
|`Timeout`|Paramètre `Int32` facultatif.<br /><br /> Spécifie le délai, en millisecondes, après lequel l’exécutable de la tâche est arrêté. La valeur par défaut est `Int.MaxValue`, ce qui indique qu’il n’existe aucun délai d’expiration.|  
|`ToolPath`|Paramètre `String` facultatif.<br /><br /> Spécifie l’emplacement à partir duquel la tâche chargera le fichier exécutable sous-jacent (vbc.exe). Si vous ne spécifiez pas ce paramètre, la tâche utilise le chemin d’installation du SDK correspondant à la version du framework qui exécute [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)].|  
|`TreatWarningsAsErrors`|Paramètre `Boolean` facultatif.<br /><br /> Si la valeur est `true`, tous les avertissements sont traités comme des erreurs. Pour plus d’informations, consultez [/warnaserror (Visual Basic)](https://msdn.microsoft.com/library/49819f1d-a1bd-4201-affe-5afe6d9712e1).|  
|`UseHostCompilerIfAvailable`|Paramètre `Boolean` facultatif.<br /><br /> Demande à la tâche d’utiliser l’objet de compilateur in-process s’il est disponible. Son utilisation est réservée à [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].|  
|`Utf8Output`|Paramètre `Boolean` facultatif.<br /><br /> Enregistre les résultats de la compilation au format d’encodage UTF-8. Ce paramètre correspond au commutateur [/utf8output](https://msdn.microsoft.com/library/8ab36b1e-027a-49ac-85b4-f48997d9e4d6) du compilateur vbc.exe.|  
|`Verbosity`|Paramètre `String` facultatif.<br /><br /> Spécifie le niveau de commentaires de la sortie du compilateur. Le niveau de commentaires peut être `Quiet`, `Normal` (la valeur par défaut) ou `Verbose`.|  
|`WarningsAsErrors`|Paramètre `String` facultatif.<br /><br /> Spécifie une liste d'avertissements à traiter comme des erreurs. Pour plus d’informations, consultez [/warnaserror (Visual Basic)](https://msdn.microsoft.com/library/49819f1d-a1bd-4201-affe-5afe6d9712e1).<br /><br /> Ce paramètre remplace le paramètre `TreatWarningsAsErrors`.|  
|`WarningsNotAsErrors`|Paramètre `String` facultatif.<br /><br /> Spécifie une liste d'avertissements à ne pas traiter comme des erreurs. Pour plus d’informations, consultez [/warnaserror (Visual Basic)](https://msdn.microsoft.com/library/49819f1d-a1bd-4201-affe-5afe6d9712e1).<br /><br /> Ce paramètre est utile uniquement si le paramètre `TreatWarningsAsErrors` est défini sur `true`.|  
|`Win32Icon`|Paramètre `String` facultatif.<br /><br /> Insère un fichier .ico dans l’assembly, ce qui donne au fichier de sortie l’apparence souhaitée dans l’Explorateur de fichiers. Ce paramètre correspond au commutateur [/win32icon](https://msdn.microsoft.com/library/aecaab01-9353-46c5-941c-6edabd4eff92) du compilateur vbc.exe.|  
|`Win32Resources`|Paramètre `String` facultatif.<br /><br /> Insère un fichier de ressources Win32 (.res) dans le fichier de sortie. Ce paramètre correspond au commutateur [/win32resource](https://msdn.microsoft.com/library/e226946d-19ce-4cc9-91f5-aed24f77aa2b) du compilateur vbc.exe.|  
  
## <a name="remarks"></a>Notes  
 En plus des paramètres énumérés ci-dessus, cette tâche hérite des paramètres de la classe <xref:Microsoft.Build.Tasks.ToolTaskExtension> , qui elle-même hérite de la classe <xref:Microsoft.Build.Utilities.ToolTask> . Pour obtenir la liste de ces paramètres supplémentaires et de leurs descriptions, consultez l’article [ToolTaskExtension Base Class (Classe de base ToolTaskExtension)](../msbuild/tooltaskextension-base-class.md).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant compile un projet [!INCLUDE[vbprvb](../includes/vbprvb-md.md)].  
  
```  
<VBC  
   Sources="@(sources)"  
   Resources="strings.resources"  
   Optimize="true"  
   OutputAssembly="out.exe"/>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Visual Basic du compilateur de ligne de commande](https://msdn.microsoft.com/library/6b57c444-50c7-4b88-8f59-ed65cff5e05c)   
 [Décrites](../msbuild/msbuild-tasks.md)   
 [Référence de tâche](../msbuild/msbuild-task-reference.md)
