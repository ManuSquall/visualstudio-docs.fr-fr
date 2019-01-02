---
title: JavaScript
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f3eee13e-30e4-4bc1-81f5-058d7e379b75
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bcd092ca1631f54f758cef95895d8509d14dec96
ms.sourcegitcommit: f6dd17b0864419083d0a1bf54910023045526437
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 12/27/2018
ms.locfileid: "53802976"
---
# <a name="javascript-in-visual-studio"></a>JavaScript dans Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

JavaScript est un langage de premier ordre dans Visual Studio. Vous pouvez utiliser la plupart ou toutes les aides standard de modification (extraits de code, IntelliSense, etc.) lorsque vous écrivez du code JavaScript dans l'IDE de Visual Studio. Vous pouvez écrire du code JavaScript pour de nombreux types d'applications et services.

 Pour obtenir la documentation de référence du langage JavaScript, consultez [JavaScript](http://msdn.microsoft.com/library/d1et7k7c\(v=vs.94\).aspx).

 Des versions ou des extensions spécifiques de Visual Studio peuvent être nécessaires pour développer des types d’applications et des services particuliers en HTML et JavaScript. La liste suivante comporte des liens permettant d'accéder à des informations complémentaires.

- Pour créer des applications multiplateformes avec Apache Cordova, [procurez-vous Visual Studio Tools pour Apache Cordova](http://go.microsoft.com/fwlink/p/?LinkId=397606).

- Pour créer des applications [Windows Store](http://dev.windows.com/develop), [Windows Phone](http://dev.windows.com/develop) et universelles (prenant en charge les deux plateformes), [procurez-vous les outils](http://dev.windows.com/en-us/develop/downloads).

- Pour créer des services cloud, consultez le [site Microsoft Azure](http://azure.microsoft.com/documentation/).

- Pour créer des sites web et applications web, [consultez le site ASP.NET](http://www.asp.net/get-started/websites).

  > [!NOTE]
  >  Vous pouvez créer un site web ASP.Net vide et l’utiliser pour la programmation HTML, CSS et JavaScript. Le fichier Webconfig fourni par ASP.NET permet de déboguer dans Visual Studio (ou vous pouvez utiliser les outils F12 quand vous exécutez l'application).

  L'éditeur JavaScript dans Visual Studio fournit la prise en charge IntelliSense. Pour plus d’informations, consultez [JavaScript IntelliSense](../ide/javascript-intellisense.md).

## <a name="whats-new-in-javascript"></a>Nouveautés de JavaScript
 Les nouvelles fonctionnalités de JavaScript sont répertoriées dans le tableau suivant.

|Fonctionnalité|Description|
|-------------|-----------------|
|Classes|La nouvelle syntaxe prend en charge la déclaration de [classes](/visualstudio/scripting-docs/javascript/reference/class-statement-javascript).|
|Promesses|Les [promesses](/visualstudio/scripting-docs/javascript/reference/promise-object-javascript) permettent d’effectuer un codage asynchrone simplifié et épuré. Les constructeurs de promesses sont pris en charge, ainsi que les méthodes utilitaires `all` et `race`.|
|Iterators|Vous pouvez désormais itérer des objets (tableaux et objets apparentés, itérateurs), en appelant un hook d'itération personnalisé contenant des instructions à exécuter pour la valeur de chaque propriété distincte. Pour plus d’informations, consultez [Itérateurs et générateurs](/visualstudio/scripting-docs/javascript/advanced/iterators-and-generators-javascript). **Remarque :**  Les générateurs ne sont pas pris en charge pour l'instant.|
|Fonctions de flèche|La fonction de flèche (=>) fournit une syntaxe raccourcie pour le mot clé `function` contenant une liaison `this` lexicale.|
|Nouvelles méthodes pour les objets intégrés|Les objets prédéfinis [Tableau](/visualstudio/scripting-docs/javascript/reference/array-object-javascript), [Mathématiques](/visualstudio/scripting-docs/javascript/reference/math-object-javascript), [Nombre](/visualstudio/scripting-docs/javascript/reference/number-object-javascript), [Objet](/visualstudio/scripting-docs/javascript/reference/object-object-javascript) et [Chaîne](/visualstudio/scripting-docs/javascript/reference/string-object-javascript) comportent de nombreuses fonctions et propriétés nouvelles pour la manipulation et l’inspection de données.|
|Améliorations du littéral d’objet|Les objets prennent désormais en charge les propriétés calculées, les définitions de méthode concises, et une syntaxe raccourcie pour les propriétés dont la valeur est initialisée à une variable du même nom. Pour plus d’informations, consultez [Création d’objets](/visualstudio/scripting-docs/javascript/creating-objects-javascript).|
|Serveurs proxy|Les [proxys](/visualstudio/scripting-docs/javascript/reference/proxy-object-javascript) permettent d’attribuer aux objets un comportement personnalisé.|
|Paramètres REST|Les paramètres REST vous permettent de convertir des arguments consécutifs d’un appel de fonction en tableau. Pour plus d’informations, consultez [Fonctions](/visualstudio/scripting-docs/javascript/functions-javascript).|
|Opérateur de diffusion|L’[opérateur de diffusion](/visualstudio/scripting-docs/javascript/reference/spread-operator-decrement-dot-dot-dot-javascript) (`…`) développe des expressions pouvant être itérées dans des arguments individuels. Par exemple, `a.b(…array)` est sensiblement identique à `a.b.apply(a, array)`.|
|Symboles|Les objets [symbole](/visualstudio/scripting-docs/javascript/reference/symbol-object-javascript) permettent d’ajouter des propriétés à un objet existant sans risque d’interférence avec les siennes propres, sans visibilité involontaire, et sans ajout non coordonné par un autre code.|
|Chaînes de modèle|Les [chaînes de modèles](/visualstudio/scripting-docs/javascript/advanced/template-strings-javascript) sont des littéraux de chaîne qui permettent l’évaluation et la concaténation des expressions avec le littéral de chaîne.|
|Améliorations Unicode|Des améliorations ont été apportées à la prise en charge d'Unicode. Par exemple, un nouveau format de séquence d'échappement prend en charge les points de code astral (points de code avec plus de quatre chiffres hexadécimaux). Pour plus d’informations, consultez [Caractères spéciaux](/visualstudio/scripting-docs/javascript/advanced/special-characters-javascript).|
|WeakSet|Un [WeakSet](/visualstudio/scripting-docs/javascript/reference/weakset-object-javascript) est une collection d’objets qui seront effacés de la mémoire s’ils ne sont référencés nulle part ailleurs.|
