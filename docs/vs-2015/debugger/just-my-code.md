---
title: Uniquement mon code | Microsoft Docs
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
ms.openlocfilehash: 62da3a36a34a2111bb139765268fbb0bef9b500d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85531922"
---
# <a name="just-my-code"></a>Uniquement mon code
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Les développeurs qui utilisent des langages du .NET Framework sont familiarisés avec la fonctionnalité du débogueur Uniquement mon code, qui avance pas à pas dans les appels du système, les appels de l'infrastructure et les appels non-utilisateurs, et réduit les appels dans les fenêtres Pile des appels. Uniquement mon code a été étendu aux langages C++ et JavaScript. Cette rubrique décrit les caractéristiques d'utilisation d'Uniquement mon code dans les projets .NET Framework, C++ natifs et JavaScript.  
  
## <a name="enable-or-disable-just-my-code"></a><a name="BKMK_Enable_or_disable_Just_My_Code"></a> Activer ou désactiver Uniquement mon code  
 Pour activer ou désactiver Uniquement mon code, choisissez **options et paramètres** dans le menu **Déboguer** . Dans le nœud **débogage**  /  **général** , sélectionnez ou désactivez **activer uniquement mon code**.  
  
 ![Activez Uniquement mon code dans la boîte de dialogue Options](../debugger/media/dbg-justmycode-options.png "DBG_JustMyCode_Options")  
  
> [!NOTE]
> Le paramètre **activer uniquement mon code** est un paramètre global qui est appliqué à tous les projets Visual Studio dans tous les langages.  
  
### <a name="override-call-stack-filtering"></a><a name="BKMK_Override_call_stack_filtering"></a> Remplacer le filtrage de pile des appels  
 Dans les affichages de la pile des appels, comme les fenêtres Pile des appels et Tâches, Uniquement mon code réduit le code non-utilisateur en un cadre annoté intitulé `[External Code]`. Pour afficher les frames réduits, choisissez **afficher le code externe** dans le menu contextuel de l’affichage de la pile des appels.  
  
> [!NOTE]
> Le paramètre **afficher le code externe** est enregistré dans le profileur de l’utilisateur actuel. Il est appliqué à tous les projets dans tous les langages qui sont ouverts par l'utilisateur.  
  
## <a name="net-framework-just-my-code"></a><a name="BKMK__NET_Framework_Just_My_Code"></a> .NET Framework Uniquement mon code  
  
### <a name="user-and-non-user-code"></a><a name="BKMK_NET_User_and_non_user_code"></a> Code utilisateur et non-utilisateur  
 Pour distinguer le code utilisateur du code non-utilisateur, Uniquement mon code examine les fichiers de symboles (. pdb) et les optimisations de programme. Le débogueur considère le code comme du code non-utilisateur quand le fichier binaire est optimisé ou quand le fichier .pdb n'est pas disponible.  
  
 Trois attributs affectent également ce que le débogueur considère comme étant du code MyCode :  
  
- <xref:System.Diagnostics.DebuggerNonUserCodeAttribute> indique au débogueur que le code auquel il est appliqué n'est pas du code MyCode.  
  
- <xref:System.Diagnostics.DebuggerHiddenAttribute> masque le code au débogueur, même si l'option Uniquement mon code est désactivée.  
  
- <xref:System.Diagnostics.DebuggerStepThroughAttribute> indique au débogueur de passer pas à pas dans le code auquel il s'applique, plutôt que d'effectuer un pas à pas détaillé du code.  
  
  Tout le reste du code est considéré comme du code utilisateur.  
  
### <a name="stepping-behavior"></a><a name="BKMK_NET_Stepping_behavior"></a> Comportement pas à pas  
 Quand vous **exécutez un pas à pas** détaillé (raccourci clavier : F11) du code non-utilisateur, le débogueur parcourt le code jusqu’à l’instruction utilisateur suivante. Quand vous **exécutez un pas à pas sortant** (clavier : Maj + F11), le débogueur s’exécute jusqu’à la ligne suivante du code utilisateur. Si aucun code utilisateur n'est rencontré, l'exécution se poursuit jusqu'à ce que l'application se termine, jusqu'à ce qu'un point d'arrêt soit atteint ou jusqu'à ce qu'une exception se produise.  
  
### <a name="breakpoint-behavior"></a><a name="BKMK_NET_Breakpoint_behavior"></a> Comportement du point d’arrêt  
 Lorsque Uniquement mon code est activé, vous pouvez choisir arrêter **tout** (raccourci clavier : Ctrl + Alt + Attn) et arrêter l’exécution à un emplacement où il n’y a aucun code utilisateur à afficher. Dans ce cas, la fenêtre Pas de code source s'affiche. Si vous choisissez ensuite une commande d'étape, le débogueur vous amène à la ligne de code utilisateur suivante.  
  
