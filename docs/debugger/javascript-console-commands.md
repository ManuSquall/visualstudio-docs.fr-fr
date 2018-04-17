---
title: Commandes de JavaScript Console dans Visual Studio | Documents Microsoft
ms.custom: ''
ms.date: 07/17/2017
ms.technology:
- vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- JavaScript Console commands [UWP apps]
- JavaScript debugging, console [UWP apps]
- debugging JavaScript, console [UWP apps]
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- uwp
- cordova
ms.openlocfilehash: df4055790cf715b3a521b6ccc09d5c6920a47136
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="javascript-console-commands-in-visual-studio"></a>Commandes de JavaScript Console dans Visual Studio
  
 Vous pouvez utiliser des commandes pour envoyer des messages et effectuer d’autres tâches dans la fenêtre de console JavaScript de Visual Studio. Pour obtenir des exemples qui illustrent l’utilisation de cette fenêtre, consultez [démarrage rapide : débogage de JavaScript](../debugger/quickstart-debug-javascript-using-the-console.md). Les informations contenues dans cette rubrique s’applique aux applications UWP et les applications créées à l’aide de Visual Studio Tools pour Apache Cordova. Pour plus d’informations sur les commandes de console prises en charge dans les applications Cordova, consultez [déboguer votre application](https://taco.visualstudio.com/en-us/docs/debug-using-visual-studio/). Pour obtenir des informations sur l’utilisation de la console dans les outils de développement F12 d’Internet Explorer, consultez [cette rubrique](http://msdn.microsoft.com/library/ie/dn255006.aspx).  
  
 Si la fenêtre de la console JavaScript est fermée, vous pouvez l’ouvrir pendant le débogage dans Visual Studio en choisissant **Déboguer** > **Windows** > **Console JavaScript**.  
  
> [!NOTE]
>  Si la fenêtre n’est pas disponible pendant une session de débogage, vérifiez que le type de débogueur est défini sur **Script** dans les propriétés de débogage du projet.  
  
## <a name="console-object-commands"></a>commandes d’objet de la console  
 Cette table montre la syntaxe des commandes de l’objet `console` , que vous pouvez utiliser dans la fenêtre de la console JavaScript ou pour envoyer des messages à la console à partir de votre code. Cet objet fournit plusieurs formes afin de pouvoir distinguer les messages d’informations et les messages d’erreur, si vous le souhaitez.  
  
 Utilisez la forme de commande plus longue `window.console.[command]` si vous devez éviter toute confusion possible avec les objets locaux nommés console.  
  
> [!TIP]
>  Les versions antérieures de Visual Studio ne prennent pas en charge l’ensemble complet des commandes. Utilisez IntelliSense sur l’objet console pour obtenir rapidement des informations sur les commandes prises en charge.  
  
|Commande|Description|Exemple|  
|-------------|-----------------|-------------|  
|`assert(expression, message)`|Envoie un message si `expression` correspond à **false**.|`console.assert((x == 1), "assert message: x != 1");`|  
|`clear()`|Efface les messages de la fenêtre de console, y compris les messages d’erreur de script. Efface également les scripts apparaissant dans la fenêtre de console. N’efface pas le script entré dans l’invite d’entrée de la console.|`console.clear();`|  
|`count(title)`|Envoie le nombre de fois que la commande count a été appelée dans la fenêtre de console. Chaque appel de count est identifié de façon unique par le paramètre facultatif `title`.<br /><br /> L’entrée existant dans la fenêtre de console est identifiée par le paramètre `title` (le cas échéant) et mise à jour par la commande count. Une nouvelle entrée n’est pas créée.|`console.count();`<br /><br /> `console.count("inner loop");`|  
|`debug(message)`|Envoie `message` dans la fenêtre de la console.<br /><br /> Cette commande est identique à console.log.<br /><br /> Les objets qui sont passés à l’aide de la commande sont convertis en valeur de chaîne.|`console.debug("logging message");`|  
|`dir(object)`|Envoie l’objet spécifié dans la fenêtre de console et l’affiche dans un visualiseur d’objets. Utilisez le visualiseur pour examiner les propriétés dans la fenêtre de la console.|`console.dir(obj);`|  
|`dirxml(object)`|Envoie le nœud XML spécifié `object` dans la fenêtre de console et l’affiche sous forme d’arborescence de nœuds XML.|`console.dirxaml(xmlNode);`|  
|`error(message)`|Envoie `message` dans la fenêtre de la console. Le texte du message est rouge et précédé d’un symbole d’erreur.<br /><br /> Les objets qui sont passés à l’aide de la commande sont convertis en valeur de chaîne.|`console.error("error message");`|  
|`group(title)`|Démarre le regroupement des messages envoyés à la fenêtre de console, puis envoie le paramètre facultatif `title` comme étiquette de groupe. Les groupes peuvent être imbriqués et s’affichent dans une arborescence dans la fenêtre de console.<br /><br /> Les commandes group* peuvent faciliter l’affichage de la sortie de la fenêtre de console dans certains scénarios, par exemple lorsqu’un modèle de composant est en cours d’utilisation.|`console.group("Level 2 Header");` <br /> `console.log("Level 2");` <br /> `console.group();` <br /> `console.log("Level 3");` <br /> `console.warn("More of level 3");` <br /> `console.groupEnd();` <br /> `console.log("Back to level 2");` <br /> `console.groupEnd();` <br /> `console.debug("Back to the outer level");`|  
|`groupCollapsed(title)`|Démarre le regroupement des messages envoyés à la fenêtre de console, puis envoie le paramètre facultatif `title` comme étiquette de groupe. Les groupes qui sont envoyés à l’aide de `groupCollapsed` s’affichent dans un affichage réduit par défaut. Les groupes peuvent être imbriqués et s’affichent dans une arborescence dans la fenêtre de console.|La syntaxe est la même que pour la commande `group` .<br /><br /> Consultez l’exemple correspondant à la commande `group` .|  
|`groupEnd()`|Met fin au groupe actif.<br /><br /> Configuration requise :<br /><br /> Visual Studio 2013|Consultez l’exemple correspondant à la commande `group` .|  
|`info(message)`|Envoie `message` dans la fenêtre de la console. Le message est précédée d’un symbole d’informations.|`console.info("info message");`<br /><br /> Pour des exemples supplémentaires, consultez [Formatting console.log output](#ConsoleLog) plus loin dans cette rubrique.|  
|`log(message)`|Envoie `message` dans la fenêtre de la console.<br /><br /> Si vous passez un objet, cette commande l’envoie à la fenêtre de la console et l’affiche dans un visualiseur d’objets. Utilisez le visualiseur pour examiner les propriétés dans la fenêtre de la console.|`console.log("logging message");`|  
|`msIsIndependentlyComposed(element)`|Utilisée dans les applications web. Non pris en charge dans les applications UWP à l’aide de JavaScript.|Non pris en charge.|  
|`profile(reportName)`|Utilisée dans les applications web. Non pris en charge dans les applications UWP à l’aide de JavaScript.|Non pris en charge.|  
|`profileEnd()`|Utilisée dans les applications web. Non pris en charge dans les applications UWP à l’aide de JavaScript.|Non pris en charge.|  
|`select(element)`|Sélectionne le code HTML spécifié `element` dans les [l’Explorateur DOM](../debugger/quickstart-debug-html-and-css.md).|console.select(element);|  
|`time (name)`|Démarre une minuterie identifiée par le paramètre facultatif `name` . Utilisée avec `console.timeEnd`, calcule le temps qui s’écoule entre `time` et `timeEnd`, puis envoie le résultat (mesuré en ms) à la console à l’aide de la chaîne `name` comme préfixe. Utilisée pour permettre l’instrumentation du code d’application pour mesurer les performances.|`console.time("app start");  app.start();  console.timeEnd("app start");`|  
|`timeEnd(name)`|Arrête une minuterie identifiée par le paramètre facultatif `name` . Consultez la commande de console `time` .|`console.time("app start"); app.start(); console.timeEnd("app start");`|  
|`trace()`|Envoie une trace de la pile à la fenêtre de console. La trace comprend la pile d’appels complète, ainsi que des informations telles que le nom de fichier, le numéro de ligne et le numéro de colonne.|`console.trace();`|  
|`warn(message)`|Envoie `message` dans la fenêtre de la console, précédée d’un symbole d’avertissement.<br /><br /> Les objets qui sont passés à l’aide de la commande sont convertis en valeur de chaîne.|`console.warn("warning message");`|  
  
## <a name="miscellaneous-commands"></a>Commandes diverses  
 Ces commandes sont également disponibles dans la fenêtre de la console JavaScript (elles ne sont pas disponibles à partir du code).  
  
|Commande|Description|Exemple|  
|-------------|-----------------|-------------|  
|`$0`, `$1`, `$2`, `$3`, `$4`|Retourne l’élément spécifié dans la fenêtre de console. `$0` retourne l'élément actuellement sélectionné dans l'Explorateur DOM, `$1` retourne l'élément précédemment sélectionné dans l'Explorateur DOM, et ainsi de suite, jusqu'au quatrième élément sélectionné précédemment.|$3|  
|`$(id)`|Retourne un élément par ID. Il s’agit d’une commande de raccourci pour `document.getElementById(id)`, où `id` est une chaîne qui représente l’ID d’élément.|`$("contenthost")`|  
|`$$(selector)`|Retourne un tableau des éléments qui correspondent au sélecteur spécifié à l’aide de la syntaxe du sélecteur CSS. Il s’agit d’une commande de raccourci pour `document.querySelectorAll()`.|`$$(".itemlist")`|  
|`cd()`<br /><br /> `cd(window)`|Permet de modifier le contexte pour l’évaluation des expressions de la fenêtre de niveau supérieur par défaut de la page jusqu’à la fenêtre du frame spécifié. L’appel de `cd()` sans paramètres retourne le contexte dans la fenêtre de niveau supérieur.|`cd();`<br /><br /> `cd(myframe);`|  
|`select(element)`|Sélectionne l’élément spécifié dans [l’Explorateur DOM](../debugger/quickstart-debug-html-and-css.md).|`select(document.getElementById("element"));`<br /><br /> `select($("element"));`<br /><br /> `select($1);`|  
|`dir(object)`|Retourne un visualiseur pour l’objet spécifié. Utilisez le visualiseur pour examiner les propriétés dans la fenêtre de la console.|`dir(obj);`|  
  
## <a name="checking-whether-a-console-command-exists"></a>Vérifier s’il existe une commande de console  
 Vous pouvez vérifier s’il existe une commande spécifique avant de tenter de l’utiliser. Cet exemple vérifie l’existence de la commande `console.log` . Si `console.log` existe, le code l’appelle.  
  
```javascript  
if (console && console.log) {  
    console.log("msg");  
}  
  
```  
  
## <a name="examining-objects-in-the-javascript-console-window"></a>Examen des objets de la fenêtre de console JavaScript  
 Lorsque vous utilisez la fenêtre de console JavaScript, vous pouvez interagir avec un objet qui est dans la portée. Pour examiner un objet hors de portée dans la fenêtre de la console, utilisez les commandes `console.log` , `console.dir`ou d’autres commandes à partir de votre code. Sinon, vous pouvez interagir avec l’objet dans la fenêtre de la console pendant qu’il est dans la portée en définissant un point d’arrêt dans votre code (**Point d’arrêt** > **Insert Point d’arrêt**).  
  
##  <a name="ConsoleLog"></a> Mise en forme la sortie de console.log  
 Si vous passez plusieurs arguments à `console.log`, la console les traite sous forme de tableau et concatène la sortie.  
  
```javascript  
var user = new Object();  
user.first = "Fred";  
user.last = "Smith";  
  
console.log(user.first, user.last);  
// Output:  
// Fred Smith  
  
```  
  
 `console.log` prend également en charge les modèles de substitution "printf" pour mettre en forme la sortie. Si vous utilisez des modèles de substitution dans le premier argument, les arguments supplémentaires servent à remplacer les modèles spécifiés dans l’ordre où ils sont utilisés.  
  
 Les modèles de substitution suivants sont pris en charge :  
  
-   %s - chaîne  
     %i - entier  
     %d - entier  
     %f - flottant  
     %o - objet  
     %b - binaire  
     %x - hexadécimal  
     %e - exposant  
  
 Voici quelques exemples d’utilisation de modèles de substitution dans `console.log`:  
  
```javascript  
var user = new Object();  
user.first = "Fred";  
user.last = "Smith";  
user.age = 10.01;  
console.log("Hi, %s %s!", user.first, user.last);  
console.log("%s is %i years old!", user.first, user.age);  
console.log("%s is %f years old!", user.first, user.age);  
  
// Output:  
// Hi, Fred Smith!  
// Fred is 10 years old!  
// Fred is 10.01 years old!  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Démarrage rapide : Déboguer du code JavaScript](../debugger/quickstart-debug-javascript-using-the-console.md)   
 [Démarrage rapide : déboguer du code HTML et CSS](../debugger/quickstart-debug-html-and-css.md)