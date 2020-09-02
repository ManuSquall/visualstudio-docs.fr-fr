---
title: JavaScript IntelliSense | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- IntelliSense [JavaScript]
- <reference> JavaScript XML tag
- JavaScript Code Editor
- XML code comments, JavaScript IntelliSense
- reference JavaScript XML tag
- JavaScript, IntelliSense
- code comments, JavaScript IntelliSense
- JavaScript, reference groups
- JavaScript Editor
- reference directives [JavaScript]
- JavaScript, XML documentation comments
- reference groups [JavaScript]
- JavaScript, reference directives
- IntelliSense [JavaScript], about
- IntelliSense extensibility [JavaScript]
- XML documentation comments [JavaScript]
ms.assetid: af1a3171-c9d8-45a3-9c96-a763e3b163ef
caps.latest.revision: 67
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 962c724e231275c9fa716d6c823b7451292392cf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75848385"
---
# <a name="javascript-intellisense"></a>IntelliSense JavaScript
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

IntelliSense vous aide à écrire du code plus vite et avec moins d'erreurs en fournissant des informations pendant l'écriture du code. Lorsque vous travaillez avec un script client dans l'éditeur JavaScript, IntelliSense répertorie les objets, les fonctions, les propriétés et les paramètres qui sont disponibles en fonction de votre contexte actuel. Vous pouvez sélectionner une option de programmation dans la liste contextuelle fournie par IntelliSense pour compléter le code.

 IntelliSense simplifie la réalisation des tâches suivantes :

- Recherche d'informations sur les membres.

- Insertion d'éléments de langage directement dans le code.

- Conservation du contexte sans quitter l'éditeur de code.

- Prise en charge de la fonction IntelliSense personnalisée avec les commentaires de documentation XML et l'extensibilité JavaScript IntelliSense.

  Cette rubrique contient les sections suivantes :

