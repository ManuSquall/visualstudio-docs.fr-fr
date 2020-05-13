---
title: Juste mon code (fr) Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 0f0df097-bbaf-46ad-9ad1-ef5f40435079
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: efcabf9c7dc201f95515cd24bf3a14727f7149fe
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302496"
---
# <a name="just-my-code"></a>Uniquement mon code
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Les développeurs qui utilisent des langages du .NET Framework sont familiarisés avec la fonctionnalité du débogueur Uniquement mon code, qui avance pas à pas dans les appels du système, les appels de l'infrastructure et les appels non-utilisateurs, et réduit les appels dans les fenêtres Pile des appels. Uniquement mon code a été étendu aux langages C++ et JavaScript. Cette rubrique décrit les caractéristiques d'utilisation d'Uniquement mon code dans les projets .NET Framework, C++ natifs et JavaScript.  
  
## <a name="enable-or-disable-just-my-code"></a><a name="BKMK_Enable_or_disable_Just_My_Code"></a> Activer ou désactiver Uniquement mon code  
 Pour activer ou désactiver Just My Code, choisissez **options et paramètres** sur le menu **Debug.** Dans le nœud**général** **de débogage,** / choisissez ou **effacez Activez juste mon code**.  
  
 ![Activez Uniquement mon code dans la boîte de dialogue Options](../debugger/media/dbg-justmycode-options.png "DBG_JustMyCode_Options")  
  
> [!NOTE]
> Le **paramètre Enable Just My Code** est un cadre global qui s’applique à tous les projets Visual Studio dans toutes les langues.  
  
### <a name="override-call-stack-filtering"></a><a name="BKMK_Override_call_stack_filtering"></a>Filtrer la pile d’appels de remplacement  
 Dans les affichages de la pile des appels, comme les fenêtres Pile des appels et Tâches, Uniquement mon code réduit le code non-utilisateur en un cadre annoté intitulé `[External Code]`. Pour afficher les cadres effondrés, choisissez **Afficher le code externe** sur le menu contextuelle de l’affichage de la pile d’appels.  
  
> [!NOTE]
> Le paramètre **Afficher le code externe** est enregistré sur le profileur de l’utilisateur actuel. Il est appliqué à tous les projets dans tous les langages qui sont ouverts par l'utilisateur.  
  
## <a name="net-framework-just-my-code"></a><a name="BKMK__NET_Framework_Just_My_Code"></a>.NET Framework Just My Code (en-)  
  
### <a name="user-and-non-user-code"></a><a name="BKMK_NET_User_and_non_user_code"></a>Code utilisateur et non utilisateur  
 Pour distinguer le code utilisateur du code non utilisateur, Just My Code examine les fichiers symboles (.pdb) et les optimisations de programme. Le débogueur considère le code comme du code non-utilisateur quand le fichier binaire est optimisé ou quand le fichier .pdb n'est pas disponible.  
  
 Trois attributs affectent également ce que le débogueur considère comme étant du code MyCode :  
  
- <xref:System.Diagnostics.DebuggerNonUserCodeAttribute> indique au débogueur que le code auquel il est appliqué n'est pas du code MyCode.  
  
- <xref:System.Diagnostics.DebuggerHiddenAttribute> masque le code au débogueur, même si l'option Uniquement mon code est désactivée.  
  
- <xref:System.Diagnostics.DebuggerStepThroughAttribute> indique au débogueur de passer pas à pas dans le code auquel il s'applique, plutôt que d'effectuer un pas à pas détaillé du code.  
  
  Tout le reste du code est considéré comme du code utilisateur.  
  
### <a name="stepping-behavior"></a><a name="BKMK_NET_Stepping_behavior"></a>Comportement de marche  
 Lorsque vous **entrez dans** (clavier raccourci: F11) code non-utilisateur, le débbuggeur étapes sur le code à la prochaine déclaration d’utilisateur. Lorsque vous **sortez** (Clavier: Shift F11), le débbuggeur s’exécute à la ligne suivante de code utilisateur. Si aucun code utilisateur n'est rencontré, l'exécution se poursuit jusqu'à ce que l'application se termine, jusqu'à ce qu'un point d'arrêt soit atteint ou jusqu'à ce qu'une exception se produise.  
  
