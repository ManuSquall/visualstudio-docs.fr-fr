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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 29ace36d35b31eeb3635d06d6244ac6fe0897ec2
ms.sourcegitcommit: 034c503ae04e22cf840ccb9770bffd012e40fb2d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/14/2019
ms.locfileid: "72305662"
---
# <a name="performance-warnings"></a>avertissements liés aux performances
Les avertissements de performances prennent en charge les bibliothèques et les applications à hautes performances.

## <a name="in-this-section"></a>Dans cette section

| Règle | Description |
| - | - |
| @NO__T 0CA1800 : Ne pas effectuer de cast inutilement @ no__t-0 | Les casts en doublon font baisser les performances, surtout lorsque les casts sont exécutés au sein d'instructions d'itération compactes. |
| @NO__T 0CA1801 : Passer en revue les paramètres inutilisés @ no__t-0 | Une signature de méthode inclut un paramètre qui n'est pas utilisé dans le corps de la méthode. |
| @NO__T 0CA1802 : Utilisez des littéraux quand @ no__t-0 est approprié | Un champ est déclaré static et en lecture seule (Shared et ReadOnly dans [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]), et est initialisé avec une valeur pouvant être calculée au moment de la compilation. La valeur est assignée au champ ciblé étant calculable à la compilation, modifiez la déclaration const (Const en [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) afin que la valeur est calculée au moment de la compilation plutôt qu’au moment de l’exécution. |
| @NO__T 0CA1804 : Supprimer les variables locales inutilisées @ no__t-0 | Les variables locales inutilisées et les assignations inutiles augmentent la taille d'un assembly et font baisser les performances. |
| @NO__T 0CA1806 : Ne pas ignorer les résultats de la méthode @ no__t-0 | Un nouvel objet est créé mais jamais utilisé, ou une méthode qui crée et retourne une nouvelle chaîne est appelée et la nouvelle chaîne n’est jamais utilisée, ou une méthode COM (Component Object Model) ou P/Invoke retourne un HRESULT ou un code d’erreur qui n’est jamais utilisé. |
| @NO__T 0CA1809 : Évitez les variables locales excessives @ no__t-0 | Une méthode d'optimisation des performances courante consiste à stocker une valeur dans un registre de processeur au lieu de la mémoire ; cette méthode est appelée « enregistrement de la valeur ».  Pour augmenter les chances que toutes les variables locales sont inscrites dans le Registre, limitez le nombre de variables locales à 64. |
| @NO__T 0CA1810 : Initialiser les champs statiques de type référence en ligne @ no__t-0 | Lorsqu’un type déclare un constructeur statique explicite, le compilateur juste-à-temps (JIT, Just-In-Time) ajoute une vérification à chacun des méthodes statiques et constructeurs d’instances du type afin de garantir que le constructeur statique a été appelé précédemment. Les vérifications des constructeurs statiques peuvent diminuer les performances. |
| @NO__T 0CA1811 : Éviter le code privé non appelé @ no__t-0 | Un membre privé ou interne (au niveau de l’assembly) n’a pas d’appelants dans l’assembly, il n’est pas appelé par le common language runtime et n’est pas appelé par un délégué. |
| @NO__T 0CA1812 : Évitez les classes internes non instanciées @ no__t-0 | Une instance d'un type de niveau assembly n'est pas créée par le code au sein de l'assembly. |
| @NO__T 0CA1813 : Évitez les attributs non scellés @ no__t-0 | .NET fournit des méthodes pour récupérer des attributs personnalisés. Par défaut, ces méthodes recherchent la hiérarchie d'héritage des attributs. Le fait de sceller l'attribut élimine la recherche dans la hiérarchie d'héritage et peut améliorer les performances. |
| @NO__T 0CA1814 : Préférer les tableaux en escalier à des tableaux multidimensionnels @ no__t-0 | Un tableau en escalier est un tableau dont les éléments sont des tableaux. Les tableaux qui composent les éléments peuvent être de différentes tailles, ce qui peut entraîner un gaspillage de l’espace pour certains jeux de données. |
| @NO__T 0CA1815 : Remplacer Equals et l’opérateur d’égalité dans les types valeur](../code-quality/ca1815.md) | Pour les types valeur, l'implémentation héritée de Equals utilise la bibliothèque Reflection et compare le contenu de tous les champs. Le processus de réflexion sollicite fortement les ressources informatiques et la comparaison de chaque champ à la recherche d'une égalité peut s'avérer inutile. Si des utilisateurs sont susceptibles de comparer ou de trier des instances, ou de les utiliser en tant que clés de table de hachage, votre type valeur doit implémenter Equals. |
| @NO__T 0CA1816 : Appelez GC. SuppressFinalize correctement @ no__t-0 | Une méthode qui est une implémentation de dispose n’appelle pas GC. SuppressFinalize, ou une méthode qui n’est pas une implémentation de dispose appelle GC. SuppressFinalize, ou une méthode appelle GC. SuppressFinalize et passe autre chose que ce (me dans [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]). |
| @NO__T 0CA1819 : Les propriétés ne doivent pas retourner des tableaux @ no__t-0 | Les tableaux retournés par les propriétés ne sont pas protégés en écriture, même si la propriété est en lecture seule. Pour protéger le tableau de toute falsification, la propriété doit retourner une copie du tableau. En général, les utilisateurs ne comprennent l'incidence négative en matière de performances de l'appel à une telle propriété. |
| @NO__T 0CA1820 : Tester les chaînes vides à l’aide de la longueur de chaîne @ no__t-0 | La comparaison de chaînes à l'aide de la propriété String.Length ou de la méthode String.IsNullOrEmpty est nettement plus rapide que l'utilisation d'Equals. |
| [CA1821 : Supprimez les finaliseurs vides](../code-quality/ca1821.md) | Évitez autant que possible d'utiliser des finaliseurs en raison de la surcharge supplémentaire des performances impliquée dans le suivi de la durée de vie de l'objet. Un finaliseur vide entraîne une surcharge supplémentaire sans aucun avantage. |
| @NO__T 0CA1822 : Marquer les membres comme static @ no__t-0 | Les membres qui n'accèdent pas aux données d'instance ou n'appellent pas de méthodes d'instance peuvent être marquées comme static (Shared en [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]). Une fois que les méthodes ont été marquées comme static, le compilateur émet des sites d'appel non virtuels vers ces membres. Cette opération se traduit par un gain de performances mesurable pour le code dépendant des performances. |
| @NO__T 0CA1823 : Évitez les champs privés inutilisés @ no__t-0 | Des champs privés qui ne sont pas accessibles dans l'assembly ont été détectés. |
| @NO__T 0CA1824 : Marquer les assemblys avec NeutralResourcesLanguageAttribute @ no__t-0 | L'attribut NeutralResourcesLanguage informe le ResourceManager de la langue qui a été utilisée pour afficher les ressources d'une culture neutre d'un assembly. Cela permet d'améliorer les performances de recherche de la première ressource chargée et de réduire votre jeu de travail. |
| @NO__T 0CA1825 : Évitez les allocations de tableau de longueur nulle @ no__t-0 | L’initialisation d’un tableau de longueur zéro provoque une allocation de mémoire inutile. Utilisez plutôt l’instance de tableau vide allouée statiquement en appelant <xref:System.Array.Empty%2A?displayProperty=nameWithType>. L’allocation de mémoire est partagée entre tous les appels de cette méthode. |