- [Détermination du contexte IntelliSense](#DeterminingIntelliSenseContext)

- [Traitement des informations IntelliSense](#ProcessingIntelliSenseInformation)

- [Fonctionnalités JavaScript IntelliSense](#Features)

- [Extensibilité JavaScript IntelliSense](#Extensibility)

- [Validation JavaScript](#Validation)

  Pour plus d'informations sur les fonctionnalités IntelliSense de [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)], consultez [Utilisation des fonctionnalités IntelliSense](../ide/using-intellisense.md).

## <a name="determining-intellisense-context"></a><a name="DeterminingIntelliSenseContext"></a> Détermination du contexte IntelliSense
 JavaScript IntelliSense fournit des choix de programmation qui s'appuient sur l'ensemble du script et qui correspondent à votre contexte de script actuel. Cela inclut des éléments de script dans le fichier courant. Cela comprend également tout code référencé directement ou indirectement depuis votre script, comme les références de fichier de script, les références de script d'assembly, les références de service et les références associées aux pages.

 Votre contexte de script actuel est créé sur la base des éléments suivants :

- Fonctions définies dans tous les blocs de script du document actif. Les blocs de script inline sont pris en charge dans les fichiers qui ont les extensions .aspx., .ascx, .master, .html, et .htm.

- Éléments `script` comportant des attributs `src` qui pointent sur un autre fichier de script. Le fichier de script cible doit avoir l'extension de nom de fichier .js.

- Fichiers JavaScript qui référencent d'autres fichiers JavaScript à l'aide d'une directive `reference`.

- Groupes de référence pour objets globaux, extensions IntelliSense ou fichiers de script chargés en différé.

- Références aux services Web XML.

- Contrôles <xref:System.Web.UI.ScriptManager> et <xref:System.Web.UI.ScriptManagerProxy>, si l'application Web est une application ASP.NET AJAX.

- [!INCLUDE[atlaslib_current_ext](../includes/atlaslib-current-ext-md.md)], si vous travaillez dans une application Web ASP.NET compatible AJAX.

    > [!NOTE]
    > IntelliSense n'est pas pris en charge pour le script qui se trouve dans les attributs de gestionnaire d'événements sur les éléments HTML, ou qui est défini dans les attributs `href`.

## <a name="processing-intellisense-information"></a><a name="ProcessingIntelliSenseInformation"></a> Traitement des informations IntelliSense
 Pour fournir JavaScript IntelliSense, le service de langage effectue les opérations suivantes :

- Crée une liste de fichiers JavaScript dépendants basés sur les références contenues dans le document actif et sur l'examen récursif des références de script dans les fichiers référencés.

- Parcourt la liste et collecte des informations de type et d'autres données pertinentes à partir de chaque fichier.

- Regroupe les données et les transmet à JavaScript Language Service, qui met les informations de type et les données à la disposition d’IntelliSense.

- Surveille les fichiers pour les modifications qui peuvent affecter la liste IntelliSense et met à jour la liste si nécessaire. Les scripts sur les magasins distants (tels que ceux référencés à l'aide du protocole HTTP) ne sont pas analysés.

## <a name="javascript-intellisense-features"></a><a name="Features"></a>Fonctionnalités de JavaScript IntelliSense
 JavaScript IntelliSense prend en charge les objets suivants :

- [Éléments DOM (Document Object Model)](#HTMLDom)

- [Objets intrinsèques](#IntrinsicObjects)

- [Variables, fonctions et objets définis par l’utilisateur](#UserDefined)

- Objets définis dans des fichiers externes à l'aide de références telles que des [références de script](#Script), des [directives de référence](#ReferenceDirectives) et des [groupes de référence](#ReferenceGroups).

- Objets définis dans des fichiers distants téléchargés par Visual Studio.

- Objets spécifiés dans des [commentaires de documentation XML](#XMLDocComments), tels que des paramètres et des champs.

- Objets décrits à l’aide d’étiquettes de commentaires JavaScript standard (//). Pour plus d'informations, consultez [Extension de JavaScript IntelliSense](../ide/extending-javascript-intellisense.md).

- Objets pris en charge à l'aide du mécanisme [Extensibilité JavaScript IntelliSense](#Extensibility). Pour plus d'informations, consultez [Extension de JavaScript IntelliSense](../ide/extending-javascript-intellisense.md).

- [Objets ASP.NET AJAX](#ASPNet)

  Si IntelliSense ne parvient pas à déterminer le type d'un objet, il fournit des options pour compléter automatiquement les instructions à l'aide d'identificateurs dans le document actif. Pour plus d'informations, consultez [Saisie semi-automatique des instructions pour les identificateurs](../ide/statement-completion-for-identifiers.md).

### <a name="html-dom-elements"></a><a name="HTMLDom"></a> Éléments DOM HTML
 JavaScript IntelliSense fournit des références de programmation pour les éléments DOM DHTML (Dynamic HTML), tels que `body`, `form` et `div`. Seuls les éléments inclus dans le document actuel et la page maître sont affichés par IntelliSense. JavaScript IntelliSense prend en charge également les objets `window` et `document`, ainsi que leurs membres.

### <a name="intrinsic-objects"></a><a name="IntrinsicObjects"></a> Objets intrinsèques
 JavaScript IntelliSense fournit des références de programmation pour les objets intrinsèques tels que `Array`, `String`, `Math`, `Date` et `Number`. Pour plus d'informations sur les objets intrinsèques, consultez [Objets intégrés standard](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects).

### <a name="user-defined-variables-functions-and-objects"></a><a name="UserDefined"></a> Variables, fonctions et objets définis par l’utilisateur
 Lorsque vous modifiez un fichier JavaScript, [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] analyse les documents ouverts et référencés pour déterminer toutes les ressources de code disponibles. Ceci inclut les variables, fonctions et objets que vous avez créés. Ces ressources sont ensuite disponibles pour JavaScript IntelliSense.

 Pour plus d'informations sur les variables, fonctions et objets définis par l'utilisateur, consultez [Création de vos propres objets](https://msdn.microsoft.com/library/202863ha.aspx) sur le site web MSDN.

### <a name="external-file-references"></a><a name="External"></a>Références de fichiers externes
 Vous pouvez inclure divers types de références de fichiers externes pour mettre en place la prise en charge d'IntelliSense dans votre code. Les références de fichiers externes peuvent être des références de script ou des directives de référence, ou elles peuvent être spécifiées à l'aide de groupes de référence.

#### <a name="script-references"></a><a name="Script"></a>Références de script
 Au lieu d'écrire tout le script client dans une page, vous pouvez référencer des fichiers externes qui incluent le code de script. Cela vous simplifie la réutilisation du code entre les pages et permet la mise en cache du script client par le navigateur.

 Si vous ne travaillez pas avec une page Web compatible ASP.NET AJAX, vous pouvez référencer un fichier de script externe en utilisant l'attribut `src` dans la balise d'ouverture d'un élément `script`. L'attribut `src` spécifie l'URL pour un fichier externe qui contient le code source ou les données.

 L’exemple suivant montre un balisage utilisant l’attribut `src` dans une étiquette <`script`> pour référencer un fichier de script.

```html
<script type="text/javascript" src="~/Scripts/JavaScript.js">

</script>
```

 Si vous travaillez avec une page Web compatible ASP.NET AJAX, vous pouvez référencer des fichiers de script à l'aide de l'objet <xref:System.Web.UI.ScriptReference> du contrôle <xref:System.Web.UI.ScriptManager>.

 L'exemple suivant montre un balisage qui utilise un objet <xref:System.Web.UI.ScriptReference> dans un contrôle <xref:System.Web.UI.ScriptManager> pour référencer un fichier de script.

```html
<asp:ScriptManager ID="ScriptManager1" runat="server">
  <Scripts>
    <asp:ScriptReference Path="~/Scripts/JavaScript.js" />
  </Scripts>
</asp:ScriptManager>
```

 IntelliSense prend également en charge des fichiers de script qui sont incorporés comme ressources dans un assembly des applications Web ASP.NET AJAX. Pour plus d'informations sur les ressources de script incorporées, consultez [Procédure pas à pas : Incorporation d'un fichier JavaScript en tant que ressource dans un assembly](https://msdn.microsoft.com/library/d8cb78cd-95a9-4dc6-92df-391866817e89).

#### <a name="reference-directives"></a><a name="ReferenceDirectives"></a>Directives de référence
 Une directive `reference` permet à [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] d'établir une relation entre le script vous modifiez actuellement et d'autres scripts. La directive `reference` vous permet d'inclure un fichier de script dans le contexte de script du fichier de script actuel. Cela permet à IntelliSense de référencer des fonctions définies extérieurement, des types et des champs lors de l'écriture de code.

 Vous créez une directive `reference` dans le formulaire d'un commentaire XML. La directive doit être déclarée dans le fichier avant tout script. Une directive `reference` peut inclure une référence de script sur disque, une référence de script basée sur un assembly, une référence de script basée sur un service ou une référence de script basée sur une page.

 L'exemple suivant montre des exemples d'utilisation de directives de référence basées sur disque. Dans le premier exemple, le service de langage recherche le fichier dans le dossier qui contient le fichier projet (par exemple, .jsproj).

 `/// <reference path="ScriptFile1.js" />`

 `/// <reference path="Scripts/ScriptFile2.js" />`

 `/// <reference path="../ScriptFile3.js" />`

 `/// <reference path="~/Scripts/ScriptFile4.js" />`

 L'exemple suivant indique comment créer une référence à un script basé sur un assembly.

 `/// <reference name "Ajax.js" assembly="System.Web.Extensions, ..." />`

 L'exemple suivant indique comment référencer un script basé sur un service :

 `/// <reference path="MyService.asmx" />`

 `/// <reference path="Services/MyService.asmx" />`

 `/// <reference path="../MyService.asmx" />`

 `/// <reference path="~/Services/MyService.asmx" />`

> [!NOTE]
> JavaScript IntelliSense n'est pas pris en charge pour le script contenu dans les fichiers de service Web (.asmx) dans WAP (Web Application Projects).

 L'exemple suivant indique comment référencer un script basé sur une page.

 `/// <reference path="Default.aspx" />`

 `/// <reference path="Admin/Default.aspx" />`

 `/// <reference path="../Default.aspx" />`

 `/// <reference path="~/Admin/Default.aspx" />`

 Les règles suivantes s'appliquent à une directive `reference`.

- Le commentaire XML `reference` doit être déclaré avant tout script.

- Vous devez utiliser la syntaxe des commentaires XML avec trois barres obliques. Les références effectuées en utilisant la syntaxe de commentaire standard (deux barres obliques) sont ignorées.

- Un seul fichier ou ressource peut être spécifié(e) par directive.

- Les références multiples aux scripts basés sur des pages ne sont pas autorisées.

- Si une référence de page est spécifiée, aucun autre type de directives de référence n'est autorisé.

- Les noms de fichiers utilisent des chemins d'accès relatifs. Vous pouvez utiliser l'opérateur tilde (`~`) pour indiquer des chemins d'accès relatifs au niveau de la racine de l'application.

- Les chemins d'accès absolus sont ignorés.

- Les directives de référence dans les pages référencées ne sont pas traitées ; autrement dit, les directives de référence ne sont pas résolues de manière récursive pour les pages. Seul le script qui est référencé directement par la page est inclus.

#### <a name="reference-groups"></a><a name="ReferenceGroups"></a>Groupes de référence
 Vous pouvez utiliser les groupes de référence prédéfinis pour spécifier que des fichiers .js IntelliSense particuliers figurent dans la portée de différents projets JavaScript. Les types de groupe de référence suivants sont disponibles :

- Implicite (Windows) pour les applications [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] en JavaScript. Les fichiers inclus dans ce groupe figurent dans la portée de chaque fichier .js ouvert dans l'éditeur de code pour le projet du type spécifié.

- Implicite (Web) pour les projets HTML5. Les fichiers inclus dans ce groupe figurent dans la portée de chaque fichier .js ouvert dans l'éditeur de code pour ces types de projet.

- Groupes de référence de processus de travail dédié pour les traitements Web HTML5. Les fichiers spécifiés dans ce groupe figurent dans la portée des fichiers .js qui possèdent une référence explicite à un groupe de référence de processus de travail dédié.

- Générique pour les autres types de projet JavaScript.

  Dans la plupart des scénarios, vous ne devez pas modifier les groupes de référence. Toutefois, si vous souhaitez apporter des modifications, vous pouvez utiliser les options de configuration pour l'éditeur de code JavaScript afin de spécifier les fichiers inclus dans les groupes de référence. Pour obtenir des instructions sur l’utilisation de cette fonctionnalité, consultez [Options, Éditeur de texte, JavaScript, IntelliSense](../ide/reference/options-text-editor-javascript-intellisense.md).

> [!TIP]
> Les références IntelliSense sont généralement utilisées pour fournir la prise en charge d’IntelliSense pour les objets globaux et pour les [extensions](#Extensibility) IntelliSense. Vous pouvez également utiliser cette fonctionnalité pour les scripts qui doivent être chargés au moment de l’exécution à l’aide du chargeur de script.

### <a name="remote-file-references"></a>Références de fichiers distants
 Vous pouvez demander à Visual Studio de télécharger des fichiers JavaScript distants référencés dans un fichier JavaScript afin d'assurer la prise en charge d'IntelliSense pour la bibliothèque ou le fichier distant. Lorsque vous utilisez cette fonctionnalité, les fichiers sont téléchargés lorsque vous les incluez en tant que référence dans votre fichier JavaScript.

> [!NOTE]
> À l'exception des projets Web, cette fonctionnalité fonctionne uniquement pour les fichiers JavaScript ouverts en dehors du contexte d'un projet. Pour les projets Web, les fichiers distants référencés dans votre projet sont téléchargés par défaut.

 Pour obtenir des instructions sur l’utilisation de cette fonctionnalité, consultez [Options, Éditeur de texte, JavaScript, IntelliSense](../ide/reference/options-text-editor-javascript-intellisense.md).

> [!WARNING]
> Si vous activez cette fonctionnalité et que vous observez un ralentissement dans l’éditeur de code, nous vous recommandons de la désactiver.

### <a name="xml-documentation-comments"></a><a name="XMLDocComments"></a> Commentaires de documentation XML
 Les commentaires de documentation XML sont des descriptions textuelles des éléments de code que vous ajoutez au script. Ces descriptions textuelles s'affichent dans IntelliSense lorsque vous référencez le script commenté. Par exemple, vous pouvez fournir des informations sur les paramètres et la valeur de retour d'une fonction. Les commentaires de documentation XML sont disponibles uniquement à partir de fichiers, d'assemblys et de services référencés. Pour plus d'informations, consultez [Commentaires sur la documentation XML](../ide/xml-documentation-comments-javascript.md) et [Créer des commentaires sur la documentation XML](../ide/create-xml-documentation-comments-for-javascript-intellisense.md).

 IntelliSense peut afficher les commentaires de documentation XML dans les scénarios suivants :

- Un fichier .js qui référence un autre fichier .js.

- Un fichier .js qui référence un fichier .aspx.

- Un fichier .aspx qui référence un fichier .js.

  IntelliSense n'est pas disponible lorsqu'un fichier .aspx référence un autre fichier .aspx.

### <a name="aspnet-ajax-objects"></a><a name="ASPNet"></a> Objets ASP.NET AJAX
 ASP.NET AJAX prend également en charge JavaScript IntelliSense. ASP.NET AJAX inclut une infrastructure cliente qui étend les types standard disponibles dans ECMAScript (JavaScript). Pour permettre à JavaScript IntelliSense de fournir des détails à propos des objets ASP.NET AJAX, des commentaires de documentation XML ont été ajoutés dans [!INCLUDE[atlaslib_current_ext](../includes/atlaslib-current-ext-md.md)]. Ces commentaires de documentation XML sont affichés lorsque vous utilisez des types et des membres contenus dans ASP.NET AJAX Library.

> [!NOTE]
> Les membres privés ne sont pas affichés par JavaScript IntelliSense. Les membres privés sont dénotés dans ASP.NET AJAX comme des membres qui commencent par un trait de soulignement (_).

## <a name="javascript-intellisense-extensibility"></a><a name="Extensibility"></a> Extensibilité JavaScript IntelliSense
 JavaScript Language Service fournit des objets et des fonctions qui vous permettent de modifier l’expérience IntelliSense pour les développeurs qui utilisent des bibliothèques tierces. Ces fonctionnalités sont particulièrement utiles lorsque le service de langage par défaut ne peut pas fournir toutes les informations que vous souhaitez fournir aux clients. Pour plus d'informations, consultez [Extension de JavaScript IntelliSense](../ide/extending-javascript-intellisense.md).

## <a name="javascript-validation"></a><a name="Validation"></a> Validation JavaScript
 La validation de script JavaScript se déroule sans interruption en arrière-plan. Lorsque [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] détecte des erreurs de syntaxe dans le code JavaScript, des commentaires sont fournis de différentes façons :

- Éléments soulignés dans l'éditeur. Les soulignements rouges ondulés indiquent des erreurs. Si vous maintenez le pointeur de la souris sur l'erreur, une info-bulle affiche la description de l'erreur.

- **Liste d’erreurs** fenêtre. La fenêtre **Liste d'erreurs** affiche la description de l'erreur, le fichier où l'erreur s'est produite, les numéros de ligne et de colonne, et le projet. Pour afficher la fenêtre **Liste d'erreurs**, dans le menu **Affichage**, cliquez sur **Liste d'erreurs**.

- La fenêtre Sortie indique les références qui n'ont pas été chargées.

## <a name="see-also"></a>Voir aussi
- [Utilisation d’IntelliSense](../ide/using-intellisense.md)
- [Créer des commentaires de documentation XML](../ide/create-xml-documentation-comments-for-javascript-intellisense.md)
- [Extension de JavaScript IntelliSense](../ide/extending-javascript-intellisense.md)
- [Saisie semi-automatique des instructions pour les identificateurs](../ide/statement-completion-for-identifiers.md)
- [Commentaires de documentation XML](../ide/xml-documentation-comments-javascript.md)
- [À propos du modèle objet DHTML](https://msdn2.microsoft.com/library/ms533022.aspx)
- [Lister les membres](https://msdn.microsoft.com/1b9cc469-9cd4-4d42-9999-1f9479635ff8)
- [Attribut SRC &#124; Propriété src](https://msdn2.microsoft.com/library/ms534642.aspx)
