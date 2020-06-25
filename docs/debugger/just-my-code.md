---
title: Déboguer le code utilisateur avec Uniquement mon code | Microsoft Docs
ms.date: 02/13/2019
ms.topic: how-to
ms.assetid: 0f0df097-bbaf-46ad-9ad1-ef5f40435079
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 58e233be301630b00031bb90cd95fc78c2697c4e
ms.sourcegitcommit: c076fe12e459f0dbe2cd508e1294af14cb53119f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2020
ms.locfileid: "85348429"
---
# <a name="debug-only-user-code-with-just-my-code"></a>Déboguer uniquement le code utilisateur avec Uniquement mon code

*Uniquement mon code* est une fonctionnalité de débogage de Visual Studio qui parcourt automatiquement les appels au système, à l’infrastructure et à tout autre code non-utilisateur. Dans la fenêtre **pile des appels** , uniquement mon code réduit ces appels dans des frames **[code externe]** .

Uniquement mon code fonctionne différemment dans les projets .NET, C++ et JavaScript.

## <a name="enable-or-disable-just-my-code"></a><a name="BKMK_Enable_or_disable_Just_My_Code"></a> Activer ou désactiver Uniquement mon code

Pour la plupart des langages de programmation, Uniquement mon code est activé par défaut.

- Pour activer ou désactiver les uniquement mon code dans Visual Studio, sous Options des **Outils**  >  **Options** (ou options de **débogage**  >  **Options**) > **débogage**  >  **général**, sélectionnez ou désélectionnez **activer les uniquement mon code**.

![Activez Uniquement mon code dans la boîte de dialogue Options](../debugger/media/dbg_justmycode_options.png "Activer Uniquement mon code")

> [!NOTE]
> **Activer uniquement mon code** est un paramètre global qui s’applique à tous les projets Visual Studio dans tous les langages.

## <a name="just-my-code-debugging"></a>Uniquement mon code (débogage)