### <a name="breakpoint-behavior"></a><a name="BKMK_NET_Breakpoint_behavior"></a>Comportement de point de rupture  
 Lorsque Just My Code est activé, vous pouvez choisir **Break All** (Clavier : Ctrl et Alt et Break) et arrêter l’exécution à un endroit où il n’y a pas de code utilisateur pour afficher. Dans ce cas, la fenêtre Pas de code source s'affiche. Si vous choisissez ensuite une commande d'étape, le débogueur vous amène à la ligne de code utilisateur suivante.  
  
### <a name="exception-behavior"></a><a name="BKMK_NET_Exception_behavior"></a>Comportement d’exception  
 Si une exception non gérée se produit dans du code non-utilisateur, le débogueur s'arrête à la ligne de code utilisateur où lequel l'exception a été générée.  
  
 Si les exceptions de première chance sont activées pour l'exception, la ligne de code utilisateur est mise en surbrillance en vert. La pile d’appels affiche un cadre annoté étiqueté **[Code externe]**.  
  
## <a name="c-just-my-code"></a><a name="BKMK_C___Just_My_Code"></a> Uniquement mon code C++  
  
### <a name="user-and-non-user-code"></a><a name="BKMK_CPP_User_and_non_user_code"></a>Code utilisateur et non utilisateur  
 Uniquement mon Code C++ est différent d'Uniquement mon code .NET Framework et JavaScript, car le comportement d'exécution pas à pas est indépendant du comportement de la pile des appels.  
  
 **Piles d’appels**  
  
 Par défaut, le débogueur considère les fonctions suivantes comme étant du code non-utilisateur dans les fenêtres de pile des appels :  
  
- Fonctions avec des informations sources supprimées dans leur fichier de symboles.  
  
- Fonctions où les fichiers de symboles indiquent qu'il n'existe pas de fichier source correspondant au frame de pile.  
  
- Fonctions spécifiées dans des fichiers `*.natjmc` du dossier `%VsInstallDirectory%\Common7\Packages\Debugger\Visualizers`.  
  
  **Exécution pas à pas**  
  
  Par défaut, seules les fonctions spécifiées dans des fichiers `*.natstepfilter` du dossier `%VsInstallDirectory%\Common7\Packages\Debugger\Visualizers` sont considérées comme du code non-utilisateur.  
  
  Vous pouvez créer vos propres fichiers `.natstepfilter` et `.natjmc` pour personnaliser le comportement de l'exécution pas à pas et de la fenêtre de pile des appels, et les placer dans le dossier `%USERPROFILE%\My Documents\Visual Studio 2015\Visualizers`.  
  
### <a name="stepping-behavior"></a><a name="BKMK_CPP_Stepping_behavior"></a>Comportement de marche  
 Lorsque vous **entrez dans** (clavier raccourci: F11) code non-utilisateur à partir du code utilisateur, le débbugger étapes sur le code à la ligne suivante de code utilisateur. Lorsque vous **sortez** (Clavier: Shift F11), le débbuggeur s’exécute à la ligne suivante de code utilisateur. Si aucun code utilisateur n'est rencontré, l'exécution se poursuit jusqu'à ce que l'application se termine, jusqu'à ce qu'un point d'arrêt soit atteint ou jusqu'à ce qu'une exception se produise.  
  
 Si le débogueur s'arrête dans du code non-utilisateur (par exemple si une commande Interrompre tout s'arrête dans du code non-utilisateur), l'exécution pas à pas continue dans le code non-utilisateur.  
  
### <a name="exception-behavior"></a><a name="BKMK_CPP_Exception_behavior"></a>Comportement d’exception  
 Quand le débogueur rencontre une exception, il s'arrête sur l'exception, qu'il s'agisse de code utilisateur ou de code non-utilisateur. Les options **non gérées par l’utilisateur** dans la boîte de dialogue **Exceptions** sont ignorées.  
  
### <a name="customize-stepping-behavior"></a><a name="BKMK_CPP_Customize_stepping_behavior"></a>Personnaliser le comportement de marche  
 Vous pouvez spécifier des fonctions que l'exécution pas à pas doit ignorer en les répertoriant comme étant du code non-utilisateur dans des fichiers `*.natstepfilter`.  
  
- Pour spécifier le code non utilisateur pour tous les utilisateurs de `%VsInstallDirectory%\Common7\Packages\Debugger\Visualizers` la machine Visual Studio, ajoutez le fichier .natstepfilter au dossier.  
  
