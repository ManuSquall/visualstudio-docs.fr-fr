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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e578bedf3e6b784321ffb14628ebbe10bc45dc20
ms.sourcegitcommit: 93859158465eab3423a0c0435f06490f0a456a57
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "82167344"
---
# <a name="performance-warnings"></a>avertissements liés aux performances
Les avertissements de performances prennent en charge les bibliothèques et les applications à hautes performances.

## <a name="in-this-section"></a>Dans cette section

| Règle | Description |
| - | - |
| [CA1800 : N'effectuez pas de cast inutilement](../code-quality/ca1800.md) | Les casts en doublon font baisser les performances, surtout lorsque les casts sont exécutés au sein d'instructions d'itération compactes. |
| [CA1801 : Passez en revue les paramètres inutilisés](../code-quality/ca1801.md) | Une signature de méthode inclut un paramètre qui n'est pas utilisé dans le corps de la méthode. |
| [CA1802 : Utilisez des littéraux quand cela est approprié](../code-quality/ca1802.md) | Un champ est déclaré statique et en lecture seule (Shared et ReadOnly [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]en), et est initialisé avec une valeur qui peut être calculée au moment de la compilation. Étant donné que la valeur assignée au champ ciblé peut être calculée au moment de la compilation, remplacez la déclaration par un champ const [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)](const in) afin que la valeur soit calculée au moment de la compilation plutôt qu’au moment de l’exécution. |
| [CA1804 : Supprimez les variables locales inutilisées](../code-quality/ca1804.md) | Les variables locales inutilisées et les assignations inutiles augmentent la taille d'un assembly et font baisser les performances. |
| [CA1806 : N'ignorez pas les résultats des méthodes](../code-quality/ca1806.md) | Un nouvel objet est créé mais jamais utilisé, ou une méthode qui crée et retourne une nouvelle chaîne est appelée et la nouvelle chaîne n’est jamais utilisée, ou une méthode COM (Component Object Model) ou P/Invoke retourne un HRESULT ou un code d’erreur qui n’est jamais utilisé. |
| [CA1809 : Évitez le surplus de variables locales](../code-quality/ca1809.md) | Une méthode d'optimisation des performances courante consiste à stocker une valeur dans un registre de processeur au lieu de la mémoire ; cette méthode est appelée « enregistrement de la valeur ».  Pour augmenter les chances d'enregistrement de toutes les variables locales, limitez le nombre de variables locales à 64. |
| [CA1810 : Initialisez les champs statiques de type référence en ligne](../code-quality/ca1810.md) | Lorsqu'un type déclare un constructeur statique explicite, le compilateur juste-à-temps (JIT, Just-In-Time) ajoute une vérification à chacun des méthodes statiques et constructeurs d'instances du type afin de garantir que le constructeur statique a été appelé précédemment. Les vérifications des constructeurs statiques peuvent diminuer les performances. |
| [CA1811 : Évitez le recours à du code privé non appelé](../code-quality/ca1811.md) | Un membre privé ou interne (au niveau de l’assembly) n’a pas d’appelants dans l’assembly, il n’est pas appelé par le common language runtime et n’est pas appelé par un délégué. |
| [CA1812 : Évitez les classes internes non instanciées](../code-quality/ca1812.md) | Une instance d'un type de niveau assembly n'est pas créée par le code au sein de l'assembly. |
| [CA1813 : Évitez les attributs unsealed](../code-quality/ca1813.md) | .NET fournit des méthodes pour récupérer des attributs personnalisés. Par défaut, ces méthodes recherchent la hiérarchie d'héritage des attributs. Le fait de sceller l'attribut élimine la recherche dans la hiérarchie d'héritage et peut améliorer les performances. |
| [CA1814 : Utilisez des tableaux en escalier à la place de tableaux multidimensionnels](../code-quality/ca1814.md) | Un tableau en escalier est un tableau dont les éléments sont des tableaux. Les tableaux qui composent les éléments peuvent être de différentes tailles, ce qui peut entraîner un gaspillage de l’espace pour certains jeux de données. |
| [CA1815 : Remplacez Equals et l'opérateur égal à dans les types valeur](../code-quality/ca1815.md) | Pour les types valeur, l'implémentation héritée de Equals utilise la bibliothèque Reflection et compare le contenu de tous les champs. Le processus de réflexion sollicite fortement les ressources informatiques et la comparaison de chaque champ à la recherche d'une égalité peut s'avérer inutile. Si des utilisateurs sont susceptibles de comparer ou de trier des instances, ou de les utiliser en tant que clés de table de hachage, votre type valeur doit implémenter Equals. |
| [CA1816 : Appeler GC.SuppressFinalize correctement](../code-quality/ca1816.md) | Une méthode qui est une implémentation de dispose n’appelle pas GC. SuppressFinalize, ou une méthode qui n’est pas une implémentation de dispose appelle GC. SuppressFinalize, ou une méthode appelle GC. SuppressFinalize et passe autre chose que ce (moi dans [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]). |
| [CA1819 : Les propriétés ne doivent pas retourner des tableaux](../code-quality/ca1819.md) | Les tableaux retournés par les propriétés ne sont pas protégés en écriture, même si la propriété est en lecture seule. Pour protéger le tableau de toute falsification, la propriété doit retourner une copie du tableau. En général, les utilisateurs ne comprennent l'incidence négative en matière de performances de l'appel à une telle propriété. |
| [CA1820 : Vérifiez la présence de chaînes vides par la longueur de chaîne](../code-quality/ca1820.md) | La comparaison de chaînes à l'aide de la propriété String.Length ou de la méthode String.IsNullOrEmpty est nettement plus rapide que l'utilisation d'Equals. |
| [CA1821 : Supprimez les finaliseurs vides](../code-quality/ca1821.md) | Évitez autant que possible d'utiliser des finaliseurs en raison de la surcharge supplémentaire des performances impliquée dans le suivi de la durée de vie de l'objet. Un finaliseur vide entraîne une surcharge supplémentaire sans aucun avantage. |
| [CA1822 : Marquez les membres comme static](../code-quality/ca1822.md) | Les membres qui n'accèdent pas aux données d'instance ou n'appellent pas de méthodes d'instance peuvent être marquées comme static (Shared en [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]). Une fois que les méthodes ont été marquées comme static, le compilateur émet des sites d'appel non virtuels vers ces membres. Cette opération se traduit par un gain de performances mesurable pour le code dépendant des performances. |
| [CA1823 : Évitez les champs privés inutilisés](../code-quality/ca1823.md) | Des champs privés qui ne sont pas accessibles dans l'assembly ont été détectés. |
| [CA1824 : Marquer les assemblys avec NeutralResourcesLanguageAttribute](../code-quality/ca1824.md) | L'attribut NeutralResourcesLanguage informe le ResourceManager de la langue qui a été utilisée pour afficher les ressources d'une culture neutre d'un assembly. Cela permet d'améliorer les performances de recherche de la première ressource chargée et de réduire votre jeu de travail. |
| [CA1825 : Éviter les allocations de tableau de longueur nulle](../code-quality/ca1825.md) | L’initialisation d’un tableau de longueur zéro provoque une allocation de mémoire inutile. Utilisez plutôt l’instance de tableau vide allouée statiquement <xref:System.Array.Empty%2A?displayProperty=nameWithType>en appelant. L’allocation de mémoire est partagée entre tous les appels de cette méthode. |
| [CA1826 : utilisez la propriété à la place de la méthode énumérable Linq](../code-quality/ca1826.md) | <xref:System.Linq.Enumerable>La méthode LINQ a été utilisée sur un type qui prend en charge une propriété équivalente et plus efficace. |
| [CA1827 : n’utilisez pas Count/LongCount lorsqu’un peut être utilisé](../code-quality/ca1827.md) | <xref:System.Linq.Enumerable.Count%2A>ou <xref:System.Linq.Enumerable.LongCount%2A> la méthode a été <xref:System.Linq.Enumerable.Any%2A> utilisée là où la méthode serait plus efficace. |
| [CA1828 : n’utilisez pas CountAsync/LongCountAsync quand AnyAsync peut être utilisé](../code-quality/ca1828.md) | <xref:Microsoft.EntityFrameworkCore.EntityFrameworkQueryableExtensions.CountAsync%2A>ou <xref:Microsoft.EntityFrameworkCore.EntityFrameworkQueryableExtensions.LongCountAsync%2A> la méthode a été <xref:Microsoft.EntityFrameworkCore.EntityFrameworkQueryableExtensions.AnyAsync%2A> utilisée là où la méthode serait plus efficace. |
| [CA1829 : utilisez la propriété Length/Count à la place de la méthode Enumerable. Count](../code-quality/ca1829.md) | <xref:System.Linq.Enumerable.Count%2A>La méthode LINQ a été utilisée sur un type qui prend en charge une `Length` propriété `Count` équivalente, plus efficace ou. |
