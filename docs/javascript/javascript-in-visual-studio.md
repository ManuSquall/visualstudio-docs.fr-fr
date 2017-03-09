---
title: "JavaScript dans Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f3eee13e-30e4-4bc1-81f5-058d7e379b75
caps.latest.revision: 17
caps.handback.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# JavaScript dans Visual Studio
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

JavaScript est un langage de premier ordre dans Visual Studio.  Vous pouvez utiliser la plupart ou toutes les aides standard de modification \(extraits de code, IntelliSense, etc.\) lorsque vous écrivez du code JavaScript dans l'IDE de Visual Studio.  Vous pouvez écrire du code JavaScript pour de nombreux types d'applications et services.  
  
 Pour obtenir la documentation relative aux informations de référence sur le langage JavaScript, consultez [JavaScript](http://msdn.microsoft.com/library/d1et7k7c\(v=vs.94\).aspx).  
  
 Des versions ou des extensions spécifiques de Visual Studio peuvent être nécessaires pour développer des types d'applications et des services particuliers en HTML et JavaScript.  La liste suivante comporte des liens permettant d'accéder à des informations complémentaires.  
  
-   Pour créer des applications multiplateformes avec Apache Cordova, [procurez\-vous Visual Studio Tools pour Apache Cordova](http://go.microsoft.com/fwlink/p/?LinkId=397606).  
  
-   Pour créer des applications [Windows Store](http://dev.windows.com/develop), [Windows Phone](http://dev.windows.com/develop) et universelles \(qui prennent en charge les deux plateformes\), [procurez\-vous les outils](http://dev.windows.com/en-us/develop/downloads).  
  
-   Pour créer des services cloud, consultez le [site Microsoft Azure](http://azure.microsoft.com/documentation/).  
  
-   Pour créer des sites et applications web, [consultez le site ASP.NET](http://www.asp.net/get-started/websites).  
  
    > [!NOTE]
    >  Vous pouvez créer un site web ASP.Net vide et l'utiliser pour la programmation HTML, CSS et JavaScript.  Le fichier Webconfig fourni par ASP.NET permet de déboguer dans Visual Studio \(ou vous pouvez utiliser les outils F12 quand vous exécutez l'application\).  
  
 L'éditeur JavaScript dans Visual Studio fournit la prise en charge IntelliSense.  Pour plus d'informations, consultez [IntelliSense JavaScript](../ide/javascript-intellisense.md).  
  
## Nouveautés de JavaScript  
 Les nouvelles fonctionnalités de JavaScript sont répertoriées dans le tableau suivant.  
  
|Fonctionnalité|Description|  
|--------------------|-----------------|  
|Classes|La nouvelle syntaxe prend en charge la déclaration de [classes](../Topic/class%20Statement%20\(JavaScript\).md).|  
|Promesses|Les [promesses](../Topic/Promise%20Object%20\(JavaScript\).md) permettent d’effectuer un codage asynchrone simplifié et épuré.  Les constructeurs de promesses sont pris en charge, ainsi que les méthodes utilitaires `all` et `race`.|  
|Itérateurs|Vous pouvez désormais itérer des objets \(tableaux et objets apparentés, itérateurs\), en appelant un hook d'itération personnalisé contenant des instructions à exécuter pour la valeur de chaque propriété distincte.  Pour plus d'informations, consultez [Itérateurs et générateurs](../Topic/Iterators%20and%20Generators%20\(JavaScript\).md). **Note:**  Les générateurs ne sont pas pris en charge pour l'instant.|  
|Fonctions de flèche|La fonction de flèche \(\=\>\) fournit une syntaxe raccourcie pour le mot clé `function` contenant une liaison `this` lexicale.|  
|Nouvelles méthodes pour les objets intégrés|Les objets intégrés [Objet Array](../Topic/Array%20Object%20\(JavaScript\).md), [Objet Math](../Topic/Math%20Object%20\(JavaScript\).md), [Number, objet](../Topic/Number%20Object%20\(JavaScript\).md), [Object, objet](../Topic/Object%20Object%20\(JavaScript\).md) et [String, objet](../Topic/String%20Object%20\(JavaScript\).md) comportent de nombreuses nouvelles fonctions et propriétés pour la manipulation et l’inspection de données.|  
|Améliorations du littéral Objet|Les objets prennent désormais en charge les propriétés calculées, les définitions de méthode concises, et une syntaxe raccourcie pour les propriétés dont la valeur est initialisée à une variable du même nom.  Pour plus d'informations, consultez [Création d'objets](../Topic/Creating%20Objects%20\(JavaScript\).md).|  
|Serveurs proxy|Les [serveurs proxy](../Topic/Proxy%20Object%20\(JavaScript\).md) permettent d’attribuer aux objets un comportement personnalisé.|  
|Paramètres REST|Les paramètres REST vous permettent de convertir des arguments consécutifs d'un appel de fonction en tableau.  Pour plus d'informations, consultez [Fonctions](../Topic/Functions%20\(JavaScript\).md).|  
|Opérateur de diffusion|L’[opérateur de diffusion](../Topic/Spread%20Operator%20\(...\)%20\(JavaScript\).md) \(`…`\) développe des expressions pouvant être itérées dans des arguments individuels.  Par exemple, `a.b(…array)` est sensiblement identique à `a.b.apply(a, array)`.|  
|Symboles|Les objets [symbole](../Topic/Symbol%20Object%20\(JavaScript\).md) permettent d’ajouter des propriétés à un objet existant sans risque d’interférence avec les siennes propres, sans visibilité involontaire, et sans ajout non coordonné par un autre code.|  
|Chaînes de modèle|Les [chaînes de modèles](../Topic/Template%20Strings%20\(JavaScript\).md) sont des littéraux de chaîne qui permettent l’évaluation et la concaténation des expressions avec le littéral de chaîne.|  
|Améliorations Unicode|Des améliorations ont été apportées à la prise en charge d'Unicode.  Par exemple, un nouveau format de séquence d'échappement prend en charge les points de code astral \(points de code avec plus de quatre chiffres hexadécimaux\).  Pour plus d'informations, consultez [Caractères spéciaux](../Topic/Special%20Characters%20\(JavaScript\).md)|  
|WeakSet|Un [WeakSet](../Topic/WeakSet%20Object%20\(JavaScript\).md) est une collection d'objets qui seront effacés de la mémoire s'ils n'apparaissent nulle part ailleurs.|