- Pour spécifier le code non utilisateur pour un utilisateur `%USERPROFILE%\My Documents\Visual Studio 2015\Visualizers` individuel, ajoutez le fichier .natstepfilter au dossier.  
  
  .natstepfilter fichiers sont des fichiers xml avec cette syntaxe:  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<StepFilter xmlns="http://schemas.microsoft.com/vstudio/debugger/natstepfilter/2010">  
    <Function>  
        <Name>FunctionSpec</Name>  
        <Action>StepAction</Action>  
    </Function>  
    <Function>  
        <Name>FunctionSpec</Name>  
        <Module>ModuleSpec</Module>  
        <Action>StepAction</Action>  
    </Function>  
</StepFilter>  
  
```  
  
|Élément|Description|  
|-------------|-----------------|  
|Fonction|Obligatoire. Spécifie une ou plusieurs fonctions comme fonctions non-utilisateur.|  
|`Name`|Obligatoire. Une expression régulière mise en forme selon ECMA-262 spécifiant le nom complet de la fonction concernée. Par exemple :<br /><br /> `<Name>MyNS::MyClass.*</Name>`<br /><br /> indique au débogueur que toutes les méthodes de `MyNS::MyClass` doivent être considérées comme du code non-utilisateur. La recherche de correspondance respecte la casse.|  
|`Module`|facultatif. Une expression régulière mise en forme selon ECMA-262 spécifiant le chemin d'accès complet au module contenant la fonction. La recherche de correspondance ne respecte pas la casse.|  
|`Action`|Obligatoire. Une des valeurs suivantes (respectant la casse) :<br /><br /> -   `NoStepInto`- dit au débbuggeur de franchir la fonction assortie.<br />-   `StepInto`- dit au débbuggeur d’entrer dans les fonctions assorties, en dominant tout autre `NoStepInto` pour les fonctions assorties.|  
  
### <a name="customize-call-stack-behavior"></a><a name="BKMK_CPP_Customize_call_stack_behavior"></a>Personnaliser le comportement de pile d’appels  
 Vous pouvez spécifier des modules, des fichiers sources et des fonctions à traiter comme du code non-utilisateur dans les piles des appels en les spécifiant dans des fichiers `*.natjmc`.  
  
- Pour spécifier le code non utilisateur pour tous les utilisateurs de `%VsInstallDirectory%\Common7\Packages\Debugger\Visualizers` la machine Visual Studio, ajoutez le fichier .natjmc au dossier.  
  
- Pour spécifier le code non utilisateur pour un utilisateur `%USERPROFILE%\My Documents\Visual Studio 2015\Visualizers` individuel, ajoutez le fichier .natjmc au dossier.  
  
  .natjmc fichiers sont des fichiers xml avec cette syntaxe:  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<NonUserCode xmlns="http://schemas.microsoft.com/vstudio/debugger/jmc/2015">  
  
  <!-- Modules -->  
  <Module Name="ModuleSpec" />  
  <Module Name="ModuleSpec" Company="CompanyName" />  
  
  <!-- Files -->  
  <File Name="FileSpec"/>  
  
  <!-- Functions -->  
  <Function Name="FunctionSpec" />  
  <Function Name="FunctionSpec" Module ="ModuleSpec" />  
  <Function Name="FunctionSpec" Module ="ModuleSpec" ExceptionImplementation="true" />  
  
</NonUserCode>  
  
```  
  
 **Attributs des éléments Module**  
  
|Attribut|Description|  
|---------------|-----------------|  
|`Name`|Obligatoire. Chemin d’accès complet du ou des modules. Vous pouvez utiliser les caractères génériques Windows `?` (zéro ou un caractère) et `*` (zéro ou plusieurs caractères). Par exemple,<br /><br /> `<Module Name=”?:\3rdParty\UtilLibs\*” />`<br /><br /> indique au débogueur de traiter tous les modules de `\3rdParty\UtilLibs` sur n'importe quel lecteur comme du code externe.|  
|`Company`|facultatif. Le nom de la société qui publie le module incorporé dans le fichier exécutable. Vous pouvez utiliser cet attribut pour lever l'ambiguïté entre les modules.|  
  
 **Attributs des éléments File**  
  
|Attribut|Description|  
|---------------|-----------------|  
|`Name`|Obligatoire. Chemin d’accès complet du ou des fichiers sources à traiter comme du code externe. Vous pouvez utiliser les caractères génériques Windows `?` et `*` quand vous spécifiez le chemin d’accès.|  
  
 **Attributs des éléments Function**  
  
