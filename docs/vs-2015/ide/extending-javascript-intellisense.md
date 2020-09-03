---
title: Extension de JavaScript IntelliSense | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- JavaScript, intellisense object
- extending JavaScript IntelliSense
- customizing JavaScript IntelliSense
- JavaScript, extending IntelliSense
- IntelliSense [JavaScript], extending
ms.assetid: 004e1ab6-bd7a-4327-9e01-89b9be96ba2f
caps.latest.revision: 43
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: bf16b6fdc307e11875f30cfad6e4bb35580b0b04
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72665752"
---
# <a name="extending-javascript-intellisense"></a>Extension de JavaScript IntelliSense
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La fonctionnalité d’extensibilité JavaScript IntelliSense vous permet de personnaliser les résultats IntelliSense dans l’éditeur JavaScript pour les bibliothèques tierces. Cela peut améliorer l’expérience des développeurs qui utilisent ces bibliothèques.

 Le service de langage JavaScript fournit des fonctionnalités IntelliSense pour les bibliothèques JavaScript tierces qui sont ajoutées à un projet. Pour la plupart des bibliothèques, la saisie semi-automatique des instructions est fournie automatiquement par le service de langage. L’illustration suivante montre un exemple de saisie semi-automatique des instructions :

 ![Exemple de fin de l'instruction](../ide/media/js-intellisense-completion.png "js_intellisense_completion")

 Si votre bibliothèque comprend des descriptions de variables, de fonctions et d’objets dans des balises de commentaire JavaScript standard (//), vous bénéficiez automatiquement, par défaut, des fonctionnalités d’extensibilité IntelliSense qui fournissent des informations descriptives dans une zone contextuelle qui s’affiche à droite des éléments d’une liste de saisie semi-automatique, ou lorsque vous tapez la parenthèse ouvrante dans un appel de fonction Les commentaires figurant dans la zone contextuelle contiennent la description du membre. L’exemple suivant illustre la zone contextuelle d’une liste de saisie semi-automatique.

 ![Exemple de zone de liste déroulante Info Express&#45;](../ide/media/js-intellisense-quickinfo.png "js_intellisense_quickinfo")

 Pour améliorer l’expérience du développeur, vous souhaiterez peut-être fournir des informations de type aux développeurs dans la zone contextuelle. Vous pouvez fournir des informations de type à l’aide de [Commentaires de documentation XML](../ide/xml-documentation-comments-javascript.md) JavaScript au lieu de balises de commentaire standard. Vous ajoutez des commentaires de documentation XML en utilisant des balises de commentaire triple barre (///) et un ensemble défini d’éléments XML.

 Vous pouvez également fournir des informations de type à l’aide de l’extensibilité JavaScript IntelliSense. Cette fonctionnalité vous permet de personnaliser les résultats IntelliSense en créant des extensions JavaScript et en les ajoutant au contexte de script. Dans l’extension, qui est un fichier JavaScript, vous vous abonnez aux événements exposés par l' `intellisense` objet du service de langage. L’extensibilité JavaScript IntelliSense est la solution recommandée pour les bibliothèques si un modèle de comportement dans la bibliothèque empêche le service de langage JavaScript de fournir le niveau souhaité de prise en charge IntelliSense et si une alternative aux commentaires de documentation XML déclaratifs est également nécessaire. En personnalisant les résultats IntelliSense, vous pouvez créer une expérience IntelliSense de première classe, quels que soient les modèles de comportement qui peuvent restreindre les fonctionnalités par défaut du service de langage. Pour plus d'informations, consultez [Saisie semi-automatique des instructions pour les identificateurs](../ide/statement-completion-for-identifiers.md).

## <a name="adding-an-extension-to-the-script-context"></a>Ajout d’une extension au contexte de script
 Pour qu’une extension IntelliSense soit exécutée, elle doit être ajoutée au contexte de script actuel. L’extension peut être automatiquement ajoutée au contexte de script par le mécanisme de détection automatique, ou vous pouvez ajouter l’extension au contexte de script manuellement à l’aide de groupes de référence ou de la directive de référence.

 Le mécanisme de détection automatique permet au service de langage de rechercher automatiquement les extensions qui suivent la Convention d’affectation de noms de fichiers *nombibliothèque*.intellisense.js et qui se trouvent dans le même répertoire que la bibliothèque à laquelle l’extension s’applique. Par exemple, une extension valide pour la bibliothèque jQuery serait jQuery.intellisense.js. Pour les extensions jQuery plus restrictives, vous pouvez utiliser des noms de fichiers tels que jQuery-1.7.1.intellisense.js (extension spécifique à la version) ou jQuery.ui.intellisense.js (une extension pour une bibliothèque jQuery étendue). La version la plus restrictive de l’extension est utilisée si plusieurs extensions sont trouvées pour une bibliothèque donnée.

 Si vous souhaitez utiliser l’extension pour tous les fichiers de votre projet JavaScript, vous pouvez choisir d’ajouter l’extension à un groupe de référence. Il existe plusieurs types de groupes de référence, soit ceux qui incluent des références implicites et ceux qui incluent des références de travail dédiées. Pour ajouter une extension, vous devez généralement ajouter le fichier en tant que groupe de référence implicite **(Windows)**, **implicite (Web)**. Les références implicites sont dans la portée pour chaque fichier. js ouvert dans l’éditeur de code. Lorsque vous utilisez cette méthode, vous devez ajouter à la fois l’extension et le fichier que l’extension complète.

 Utilisez la page **IntelliSense** de la boîte de dialogue **options** pour ajouter une extension en tant que groupe de référence. Vous pouvez accéder à la page **IntelliSense** en choisissant **Outils**, **options** dans la barre de menus, puis en choisissant **éditeur de texte**, **JavaScript**, **IntelliSense**, **références**. Pour plus d’informations sur les groupes de référence, consultez [JavaScript IntelliSense](../ide/javascript-intellisense.md) et [options, éditeur de texte, JavaScript, IntelliSense](../ide/reference/options-text-editor-javascript-intellisense.md).

 Si vous souhaitez utiliser l’extension pour un ensemble spécifique de fichiers, utilisez une directive de référence. Lorsque vous utilisez cette méthode, vous devez référencer à la fois l’extension et le fichier que l’extension complète. Pour plus d’informations sur l’utilisation de la directive de référence, consultez [JavaScript IntelliSense](../ide/javascript-intellisense.md).

## <a name="handling-intellisense-events"></a>Gestion des événements IntelliSense
 La fonctionnalité d’extensibilité vous permet de personnaliser les résultats IntelliSense en s’abonnant à des événements tels que l' `statementcompletion` événement de l’objet de service de langage `intellisense` . L’exemple suivant montre une extension simple qui est utilisée par le service de langage pour masquer les membres qui commencent par un trait de soulignement à partir de la saisie semi-automatique des instructions. Ce code est contenu dans underscorefilter.js et se trouve dans le \\ \\ dossier \JavaScript\References du *chemin d’installation de Visual Studio*.

```javascript
intellisense.addEventListener('statementcompletion', function (event) {
    if (event.targetName === "this") return;

    var filterRegex;

    if (event.target === undefined || event.target === window)
        filterRegex = /^_.*\d{2,}/;
    else
        filterRegex = /^_.*/;

    event.items = event.items.filter(function (item) {
        return !filterRegex.test(item.name);
    });
});
```

 Dans le code précédent, l’extension vérifie la [propriété TargetName](#TargetName) et les propriétés de [propriété cibles](#Target) de l' `statementcompletion` objet d’événement pour exclure des objets tels que `this` et `window` , et pour s’assurer qu’une liste de saisie semi-automatique de l’instruction valide peut être identifiée. Si une liste de saisie semi-automatique peut être identifiée, l’extension met à jour la collection de [propriétés d’éléments](#Items) de saisie semi-automatique des instructions en filtrant les membres qui commencent par un trait de soulignement.

 Pour obtenir des exemples supplémentaires, consultez le \\ \\ dossier \JavaScript\References du *chemin d’installation de Visual Studio*. Le fichier showPlainComments.js dans ce dossier fournit des exemples d’utilisation d’autres événements pour fournir une prise en charge IntelliSense par défaut pour les balises de commentaire JavaScript standard (//). Comme underscorefilter.js, showPlainComments.js est déjà disponible en tant qu’extension de travail, et vous pouvez voir les informations IntelliSense qui en résultent lorsque vous utilisez des balises de commentaire dans votre code pour des variables, des fonctions et des objets. Pour obtenir des exemples supplémentaires, consultez [exemples de code](#CodeExamples).

> [!WARNING]
> Si vous modifiez les fichiers d’extension inclus dans Visual Studio, vous pouvez désactiver JavaScript IntelliSense ou la fonctionnalité prise en charge par l’extension.

 Dans votre code d’extension, vous pouvez créer des gestionnaires pour les types d’événements suivants à l’aide de `addEventListener` :

- `statementcompletion`, qui ajoute un gestionnaire pour un événement d’achèvement d’instruction. La saisie semi-automatique des instructions fournit une liste de membres pour un type particulier qui apparaît une fois que vous avez tapé un caractère spécial, tel qu’un point (.), ou une liste d’identificateurs qui s’affiche lorsque vous tapez ou lorsque vous appuyez sur CTRL + J. Le gestionnaire reçoit un objet d’événement de type `CompletionEvent` , qui prend en charge les membres suivants : [Items](#Items), Property, [Target Property](#Target), [TargetName Property](#TargetName)et [scope Property](#Scope).

- `signaturehelp`, qui ajoute un gestionnaire pour les informations sur les paramètres IntelliSense. Les informations sur les paramètres vous donnent des informations sur le nombre, les noms et les types de paramètres requis par une fonction. Le gestionnaire reçoit un objet d’événement de type `SignatureHelpEvent` , qui prend en charge les membres suivants : [propriété cible](#Target), propriété [ParentObject](#ParentObject), propriété [functionComments](#FunctionComments), propriété [functionHelp](#FunctionHelp).

- `statementcompletionhint`, qui ajoute un gestionnaire pour info Express IntelliSense. La zone contextuelle Info Express affiche la déclaration complète des identificateurs dans votre code. Le gestionnaire reçoit un objet d’événement de type `CompletionHintEvent` , qui prend en charge les membres suivants : [CompletionItem, Property](#CompletionItem)et [symbolHelp](#SymbolHelp).

  Pour obtenir des exemples qui illustrent des fonctionnalités IntelliSense telles que la saisie semi-automatique des instructions, des informations sur les paramètres et des informations rapides, consultez [utilisation d’IntelliSense](../ide/using-intellisense.md).

> [!NOTE]
> En JavaScript, info Express fait référence à la zone contextuelle qui s’affiche à droite d’une liste de saisie semi-automatique. Vous ne pouvez pas appeler manuellement Info Express.

## <a name="intellisense-object"></a><a name="intellisenseObject"></a> Objet intellisense
 Le tableau suivant présente les fonctions disponibles pour l' `intellisense` objet. L' `intellisense` objet est uniquement disponible au moment de la conception.

|Fonction|Description|
|--------------|-----------------|
|`addEventListener(type, handler);`|Ajoute un gestionnaire d’événements pour un événement IntelliSense.<br /><br /> `type` est une valeur de chaîne. Les valeurs valides sont `statementcompletion`, `signaturehelp` et `statementcompletionhint`.<br /><br /> `handler` est une fonction de gestionnaire d’événements qui reçoit un objet d’événement de l’un des types suivants :<br /><br /> -   `CompletionEvent`, utilisé pour l' `statementcompletion` événement.<br />-   `SignatureHelpEvent`, utilisé pour l' `signaturehelp` événement.<br />-   `CompletionHintEvent`, utilisé pour l' `statementcompletionhint` événement.<br /><br /> Pour obtenir des exemples qui utilisent cette fonction, consultez [exemples de code](#CodeExamples).|
|`annotate(obj, doc);`|Spécifie la documentation d’un objet en copiant les commentaires de documentation d’un objet dans un autre objet.<br /><br /> `obj` Spécifie l’objet dans lequel la documentation doit être copiée.<br /><br /> `doc` Spécifie l’objet à partir duquel la documentation doit être copiée.<br /><br /> Pour obtenir un exemple qui montre comment utiliser cette fonction, consultez [Ajout d’annotations IntelliSense](#Annotations).|
|`getFunctionComments(func);`|Retourne les commentaires pour une fonction spécifiée.<br /><br /> `func` spécifie la fonction pour laquelle les commentaires sont retournés.<br /><br /> Vous pouvez définir le `func` paramètre à l’aide de `completionItem.value` .<br /><br /> L' `functionComments` objet retourné comprend les membres suivants : `above` , `inside` et `paramComment` . Pour plus d’informations, consultez la propriété de [propriété functionComments](#FunctionComments) .<br /><br /> `getFunctionComments` peut être appelé uniquement à partir de l’un des gestionnaires d’événements inscrits par `addEventListener` .<br /><br /> Pour obtenir un exemple qui montre comment utiliser cette fonction, consultez \\ \\ *chemin d’installation de Visual Studio*\JavaScript\References\showPlainComments.js.|
|`logMessage(msg);`|Envoie des messages de diagnostic dans la fenêtre sortie.<br /><br /> `msg` chaîne qui contient le message.<br /><br /> Pour obtenir un exemple qui montre comment utiliser cette fonction, consultez [envoi de messages à l’fenêtre Sortie](#Logging).|
|`nullWithCompletionsOf(value);`|Retourne une valeur null spéciale pour laquelle la liste de saisie semi-automatique est déterminée par l’objet passé dans le `value` paramètre.<br /><br /> `value` détermine la liste de saisie semi-automatique pour la valeur retournée. `value` peut être n’importe quel type.<br /><br /> La valeur de retour NULL est traitée comme null au moment de la conception, mais la liste de saisie semi-automatique de la valeur de retour est la même que la liste de saisie semi-automatique pour le `value` paramètre.<br /><br /> Une utilisation de cette fonction consiste à fournir à IntelliSense une valeur de retour lorsque le type de retour est prévisible lors de l’exécution, mais la valeur de retour est `null` au moment de la conception.|
|`redirectDefinition(func, definition);`|Indique à IntelliSense d’utiliser la fonction de définition fournie à la place de la fonction Func d’origine lorsque l’aide sur les paramètres ou l' **accès à la définition** est demandé.<br /><br /> `func` spécifie la fonction cible.<br /><br /> `definition` spécifie la fonction à utiliser à la place de la fonction cible pour obtenir des informations sur les paramètres et **atteindre la définition**.|
|`setCallContext(func, thisArg);`|Définit le contexte d’appel, ou portée, pour la fonction spécifiée.<br /><br /> `func` spécifie la fonction pour laquelle définir l’étendue.<br /><br /> `thisArg` est un littéral d’objet auquel le `this` mot clé peut faire référence, qui spécifie la nouvelle portée pour le membre. Vous pouvez inclure des arguments à passer dans ce paramètre, par exemple, `intellisense.setCallContext(func, { thisArg: "", args: [23,2] });`<br /><br /> `setCallContext` fournit un comportement semblable à `Function.prototype.bind` , à ceci près qu’il est utilisé uniquement pour la prise en charge IntelliSense au moment du Design. Vous pouvez utiliser `setCallContext` pour définir la portée de la fonction si vous devez simuler un appel à du code qui n’est pas accessible autrement. ainsi, lorsque vous appelez la fonction, l’appel de fonction inclut la portée et les arguments corrects.|
|`undefinedWithCompletionsOf(value);`|Retourne une valeur non définie spéciale pour laquelle la liste de saisie semi-automatique est déterminée par l’objet passé dans le `value` paramètre.<br /><br /> `value` détermine la liste de saisie semi-automatique pour la valeur retournée. `value` peut être n’importe quel type.<br /><br /> La valeur de retour non définie est traitée comme non définie au moment de la conception, mais la liste de saisie semi-automatique de la valeur de retour est la même que la liste de saisie semi-automatique pour le `value` paramètre.<br /><br /> Une utilisation de cette fonction consiste à fournir à IntelliSense une valeur de retour lorsque le type de retour est prévisible lors de l’exécution, mais que la valeur de retour n’est pas définie au moment de la conception.|
|`version()`|Retourne la version de Visual Studio.|

## <a name="event-members"></a>Membres d’événement
 Les sections suivantes décrivent les membres qui sont exposés dans l’objet d’événement pour les événements suivants : `statementcompletion` , `signaturehelp` et `statementcompletionhint` .

### <a name="completionitem-property"></a><a name="CompletionItem"></a> Propriété completionItem
 Retourne l’identificateur, connu sous le nom d’élément de saisie semi-automatique, pour lequel une zone contextuelle Info Express est demandée. Cette propriété est disponible pour l' `statementcompletionhint` objet d’événement et pour la propriété [Items](#Items) de l' `statementcompletion` objet Event.

 Valeur de retour : `completionItem` objet

 Voici les membres de l' `completionItem` objet :

- `name`. En lecture/écriture en cas d’utilisation dans la `items` collection ; sinon, en lecture seule. Retourne une chaîne qui identifie l’élément de saisie semi-automatique.

- `kind`. En lecture/écriture en cas d’utilisation dans la `items` collection ; sinon, en lecture seule. Retourne une chaîne qui représente le type d’élément de saisie semi-automatique. Les valeurs possibles sont Method, Field, Property, Parameter, variable et reserved.

- `glyph`. En lecture/écriture en cas d’utilisation dans la `items` collection ; sinon, en lecture seule. Retourne une chaîne qui représente une icône affichée dans la liste de saisie semi-automatique. Les valeurs possibles pour `glyph` utilisent le format suivant : vs :*glyphType*, où *glyphType* correspond aux membres indépendants du langage dans l' <xref:Microsoft.VisualStudio.Language.Intellisense.StandardGlyphGroup> énumération. Par exemple, `vs:GlyphGroupMethod` est une valeur possible pour `glyph` . Lorsque `glyph` n’est pas défini, la `kind` propriété détermine l’icône par défaut.

- `parentObject`. Lecture seule. Retourne l’objet parent.

- `value`. Lecture seule. Retourne un objet qui représente la valeur de l’élément de saisie semi-automatique.

- `comments`. Lecture seule. Retourne une chaîne qui contient les commentaires qui se trouvent au-dessus du champ ou de la variable.

- `scope`. Lecture seule. Retourne l’étendue de l’élément de saisie semi-automatique. Les valeurs possibles sont global, local, Parameter et member.

### <a name="items-property"></a><a name="Items"></a> Items, propriété
 Obtient ou définit le tableau d’éléments de saisie semi-automatique des instructions. Chaque élément du tableau est un objet de [propriété completionItem](#CompletionItem) . La `items` propriété est disponible pour l' `statementcompletion` objet d’événement.

 Valeur de retour : Array

### <a name="functioncomments-property"></a><a name="FunctionComments"></a> Propriété functionComments
 Retourne les commentaires pour la fonction. Cette propriété est disponible pour l' `signaturehelp` objet d’événement.

 Valeur de retour : `comments` objet

 Voici les membres de l' `comments` objet :

- `above`. Retourne les commentaires au-dessus de la fonction.

- `inside`. Retourne les commentaires à l’intérieur de la fonction, en général au format VSDoc.

- `paramComments`. Retourne un tableau représentant des commentaires pour chaque paramètre de la fonction. Les membres du tableau sont les suivants :

  - `name`. Retourne une chaîne représentant le nom du paramètre.

  - `comment`. Retourne une chaîne qui contient le commentaire de paramètre.

### <a name="functionhelp-property"></a><a name="FunctionHelp"></a> Propriété functionHelp
 Retourne l’aide de la fonction. Cette propriété est disponible pour l' `signaturehelp` objet d’événement.

 Valeur de retour : `functionHelp` objet

 Voici les membres de l' `functionHelp` objet :

- `functionName`. En lecture/écriture. Retourne une chaîne qui contient le nom de la fonction.

- `signatures`. En lecture/écriture. Obtient ou définit le tableau des signatures de fonction. Chaque élément du tableau est un `signature` objet. Certaines `signature` Propriétés, telles que `locid` , correspondent à des attributs de [Commentaires de documentation XML](../ide/xml-documentation-comments-javascript.md) communs.

  Les membres de l' `signature` objet sont les suivants :

  - `description`. En lecture/écriture. Retourne une chaîne qui décrit la fonction.

  - `locid`. En lecture/écriture. Retourne un identificateur de chaîne qui contient des informations de localisation à propos de la fonction.

  - `helpKeyword`. En lecture/écriture. Retourne une chaîne qui contient le mot clé d’aide.

  - `externalFile`. En lecture/écriture. Retourne une chaîne qui représente le fichier qui contient l’ID de membre.

  - `externalid`. En lecture/écriture. Retourne une chaîne qui représente l’ID de membre de la fonction.

  - `params`. En lecture/écriture. Obtient ou définit le tableau de paramètres pour la fonction. Chaque élément du tableau de paramètres est un `parameter` objet qui a des propriétés qui correspondent aux attributs suivants de l' [\<param>](../ide/param-javascript.md) élément :

    - `name`. En lecture/écriture. Retourne une chaîne qui représente le nom du paramètre.

    - `type`. En lecture/écriture. Retourne une chaîne qui représente le type de paramètre.

    - `elementType`. En lecture/écriture. Si le type est `Array` , retourne une chaîne qui représente le type des éléments dans le tableau.

    - `description`. En lecture/écriture. Retourne une chaîne qui décrit le paramètre.

    - `locid`. En lecture/écriture. Retourne un identificateur de chaîne qui contient des informations de localisation à propos de la fonction.

    - `optional`. En lecture/écriture. Retourne une chaîne qui indique si le paramètre est facultatif. `true` indique que le paramètre est facultatif ; `false` indique que ce n’est pas le cas.

  - `returnValue`. En lecture/écriture. Obtient ou définit un objet de valeur de retour avec des propriétés qui correspondent aux attributs suivants de l' [\<returns>](../ide/returns-javascript.md) élément :

    - `type`. En lecture/écriture. Retourne une chaîne qui représente le type de retour.

    - `elementType`. En lecture/écriture. Si le type est `Array` , retourne une chaîne qui représente le type des éléments dans le tableau.

    - `description`. En lecture/écriture. Retourne une chaîne qui décrit la valeur de retour.

    - `locid`. En lecture/écriture. Retourne un identificateur de chaîne qui contient des informations de localisation à propos de la fonction.

    - `helpKeyword`. En lecture/écriture. Retourne une chaîne qui contient le mot clé d’aide.

    - `externalFile`. En lecture/écriture. Retourne une chaîne qui représente le fichier qui contient l’ID de membre.

    - `externalid`. En lecture/écriture. Retourne une chaîne qui représente l’ID de membre de la fonction.

### <a name="parentobject-property"></a><a name="ParentObject"></a> Propriété parentObject
 Retourne l’objet parent d’une fonction membre. Par exemple, pour `document.getElementByID` , `parentObject` retourne l' `document` objet. Cette propriété est disponible pour l' `signaturehelp` objet d’événement.

 Valeur de retour : objet

### <a name="target-property"></a><a name="Target"></a> Propriété cible
 Retourne un objet qui représente l’élément à gauche du caractère de déclenchement, qui est un point (.). Pour les fonctions, `target` retourne la fonction pour laquelle les informations sur les paramètres sont demandées. Cette propriété est disponible pour les `statementcompletion` `signaturehelp` objets d’événement et.

 Valeur de retour : objet

### <a name="targetname-property"></a><a name="TargetName"></a> targetName, propriété
 Retourne une chaîne qui représente la cible. Par exemple, pour « This. », `targetName` retourne « This ». Pour « A. B » (lorsque le curseur se trouve après « B »), `targetName` retourne « b ». Cette propriété est disponible pour l' `statementcompletion` objet d’événement.

 Valeur de retour : chaîne

### <a name="symbolhelp-property"></a><a name="SymbolHelp"></a> Propriété symbolHelp
 Retourne l’élément de saisie semi-automatique pour lequel une zone contextuelle Info Express est demandée. Cette propriété est disponible pour l' `statementcompletionhint` objet d’événement.

 Valeur de retour : `symbolHelp` objet.

 Certaines propriétés de l' `symbolHelp` objet, telles que `locid` , correspondent à des attributs de [Commentaires de documentation XML](../ide/xml-documentation-comments-javascript.md) communs.

 Voici les membres de l' `symbolHelp` objet :

- `name`. En lecture/écriture. Retourne une chaîne qui contient le nom de l’identificateur.

- `symbolType`. En lecture/écriture. Retourne une chaîne qui représente le type de symbole. Les valeurs possibles sont Unknown, Boolean, Number, String, Object, Function, Array, date et Regex.

- `symbolDisplayType`. En lecture/écriture. Retourne une chaîne qui contient le nom de type à afficher. Si `symbolDisplayType` n’est pas défini, `symbolType` est utilisé.

- `elementType`. En lecture/écriture. Si `symbolType` est `Array` , retourne une chaîne qui représente le type des éléments dans le tableau.

- `scope`. En lecture/écriture. Retourne une chaîne qui représente la portée du symbole. Les valeurs possibles sont global, local, Parameter et member.

- `description`. En lecture/écriture. Retourne une chaîne qui contient une description du symbole.

- `locid`. En lecture/écriture. Retourne un identificateur de chaîne qui contient des informations de localisation sur le symbole.

- `helpKeyword`. En lecture/écriture. Retourne une chaîne qui contient le mot clé d’aide.

- `externalFile`. En lecture/écriture. Retourne une chaîne qui représente le fichier qui contient l’ID de membre.

- `externalid`. En lecture/écriture. Retourne une chaîne qui représente l’ID de membre du symbole.

- `functionHelp`. En lecture/écriture. Retourne une [propriété functionHelp](#FunctionHelp), qui peut contenir des informations lorsque la `symbolType` fonction est.

### <a name="scope-property"></a><a name="Scope"></a> Scope, propriété
 Retourne la portée de fin de l’événement. Les valeurs possibles pour la portée d’achèvement sont global et members. Cette propriété est disponible pour l' `statementcompletion` objet d’événement.

 Valeur de retour : chaîne

## <a name="debugging-intellisense-extensions"></a>Débogage d’extensions IntelliSense
 Vous ne pouvez pas déboguer des extensions, mais vous pouvez utiliser la fonction d' [objet IntelliSense](#intellisenseObject) pour envoyer des informations à la fenêtre sortie de Visual Studio. Pour obtenir un exemple qui montre comment utiliser cette fonction, consultez [envoi de messages au fenêtre Sortie](#Logging) , plus loin dans cette rubrique. Pour `logMessage` que fonctionne, au moins un gestionnaire d’événements doit être inscrit dans une extension.

## <a name="code-examples"></a><a name="CodeExamples"></a> Exemples de code
 Cette section contient des exemples de code qui montrent comment utiliser les API d’extensibilité IntelliSense. Il existe également d’autres façons d’utiliser ces API. Pour obtenir des exemples supplémentaires, consultez les fichiers suivants dans le \\ \\ dossier \JavaScript\References du *chemin d’installation de Visual Studio*. Il s’agit d’exemples fonctionnels utilisés par le service de langage JavaScript.

- underscoreFilter.js. Ce code masque les membres privés d’IntelliSense. Il comprend des gestionnaires d’événements pour l' `statementcompletion` événement.

- showPlainComments.js. Ce code fournit la prise en charge IntelliSense pour les commentaires standard. Il comprend des gestionnaires d’événements pour `signaturehelp` les `statementcompletionhint` événements et.

### <a name="adding-intellisense-annotations"></a><a name="Annotations"></a> Ajout d’annotations IntelliSense
 La procédure suivante montre comment fournir la prise en charge de la documentation IntelliSense pour une bibliothèque tierce sans modifier directement la bibliothèque. Pour ce faire, vous pouvez utiliser `intellisense.annotate` dans une extension.

 Pour que cet exemple fonctionne, vous avez besoin des fichiers JavaScript suivants dans votre projet :

- demoLib.js, qui est un fichier projet qui représente une bibliothèque tierce.

- demoLib.intellisense.js, qui est l’extension IntelliSense. Ce fichier n’a pas besoin d’être inclus dans le projet, mais il doit se trouver dans le même dossier que exampleLib.js.

- appCode.js, qui est un fichier projet qui représente le code de l'application.

##### <a name="to-add-an-intellisense-annotation"></a>Pour ajouter une annotation IntelliSense

1. Ajoutez le code suivant à demoLib.js.

    ```javascript
    function someFunc(a) { };
    var rectangle;

    ```

2. Ajoutez le code suivant à demoLib.intellisense.js.

    ```javascript
    intellisense.annotate(someFunc, function (a) {
        /// <signature>
        /// <summary>Description of someFunc</summary>
        /// <param name="a">Param a</param>
        /// </signature>
    });

    intellisense.annotate(window, {
        // This is a comment on a global variable named rectangle.
        rectangle: undefined
    });
    ```

3. Ajoutez la directive de référence suivante comme première ligne dans appCode.js. Le chemin d'accès utilisé ici indique que les fichiers JavaScript sont dans le même dossier.

    ```javascript
    /// <reference path="demoLib.js" />

    ```

4. Dans appCode.js, tapez le code suivant. Vous verrez les commentaires de documentation XML dans l’extension affichée en tant qu’informations sur les paramètres IntelliSense.

     ![Exemple illustrant l'utilisation de l'annotation intellisense](../ide/media/js-intellisense-annotate-paraminfo.png "js_intellisense_annotate_paraminfo")

5. Dans appCode.js, tapez le code suivant. Pendant que vous tapez, les commentaires standard de l’extension s’affichent sous forme d’info Express IntelliSense.

     ![Exemple illustrant l'utilisation de l'annotation intellisense](../ide/media/js-intellisense-annotations.png "js_intellisense_annotations")

### <a name="sending-messages-to-the-output-window"></a><a name="Logging"></a> Envoi de messages au Fenêtre Sortie
 La procédure suivante montre comment envoyer des messages à la fenêtre sortie. Vous pouvez envoyer des messages pour vous aider à déboguer les extensions IntelliSense.

 Pour que cet exemple fonctionne, vous avez besoin des fichiers JavaScript suivants dans votre projet :

- exampleLib.js, qui est un fichier projet qui représente une bibliothèque tierce.

- exampleLib.intellisense.js, qui est l’extension IntelliSense. Ce fichier n’a pas besoin d’être inclus dans le projet, mais il doit se trouver dans le même dossier que exampleLib.js.

- appCode.js, qui est un fichier projet qui représente le code de l'application.

##### <a name="to-send-a-message-to-the-output-window"></a>Pour envoyer un message à la fenêtre sortie

1. Ajoutez le code suivant à exampleLib.js.

    ```javascript
    var someVar = {
        a: 1,
        b: 'hello'
    };
    ```

2. Ajoutez le code suivant à exampleLib.intellisense.js.

    ```javascript
    intellisense.addEventListener('statementcompletion', function (e) {
        // Prints out statement completion info: Either (1) the member
        // list, if the trigger character was typed, or (2) the
        // statement completion identifiers.
        // e.target represents the object left of the trigger character.
        intellisense.logMessage(
            e.target ? 'member list requested, target: ' + e.targetName : 'statement completion for current scope requested');

        // Prints out all statement completion items.
        e.items.forEach(function (item) {
            intellisense.logMessage('[completion item] ' + item.name + ', kind:' + item.kind + ', scope:' + item.scope + ', value:' + item.value);
        });
    });
    ```

3. Ajoutez la directive de référence suivante comme première ligne dans appCode.js. Le chemin d'accès utilisé ici indique que les fichiers JavaScript sont dans le même dossier.

    ```javascript
    /// <reference path="exampleLib.js" />

    ```

4. Dans la fenêtre sortie, choisissez **JavaScript Language Service** dans la liste **afficher la sortie à partir de** . (Pour afficher la fenêtre sortie, sélectionnez **sortie** dans le menu Affichage.)

5. Dans appCode.js, tapez le code suivant. Pendant que vous tapez, la fenêtre sortie affiche les messages du service de langage. Le premier message dans la fenêtre sortie indique que la saisie semi-automatique des instructions pour la portée actuelle a été demandée.

    ```javascript
    some
    ```

     Voici une vue partielle de la sortie que vous devez voir.

    ```scr
    03:16:14.3113: statement completion for current scope requested
    03:16:14.3113: [completion item] break, kind:reserved, scope:undefined, value:undefined
    03:16:14.3113: [completion item] case, kind:reserved, scope:undefined, value:undefined
    03:16:14.3113: [completion item] catch, kind:reserved, scope:undefined, value:undefined

    …
    ```

6. Choisissez le bouton **Effacer tout** dans la fenêtre sortie.

7. Tapez le code suivant. Le premier message dans la fenêtre sortie indique qu’une liste de membres a été demandée.

    ```javascript
    someVar.
    ```

     Voici une vue partielle de la sortie que vous devez voir :

    ```scr
    03:17:43.4032: member list requested, target: someVar
    03:17:43.4032: [completion item] a, kind:field, scope:member, value:1
    03:17:43.4032: [completion item] b, kind:field, scope:member, value:hello
    03:17:43.4032: [completion item] constructor, kind:method, scope:member, value:

    …
    ```

### <a name="changing-the-intellisense-icons"></a><a name="Icons"></a> Modification des icônes IntelliSense
 La procédure suivante montre comment modifier par défaut les icônes affichées par IntelliSense. Cela peut être utile lorsque vous fournissez des informations IntelliSense sur les concepts spécifiques à la bibliothèque, tels que les espaces de noms, les classes, les interfaces et les énumérations.

 Pour connaître les valeurs d’icône disponibles, consultez <xref:Microsoft.VisualStudio.Language.Intellisense.StandardGlyphGroup> .

 Pour que cet exemple fonctionne, vous avez besoin des fichiers JavaScript suivants dans votre projet :

- exampleLib.js, qui est un fichier projet qui represens une bibliothèque tierce.

- exampleLib.intellisense.js, qui est l’extension IntelliSense. Ce fichier n’a pas besoin d’être inclus dans le projet, mais il doit se trouver dans le même dossier que exampleLib.js.

- appCode.js, qui est un fichier projet qui représente le code de l'application.

##### <a name="to-change-the-icons"></a>Pour modifier les icônes

1. Ajoutez le code suivant à exampleLib.js.

    ```javascript
    function Namespace(name) {
        this._isNamespace = true;
        window[name] = this;
    };

    function Enum(values) {
        var e = Object.create(values);
        e._isEnum = true;
        return e;
    };

    var SomeNamespace = new Namespace('SomeNamespace');
    // A constructor function is considered a class.
    SomeNamespace.SomeClass1 = function () { }
    SomeNamespace.Enum1 = new Enum({ VALUE1: 0, VALUE2: 1 });
    ```

2. Ajoutez le code suivant à exampleLib.intellisense.js.

    ```javascript
    intellisense.addEventListener('statementcompletion', function (e) {
        e.items.forEach(function (item) {
            // Detect a namespace by using the _isNamespace flag.
            if (item.value && item.value._isNamespace) {
                item.glyph = 'vs:GlyphGroupNamespace';
                }

            if (item.parentObject && item.parentObject._isNamespace) {
                // The item is a member of a namespace.

                // All constructor functions that are part of a namespace
                // are considered classes.
                // A constructor function starts with
                // an uppercase letter by convention.
                if (typeof item.value == 'function' && (item.name[0].toUpperCase()
                    == item.name[0])) {
                    item.glyph = 'vs:GlyphGroupClass';
                }

                // Detect an enumeration by using the _isEnum flag.
                if (item.value && item.value._isEnum) {
                    item.glyph = 'vs:GlyphGroupEnum';
                }
            }
        });
    });

    intellisense.addEventListener('statementcompletionhint', function (e) {
        if (e.completionItem.value) {
            if (e.completionItem.value._isNamespace) {
                e.symbolHelp.symbolDisplayType = 'Namespace';
            }
            if (e.completionItem.value._isEnum) {
                e.symbolHelp.symbolDisplayType = 'Enum';
            }
        }
    });
    ```

3. Ajoutez la directive de référence suivante comme première ligne dans appCode.js. Le chemin d'accès utilisé ici indique que les fichiers JavaScript sont dans le même dossier.

    ```javascript
    /// <reference path="exampleLib.js" />

    ```

4. Dans appCode.js, tapez le code suivant. Pendant que vous tapez, vous verrez que l’icône de l’espace de noms a été remplacée par « {} », comme c’est le cas dans C#.

     ![Exemple illustrant l'utilisation de la propriété glyphe](../ide/media/js-intellisense-glyph-namespace.png "js_intellisense_glyph_namespace")

5. Dans appCode.js, tapez le code suivant. Pendant que vous tapez, vous voyez une nouvelle icône d’énumération pour le membre Enum1 et une nouvelle icône de classe pour le membre SomeClass1.

     ![Exemple illustrant l'utilisation de la propriété glyphe](../ide/media/js-intellisense-glyph-class-enum.png "js_intellisense_glyph_class_enum")

### <a name="avoiding-run-time-effects-on-intellisense-results"></a><a name="Overriding"></a> Éviter les effets d’exécution sur les résultats IntelliSense
 Le service de langage JavaScript exécute du code pour fournir dynamiquement des informations IntelliSense. Par conséquent, le comportement au moment de l’exécution peut parfois interférer avec les résultats souhaités. La procédure suivante montre comment substituer les résultats d’IntelliSense lorsque le comportement de l’exécution entraîne un IntelliSense incorrect.

 Pour que cet exemple fonctionne, vous avez besoin des fichiers JavaScript suivants dans votre projet :

- exampleLib.js, qui est un fichier projet qui représente une bibliothèque tierce.

- exampleLib.intellisense.js, qui est l’extension IntelliSense. Ce fichier n’a pas besoin d’être inclus dans le projet, mais il doit se trouver dans le même dossier que exampleLib.js.

- appCode.js, qui est un fichier projet qui représente le code de l'application.

##### <a name="to-avoid-run-time-effects-on-intellisense-results"></a>Pour éviter les effets d’exécution sur les résultats IntelliSense

1. Ajoutez le code suivant à exampleLib.js.

    ```javascript
    function after(count, func) {
        return function () {
            if (--times < 1) {
                return func.apply(this, arguments);
            }
        };
    };
    ```

     Dans le code précédent, la fonction encapsulée ignore les appels initiaux, en fonction de la valeur de `count` , et ne retourne pas de résultats.

2. Ajoutez la directive de référence suivante comme première ligne dans appCode.js. Le chemin d'accès utilisé ici indique que les fichiers JavaScript sont dans le même dossier.

    ```javascript
    /// <reference path="exampleLib.js" />

    ```

3. Dans appCode.js, tapez le code suivant. La liste d’identificateurs s’affiche à la place d’IntelliSense, car la fonction encapsulée n’est jamais appelée, ce qui signifie que la `throttled` fonction ne retourne aucun résultat.

     ![Exemple de substitution de résultats IntelliSense](../ide/media/js-intellisense-override.png "js_intellisense_override")

4. Ajoutez le code suivant à exampleLib.intellisense.js. Cela modifiera le comportement au moment de la conception afin qu’IntelliSense soit affiché pour la fonction encapsulée, comme prévu.

    ```javascript
    window.after = function (count, func) {
        // Just return func.
        return func;
    };
    ```

5. Dans appCode.js, testez les résultats en tapant le même code que celui que vous avez tapé précédemment. Cette fois, IntelliSense fournit les informations souhaitées.

     ![Exemple de la substitution des résultats IntelliSense](../ide/media/js-intellisense-override-fixed.png "js_intellisense_override_fixed")

## <a name="see-also"></a>Voir aussi
 [JavaScript IntelliSense](../ide/javascript-intellisense.md) [Saisie semi-automatique des instructions JavaScript IntelliSense pour les identificateurs](../ide/statement-completion-for-identifiers.md)
