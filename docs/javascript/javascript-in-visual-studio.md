---
title: JavaScript dans Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f3eee13e-30e4-4bc1-81f5-058d7e379b75
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: d4741ff741b89997bbfe4fea9b0f60bba84e63db
ms.lasthandoff: 02/22/2017

---
# <a name="javascript-in-visual-studio"></a>JavaScript dans Visual Studio
JavaScript est un langage de premier ordre dans Visual Studio. Vous pouvez utiliser la plupart ou toutes les aides standard de modification (extraits de code, IntelliSense, etc.) lorsque vous écrivez du code JavaScript dans l'IDE de Visual Studio. Vous pouvez écrire du code JavaScript pour de nombreux types d'applications et services.  
  
 Pour obtenir la documentation de référence du langage JavaScript, consultez [JavaScript](http://msdn.microsoft.com/library/d1et7k7c\(v=vs.94\).aspx).  
  
 Des versions ou des extensions spécifiques de Visual Studio peuvent être nécessaires pour développer des types d’applications et des services particuliers en HTML et JavaScript. La liste suivante comporte des liens permettant d'accéder à des informations complémentaires.  
  
-   Pour créer des applications multiplateformes avec Apache Cordova, [procurez-vous Visual Studio Tools pour Apache Cordova](http://go.microsoft.com/fwlink/p/?LinkId=397606).  
  
-   Pour créer des applications [Windows Store](http://dev.windows.com/develop), [Windows Phone](http://dev.windows.com/develop) et universelles (prenant en charge les deux plateformes), [procurez-vous les outils](http://dev.windows.com/en-us/develop/downloads).  
  
-   Pour créer des services cloud, consultez le [site Microsoft Azure](http://azure.microsoft.com/documentation/).  
  
-   Pour créer des sites web et applications web, [consultez le site ASP.NET](http://www.asp.net/get-started/websites).  
  
    > [!NOTE]
    >  Vous pouvez créer un site web ASP.Net vide et l’utiliser pour la programmation HTML, CSS et JavaScript. Le fichier Webconfig fourni par ASP.NET permet de déboguer dans Visual Studio (ou vous pouvez utiliser les outils F12 quand vous exécutez l'application).  
  
 L'éditeur JavaScript dans Visual Studio fournit la prise en charge IntelliSense. Pour plus d’informations, consultez [JavaScript IntelliSense](../ide/javascript-intellisense.md).  
  
## <a name="whats-new-in-javascript"></a>Nouveautés de JavaScript  
 Les nouvelles fonctionnalités de JavaScript sont répertoriées dans le tableau suivant.  
  
|Fonctionnalité|Description|  
|-------------|-----------------|  
|Classes|La nouvelle syntaxe prend en charge la déclaration de [classes](http://msdn.microsoft.com/Library/bf45ebad-4678-4062-88df-55d32b603c69).|  
|Promesses|Les [promesses](http://msdn.microsoft.com/Library/358ad98b-f7fa-448c-9ee0-ef1e2a45e9c6) permettent d’effectuer un codage asynchrone simplifié et épuré. Les constructeurs de promesses sont pris en charge, ainsi que les méthodes utilitaires `all` et `race`.|  
|Itérateurs|Vous pouvez désormais itérer des objets (tableaux et objets apparentés, itérateurs), en appelant un hook d'itération personnalisé contenant des instructions à exécuter pour la valeur de chaque propriété distincte. Pour plus d’informations, consultez [Itérateurs et générateurs](http://msdn.microsoft.com/Library/68ef5b2f-0349-492b-b557-73ff2a2f90cf). **Remarque :** Les générateurs ne sont pas pris en charge pour l’instant.|  
|Fonctions de flèche|La fonction de flèche (=>) fournit une syntaxe raccourcie pour le mot clé `function` contenant une liaison `this` lexicale.|  
|Nouvelles méthodes pour les objets intégrés|Les objets prédéfinis [Tableau](http://msdn.microsoft.com/Library/08e5f552-0797-4b48-8164-609582fc18c9), [Mathématiques](http://msdn.microsoft.com/Library/607b94cb-921c-43cd-b514-fdbc13aeced6), [Nombre](http://msdn.microsoft.com/Library/76e87c37-cf6c-46cc-bafa-04be1fe3d78d), [Objet](http://msdn.microsoft.com/Library/d24ef8fc-217b-4828-94e1-19f72780bae0) et [Chaîne](http://msdn.microsoft.com/Library/8063ecd5-5778-4e87-b985-b21420171914) comportent de nombreuses fonctions et propriétés nouvelles pour la manipulation et l’inspection de données.|  
|Améliorations du littéral d’objet|Les objets prennent désormais en charge les propriétés calculées, les définitions de méthode concises, et une syntaxe raccourcie pour les propriétés dont la valeur est initialisée à une variable du même nom. Pour plus d’informations, consultez [Création d’objets](http://msdn.microsoft.com/Library/58d1baa5-4fe8-4a56-a926-5b11765df704).|  
|Serveurs proxy|Les [proxys](http://msdn.microsoft.com/Library/2b89abee-04fa-47e6-9676-980016cff5f8) permettent d’attribuer aux objets un comportement personnalisé.|  
|Paramètres REST|Les paramètres REST vous permettent de convertir des arguments consécutifs d’un appel de fonction en tableau. Pour plus d’informations, consultez [Fonctions](http://msdn.microsoft.com/Library/e2a72b5a-3edd-43d8-95e8-91721b38c1c1).|  
|Opérateur de diffusion|L’[opérateur de diffusion](http://msdn.microsoft.com/Library/10263a4c-bd27-4d87-9917-fb4b6bf373db) (`…`) développe des expressions pouvant être itérées dans des arguments individuels. Par exemple, `a.b(…array)` est sensiblement identique à `a.b.apply(a, array)`.|  
|Symboles|Les objets [symbole](http://msdn.microsoft.com/Library/2ad059f1-4b7f-4758-882a-c74ce1283ab0) permettent d’ajouter des propriétés à un objet existant sans risque d’interférence avec les siennes propres, sans visibilité involontaire, et sans ajout non coordonné par un autre code.|  
|Chaînes de modèle|Les [chaînes de modèles](http://msdn.microsoft.com/Library/f2e525a5-b0fc-49c3-95a0-641788e5c12a) sont des littéraux de chaîne qui permettent l’évaluation et la concaténation des expressions avec le littéral de chaîne.|  
|Améliorations Unicode|Des améliorations ont été apportées à la prise en charge d'Unicode. Par exemple, un nouveau format de séquence d'échappement prend en charge les points de code astral (points de code avec plus de quatre chiffres hexadécimaux). Pour plus d’informations, consultez [Caractères spéciaux](http://msdn.microsoft.com/Library/3b38b1bd-1f0f-4748-b13e-55cab36fd126).|  
|WeakSet|Un [WeakSet](http://msdn.microsoft.com/Library/f97e6e7c-d678-4e32-978e-d949a7cafa3a) est une collection d’objets qui seront effacés de la mémoire s’ils ne sont référencés nulle part ailleurs.|
