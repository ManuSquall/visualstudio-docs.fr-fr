---
title: avertissements liés aux performances
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.codeanalysis.performancerules
helpviewer_keywords:
- warnings, performance
- performance warnings
- performance, warnings
- managed code analysis warnings, performance warnings
ms.assetid: e014ac3a-02e6-46d9-942c-3491dd63782f
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0ebbe15bdcef27b7b19474b2c42f0b62741fd53a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72649153"
---
# <a name="performance-warnings"></a>avertissements liés aux performances
Les avertissements de performances prennent en charge les bibliothèques et les applications à hautes performances.

## <a name="in-this-section"></a>Dans cette section

| Règle | Description |
| - | - |
| [CA1800 : N’effectuez pas de cast inutilement ](../code-quality/ca1800.md) | Les casts en doublon font baisser les performances, surtout lorsque les casts sont exécutés au sein d'instructions d'itération compactes. |
| [CA1801 : Passez en revue les paramètres inutilisés ](../code-quality/ca1801.md) | Une signature de méthode inclut un paramètre qui n'est pas utilisé dans le corps de la méthode. |
| [CA1802 : Utilisez des littéraux quand cela est approprié ](../code-quality/ca1802.md) | Un champ est déclaré static et en lecture seule (Shared et ReadOnly dans [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]), et est initialisé avec une valeur pouvant être calculée au moment de la compilation. Étant donné que la valeur assignée au champ ciblé peut être calculée au moment de la compilation, remplacez la déclaration par un champ const (const dans [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) afin que la valeur soit calculée au moment de la compilation plutôt qu’au moment de l’exécution. |
| [CA1804 : Supprimer les variables locales inutilisées ](../code-quality/ca1804.md) | Les variables locales inutilisées et les assignations inutiles augmentent la taille d'un assembly et font baisser les performances. |
| [CA1806 : N’ignorez pas les résultats de méthode ](../code-quality/ca1806.md) | Un nouvel objet est créé mais jamais utilisé, ou une méthode qui crée et retourne une nouvelle chaîne est appelée et la nouvelle chaîne n’est jamais utilisée, ou une méthode COM (Component Object Model) ou P/Invoke retourne un HRESULT ou un code d’erreur qui n’est jamais utilisé. |
| [CA1809 : Évitez les variables locales excessives ](../code-quality/ca1809.md) | Une méthode d'optimisation des performances courante consiste à stocker une valeur dans un registre de processeur au lieu de la mémoire ; cette méthode est appelée « enregistrement de la valeur ».  Pour augmenter le risque que toutes les variables locales soient inscrites, limitez le nombre de variables locales à 64. |
| [CA1810 : Initialisez les champs statiques de type référence en ligne ](../code-quality/ca1810.md) | Lorsqu'un type déclare un constructeur statique explicite, le compilateur juste-à-temps (JIT, Just-In-Time) ajoute une vérification à chacun des méthodes statiques et constructeurs d'instances du type afin de garantir que le constructeur statique a été appelé précédemment. Les vérifications des constructeurs statiques peuvent diminuer les performances. |
| [CA1811 : Évitez les ](../code-quality/ca1811.md) de code privé qui ne sont pas appelés | Un membre privé ou interne (au niveau de l’assembly) n’a pas d’appelants dans l’assembly, il n’est pas appelé par le common language runtime et n’est pas appelé par un délégué. |
| [CA1812 : Évitez les classes internes non instanciées ](../code-quality/ca1812.md) | Une instance d'un type de niveau assembly n'est pas créée par le code au sein de l'assembly. |
| [CA1813 : Évitez les attributs non scellés ](../code-quality/ca1813.md) | .NET fournit des méthodes pour récupérer des attributs personnalisés. Par défaut, ces méthodes recherchent la hiérarchie d'héritage des attributs. Le fait de sceller l'attribut élimine la recherche dans la hiérarchie d'héritage et peut améliorer les performances. |
| [CA1814 : Préférer les tableaux en escalier aux ](../code-quality/ca1814.md) multidimensionnels | Un tableau en escalier est un tableau dont les éléments sont des tableaux. Les tableaux qui composent les éléments peuvent être de différentes tailles, ce qui peut entraîner un gaspillage de l’espace pour certains jeux de données. |
| [CA1815 : Remplacer Equals et l’opérateur d’égalité dans les types valeur](../code-quality/ca1815.md) | Pour les types valeur, l'implémentation héritée de Equals utilise la bibliothèque Reflection et compare le contenu de tous les champs. Le processus de réflexion sollicite fortement les ressources informatiques et la comparaison de chaque champ à la recherche d'une égalité peut s'avérer inutile. Si des utilisateurs sont susceptibles de comparer ou de trier des instances, ou de les utiliser en tant que clés de table de hachage, votre type valeur doit implémenter Equals. |
| [CA1816 : Appelez GC. SuppressFinalize correctement ](../code-quality/ca1816.md) | Une méthode qui est une implémentation de dispose n’appelle pas GC. SuppressFinalize, ou une méthode qui n’est pas une implémentation de dispose appelle GC. SuppressFinalize, ou une méthode appelle GC. SuppressFinalize et passe autre chose que ce (me dans [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]). |
| [CA1819 : Les propriétés ne doivent pas retourner des tableaux ](../code-quality/ca1819.md) | Les tableaux retournés par les propriétés ne sont pas protégés en écriture, même si la propriété est en lecture seule. Pour protéger le tableau de toute falsification, la propriété doit retourner une copie du tableau. En général, les utilisateurs ne comprennent l'incidence négative en matière de performances de l'appel à une telle propriété. |
| [CA1820 : Tester les chaînes vides à l’aide de la longueur de chaîne ](../code-quality/ca1820.md) | La comparaison de chaînes à l'aide de la propriété String.Length ou de la méthode String.IsNullOrEmpty est nettement plus rapide que l'utilisation d'Equals. |
| [CA1821 : Supprimez les finaliseurs vides](../code-quality/ca1821.md) | Évitez autant que possible d'utiliser des finaliseurs en raison de la surcharge supplémentaire des performances impliquée dans le suivi de la durée de vie de l'objet. Un finaliseur vide entraîne une surcharge supplémentaire sans aucun avantage. |
| [CA1822 : Marquer les membres comme des ](../code-quality/ca1822.md) statiques | Les membres qui n'accèdent pas aux données d'instance ou n'appellent pas de méthodes d'instance peuvent être marquées comme static (Shared en [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]). Une fois que les méthodes ont été marquées comme static, le compilateur émet des sites d'appel non virtuels vers ces membres. Cette opération se traduit par un gain de performances mesurable pour le code dépendant des performances. |
| [CA1823 : Évitez les champs privés inutilisés ](../code-quality/ca1823.md) | Des champs privés qui ne sont pas accessibles dans l'assembly ont été détectés. |
| [CA1824 : Marquer les assemblys avec NeutralResourcesLanguageAttribute ](../code-quality/ca1824.md) | L'attribut NeutralResourcesLanguage informe le ResourceManager de la langue qui a été utilisée pour afficher les ressources d'une culture neutre d'un assembly. Cela permet d'améliorer les performances de recherche de la première ressource chargée et de réduire votre jeu de travail. |
| [CA1825 : Évitez les allocations de tableau de longueur zéro ](../code-quality/ca1825.md) | L’initialisation d’un tableau de longueur zéro provoque une allocation de mémoire inutile. Utilisez plutôt l’instance de tableau vide allouée statiquement en appelant <xref:System.Array.Empty%2A?displayProperty=nameWithType>. L’allocation de mémoire est partagée entre tous les appels de cette méthode. |
