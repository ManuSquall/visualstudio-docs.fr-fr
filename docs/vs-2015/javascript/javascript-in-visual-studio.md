---
title: JavaScript
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-javascript
ms.topic: conceptual
ms.assetid: f3eee13e-30e4-4bc1-81f5-058d7e379b75
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b9005b6cf7f23639481505a4727f8faa08241684
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63433483"
---
# <a name="javascript-in-visual-studio"></a>JavaScript dans Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

JavaScript est un langage de premier ordre dans Visual Studio. Vous pouvez utiliser la plupart ou toutes les aides standard de modification (extraits de code, IntelliSense, etc.) lorsque vous écrivez du code JavaScript dans l'IDE de Visual Studio. Vous pouvez écrire du code JavaScript pour de nombreux types d'applications et services.

 Pour obtenir la documentation de référence du langage JavaScript, consultez [JavaScript](http://msdn.microsoft.com/library/d1et7k7c\(v=vs.94\).aspx).

 Des versions ou des extensions spécifiques de Visual Studio peuvent être nécessaires pour développer des types d’applications et des services particuliers en HTML et JavaScript. La liste suivante comporte des liens permettant d'accéder à des informations complémentaires.

- Pour créer des applications multiplateformes avec Apache Cordova, [procurez-vous Visual Studio Tools pour Apache Cordova](http://go.microsoft.com/fwlink/p/?LinkId=397606).

- Pour créer des applications [Windows Store](http://dev.windows.com/develop), [Windows Phone](http://dev.windows.com/develop) et universelles (prenant en charge les deux plateformes), [procurez-vous les outils](https://developer.microsoft.com/windows/downloads).

- Pour créer des services cloud, consultez le [site Microsoft Azure](http://azure.microsoft.com/documentation/).

- Pour créer des sites web et applications web, [consultez le site ASP.NET](http://www.asp.net/get-started/websites).

  > [!NOTE]
  > Vous pouvez créer un site web ASP.Net vide et l’utiliser pour la programmation HTML, CSS et JavaScript. Le fichier Webconfig fourni par ASP.NET permet de déboguer dans Visual Studio (ou vous pouvez utiliser les outils F12 quand vous exécutez l'application).

  L'éditeur JavaScript dans Visual Studio fournit la prise en charge IntelliSense. Pour plus d’informations, consultez [JavaScript IntelliSense](../ide/javascript-intellisense.md).

## <a name="whats-new-in-javascript"></a>Nouveautés de JavaScript
 Les nouvelles fonctionnalités de JavaScript sont répertoriées dans le tableau suivant.

|Fonctionnalité|Description|
|-------------|-----------------|
|Classes|La nouvelle syntaxe prend en charge la déclaration de [classes](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Statements/class).|
|Promesses|Les [promesses](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Promise) permettent d’effectuer un codage asynchrone simplifié et épuré. Les constructeurs de promesses sont pris en charge, ainsi que les méthodes utilitaires `all` et `race`.|
|Iterators|Vous pouvez désormais itérer des objets (tableaux et objets apparentés, itérateurs), en appelant un hook d'itération personnalisé contenant des instructions à exécuter pour la valeur de chaque propriété distincte. Pour plus d’informations, consultez [Itérateurs et générateurs](https://developer.mozilla.org/docs/Web/JavaScript/Guide/Iterators_and_Generators). **Remarque :**  Les générateurs ne sont pas pris en charge pour l'instant.|
|Fonctions de flèche|La fonction de flèche (=>) fournit une syntaxe raccourcie pour le mot clé `function` contenant une liaison `this` lexicale.|
|Nouvelles méthodes pour les objets intégrés|Les objets prédéfinis [Tableau](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Array), [Mathématiques](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Math), [Nombre](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Number), [Objet](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Object) et [Chaîne](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String) comportent de nombreuses fonctions et propriétés nouvelles pour la manipulation et l’inspection de données.|
|Améliorations du littéral d’objet|Les objets prennent désormais en charge les propriétés calculées, les définitions de méthode concises, et une syntaxe raccourcie pour les propriétés dont la valeur est initialisée à une variable du même nom. Pour plus d’informations, consultez [Création d’objets](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Object).|
|Serveurs proxy|Les [proxys](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Proxy) permettent d’attribuer aux objets un comportement personnalisé.|
|Paramètres REST|Les paramètres REST vous permettent de convertir des arguments consécutifs d’un appel de fonction en tableau. Pour plus d’informations, consultez [Fonctions](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Function).|
|Opérateur de diffusion|L’[opérateur de diffusion](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Operators/Spread_operator) (`…`) développe des expressions pouvant être itérées dans des arguments individuels. Par exemple, `a.b(…array)` est sensiblement identique à `a.b.apply(a, array)`.|
|Symbols|Les objets [symbole](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Symbol) permettent d’ajouter des propriétés à un objet existant sans risque d’interférence avec les siennes propres, sans visibilité involontaire, et sans ajout non coordonné par un autre code.|
|Chaînes de modèle|Les [chaînes de modèles](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Template_literals) sont des littéraux de chaîne qui permettent l’évaluation et la concaténation des expressions avec le littéral de chaîne.|
|Améliorations Unicode|Des améliorations ont été apportées à la prise en charge d'Unicode. Par exemple, un nouveau format de séquence d'échappement prend en charge les points de code astral (points de code avec plus de quatre chiffres hexadécimaux). Pour plus d’informations, consultez [Caractères spéciaux](https://developer.mozilla.org/docs/Web/JavaScript/Guide/Regular_Expressions#Types_of_special_characters).|
|WeakSet|Un [WeakSet](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/WeakSet) est une collection d’objets qui seront effacés de la mémoire s’ils ne sont référencés nulle part ailleurs.|
