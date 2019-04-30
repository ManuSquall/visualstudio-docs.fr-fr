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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: e995d9cfd37c625c03df0b607a9dd5184bec5d08
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63441466"
---
# <a name="extending-javascript-intellisense"></a>Extension de JavaScript IntelliSense
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La fonctionnalité d’extensibilité JavaScript IntelliSense vous permet de personnaliser les résultats d’IntelliSense dans l’éditeur JavaScript pour des bibliothèques tierces. Cela peut améliorer l’expérience de développeurs qui utilisent ces bibliothèques.  
  
 Le service de langage JavaScript offre des fonctionnalités IntelliSense pour les bibliothèques JavaScript tierces qui sont ajoutés à un projet. Pour la plupart des bibliothèques, la saisie semi-automatique des instructions sont fournie automatiquement par le service de langage. L’illustration suivante montre un exemple de saisie semi-automatique des instructions :  
  
 ![Exemple de saisie semi-automatique des instructions](../ide/media/js-intellisense-completion.png "js_intellisense_completion")  
  
 Si votre bibliothèque inclut les descriptions des variables, fonctions et objets dans des balises de commentaire JavaScript standard (/ /), vous bénéficiez automatiquement, par défaut, dans les fonctionnalités d’extensibilité IntelliSense, qui fournissent des informations descriptives dans une fenêtre indépendante qui apparaît à droite des éléments dans une liste de saisie semi-automatique, ou lorsque vous tapez la parenthèse ouvrante dans un appel de fonction. Les commentaires dans la zone contextuelle contiennent la description du membre. L’exemple suivant montre la zone contextuelle pour une liste de saisie semi-automatique.  
  
 ![Exemple d’un point de présence Info Express&#45;boîte](../ide/media/js-intellisense-quickinfo.png "js_intellisense_quickinfo")  
  
 Pour améliorer l’expérience de développement, vous souhaiterez peut-être fournissent des informations de type pour les développeurs dans la zone contextuelle. Vous pouvez fournir des informations de type à l’aide de JavaScript [commentaires de Documentation XML](../ide/xml-documentation-comments-javascript.md) au lieu de balises de commentaire standard. Vous ajoutez des commentaires de Documentation XML à l’aide de balises de commentaire de trois barres obliques (/ / /) et un ensemble défini d’éléments XML.  
  
 Ou bien, vous pouvez fournir des informations de type à l’aide d’extensibilité JavaScript IntelliSense. Cette fonctionnalité vous permet de personnaliser les résultats d’IntelliSense en créant des extensions de JavaScript et les ajouter au contexte de script. Dans l’extension, qui est un fichier JavaScript, vous vous abonnez à des événements qui sont exposées par le `intellisense` objet du service de langage. Extensibilité JavaScript IntelliSense est la solution pour les bibliothèques par défaut si un modèle de comportement dans la bibliothèque empêche le service de langage JavaScript de fournir le niveau de prise en charge IntelliSense souhaité et si une alternative à XML déclaratif Commentaires de documentation est également nécessaire. En personnalisant les résultats d’IntelliSense, vous pouvez créer une expérience de première classe IntelliSense, quel que soit les modèles de comportement qui peut restreindre les capacités de valeur par défaut du service de langage. Pour plus d'informations, consultez [Saisie semi-automatique des instructions pour les identificateurs](../ide/statement-completion-for-identifiers.md).  
  
## <a name="adding-an-extension-to-the-script-context"></a>Ajout d’une Extension pour le contexte de Script  
 Pour une extension IntelliSense doit être exécuté, il doit être ajouté au contexte de script actuel. L’extension peut être ajoutée automatiquement au contexte de script par le mécanisme de découverte automatique, ou vous pouvez ajouter l’extension pour le contexte de script manuellement à l’aide de groupes de référence ou la directive de référence.  
  
 Le mécanisme de découverte automatique permet au service de langage rechercher automatiquement les extensions qui suivent la convention d’affectation de noms de fichier *nom_bibliothèque*. intellisense.js et qui se trouvent dans le même répertoire que la bibliothèque qui l’extension s’applique. Par exemple, une extension valide pour la bibliothèque jQuery serait jQuery.intellisense.js. Pour les extensions de jQuery plus restrictives, vous pouvez utiliser des noms de fichiers telles que jQuery-1.7.1.intellisense.js (une extension spécifique à la version) ou jQuery.ui.intellisense.js (il s’agit d’une extension pour une bibliothèque jQuery avec étendue). La version la plus restrictive de l’extension est utilisée si plusieurs extensions sont trouvée pour une bibliothèque donnée.  
  
 Si vous souhaitez utiliser l’extension pour tous les fichiers de votre projet JavaScript, vous pouvez choisir à la place ajouter l’extension à un groupe de référence. Il existe plusieurs types de groupes de référence, soit ceux qui incluent des références implicites et ceux qui incluent des références de travail dédié. Pour ajouter une extension, vous devez généralement ajouter le fichier en tant qu’un groupe de référence implicite, soit **implicite (Windows)**, **implicite (Web)**. Références implicites sont dans la portée de chaque fichier .js ouvert dans l’éditeur de Code. Lorsque vous utilisez cette méthode, vous devez ajouter l’extension et le fichier en complément de l’extension.  
  
 Utilisez le **IntelliSense** page de la **Options** boîte de dialogue Ajouter une extension comme un groupe de référence. Vous pouvez accéder à la **IntelliSense** page en choisissant **outils**, **Options** dans la barre de menus, puis en sélectionnant **éditeur de texte**, **JavaScript**, **IntelliSense**, **références**. Pour plus d’informations sur les groupes de référence, consultez [JavaScript IntelliSense](../ide/javascript-intellisense.md) et [Options, éditeur de texte, JavaScript, IntelliSense](../ide/reference/options-text-editor-javascript-intellisense.md).  
  
 Si vous souhaitez utiliser l’extension pour un ensemble spécifique de fichiers, utilisez une directive de référence. Lorsque vous utilisez cette méthode, vous devez référencer l’extension et le fichier en complément de l’extension. Pour plus d’informations sur l’utilisation de la directive de référence, consultez [JavaScript IntelliSense](../ide/javascript-intellisense.md).  
  
## <a name="handling-intellisense-events"></a>Gestion des événements d’IntelliSense  
 La fonctionnalité d’extensibilité vous permet de personnaliser les résultats d’IntelliSense en vous abonnant aux événements tels que le `statementcompletion` événement du service de langage `intellisense` objet. L’exemple suivant montre une extension simple qui est utilisée par le service de langage pour masquer les membres qui commencent par un trait de soulignement à partir de la saisie semi-automatique des instructions. Ce code est contenu dans underscorefilter.js et se trouve dans le \\ \\ *chemin d’installation de Visual Studio*\JavaScript\References dossier.  
  
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
  
 Dans le code précédent, l’extension vérifie le [targetName propriété](#TargetName) et [propriété cible](#Target) propriétés de la `statementcompletion` objet d’événement pour exclure des objets tels que `this` et `window`et pour vous assurer qu’une liste de saisie semi-automatique d’instruction valide peut être identifiée. Si une liste de saisie semi-automatique peut être identifiée, l’extension met à jour la saisie semi-automatique des instructions [propriété des éléments](#Items) collection en filtrant les membres qui commencent par un trait de soulignement.  
  
 Pour obtenir des exemples supplémentaires, recherchez dans le \\ \\ *chemin d’installation de Visual Studio*\JavaScript\References dossier. Le fichier showPlainComments.js dans ce dossier fournit des exemples d’utilisation d’autres événements pour prendre en charge de IntelliSense par défaut des étiquettes de commentaires JavaScript standards (/ /). Comme underscorefilter.js, showPlainComments.js est déjà disponible en tant qu’une extension de travail, et vous pouvez voir les informations IntelliSense lors de l’utilisation de balises de commentaire dans votre code pour les variables, fonctions et objets. Pour obtenir des exemples supplémentaires, consultez [exemples de Code](#CodeExamples).  
  
> [!WARNING]
> Si vous modifiez les fichiers d’extension inclus avec Visual Studio, vous pouvez désactiver JavaScript IntelliSense ou la fonctionnalité de prise en charge par l’extension.  
  
 Dans votre code d’extension, vous pouvez créer des gestionnaires pour les types d’événements à l’aide de `addEventListener`:  
  
- `statementcompletion`, qui ajoute un gestionnaire pour un événement de fin d’instruction. Saisie semi-automatique des instructions fournit une liste de membres pour un type particulier qui apparaît une fois que vous tapez un caractère spécial, comme un point (.) ou une liste d’identificateurs qui s’affiche en cours de frappe ou lorsque vous appuyez sur CTRL + J. Le gestionnaire reçoit un objet d’événement de type `CompletionEvent`, qui prend en charge les membres suivants : [propriété des éléments](#Items), [propriété cible](#Target), [targetName propriété](#TargetName), et [scope, propriété](#Scope).  
  
- `signaturehelp`, qui ajoute un gestionnaire d’informations sur les paramètres IntelliSense. Informations sur les paramètres fournit des informations sur le nombre, les noms et les types de paramètres requis par une fonction. Le gestionnaire reçoit un objet d’événement de type `SignatureHelpEvent`, qui prend en charge les membres suivants : [propriété cible](#Target), [parentObject propriété](#ParentObject), [functionComments propriété](#FunctionComments), [functionHelp propriété](#FunctionHelp).  
  
- `statementcompletionhint`, qui ajoute un gestionnaire pour Info express IntelliSense. La zone contextuelle Info Express affiche la déclaration complète pour les identificateurs dans votre code. Le gestionnaire reçoit un objet d’événement de type `CompletionHintEvent`, qui prend en charge les membres suivants : [completionItem propriété](#CompletionItem), et [symbolHelp propriété](#SymbolHelp).  
  
  Pour obtenir des exemples qui montrent les fonctionnalités IntelliSense telles que la saisie semi-automatique des instructions, des informations sur les paramètres et Infos Express, consultez [IntelliSense à l’aide de](../ide/using-intellisense.md).  
  
> [!NOTE]
> Dans JavaScript, Info Express fait référence à la zone contextuelle qui apparaît à droite d’une liste de saisie semi-automatique. Vous ne pouvez pas appeler manuellement la Info Express.  
  
## <a name="intellisenseObject"></a> Objet intellisense  
 Le tableau suivant présente les fonctions qui sont disponibles pour le `intellisense` objet. Le `intellisense` objet n’est disponible uniquement au moment du design.  
  
|Fonction|Description|  
|--------------|-----------------|  
|`addEventListener(type, handler);`|Ajoute un gestionnaire d’événements pour un événement d’IntelliSense.<br /><br /> `type` est une valeur de chaîne. Les valeurs valides sont `statementcompletion`, `signaturehelp` et `statementcompletionhint`.<br /><br /> `handler` est une fonction de gestionnaire d’événements qui reçoit un objet d’événement d’un des types suivants :<br /><br /> -   `CompletionEvent`, utilisé pour le `statementcompletion` événement.<br />-   `SignatureHelpEvent`, utilisé pour le `signaturehelp` événement.<br />-   `CompletionHintEvent`, utilisé pour le `statementcompletionhint` événement.<br /><br /> Pour obtenir des exemples qui utilisent cette fonction, consultez [exemples de Code](#CodeExamples).|  
|`annotate(obj, doc);`|Spécifie la documentation pour un objet en copiant les commentaires de documentation à partir d’un objet à un autre objet.<br /><br /> `obj` Spécifie l’objet vers lequel copier la documentation.<br /><br /> `doc` Spécifie l’objet à partir duquel copier la documentation.<br /><br /> Pour obtenir un exemple qui montre comment utiliser cette fonction, consultez [Ajout des Annotations IntelliSense](#Annotations).|  
|`getFunctionComments(func);`|Retourne les commentaires pour une fonction spécifiée.<br /><br /> `func` Spécifie la fonction pour laquelle les commentaires sont retournés.<br /><br /> Vous pouvez définir le `func` paramètre à l’aide de `completionItem.value`.<br /><br /> Retourné `functionComments` objet inclut les membres suivants : `above`, `inside`, et `paramComment`. Pour plus d’informations, consultez le [functionComments propriété](#FunctionComments) propriété.<br /><br /> `getFunctionComments` peut être appelée uniquement à partir d’un des gestionnaires d’événements qui sont inscrits par `addEventListener`.<br /><br /> Pour obtenir un exemple qui montre comment utiliser cette fonction, consultez \\ \\ *chemin d’installation de Visual Studio*\JavaScript\References\showPlainComments.js.|  
|`logMessage(msg);`|Envoie des messages de diagnostic dans la fenêtre Sortie.<br /><br /> `msg` est une chaîne qui contient le message.<br /><br /> Pour obtenir un exemple qui montre comment utiliser cette fonction, consultez [envoi de Messages dans la fenêtre sortie](#Logging).|  
|`nullWithCompletionsOf(value);`|Retourne une valeur null spéciale pour lequel la liste de saisie semi-automatique est déterminée par l’objet passé dans le `value` paramètre.<br /><br /> `value` Détermine la liste de saisie semi-automatique de la valeur retournée. `value` peut être n’importe quel type.<br /><br /> La valeur de retournée null est traitée comme null au moment du design, mais la liste de saisie semi-automatique pour la valeur de retour est identique à la liste de saisie semi-automatique pour le `value` paramètre.<br /><br /> Une utilisation de cette fonction est de fournir IntelliSense pour une valeur de retour lorsque le type de retour est prévisible lors de l’exécution, mais la valeur de retour est `null` au moment du design.|  
|`redirectDefinition(func, definition);`|Indique à IntelliSense à utiliser la fonction de la définition fournie au lieu de la fonction %{func/} d’origine lors de l’aide sur les paramètres ou **atteindre la définition** est demandée.<br /><br /> `func` Spécifie la fonction cible.<br /><br /> `definition` Spécifie la fonction à utiliser pour les informations de paramètre au lieu de la fonction cible et **atteindre la définition**.|  
|`setCallContext(func, thisArg);`|Définit le contexte d’appel, ou étendue, pour la fonction spécifiée.<br /><br /> `func` Spécifie la fonction pour laquelle définir l’étendue.<br /><br /> `thisArg` est un objet littéral auquel le `this` mot clé peut faire référence, qui spécifie la nouvelle étendue pour le membre. Vous pouvez inclure des arguments à passer dans ce paramètre, par exemple, `intellisense.setCallContext(func, { thisArg: "", args: [23,2] });`<br /><br /> `setCallContext` fournit un comportement similaire à `Function.prototype.bind`, sauf qu’il est utilisé uniquement pour la prise en charge de IntelliSense au moment du design. Vous pouvez utiliser `setCallContext` pour définir l’étendue de la fonction si vous avez besoin simuler un appel au code qui est sinon inaccessible, afin que lorsque vous appelez la fonction, l’appel de fonction inclura les arguments et l’étendue correcte.|  
|`undefinedWithCompletionsOf(value);`|Retourne une valeur non définie spéciale pour lequel la liste de saisie semi-automatique est déterminée par l’objet passé dans le `value` paramètre.<br /><br /> `value` Détermine la liste de saisie semi-automatique de la valeur retournée. `value` peut être n’importe quel type.<br /><br /> Retourne l’undefined est considérée comme non défini au moment du design, mais l’achèvement liste pour la valeur de retour est identique à la liste de saisie semi-automatique pour le `value` paramètre.<br /><br /> Une utilisation de cette fonction consiste à fournir une expérience IntelliSense pour une valeur de retour lorsque le type de retour est prévisible lors de l’exécution, mais la valeur de retour n’est pas définie au moment du design.|  
|`version()`|Retourne la version de Visual Studio.|  
  
## <a name="event-members"></a>Membres de l’événement  
 Les sections suivantes décrivent les membres qui sont exposés dans l’objet d’événement pour les événements suivants : `statementcompletion`, `signaturehelp`, et `statementcompletionhint`.  
  
### <a name="CompletionItem"></a> completionItem, propriété  
 Retourne l’identificateur, appelé l’élément de saisie semi-automatique, pour laquelle une info-bulle Info rapide est demandée. Cette propriété est disponible pour le `statementcompletionhint` objet d’événement et pour le [propriété des éléments](#Items) propriété de la `statementcompletion` objet d’événement.  
  
 Valeur de retour : `completionItem` objet  
  
 Voici les membres de la `completionItem` objet :  
  
- `name`. En lecture/écriture lorsqu’il est utilisé dans le `items` collection ; sinon, en lecture seule. Retourne une chaîne qui identifie l’élément de saisie semi-automatique.  
  
- `kind`. En lecture/écriture lorsqu’il est utilisé dans le `items` collection ; sinon, en lecture seule. Retourne une chaîne qui représente le type d’élément de saisie semi-automatique. Les valeurs possibles sont une méthode, champ, propriété, paramètre, variable et réservé.  
  
- `glyph`. En lecture/écriture lorsqu’il est utilisé dans le `items` collection ; sinon, en lecture seule. Retourne une chaîne qui représente une icône qui s’affiche dans la liste de saisie semi-automatique. Les valeurs possibles pour `glyph` utilisez le format suivant : vs :*glyphType*, où *glyphType* correspond aux membres indépendants du langage dans le <xref:Microsoft.VisualStudio.Language.Intellisense.StandardGlyphGroup> énumération. Par exemple, `vs:GlyphGroupMethod` est une valeur possible pour `glyph`. Lorsque `glyph` n’est pas définie, le `kind` propriété détermine l’icône par défaut.  
  
- `parentObject`. Lecture seule. Retourne l’objet parent.  
  
- `value`. Lecture seule. Retourne un objet qui représente la valeur de l’élément de saisie semi-automatique.  
  
- `comments`. Lecture seule. Retourne une chaîne qui contient les commentaires qui se trouvent au-dessus du champ ou de variable.  
  
- `scope`. Lecture seule. Retourne la portée de l’élément de saisie semi-automatique. Les valeurs possibles sont le paramètre global, local et membre.  
  
### <a name="Items"></a> éléments de propriété  
 Obtient ou définit le tableau d’instruction éléments de saisie semi-automatique. Chaque élément du tableau est un [completionItem propriété](#CompletionItem) objet. Le `items` propriété n’est disponible pour le `statementcompletion` objet d’événement.  
  
 Valeur de retour : tableau  
  
### <a name="FunctionComments"></a> functionComments, propriété  
 Retourne les commentaires pour la fonction. Cette propriété est disponible pour le `signaturehelp` objet d’événement.  
  
 Valeur de retour : `comments` objet  
  
 Voici les membres de la `comments` objet :  
  
- `above`. Retourne les commentaires au-dessus de la fonction.  
  
- `inside`. Retourne les commentaires à l’intérieur de la fonction, généralement au format de VSDoc.  
  
- `paramComments`. Retourne un tableau qui représente des commentaires pour chaque paramètre dans la fonction. Les membres du tableau sont les suivantes :  
  
    - `name`. Retourne une chaîne représentant le nom du paramètre.  
  
    - `comment`. Retourne une chaîne qui contient le paramètre de commentaire.  
  
### <a name="FunctionHelp"></a> functionHelp, propriété  
 Retourne à l’aide de la fonction. Cette propriété est disponible pour le `signaturehelp` objet d’événement.  
  
 Valeur de retour : `functionHelp` objet  
  
 Voici les membres de la `functionHelp` objet :  
  
- `functionName`. Lecture/écriture. Retourne une chaîne qui contient le nom de fonction.  
  
- `signatures`. Lecture/écriture. Obtient ou définit le tableau de signatures de fonction. Chaque élément du tableau est un `signature` objet. Certains `signature` propriétés, telles que `locid`, correspondent aux commun [commentaires de Documentation XML](../ide/xml-documentation-comments-javascript.md) attributs.  
  
     Les membres de la `signature` objet incluent :  
  
    - `description`. Lecture/écriture. Retourne une chaîne qui décrit la fonction.  
  
    - `locid`. Lecture/écriture. Retourne un identificateur de chaîne qui contient les informations de localisation de la fonction.  
  
    - `helpKeyword`. Lecture/écriture. Retourne une chaîne qui contient le mot clé d’aide.  
  
    - `externalFile`. Lecture/écriture. Retourne une chaîne qui représente le fichier qui contient l’ID de membre.  
  
    - `externalid`. Lecture/écriture. Retourne une chaîne qui représente l’ID de membre de la fonction.  
  
    - `params`. Lecture/écriture. Obtient ou définit le tableau de paramètres pour la fonction. Chaque élément dans le tableau de paramètres est un `parameter` objet qui possède des propriétés qui correspondent aux attributs suivants de la [ \<param >](../ide/param-javascript.md) élément :  
  
        - `name`. Lecture/écriture. Retourne une chaîne qui représente le nom du paramètre.  
  
        - `type`. Lecture/écriture. Retourne une chaîne qui représente le type de paramètre.  
  
        - `elementType`. Lecture/écriture. Si le type est `Array`, retourne une chaîne qui représente le type des éléments dans le tableau.  
  
        - `description`. Lecture/écriture. Retourne une chaîne qui décrit le paramètre.  
  
        - `locid`. Lecture/écriture. Retourne un identificateur de chaîne qui contient les informations de localisation de la fonction.  
  
        - `optional`. Lecture/écriture. Retourne une chaîne qui indique si le paramètre est facultatif. `true` Indique que le paramètre est facultatif ; `false` indique qu’il n’est pas.  
  
    - `returnValue`. Lecture/écriture. Obtient ou définit un objet de valeur de retour avec des propriétés qui correspondent aux attributs suivants de la [ \<retourne >](../ide/returns-javascript.md) élément :  
  
        - `type`. Lecture/écriture. Retourne une chaîne qui représente le type de retour.  
  
        - `elementType`. Lecture/écriture. Si le type est `Array`, retourne une chaîne qui représente le type des éléments dans le tableau.  
  
        - `description`. Lecture/écriture. Retourne une chaîne qui décrit la valeur de retour.  
  
        - `locid`. Lecture/écriture. Retourne un identificateur de chaîne qui contient les informations de localisation de la fonction.  
  
        - `helpKeyword`. Lecture/écriture. Retourne une chaîne qui contient le mot clé d’aide.  
  
        - `externalFile`. Lecture/écriture. Retourne une chaîne qui représente le fichier qui contient l’ID de membre.  
  
        - `externalid`. Lecture/écriture. Retourne une chaîne qui représente l’ID de membre de la fonction.  
  
### <a name="ParentObject"></a> parentObject, propriété  
 Retourne l’objet parent d’une fonction membre. Par exemple, pour `document.getElementByID`, `parentObject` retourne le `document` objet. Cette propriété est disponible pour le `signaturehelp` objet d’événement.  
  
 Valeur de retour : objet  
  
### Propriété target <a name="Target"></a>  
 Retourne un objet qui représente l’élément à gauche du caractère déclencheur, qui est un point (.). Pour les fonctions, `target` retourne la fonction pour laquelle les informations sur les paramètres sont demandées. Cette propriété est disponible pour le `statementcompletion` et `signaturehelp` objets événement.  
  
 Valeur de retour : objet  
  
### <a name="TargetName"></a> targetName, propriété  
 Retourne une chaîne qui représente la cible. Par exemple, pour « this. », `targetName` retourne « this ». Pour « A.B » (lorsque le curseur se trouve après « B »), `targetName` retourne « B ». Cette propriété est disponible pour le `statementcompletion` objet d’événement.  
  
 Valeur de retour : chaîne  
  
### <a name="SymbolHelp"></a> symbolHelp, propriété  
 Retourne l’élément de saisie semi-automatique pour laquelle une info-bulle Info rapide est demandée. Cette propriété est disponible pour le `statementcompletionhint` objet d’événement.  
  
 Valeur de retour : `symbolHelp` objet.  
  
 Certaines propriétés de la `symbolHelp` l’objet, tel que `locid`, correspondent aux commun [commentaires de Documentation XML](../ide/xml-documentation-comments-javascript.md) attributs.  
  
 Voici les membres de la `symbolHelp` objet :  
  
- `name`. Lecture/écriture. Retourne une chaîne qui contient le nom d’identificateur.  
  
- `symbolType`. Lecture/écriture. Retourne une chaîne qui représente le type de symbole. Les valeurs possibles sont inconnu, booléen, nombre, chaîne, objet, fonction, tableau, Date et Regex.  
  
- `symbolDisplayType`. Lecture/écriture. Retourne une chaîne qui contient le nom de type à afficher. Si `symbolDisplayType` n’est pas définie, `symbolType` est utilisé.  
  
- `elementType`. Lecture/écriture. Si le `symbolType` est `Array`, retourne une chaîne qui représente le type des éléments dans le tableau.  
  
- `scope`. Lecture/écriture. Retourne une chaîne qui représente la portée du symbole. Les valeurs possibles incluent le paramètre global, local et membre.  
  
- `description`. Lecture/écriture. Retourne une chaîne qui contient une description du symbole.  
  
- `locid`. Lecture/écriture. Retourne un identificateur de chaîne qui contient des informations de localisation sur le symbole.  
  
- `helpKeyword`. Lecture/écriture. Retourne une chaîne qui contient le mot clé d’aide.  
  
- `externalFile`. Lecture/écriture. Retourne une chaîne qui représente le fichier qui contient l’ID de membre.  
  
- `externalid`. Lecture/écriture. Retourne une chaîne qui représente l’ID de membre du symbole.  
  
- `functionHelp`. Lecture/écriture. Retourne un [functionHelp propriété](#FunctionHelp), qui peuvent contenir des informations lorsque le `symbolType` est la fonction.  
  
### <a name="Scope"></a> Scope, propriété  
 Retourne la portée de l’achèvement de l’événement. Les valeurs possibles pour l’achèvement d’étendue sont global et des membres. Cette propriété est disponible pour le `statementcompletion` objet d’événement.  
  
 Valeur de retour : chaîne  
  
## <a name="debugging-intellisense-extensions"></a>Débogage d’extensions IntelliSense  
 Vous ne pouvez pas déboguer des extensions, mais vous pouvez utiliser la [intellisense objet](#intellisenseObject) (fonction) pour envoyer des informations à la fenêtre Sortie de Visual Studio. Pour obtenir un exemple qui montre comment utiliser cette fonction, consultez [envoi de Messages dans la fenêtre sortie](#Logging) plus loin dans cette rubrique. Pour `logMessage` pour fonctionner, au moins un gestionnaire d’événements doit être inscrite dans une extension.  
  
## <a name="CodeExamples"></a> Exemples de code  
 Cette section inclut des exemples de code qui montrent comment utiliser les API d’extensibilité IntelliSense. Il existe également d’autres façons d’utiliser ces API. Pour obtenir des exemples supplémentaires, consultez les fichiers suivants dans le \\ \\ *chemin d’installation de Visual Studio*\JavaScript\References dossier. Ceux-ci fonctionnent exemples utilisés par le service de langage JavaScript.  
  
- underscoreFilter.js. Ce code masque les membres privés d’IntelliSense. Il inclut des gestionnaires d’événements pour le `statementcompletion` événement.  
  
- showPlainComments.js. Ce code fournit la prise en charge IntelliSense pour les commentaires standards. Il inclut des gestionnaires d’événements pour le `signaturehelp` et `statementcompletionhint` événements.  
  
### <a name="Annotations"></a> Ajout d’Annotations IntelliSense  
 La procédure suivante montre comment fournir la prise en charge de la documentation IntelliSense pour une bibliothèque tierce sans modifier directement de la bibliothèque. Pour ce faire, vous pouvez utiliser `intellisense.annotate` dans une extension.  
  
 Pour que cet exemple fonctionne, vous avez besoin des fichiers JavaScript suivants dans votre projet :  
  
- demoLib.js, qui est un fichier de projet qui représente une bibliothèque tierce.  
  
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
  
4. Dans appCode.js, tapez le code suivant. Vous verrez les commentaires de documentation XML dans l’extension affiché sous la forme d’informations sur les paramètres IntelliSense.  
  
     ![Exemple illustrant l’utilisation de l’annotation IntelliSense](../ide/media/js-intellisense-annotate-paraminfo.png "js_intellisense_annotate_paraminfo")  
  
5. Dans appCode.js, tapez le code suivant. En cours de frappe, vous verrez les commentaires standards dans l’extension affiché sous la forme d’Info express IntelliSense.  
  
     ![Exemple illustrant l’utilisation de l’annotation IntelliSense](../ide/media/js-intellisense-annotations.png "js_intellisense_annotations")  
  
### <a name="Logging"></a> Envoi de Messages dans la fenêtre Sortie  
 La procédure suivante montre comment envoyer des messages dans la fenêtre Sortie. Vous pouvez envoyer des messages pour aider à déboguer des extensions IntelliSense.  
  
 Pour que cet exemple fonctionne, vous avez besoin des fichiers JavaScript suivants dans votre projet :  
  
- exampleLib.js, qui est un fichier de projet qui représente une bibliothèque tierce.  
  
- exampleLib.intellisense.js, qui est l’extension IntelliSense. Ce fichier n’a pas besoin d’être inclus dans le projet, mais il doit se trouver dans le même dossier que exampleLib.js.  
  
- appCode.js, qui est un fichier projet qui représente le code de l'application.  
  
##### <a name="to-send-a-message-to-the-output-window"></a>Pour envoyer un message dans la fenêtre Sortie  
  
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
  
4. Dans la fenêtre Sortie, choisissez **Service de langage JavaScript** dans le **afficher la sortie à partir de** liste. (Pour afficher la fenêtre Sortie, sélectionnez **sortie** dans le menu Affichage.)  
  
5. Dans appCode.js, tapez le code suivant. En cours de frappe, la fenêtre Sortie affiche des messages à partir du service de langage. Le premier message dans la fenêtre Sortie indique que la saisie semi-automatique des instructions pour l’étendue actuelle a été demandée.  
  
    ```javascript  
    some  
    ```  
  
     Voici une vue partielle de la sortie que doit s’afficher.  
  
    ```scr  
    03:16:14.3113: statement completion for current scope requested  
    03:16:14.3113: [completion item] break, kind:reserved, scope:undefined, value:undefined  
    03:16:14.3113: [completion item] case, kind:reserved, scope:undefined, value:undefined  
    03:16:14.3113: [completion item] catch, kind:reserved, scope:undefined, value:undefined  
  
    …  
    ```  
  
6. Choisissez le **Effacer tout** bouton dans la fenêtre Sortie.  
  
7. Tapez le code suivant. Le premier message dans la fenêtre Sortie indique qu’une liste des membres a été demandée.  
  
    ```javascript  
    someVar.  
    ```  
  
     Voici une vue partielle de la sortie que doit s’afficher :  
  
    ```scr  
    03:17:43.4032: member list requested, target: someVar  
    03:17:43.4032: [completion item] a, kind:field, scope:member, value:1  
    03:17:43.4032: [completion item] b, kind:field, scope:member, value:hello  
    03:17:43.4032: [completion item] constructor, kind:method, scope:member, value:  
  
    …  
    ```  
  
### <a name="Icons"></a> Modifier les icônes IntelliSense  
 La procédure suivante montre comment modifier les icônes affichées par IntelliSense par défaut. Cela peut être utile lorsque vous fournissez des informations IntelliSense sur les concepts de bibliothèque spécifiques tels que des espaces de noms, classes, interfaces et énumérations.  
  
 Pour les valeurs d’icône disponibles, consultez <xref:Microsoft.VisualStudio.Language.Intellisense.StandardGlyphGroup>.  
  
 Pour que cet exemple fonctionne, vous avez besoin des fichiers JavaScript suivants dans votre projet :  
  
- Cette bibliothèque represens un tiers du fichier exampleLib.js, qui est un projet.  
  
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
  
4. Dans appCode.js, tapez le code suivant. En cours de frappe, vous verrez que l’icône de l’espace de noms est passée à «{}», comme est utilisé dans c#.  
  
     ![Exemple illustrant l’utilisation de la propriété glyphe](../ide/media/js-intellisense-glyph-namespace.png "js_intellisense_glyph_namespace")  
  
5. Dans appCode.js, tapez le code suivant. En cours de frappe, vous verrez une nouvelle icône d’énumération pour le membre Enum1 et une nouvelle icône de classe pour le membre SomeClass1.  
  
     ![Exemple montrant l’utilisation de la propriété glyphe](../ide/media/js-intellisense-glyph-class-enum.png "js_intellisense_glyph_class_enum")  
  
### <a name="Overriding"></a> Éviter les effets d’exécution sur les résultats d’IntelliSense  
 Le service de langage JavaScript exécute du code pour fournir des informations IntelliSense de manière dynamique. Par conséquent, comportement au moment de l’exécution peut parfois interférer avec les résultats souhaités. La procédure suivante montre comment substituer les résultats d’IntelliSense lors de comportement au moment de l’exécution des résultats dans IntelliSense incorrecte.  
  
 Pour que cet exemple fonctionne, vous avez besoin des fichiers JavaScript suivants dans votre projet :  
  
- exampleLib.js, qui est un fichier de projet qui représente une bibliothèque tierce.  
  
- exampleLib.intellisense.js, qui est l’extension IntelliSense. Ce fichier n’a pas besoin d’être inclus dans le projet, mais il doit se trouver dans le même dossier que exampleLib.js.  
  
- appCode.js, qui est un fichier projet qui représente le code de l'application.  
  
##### <a name="to-avoid-run-time-effects-on-intellisense-results"></a>Pour éviter les effets d’exécution sur les résultats d’IntelliSense  
  
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
  
     Dans le code précédent, la fonction encapsulée ignore les appels initiales, selon la valeur de `count`et ne retourne des résultats.  
  
2. Ajoutez la directive de référence suivante comme première ligne dans appCode.js. Le chemin d'accès utilisé ici indique que les fichiers JavaScript sont dans le même dossier.  
  
    ```javascript  
    /// <reference path="exampleLib.js" />  
  
    ```  
  
3. Dans appCode.js, tapez le code suivant. La liste de l’identificateur s’affiche au lieu d’IntelliSense, car la fonction encapsulée est jamais appelée, ce qui signifie que le `throttled` fonction ne retourne aucun résultat.  
  
     ![Exemple de substitution des résultats intellisense](../ide/media/js-intellisense-override.png "js_intellisense_override")  
  
4. Ajoutez le code suivant à exampleLib.intellisense.js. Cela modifiera le comportement au moment du design afin qu’IntelliSense s’affiche pour la fonction encapsulée, comme prévu.  
  
    ```javascript  
    window.after = function (count, func) {  
        // Just return func.   
        return func;  
    };  
    ```  
  
5. Dans appCode.js, les résultats des tests en tapant le même code que vous avez tapé précédemment. Cette fois-ci, IntelliSense fournit les informations souhaitées.  
  
     ![Exemple de substitution des résultats IntelliSense](../ide/media/js-intellisense-override-fixed.png "js_intellisense_override_fixed")  
  
## <a name="see-also"></a>Voir aussi  
 [JavaScript IntelliSense](../ide/javascript-intellisense.md)   
 [Saisie semi-automatique des instructions pour les identificateurs](../ide/statement-completion-for-identifiers.md)