### <a name="exception-behavior"></a><a name="BKMK_NET_Exception_behavior"></a> Comportement de l’exception  
 Si une exception non gérée se produit dans du code non-utilisateur, le débogueur s'arrête à la ligne de code utilisateur où lequel l'exception a été générée.  
  
 Si les exceptions de première chance sont activées pour l'exception, la ligne de code utilisateur est mise en surbrillance en vert. La pile des appels affiche un frame annoté intitulé **[code externe]**.  
  
## <a name="c-just-my-code"></a><a name="BKMK_C___Just_My_Code"></a> Uniquement mon code C++  
  
### <a name="user-and-non-user-code"></a><a name="BKMK_CPP_User_and_non_user_code"></a> Code utilisateur et non-utilisateur  
 Uniquement mon Code C++ est différent d'Uniquement mon code .NET Framework et JavaScript, car le comportement d'exécution pas à pas est indépendant du comportement de la pile des appels.  
  
 **Piles des appels**  
  
 Par défaut, le débogueur considère les fonctions suivantes comme étant du code non-utilisateur dans les fenêtres de pile des appels :  
  
- Fonctions avec des informations sources supprimées dans leur fichier de symboles.  
  
- Fonctions où les fichiers de symboles indiquent qu'il n'existe pas de fichier source correspondant au frame de pile.  
  
- Fonctions spécifiées dans des fichiers `*.natjmc` du dossier `%VsInstallDirectory%\Common7\Packages\Debugger\Visualizers`.  
  
  **Exécution pas à pas**  
  
  Par défaut, seules les fonctions spécifiées dans des fichiers `*.natstepfilter` du dossier `%VsInstallDirectory%\Common7\Packages\Debugger\Visualizers` sont considérées comme du code non-utilisateur.  
  
  Vous pouvez créer vos propres fichiers `.natstepfilter` et `.natjmc` pour personnaliser le comportement de l'exécution pas à pas et de la fenêtre de pile des appels, et les placer dans le dossier `%USERPROFILE%\My Documents\Visual Studio 2015\Visualizers`.  
  
### <a name="stepping-behavior"></a><a name="BKMK_CPP_Stepping_behavior"></a> Comportement pas à pas  
 Quand vous **exécutez un pas à pas** détaillé (raccourci clavier : F11) du code non-utilisateur à partir du code utilisateur, le débogueur parcourt le code jusqu’à la ligne suivante du code utilisateur. Quand vous **exécutez un pas à pas sortant** (clavier : Maj + F11), le débogueur s’exécute jusqu’à la ligne suivante du code utilisateur. Si aucun code utilisateur n'est rencontré, l'exécution se poursuit jusqu'à ce que l'application se termine, jusqu'à ce qu'un point d'arrêt soit atteint ou jusqu'à ce qu'une exception se produise.  
  
 Si le débogueur s'arrête dans du code non-utilisateur (par exemple si une commande Interrompre tout s'arrête dans du code non-utilisateur), l'exécution pas à pas continue dans le code non-utilisateur.  
  
### <a name="exception-behavior"></a><a name="BKMK_CPP_Exception_behavior"></a> Comportement de l’exception  
 Quand le débogueur rencontre une exception, il s'arrête sur l'exception, qu'il s'agisse de code utilisateur ou de code non-utilisateur. Les options **non gérées** par l’utilisateur dans la boîte de dialogue **exceptions** sont ignorées.  
  
### <a name="customize-stepping-behavior"></a><a name="BKMK_CPP_Customize_stepping_behavior"></a> Personnaliser le comportement d’exécution pas à pas  
 Vous pouvez spécifier des fonctions que l'exécution pas à pas doit ignorer en les répertoriant comme étant du code non-utilisateur dans des fichiers `*.natstepfilter`.  
  
- Pour spécifier du code non-utilisateur pour tous les utilisateurs de l’ordinateur Visual Studio, ajoutez le fichier.. natstepfilter au `%VsInstallDirectory%\Common7\Packages\Debugger\Visualizers` dossier.  
  