|Attribut|Description|  
|---------------|-----------------|  
|`Name`|Obligatoire. Le nom complet de la fonction à traiter comme du code externe.|  
|`Module`|facultatif. Le nom ou le chemin d'accès complet au module qui contient la fonction. Vous pouvez utiliser cet attribut pour lever l'ambiguïté entre des fonctions du même nom.|  
|`ExceptionImplementation`|Quand la valeur est définie sur `true`, la pile des appels affiche la fonction qui a levé l'exception, au lieu de cette fonction.|  
  
## <a name="javascript-just-my-code"></a><a name="BKMK_JavaScript_Just_My_Code"></a> Uniquement mon code JavaScript  
  
### <a name="user-and-non-user-code"></a><a name="BKMK_JS_User_and_non_user_code"></a>Code utilisateur et non utilisateur  
 **Classification du code**  
  
 Uniquement mon Code JavaScript contrôle l'exécution pas à pas et l'affichage de la pile des appels en catégorisant le code selon la classification suivante :  
  
|||  
|-|-|  
|**MyCode**|Code utilisateur dont vous êtes propriétaire et que vous contrôlez.|  
|**LibraryCode**|Code non-utilisateur provenant de bibliothèques que vous utilisez régulièrement et sur lequel votre application s'appuie pour fonctionner correctement (par exemple WinJS ou jQuery).|  
|**UnrelatedCode**|Code non utilisateur qui pourrait être en cours d’exécution dans votre application, mais vous ne possédez pas et votre application ne compte pas directement sur elle pour fonctionner correctement (par exemple, une publicité SDK qui affiche des annonces). Dans les projets du Windows Store, tout code chargé dans votre application à partir d'une URI HTTP ou HTTPS est également considéré comme du code UnrelatedCode.|  
  
 Le débogueur JavaScript classe automatiquement ces types de code :  
  
- Le script qui est exécuté en passant `eval` une chaîne à la fonction fournie par l’hôte est classé comme **MyCode**.  
  
- Le script qui est exécuté en `Function` passant une chaîne au constructeur est classé comme **LibraryCode**.  
  
- Le script contenu dans une référence-cadre, comme WinJS ou azure SDK, est classé comme **LibraryCode**.  
  
- Script qui est exécuté en passant `setTimeout` `setImmediate`une `setInterval` chaîne à la , ou les fonctions est classé comme **UnrelatedCode**.  
  
- Le fichier `%VSInstallDirectory%\JavaScript\JustMyCode\mycode.default.wwa.json` spécifie d'autres codes utilisateur et non-utilisateur pour tous les projets JavaScript Visual Studio.  
  
  Vous pouvez modifier les classifications par défaut et classer des fichiers et des URL spécifiques en ajoutant un fichier .json nommé `mycode.json` au dossier racine d’un projet.  
  
  Le reste du code est classé comme **MyCode**.  
  
### <a name="stepping-behavior"></a><a name="BKMK_JS_Stepping_behavior"></a>Comportement de marche  
  
- Si une fonction n’est pas l’utilisateur (**MyCode**) code, **Step Into** (clavier raccourci: F11) se comporte comme **Step Over** (Clavier: F10).  
  
- Si une étape commence dans le code non-utilisateur (**LibraryCode** ou **UnrelatedCode),** alors l’étape se comporte temporairement comme si Just My Code n’est pas activé. Dès que vous exécutez pas à pas à nouveau dans du code utilisateur, Uniquement mon Code est réactivé.  
  
- Quand une étape dans du code utilisateur aboutit à quitter le contexte d'exécution actuel (par exemple effectuer une étape dans la dernière ligne d'un gestionnaire d'événements), le débogueur s'arrête à la ligne de code utilisateur exécutée qui suit. Par exemple, si un rappel s’exécute dans le code **LibraryCode,** le débbuggeur se poursuit jusqu’à ce que la prochaine ligne de code utilisateur s’exécute.  
  