Pendant une session de débogage, la fenêtre **modules** affiche les modules de code que le débogueur traite comme mon code (code utilisateur), ainsi que leur état de chargement de symboles. Pour plus d’informations, consultez [se familiariser avec la façon dont le débogueur s’attache à votre application](../debugger/debugger-tips-and-tricks.md#modules_window).

![Code utilisateur dans la fenêtre Modules](../debugger/media/dbg_justmycode_module.png "Code utilisateur dans la fenêtre Modules")

Dans la fenêtre **pile des appels** ou **tâches** , uniquement mon code réduit le code non-utilisateur dans une trame de code annotée grisée intitulée `[External Code]` .

![Frame de code externe dans la fenêtre pile des appels](../debugger/media/dbg_justmycode_externalcode.png "Frame de code externe")

>[!TIP]
>Pour ouvrir les **modules**, **pile des appels**, **tâches**ou la plupart des autres fenêtres de débogage, vous devez être dans une session de débogage. Pendant le débogage, sous **Debug**  >  **fenêtres**de débogage, sélectionnez les fenêtres que vous souhaitez ouvrir.

<a name="BKMK_Override_call_stack_filtering"></a>Pour afficher le code dans un frame **[code externe]** réduit, cliquez avec le bouton droit dans **la pile des appels** ou la fenêtre de **tâche** , puis sélectionnez **afficher le code externe** dans le menu contextuel. Les lignes de code externe développées remplacent le frame **[code externe**].

![Afficher le code externe dans la fenêtre pile des appels](../debugger/media/dbg_justmycode_showexternalcode.png "Afficher le code externe")

> [!NOTE]
> **Afficher le code externe** est un paramètre actuel du profileur de l’utilisateur qui s’applique à tous les projets de tous les langages ouverts par l’utilisateur.

Le fait de double-cliquer sur une ligne de code externe développée dans la fenêtre **pile des appels** met en surbrillance la ligne de code appelante en vert dans le code source. Pour les dll ou d’autres modules introuvables ou chargés, une page symbole ou source introuvable peut s’ouvrir.

## <a name="net-just-my-code"></a><a name="BKMK__NET_Framework_Just_My_Code"></a>Uniquement mon code .NET

Dans les projets .NET, Uniquement mon code utilise des fichiers de symboles (*. pdb*) et des optimisations de programme pour classifier le code utilisateur et non-utilisateur. Le débogueur .NET prend en compte les fichiers binaires optimisés et les fichiers *. pdb* non chargés comme du code non-utilisateur.

Trois attributs du compilateur affectent également ce que le débogueur .NET considère comme étant du code utilisateur :

- <xref:System.Diagnostics.DebuggerNonUserCodeAttribute>indique au débogueur que le code auquel il est appliqué n’est pas du code utilisateur.
- <xref:System.Diagnostics.DebuggerHiddenAttribute> masque le code au débogueur, même si l'option Uniquement mon code est désactivée.
- <xref:System.Diagnostics.DebuggerStepThroughAttribute>indique au débogueur d’effectuer un pas à pas détaillé du code auquel il est appliqué, plutôt que d’effectuer un pas à pas détaillé dans le code.

Le débogueur .NET considère que tout autre code est du code utilisateur.

Lors du débogage .NET :

- **Débogage**  >  **Pas à pas** détaillé (ou **F11**) des étapes de code non-utilisateur sur le code à la ligne suivante du code utilisateur.
- **Débogage**  >  **Pas à pas sortant** (ou **MAJ** + **F11**) sur le code non-utilisateur s’exécute jusqu’à la ligne suivante du code utilisateur.

S’il n’y a plus de code utilisateur, le débogage continue jusqu’à ce qu’il se termine, atteint un autre point d’arrêt ou génère une erreur.

<a name="BKMK_NET_Breakpoint_behavior"></a>Si le débogueur s’arrête dans du code non-utilisateur (par exemple, vous utilisez l’instruction **Debug**  >  **break All** et la pause dans du code non-utilisateur), la fenêtre **aucune source** s’affiche. Vous pouvez ensuite utiliser une **Debug**  >  commande d'**étape** de débogage pour accéder à la ligne suivante du code utilisateur.

Si une exception non gérée se produit dans du code non-utilisateur, le débogueur s’arrête au niveau de la ligne de code utilisateur où l’exception a été générée.

Si les exceptions de première chance sont activées pour l’exception, la ligne de code utilisateur appelant est mise en surbrillance en vert dans le code source. La fenêtre **pile des appels** affiche le cadre annoté intitulé **[code externe]**.

## <a name="c-just-my-code"></a><a name="BKMK_C___Just_My_Code"></a> Uniquement mon code C++

À compter de Visual Studio 2017 version 15,8, Uniquement mon code pour le code pas à pas est également pris en charge. Cette fonctionnalité nécessite également l’utilisation du commutateur de compilateur [/JMC (uniquement mon code)](/cpp/build/reference/jmc) . Le commutateur est activé par défaut dans les projets C++. Pour la prise en charge de la fenêtre **pile des appels** et de la pile des appels dans uniquement mon code, le commutateur/JMC n’est pas requis.

<a name="BKMK_CPP_User_and_non_user_code"></a>Pour être classé comme code utilisateur, le fichier PDB pour le binaire contenant le code utilisateur doit être chargé par le débogueur (utilisez la fenêtre **modules** pour vérifier cela).

Pour le comportement de la pile des appels, par exemple dans la fenêtre **pile des appels** , uniquement mon code en C++ considère uniquement ces fonctions comme du *code non-utilisateur*:

- Fonctions avec des informations sources supprimées dans leur fichier de symboles.
- Fonctions où les fichiers de symboles indiquent qu'il n'existe pas de fichier source correspondant au frame de pile.
- Fonctions spécifiées dans les fichiers * \* .. natjmc* dans le dossier *%VsInstallDirectory%\Common7\Packages\Debugger\Visualizers* .

Pour le comportement d’exécution pas à pas du code, Uniquement mon code en C++ considère uniquement ces fonctions comme du *code non-utilisateur*:

- Fonctions pour lesquelles le fichier PDB correspondant n’a pas été chargé dans le débogueur.
- Fonctions spécifiées dans les fichiers * \* .. natjmc* dans le dossier *%VsInstallDirectory%\Common7\Packages\Debugger\Visualizers* .

> [!NOTE]
> Pour la prise en charge de l’exécution pas à pas du code dans Uniquement mon code, le code C++ doit être compilé à l’aide des compilateurs MSVC dans Visual Studio 15,8 Preview 3 ou version ultérieure, et le commutateur du compilateur/JMC doit être activé (il est activé par défaut). Pour plus d’informations, consultez [personnaliser la pile des appels C++ et le comportement](#BKMK_CPP_Customize_call_stack_behavior)de l’exécution du code) et ce billet de [blog](https://devblogs.microsoft.com/cppblog/announcing-jmc-stepping-in-visual-studio/). Pour le code compilé à l’aide d’un compilateur plus ancien, les fichiers *.. natstepfilter* sont le seul moyen de personnaliser l’exécution pas à pas du code, qui est indépendant de uniquement mon code. Consultez [personnaliser le comportement d’exécution pas à pas C++](#BKMK_CPP_Customize_stepping_behavior).

<a name="BKMK_CPP_Stepping_behavior"></a>Lors du débogage C++ :

- **Débogage**  >  **Pas à pas** détaillé (ou **F11**) des étapes de code non-utilisateur sur le code à la ligne suivante du code utilisateur.
- **Débogage**  >  **Pas à pas sortant** (ou **MAJ** + **F11**) sur le code non-utilisateur s’exécute jusqu’à la ligne suivante du code utilisateur.

S’il n’y a plus de code utilisateur, le débogage continue jusqu’à ce qu’il se termine, atteint un autre point d’arrêt ou génère une erreur.

Si le débogueur s’arrête dans du code non-utilisateur (par exemple, vous utilisez l’instruction **Debug**  >  **break All** et la pause dans du code non-utilisateur), l’exécution pas à pas continue dans le code non-utilisateur.

Si le débogueur rencontre une exception, il s’arrête sur l’exception, qu’il soit en code utilisateur ou non-utilisateur. Les options **non gérées** par l’utilisateur dans la boîte de dialogue **paramètres d’exception** sont ignorées.

### <a name="customize-c-call-stack-and-code-stepping-behavior"></a><a name="BKMK_CPP_Customize_call_stack_behavior"></a>Personnaliser la pile des appels C++ et le comportement du code pas à pas

Pour les projets C++, vous pouvez spécifier les modules, les fichiers sources et les fonctions que la fenêtre **pile des appels** traite comme du code non-utilisateur en les spécifiant dans des fichiers * \* .. natjmc* . Cette personnalisation s’applique également au code pas à pas si vous utilisez le compilateur le plus récent (consultez [C++ uniquement mon code](#BKMK_CPP_User_and_non_user_code)).

- Pour spécifier du code non-utilisateur pour tous les utilisateurs de l’ordinateur Visual Studio, ajoutez le fichier *.. natjmc* au dossier *%VsInstallDirectory%\Common7\Packages\Debugger\Visualizers* .
- Pour spécifier du code non-utilisateur pour un utilisateur individuel, ajoutez le fichier *.. natjmc* au dossier *%UserProfile%\My documents \\<Visual Studio version \> \Visualizers* .

Un fichier *.. natjmc* est un fichier XML avec la syntaxe suivante :

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
|`Name`|Obligatoire. Chemin d’accès complet du ou des modules. Vous pouvez utiliser les caractères génériques Windows `?` (zéro ou un caractère) et `*` (zéro, un ou plusieurs caractères). Par exemple,<br /><br /> `<Module Name="?:\3rdParty\UtilLibs\*" />`<br /><br /> indique au débogueur de traiter tous les modules dans *\3rdParty\UtilLibs* sur n’importe quel lecteur comme du code externe.|
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

### <a name="customize-c-stepping-behavior-independent-of-just-my-code-settings"></a><a name="BKMK_CPP_Customize_stepping_behavior"></a>Personnaliser le comportement d’exécution pas à pas C++ indépendamment des paramètres de Uniquement mon code

Dans les projets C++, vous pouvez spécifier des fonctions pour effectuer un pas à pas principal en les répertoriant comme du code non-utilisateur dans des fichiers * \* .. natstepfilter* . Les fonctions répertoriées dans les fichiers * \* .. natstepfilter* ne dépendent pas des paramètres de uniquement mon code.

- Pour spécifier du code non-utilisateur pour tous les utilisateurs de Visual Studio locaux, ajoutez le fichier *.. natstepfilter* au dossier *%VsInstallDirectory%\Common7\Packages\Debugger\Visualizers* .
- Pour spécifier du code non-utilisateur pour un utilisateur individuel, ajoutez le fichier *.. natstepfilter* au dossier *%UserProfile%\My documents \\<Visual Studio version \> \Visualizers* .

Un fichier *.. natstepfilter* est un fichier XML avec la syntaxe suivante :

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
|`Function`|Obligatoire. Spécifie une ou plusieurs fonctions comme fonctions non-utilisateur.|
|`Name`|Obligatoire. Une expression régulière mise en forme selon ECMA-262 spécifiant le nom complet de la fonction concernée. Par exemple :<br /><br /> `<Name>MyNS::MyClass.*</Name>`<br /><br /> indique au débogueur que toutes les méthodes de `MyNS::MyClass` doivent être considérées comme du code non-utilisateur. La recherche de correspondance respecte la casse.|
|`Module`|facultatif. Une expression régulière mise en forme selon ECMA-262 spécifiant le chemin d'accès complet au module contenant la fonction. La recherche de correspondance ne respecte pas la casse.|
|`Action`|Obligatoire. Une des valeurs suivantes (respectant la casse) :<br /><br /> `NoStepInto`: indique au débogueur d’effectuer un pas à pas principal dans la fonction.<br /> `StepInto`: indique au débogueur d’effectuer un pas à pas détaillé dans la fonction, en substituant tout autre élément `NoStepInto` pour la fonction correspondante.|

## <a name="javascript-just-my-code"></a><a name="BKMK_JavaScript_Just_My_Code"></a> Uniquement mon code JavaScript

<a name="BKMK_JS_User_and_non_user_code"></a>JavaScript Uniquement mon code contrôle l’affichage pas à pas et la pile des appels en classant le code dans l’une de ces classifications :

|||
|-|-|
|**MyCode**|Code utilisateur dont vous êtes propriétaire et que vous contrôlez.|
|**LibraryCode**|Le code non-utilisateur des bibliothèques que vous utilisez régulièrement et votre application s’appuie sur pour fonctionner correctement (par exemple, WinJS ou jQuery).|
|**UnrelatedCode**|Code non-utilisateur dans votre application dont vous n’êtes pas propriétaire et votre application ne fonctionne pas correctement. Par exemple, un kit de développement logiciel (SDK) publicitaire qui affiche des publicités peut être UnrelatedCode. Dans les projets UWP, tout code qui est chargé dans votre application à partir d’un URI HTTP ou HTTPs est également considéré comme UnrelatedCode.|

Le débogueur JavaScript classe le code en tant qu’utilisateur ou non utilisateur dans cet ordre :

1. Classifications par défaut.
   - Le script exécuté en passant une chaîne à la fonction fournie par l’hôte `eval` est **MyCode**.
   - Le script exécuté en passant une chaîne au `Function` constructeur est **LibraryCode**.
   - Un script dans une référence d’infrastructure, tel que WinJS ou le kit de développement logiciel (SDK) Azure, est **LibraryCode**.
   - Le script exécuté en passant une chaîne aux `setTimeout` `setImmediate` fonctions, ou `setInterval` est **UnrelatedCode**.

2. Classifications spécifiées pour tous les projets Visual Studio JavaScript dans le fichier *% VSInstallDirectory% \JavaScript\JustMyCode\mycode.default.wwa.js* .

3. Classifications dans le *mycode.js* fichier du projet actif.

Chaque étape de classification remplace les étapes précédentes.

Le reste du code est classé comme **MyCode**.

Vous pouvez modifier les classifications par défaut et classer des fichiers et des URL spécifiques en tant que code utilisateur ou non utilisateur, en ajoutant un fichier *. JSON* nommé *mycode.jsdans* le dossier racine d’un projet JavaScript. Consultez [personnaliser les uniquement mon code JavaScript](#BKMK_JS_Customize_Just_My_Code).

<a name="BKMK_JS_Stepping_behavior"></a>Lors du débogage JavaScript :

- Si une fonction est du code non-utilisateur, le **débogage**  >  **pas à pas** détaillé (ou **F11**) se comporte de la même façon que le **débogage**  >  **pas à pas principal** (ou **F10**).
- Si une étape commence dans du code non-utilisateur (**LibraryCode** ou **UnrelatedCode**), l’exécution pas à pas se comporte temporairement comme si uniquement mon code n’est pas activé. Lorsque vous revenez au code utilisateur, Uniquement mon code pas à pas est réactivé.
- Quand une étape de code utilisateur se traduit par la sortie du contexte d’exécution actuel, le débogueur s’arrête à la ligne de code utilisateur exécutée suivante. Par exemple, si un rappel s’exécute dans du code **LibraryCode**, le débogueur continue jusqu’à ce que la ligne suivante du code utilisateur s’exécute.
- **Pas à pas sortant** (ou **MAJ** + **F11**) s’arrête à la ligne suivante du code utilisateur.

S’il n’y a plus de code utilisateur, le débogage continue jusqu’à ce qu’il se termine, atteint un autre point d’arrêt ou génère une erreur.

Les points d’arrêt définis dans le code sont toujours atteints, mais le code est classifié.

- Si le `debugger` mot clé se trouve dans **LibraryCode**, le débogueur s’arrête toujours.
- Si le `debugger` mot clé se trouve dans **UnrelatedCode**, le débogueur ne s’arrête pas.

<a name="BKMK_JS_Exception_behavior"></a>Si une exception non gérée se produit dans le code **MyCode** ou **LibraryCode** , le débogueur s’arrête toujours.

Si une exception non gérée se produit dans **UnrelatedCode**, et **MyCode** ou **LibraryCode** se trouve sur la pile des appels, le débogueur s’arrête.

Si les exceptions de première chance sont activées pour l’exception et que l’exception se produit dans **LibraryCode** ou **UnrelatedCode**:

- Si l’exception est gérée, le débogueur ne s’arrête pas.
- Si l'exception n'est pas gérée, le débogueur s'arrête.

### <a name="customize-javascript-just-my-code"></a><a name="BKMK_JS_Customize_Just_My_Code"></a>Personnaliser les Uniquement mon code JavaScript

Pour classer par catégorie le code utilisateur et non-utilisateur pour un seul projet JavaScript, vous pouvez ajouter un fichier *. JSON* nommé *mycode.jsdans* le dossier racine du projet.

Les spécifications de ce fichier remplacent les classifications par défaut et le *mycode.default.wwa.jssur* le fichier. Le *mycode.jssur* le fichier n’a pas besoin de répertorier toutes les paires clé/valeur. Les valeurs d' **MyCode**, de **bibliothèques**et non **liées** peuvent être des tableaux vides.

*Mycode.jssur* les fichiers, utilisez la syntaxe suivante :

```json
{
    "Eval" : "Classification",
    "Function" : "Classification",
    "ScriptBlock" : "Classification",
    "MyCode" : [
        "UrlOrFileSpec",
        . . .
        "UrlOrFileSpec"
    ],
    "Libraries" : [
        "UrlOrFileSpec",
        . .
        "UrlOrFileSpec"
    ],
    "Unrelated" : [
        "UrlOrFileSpec",
        . . .
        "UrlOrFileSpec"
    ]
}

```

**Eval, Function et ScriptBlock**

Les paires clé-valeur **Eval**, **Function** et **ScriptBlock** déterminent comment le code généré dynamiquement est classifié :

|||
|-|-|
|**Eval**|un script qui est exécuté en passant une chaîne à la fonction `eval` fournie par l'hôte. Par défaut, le script Eval est classifié comme **MyCode**.|
|**Fonction**|un script qui est exécuté en passant une chaîne au constructeur `Function`. Par défaut, le script Function est classé comme **LibraryCode**.|
|**ScriptBlock**|un script qui est exécuté en passant une chaîne aux fonctions `setTimeout`, `setImmediate` ou `setInterval`. Par défaut, le script ScriptBlock est classé comme **UnrelatedCode**.|

Vous pouvez changer la valeur en un de ces mots clés :

- `MyCode` classifie le script comme **MyCode**.
- `Library` classifie le script comme **LibraryCode**.
- `Unrelated` classifie le script comme **UnrelatedCode**.

**MyCode, Libraries et Unrelated**

Les paires clé-valeur **MyCode**, **Libraries** et **Unrelated** spécifient les URL ou les fichiers que vous voulez inclure dans une classification :

|||
|-|-|
|**MyCode**|Un tableau d’URL ou de fichiers qui sont classés comme **MyCode**.|
|**Bibliothèques**|Un tableau d’URL ou de fichiers qui sont classifiés comme **LibraryCode**.|
|**Unrelated**|Un tableau d’URL ou de fichiers qui sont classés comme **UnrelatedCode**.|

L’URL ou la chaîne de fichier peut avoir un ou plusieurs `*` caractères, qui correspondent à zéro ou plusieurs caractères. `*`est identique à l’expression régulière `.*` .