- Pour spécifier du code non-utilisateur pour un utilisateur individuel, ajoutez le fichier.. natstepfilter au `%USERPROFILE%\My Documents\Visual Studio 2015\Visualizers` dossier.  
  
  les fichiers.. natstepfilter sont des fichiers XML avec la syntaxe suivante :  
  
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
|`Action`|Obligatoire. Une des valeurs suivantes (respectant la casse) :<br /><br /> -   `NoStepInto`  : indique au débogueur d’effectuer un pas à pas principal dans la fonction correspondante.<br />-   `StepInto`  : indique au débogueur d’effectuer un pas à pas détaillé dans les fonctions correspondantes, en substituant tout autre élément `NoStepInto` pour les fonctions correspondantes.|  
  
### <a name="customize-call-stack-behavior"></a><a name="BKMK_CPP_Customize_call_stack_behavior"></a> Personnaliser le comportement de la pile des appels  
 Vous pouvez spécifier des modules, des fichiers sources et des fonctions à traiter comme du code non-utilisateur dans les piles des appels en les spécifiant dans des fichiers `*.natjmc`.  
  
- Pour spécifier du code non-utilisateur pour tous les utilisateurs de l’ordinateur Visual Studio, ajoutez le fichier.. natjmc au `%VsInstallDirectory%\Common7\Packages\Debugger\Visualizers` dossier.  
  
- Pour spécifier du code non-utilisateur pour un utilisateur individuel, ajoutez le fichier.. natjmc au `%USERPROFILE%\My Documents\Visual Studio 2015\Visualizers` dossier.  
  
  les fichiers.. natjmc sont des fichiers XML avec la syntaxe suivante :  
  
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
  
### <a name="user-and-non-user-code"></a><a name="BKMK_JS_User_and_non_user_code"></a> Code utilisateur et non-utilisateur  
 **Classification du code**  
  
 Uniquement mon Code JavaScript contrôle l'exécution pas à pas et l'affichage de la pile des appels en catégorisant le code selon la classification suivante :  
  
|Nom|Description|
|-|-|  
|**MyCode**|Code utilisateur dont vous êtes propriétaire et que vous contrôlez.|  
|**LibraryCode**|Code non-utilisateur provenant de bibliothèques que vous utilisez régulièrement et sur lequel votre application s'appuie pour fonctionner correctement (par exemple WinJS ou jQuery).|  
|**UnrelatedCode**|Code non-utilisateur qui peut être en cours d’exécution dans votre application, mais que vous ne possédez pas et que votre application ne s’appuie pas directement dessus pour fonctionner correctement (par exemple, un kit de développement logiciel (SDK) publicitaire qui affiche des publicités). Dans les projets du Windows Store, tout code chargé dans votre application à partir d'une URI HTTP ou HTTPS est également considéré comme du code UnrelatedCode.|  
  
 Le débogueur JavaScript classe automatiquement ces types de code :  
  
- Le script qui est exécuté en passant une chaîne à la fonction fournie par l’hôte `eval` est classé comme **MyCode**.  
  
- Le script qui est exécuté en passant une chaîne au `Function` constructeur est classé en tant que **LibraryCode**.  
  
- Le script contenu dans une référence d’infrastructure, tel que WinJS ou le kit de développement logiciel (SDK) Azure, est classé en tant que **LibraryCode**.  
  
- Le script qui est exécuté en passant une chaîne aux `setTimeout` `setImmediate` fonctions, ou `setInterval` est classé comme **UnrelatedCode**.  
  
- Le fichier `%VSInstallDirectory%\JavaScript\JustMyCode\mycode.default.wwa.json` spécifie d'autres codes utilisateur et non-utilisateur pour tous les projets JavaScript Visual Studio.  
  
  Vous pouvez modifier les classifications par défaut et classer des fichiers et des URL spécifiques en ajoutant un fichier .json nommé `mycode.json` au dossier racine d’un projet.  
  
  Le reste du code est classé comme **MyCode**.  
  
### <a name="stepping-behavior"></a><a name="BKMK_JS_Stepping_behavior"></a> Comportement pas à pas  
  
- Si une fonction n’est pas un code utilisateur (**MyCode**), **pas à pas** détaillé (raccourci clavier : F11) se comporte comme **pas à pas principal** (clavier : F10).  
  
- Si une étape commence dans du code non-utilisateur (**LibraryCode** ou **UnrelatedCode**), l’exécution pas à pas se comporte temporairement comme si uniquement mon code n’était pas activé. Dès que vous exécutez pas à pas à nouveau dans du code utilisateur, Uniquement mon Code est réactivé.  
  
- Quand une étape dans du code utilisateur aboutit à quitter le contexte d'exécution actuel (par exemple effectuer une étape dans la dernière ligne d'un gestionnaire d'événements), le débogueur s'arrête à la ligne de code utilisateur exécutée qui suit. Par exemple, si un rappel s’exécute dans du code **LibraryCode** , le débogueur continue jusqu’à ce que la ligne suivante du code utilisateur s’exécute.  
  
