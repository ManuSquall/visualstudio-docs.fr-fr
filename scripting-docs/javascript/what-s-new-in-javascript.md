---
title: "Nouveautés de JavaScript | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 342b68ef-df93-48c4-81de-bdf6b6ce58d9
caps.latest.revision: 33
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 47057e9611b824c17077b9127f8d2f8b192d6eb8
ms.openlocfilehash: 540d10958a7f2d406a6d70a633fc09a2cada8f41
ms.contentlocale: fr-fr
ms.lasthandoff: 08/11/2017

---
# <a name="what39s-new-in-javascript"></a>Nouveautés de JavaScript
Ce document répertorie les nouvelles fonctionnalités de JavaScript prises en charge dans le [mode Edge](http://blogs.msdn.com/b/ie/archive/2014/11/11/living-on-the-edge-our-next-step-in-interoperability.aspx), le [!INCLUDE[win8_appname_long](../javascript/includes/win8-appname-long-md.md)] et les applications du Windows Phone Store.  
  
 Pour connaître les éléments JavaScript pris en charge dans les applications en mode Edge, mais déconseillés dans les applications [!INCLUDE[win8_appname_long](../javascript/includes/win8-appname-long-md.md)], consultez [Informations sur les versions](../javascript/reference/javascript-version-information.md).  
  
> [!IMPORTANT]
>  Pour plus d’informations sur la création d’applications du [!INCLUDE[win8_appname_long](../javascript/includes/win8-appname-long-md.md)] et du Windows Phone Store avec JavaScript, notamment des informations sur l’éditeur JavaScript Visual Studio et d’autres fonctionnalités, consultez [Développer des applications du Windows Store à l’aide de Visual Studio 2013](http://go.microsoft.com/fwlink/p/?LinkID=238263).  
  
## <a name="new-features-in-javascript"></a>Nouvelles fonctionnalités de JavaScript  
  
|Fonctionnalité|Description|  
|-------------|-----------------|  
|Classes|La nouvelle syntaxe prend en charge la déclaration de [classes](../javascript/reference/class-statement-javascript.md).|  
|Promesses|Les [promesses](../javascript/reference/promise-object-javascript.md) permettent d’effectuer un codage asynchrone simplifié et épuré. Les constructeurs de promesses sont pris en charge, ainsi que les méthodes utilitaires `all` et `race`.|  
|Itérateurs|Vous pouvez désormais itérer des objets (tableaux et objets apparentés, itérateurs), en appelant un hook d'itération personnalisé contenant des instructions à exécuter pour la valeur de chaque propriété distincte. Pour plus d’informations, consultez [Itérateurs et générateurs](../javascript/advanced/iterators-and-generators-javascript.md). **Remarque :** Les générateurs ne sont pas pris en charge pour l’instant.|  
|Fonctions de flèche|La fonction de flèche (=>) fournit une syntaxe raccourcie pour le mot clé `function` contenant une liaison `this` lexicale.|  
|Nouvelles méthodes pour les objets intégrés|Les objets prédéfinis [Tableau](../javascript/reference/array-object-javascript.md), [Mathématiques](../javascript/reference/math-object-javascript.md), [Nombre](../javascript/reference/number-object-javascript.md), [Objet](../javascript/reference/object-object-javascript.md) et [Chaîne](../javascript/reference/string-object-javascript.md) comportent de nombreuses fonctions et propriétés nouvelles pour la manipulation et l’inspection de données.|  
|Améliorations du littéral d’objet|Les objets prennent désormais en charge les propriétés calculées, les définitions de méthode concises, et une syntaxe raccourcie pour les propriétés dont la valeur est initialisée à une variable du même nom. Pour plus d’informations, consultez [Création d’objets](../javascript/creating-objects-javascript.md).|  
|Serveurs proxy|Les [proxys](../javascript/reference/proxy-object-javascript.md) permettent d’attribuer aux objets un comportement personnalisé.|  
|Paramètres REST|Les paramètres REST vous permettent de convertir des arguments consécutifs d’un appel de fonction en tableau. Pour plus d’informations, consultez [Fonctions](../javascript/functions-javascript.md).|  
|Opérateur de diffusion|L’[opérateur de diffusion](../javascript/reference/spread-operator-decrement-dot-dot-dot-javascript.md) (`...`) développe des expressions pouvant être itérées dans des arguments individuels. Par exemple, `a.b(...array)` est sensiblement identique à `a.b.apply(a, array)`.|  
|Symboles|Les objets [symbole](../javascript/reference/symbol-object-javascript.md) permettent d’ajouter des propriétés à un objet existant sans risque d’interférence avec les siennes propres, sans visibilité involontaire, et sans ajout non coordonné par un autre code.|  
|Chaînes de modèle|Les [chaînes de modèles](../javascript/advanced/template-strings-javascript.md) sont des littéraux de chaîne qui permettent l’évaluation et la concaténation des expressions avec le littéral de chaîne.|  
|Améliorations Unicode|Des améliorations ont été apportées à la prise en charge d'Unicode. Par exemple, un nouveau format de séquence d'échappement prend en charge les points de code astral (points de code avec plus de quatre chiffres hexadécimaux). Pour plus d’informations, consultez [Caractères spéciaux](../javascript/advanced/special-characters-javascript.md).|  
|WeakSet|Un [WeakSet](../javascript/reference/weakset-object-javascript.md) est une collection d’objets qui seront effacés de la mémoire s’ils ne sont référencés nulle part ailleurs.|  
  
## <a name="see-also"></a>Voir aussi  
 [Référence sur le langage JavaScript](../javascript/javascript-language-reference.md)