- **Step Out** (Clavier: Shift ' F11) s’arrête sur la ligne suivante du code utilisateur. Si aucun code utilisateur n'est rencontré, l'exécution se poursuit jusqu'à ce que l'application se termine, jusqu'à ce qu'un point d'arrêt soit atteint ou jusqu'à ce qu'une exception se produise.  
  
### <a name="breakpoint-behavior"></a><a name="BKMK_JS_Breakpoint_behavior"></a>Comportement de point de rupture  
  
- Les points d'arrêt qui ont été définis dans du code seront toujours atteints, quelle que soit la classification de ce code.  
  
- Si le mot clé `debugger` est rencontré dans :  
  
  - **LibraryCode** code, le débbuggeur se casse toujours.  

  - **Code code sans rapport,** le débbuggeur ne s’arrête pas.  
  
### <a name="exception-behavior"></a><a name="BKMK_JS_Exception_behavior"></a>Comportement d’exception  
 Si une exception non gérée se produit dans :  
  
- **Code MyCode** ou **LibraryCode,** le débbuggeur se casse toujours.  
  
- **Code Code sans rapport,** et le code **MyCode** ou **LibraryCode** est sur la pile d’appels, le débbugger se casse.  
  
  Si des exceptions de première chance sont activées pour l’exception sur la boîte de dialogue Exceptions, et que l’exception est projetée dans **LibraryCode** ou le code **UnrelatedCode** :  
  
- Si l'exception est gérée, le débogueur ne s'arrête pas.  
  
- Si l'exception n'est pas gérée, le débogueur s'arrête.  
  
### <a name="customize-just-my-code"></a><a name="BKMK_JS_Customize_Just_My_Code"></a>Personnaliser Just My Code  
 Pour classer par catégorie du code utilisateur et non-utilisateur pour un seul projet Visual Studio, ajoutez un fichier .json nommé `mycode.json` dans le dossier racine du projet.  
  
 Les classifications sont effectuées dans cet ordre :  
  
1. Classifications par défaut  
  
2. Classifications du fichier `%VSInstallDirectory%\JavaScript\JustMyCode\mycode.default.wwa.json`  
  
3. Classifications du fichier `mycode. json` du projet actuel  
  
   Chaque étape de classification remplace les étapes précédentes. Un fichier .json n’a pas besoin d’énumérer toutes les paires de valeurs clés, et le **MyCode**, **bibliothèques**, et les valeurs **indépendantes** peuvent être des tableaux vides.  
  
   Les fichiers .json My Code utilisent cette syntaxe :  
  
```json  
{  
    "Eval" : "Classification",  
    "Function" : "Classification",  
    "ScriptBlock" : "Classification",  
    "MyCode" : [  
        "UrlOrFileSpec”,  
        . . .  
        "UrlOrFileSpec”  
    ],  
    "Libraries" : [  
        "UrlOrFileSpec”,  
        . .  
        "UrlOrFileSpec”  
    ],  
    "Unrelated" : [  
        "UrlOrFileSpec”,  
        . . .  
        "UrlOrFileSpec”  
    ]  
}  
  
```  
  
 **Eval, Function et ScriptBlock**  
  
 Les paires de valeurs clés **Eval,** **Function**et **ScriptBlock** déterminent la classification dynamique du code.  
  
|||  
|-|-|  
|**Eval**|un script qui est exécuté en passant une chaîne à la fonction `eval` fournie par l'hôte. Par défaut, le script Eval est classifié comme **MyCode**.|  
|**Fonction**|un script qui est exécuté en passant une chaîne au constructeur `Function`. Par défaut, le script Function est classé comme **LibraryCode**.|  
|**ScriptBlock**|un script qui est exécuté en passant une chaîne aux fonctions `setTimeout`, `setImmediate` ou `setInterval`. Par défaut, le script ScriptBlock est classé comme **UnrelatedCode**.|  
  
 Vous pouvez changer la valeur en un de ces mots clés :  
  
- `MyCode`classe le script comme **MyCode**.  
  
- `Library`classe le script comme **LibraryCode**.  
  
- `Unrelated`classe le script comme **UnrelatedCode**.  
  
  **MyCode, Libraries et Unrelated**  
  
  Les paires de valeurs **clés MyCode**, **Bibliothèques**et **Unrelated** précisent les URLs ou les fichiers que vous souhaitez inclure dans une classification :  
  
|||  
|-|-|  
|**MyCode**|Une gamme d’URLs ou de fichiers qui sont classés comme **MyCode**.|  
|**Bibliothèques**|Une gamme d’URLs ou de fichiers qui sont classés comme **LibraryCode**.|  
|**Unrelated**|Une gamme d’URLs ou de fichiers qui sont classés comme **UnrelatedCode**.|  
  
 La chaîne d'URL ou de fichiers peut contenir un ou plusieurs caractères `*`, qui correspondent à zéro ou plusieurs caractères. `*` est l'équivalent de l'expression régulière `.*`.