- **Pas à pas sortant** (clavier : Maj + F11) s’arrête à la ligne suivante du code utilisateur. Si aucun code utilisateur n'est rencontré, l'exécution se poursuit jusqu'à ce que l'application se termine, jusqu'à ce qu'un point d'arrêt soit atteint ou jusqu'à ce qu'une exception se produise.  
  
### <a name="breakpoint-behavior"></a><a name="BKMK_JS_Breakpoint_behavior"></a> Comportement du point d’arrêt  
  
- Les points d'arrêt qui ont été définis dans du code seront toujours atteints, quelle que soit la classification de ce code.  
  
- Si le mot clé `debugger` est rencontré dans :  
  
  - Code **LibraryCode** , le débogueur s’arrête toujours.  

  - Code **UnrelatedCode** , le débogueur ne fonctionne pas.  
  
### <a name="exception-behavior"></a><a name="BKMK_JS_Exception_behavior"></a> Comportement de l’exception  
 Si une exception non gérée se produit dans :  
  
- Le code **MyCode** ou **LibraryCode** , le débogueur s’arrête toujours.  
  
- Le code **UnrelatedCode** et le code **MyCode** ou **LibraryCode** se trouvent dans la pile des appels, le débogueur s’arrête.  
  
  Si les exceptions de première chance sont activées pour l’exception dans la boîte de dialogue exceptions, et si l’exception est levée dans le code **LibraryCode** ou **UnrelatedCode** :  
  
- Si l'exception est gérée, le débogueur ne s'arrête pas.  
  
- Si l'exception n'est pas gérée, le débogueur s'arrête.  
  
### <a name="customize-just-my-code"></a><a name="BKMK_JS_Customize_Just_My_Code"></a> Personnaliser Uniquement mon code  
 Pour classer par catégorie du code utilisateur et non-utilisateur pour un seul projet Visual Studio, ajoutez un fichier .json nommé `mycode.json` dans le dossier racine du projet.  
  
 Les classifications sont effectuées dans cet ordre :  
  
1. Classifications par défaut  
  
2. Classifications du fichier `%VSInstallDirectory%\JavaScript\JustMyCode\mycode.default.wwa.json`  
  
3. Classifications du fichier `mycode. json` du projet actuel  
  
   Chaque étape de classification remplace les étapes précédentes. Un fichier. JSON n’a pas besoin de répertorier toutes les paires clé/valeur, et les ensembles d’éléments de liste ( **MyCode**), les **bibliothèques**et les valeurs non **liées** peuvent être des tableaux vides.  
  
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
  
 Les paires clé-valeur **eval**, **Function**et **scriptblock** déterminent le mode de classement du code généré dynamiquement.  
  
|Nom|Description|
|-|-|  
|**Évaluation**|un script qui est exécuté en passant une chaîne à la fonction `eval` fournie par l'hôte. Par défaut, le script Eval est classifié comme **MyCode**.|  
|**Fonction**|un script qui est exécuté en passant une chaîne au constructeur `Function`. Par défaut, le script Function est classé comme **LibraryCode**.|  
|**ScriptBlock**|un script qui est exécuté en passant une chaîne aux fonctions `setTimeout`, `setImmediate` ou `setInterval`. Par défaut, le script ScriptBlock est classé comme **UnrelatedCode**.|  
  
 Vous pouvez changer la valeur en un de ces mots clés :  
  
- `MyCode`  classe le script comme **MyCode**.  
  
- `Library`  classe le script comme **LibraryCode**.  
  
- `Unrelated`  classe le script comme **UnrelatedCode**.  
  
  **MyCode, Libraries et Unrelated**  
  
  Les paires de valeurs de clés d' **MyCode**, de **bibliothèques**et non **liées** spécifient les URL ou les fichiers à inclure dans une classification :  
  
|Nom|Description|
|-|-|  
|**MyCode**|Tableau d’URL ou de fichiers qui sont classés comme **MyCode**.|  
|**Bibliothèques**|Tableau d’URL ou de fichiers qui sont classés en tant que **LibraryCode**.|  
|**Unrelated**|Tableau d’URL ou de fichiers qui sont classés en tant que **UnrelatedCode**.|  
  
 La chaîne d'URL ou de fichiers peut contenir un ou plusieurs caractères `*`, qui correspondent à zéro ou plusieurs caractères. `*` est l'équivalent de l'expression régulière `.*`.
