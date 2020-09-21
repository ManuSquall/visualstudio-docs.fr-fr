---
title: Règles de performance
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.codeanalysis.performancerules
helpviewer_keywords:
- rules, performance
- performance rules
- performance, rules
- managed code analysis rules, performance rules
ms.assetid: e014ac3a-02e6-46d9-942c-3491dd63782f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7ee44b74ca47de8059b68d95ea5e06c801842bc7
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2020
ms.locfileid: "90808569"
---
# <a name="performance-rules"></a>Règles de performance
Les règles de performances prennent en charge les bibliothèques et les applications hautes performances.

## <a name="in-this-section"></a>Dans cette section

| Règle | Description |
| - | - |
| [CA1802 : Utilisez des littéraux quand cela est approprié](../code-quality/ca1802.md) | Un champ est déclaré statique et en lecture seule (Shared et ReadOnly en [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] ), et est initialisé avec une valeur qui peut être calculée au moment de la compilation. Étant donné que la valeur assignée au champ ciblé peut être calculée au moment de la compilation, remplacez la déclaration par un champ const (const in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] ) afin que la valeur soit calculée au moment de la compilation plutôt qu’au moment de l’exécution. |
| [CA1805 : Ne pas initialiser inutilement](../code-quality/ca1805.md) | Le Runtime .NET initialise tous les champs de type référence à leurs valeurs par défaut avant d’exécuter le constructeur. Dans la plupart des cas, l’initialisation explicite d’un champ à sa valeur par défaut est redondante, ce qui augmente les coûts de maintenance et peut dégrader les performances (par exemple, avec une taille d’assembly accrue). |
| [CA1806 : N'ignorez pas les résultats des méthodes](../code-quality/ca1806.md) | Un nouvel objet est créé mais jamais utilisé, ou une méthode qui crée et retourne une nouvelle chaîne est appelée et la nouvelle chaîne n’est jamais utilisée, ou une méthode COM (Component Object Model) ou P/Invoke retourne un HRESULT ou un code d’erreur qui n’est jamais utilisé. |
| [CA1810 : Initialisez les champs statiques de type référence en ligne](../code-quality/ca1810.md) | Lorsqu'un type déclare un constructeur statique explicite, le compilateur juste-à-temps (JIT, Just-In-Time) ajoute une vérification à chacun des méthodes statiques et constructeurs d'instances du type afin de garantir que le constructeur statique a été appelé précédemment. Les vérifications des constructeurs statiques peuvent diminuer les performances. |
| [CA1812 : Évitez les classes internes non instanciées](../code-quality/ca1812.md) | Une instance d'un type de niveau assembly n'est pas créée par le code au sein de l'assembly. |
| [CA1813 : Évitez les attributs unsealed](../code-quality/ca1813.md) | .NET fournit des méthodes pour récupérer des attributs personnalisés. Par défaut, ces méthodes recherchent la hiérarchie d'héritage des attributs. Le fait de sceller l'attribut élimine la recherche dans la hiérarchie d'héritage et peut améliorer les performances. |
| [CA1814 : Utilisez des tableaux en escalier à la place de tableaux multidimensionnels](../code-quality/ca1814.md) | Un tableau en escalier est un tableau dont les éléments sont des tableaux. Les tableaux qui composent les éléments peuvent être de différentes tailles, ce qui peut entraîner un gaspillage de l’espace pour certains jeux de données. |
| [CA1815 : Remplacez Equals et l'opérateur égal à dans les types valeur](../code-quality/ca1815.md) | Pour les types valeur, l'implémentation héritée de Equals utilise la bibliothèque Reflection et compare le contenu de tous les champs. Le processus de réflexion sollicite fortement les ressources informatiques et la comparaison de chaque champ à la recherche d'une égalité peut s'avérer inutile. Si des utilisateurs sont susceptibles de comparer ou de trier des instances, ou de les utiliser en tant que clés de table de hachage, votre type valeur doit implémenter Equals. |
| [CA1819 : Les propriétés ne doivent pas retourner des tableaux](../code-quality/ca1819.md) | Les tableaux retournés par les propriétés ne sont pas protégés en écriture, même si la propriété est en lecture seule. Pour protéger le tableau de toute falsification, la propriété doit retourner une copie du tableau. En général, les utilisateurs ne comprennent l'incidence négative en matière de performances de l'appel à une telle propriété. |
| [CA1820 : Vérifiez la présence de chaînes vides par la longueur de chaîne](../code-quality/ca1820.md) | La comparaison de chaînes à l'aide de la propriété String.Length ou de la méthode String.IsNullOrEmpty est nettement plus rapide que l'utilisation d'Equals. |
| [CA1821 : Supprimez les finaliseurs vides](../code-quality/ca1821.md) | Évitez autant que possible d'utiliser des finaliseurs en raison de la surcharge supplémentaire des performances impliquée dans le suivi de la durée de vie de l'objet. Un finaliseur vide entraîne une surcharge supplémentaire sans aucun avantage. |
| [CA1822 : Marquez les membres comme static](../code-quality/ca1822.md) | Les membres qui n'accèdent pas aux données d'instance ou n'appellent pas de méthodes d'instance peuvent être marquées comme static (Shared en [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]). Une fois que les méthodes ont été marquées comme static, le compilateur émet des sites d'appel non virtuels vers ces membres. Cette opération se traduit par un gain de performances mesurable pour le code dépendant des performances. |
| [CA1823 : Évitez les champs privés inutilisés](../code-quality/ca1823.md) | Des champs privés qui ne sont pas accessibles dans l'assembly ont été détectés. |
| [CA1824 : Marquer les assemblys avec NeutralResourcesLanguageAttribute](../code-quality/ca1824.md) | L’attribut NeutralResourcesLanguage indique la Gestionnaire des ressources de la langue utilisée pour afficher les ressources d’une culture neutre pour un assembly. Cela permet d'améliorer les performances de recherche de la première ressource chargée et de réduire votre jeu de travail. |
| [CA1825 : Éviter les allocations de tableau de longueur nulle](../code-quality/ca1825.md) | L’initialisation d’un tableau de longueur zéro provoque une allocation de mémoire inutile. Utilisez plutôt l’instance de tableau vide allouée statiquement en appelant <xref:System.Array.Empty%2A?displayProperty=nameWithType> . L’allocation de mémoire est partagée entre tous les appels de cette méthode. |
| [CA1826 : Utiliser une propriété au lieu de la méthode Linq Enumerable](../code-quality/ca1826.md) | <xref:System.Linq.Enumerable> La méthode LINQ a été utilisée sur un type qui prend en charge une propriété équivalente et plus efficace. |
| [CA1827 : N’utilisez pas Count/LongCount quand Any peut être utilisé](../code-quality/ca1827.md) | <xref:System.Linq.Enumerable.Count%2A> ou la <xref:System.Linq.Enumerable.LongCount%2A> méthode a été utilisée là où la <xref:System.Linq.Enumerable.Any%2A> méthode serait plus efficace. |
| [CA1828 : N’utilisez pas CountAsync/LongCountAsync quand AnyAsync peut être utilisé](../code-quality/ca1828.md) | <xref:Microsoft.EntityFrameworkCore.EntityFrameworkQueryableExtensions.CountAsync%2A> ou la <xref:Microsoft.EntityFrameworkCore.EntityFrameworkQueryableExtensions.LongCountAsync%2A> méthode a été utilisée là où la <xref:Microsoft.EntityFrameworkCore.EntityFrameworkQueryableExtensions.AnyAsync%2A> méthode serait plus efficace. |
| [CA1829 : Utilisez la propriété Length/Count au lieu de la méthode Enumerable.Count](../code-quality/ca1829.md) | <xref:System.Linq.Enumerable.Count%2A> La méthode LINQ a été utilisée sur un type qui prend en charge une propriété équivalente, plus efficace `Length` ou `Count` . |
| [CA1830 : Préférer les surcharges de méthode Append et Insert fortement typées sur StringBuilder](../code-quality/ca1830.md) | <xref:System.Text.StringBuilder.Append%2A> et <xref:System.Text.StringBuilder.Insert%2A> fournissent des surcharges pour plusieurs types au-delà de System. String.  Dans la mesure du possible, préférez les surcharges fortement typées à l’aide de ToString () et de la surcharge basée sur une chaîne. |
| [CA1831 : Utiliser AsSpan à la place d’indexeurs basés sur Range pour une chaîne si approprié](../code-quality/ca1831.md) | Lors de l’utilisation d’un indexeur de plages sur une chaîne et de l’assignation implicite de la valeur à un &lt; type char ReadOnlySpan &gt; , la méthode <xref:System.String.Substring%2A?#System_String_Substring_System_Int32_System_Int32_> est utilisée à la place de <xref:System.Span%601.Slice%2A?#System_Span_1_Slice_System_Int32_System_Int32_> , ce qui génère une copie de la partie demandée de la chaîne. |
| [CA1832 : Utiliser AsSpan ou AsMemory à la place d’indexeurs basés sur Range pour obtenir la partie ReadOnlySpan ou ReadOnlyMemory d’un tableau](../code-quality/ca1832.md) | Lors de l’utilisation d’un indexeur de plages sur un tableau et de l’assignation implicite de la valeur à un <xref:System.ReadOnlySpan%601> <xref:System.ReadOnlyMemory%601> type ou, la méthode <xref:System.Runtime.CompilerServices.RuntimeHelpers.GetSubArray%2A> est utilisée à la place de <xref:System.Span%601.Slice%2A?#System_Span_1_Slice_System_Int32_System_Int32_> , ce qui produit une copie de la partie demandée du tableau. |
| [CA1833 : Utiliser AsSpan ou AsMemory à la place d’indexeurs basés sur Range pour obtenir la partie Span ou Memory d’un tableau](../code-quality/ca1833.md) | Lors de l’utilisation d’un indexeur de plages sur un tableau et de l’assignation implicite de la valeur à un <xref:System.Span%601> <xref:System.Memory%601> type ou, la méthode <xref:System.Runtime.CompilerServices.RuntimeHelpers.GetSubArray%2A> est utilisée à la place de <xref:System.Span%601.Slice%2A?#System_Span_1_Slice_System_Int32_System_Int32_> , ce qui produit une copie de la partie demandée du tableau. |
| [CA1834 : Utiliser StringBuilder.Append (char) pour les chaînes de caractères uniques](../code-quality/ca1834.md) | <xref:System.Text.StringBuilder> a une `Append` surcharge qui prend un `char` comme argument. Préférez l’appel `char` de la surcharge pour améliorer les performances. |
| [CA1835 : préférer les surcharges « Memory' » pour « ReadAsync » et « WriteAsync »](../code-quality/ca1835.md) | 'Stream’a une surcharge’ReadAsync’qui accepte’Memory &lt; Byte &gt; 'comme premier argument et une surcharge’WriteAsync’qui prend un’ReadOnlyMemory &lt; Byte &gt; 'comme premier argument. Préférez appeler les surcharges basées sur la mémoire, qui sont plus efficaces. |
| [CA1836 : préférer `IsEmpty` le `Count` cas échéant](../code-quality/ca1836.md) | Préférer `IsEmpty` la propriété qui est plus efficace `Count` que `Length` , <xref:System.Linq.Enumerable.Count%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%29> ou <xref:System.Linq.Enumerable.LongCount%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%29> pour déterminer si l’objet contient ou non des éléments. |
| [CA1837 : utilisez à la `Environment.ProcessId` place de `Process.GetCurrentProcess().Id`](../code-quality/ca1837.md) | `Environment.ProcessId` est plus simple et plus rapide que `Process.GetCurrentProcess().Id` . |
| [CA1838 : éviter `StringBuilder` les paramètres pour les P/Invoke](../code-quality/ca1838.md) | Le marshaling de `StringBuilder` crée toujours une copie de mémoire tampon native, ce qui entraîne plusieurs allocations pour une opération de marshaling. |
