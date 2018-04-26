---
title: avertissements liés aux performances
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8ec04b6c432d5da9504634dd502158f783325537
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
---
# <a name="performance-warnings"></a>avertissements liés aux performances
Avertissements liés aux performances prennent en charge les applications et bibliothèques de hautes performances.

## <a name="in-this-section"></a>Dans cette section

|Règle|Description|
|----------|-----------------|
|[CA1800 : N’effectuez pas de cast inutilement](../code-quality/ca1800-do-not-cast-unnecessarily.md)|Les casts en doublon font baisser les performances, surtout lorsque les casts sont exécutés au sein d'instructions d'itération compactes.|
|[CA1801 : Passez en revue les paramètres inutilisés](../code-quality/ca1801-review-unused-parameters.md)|Une signature de méthode inclut un paramètre qui n'est pas utilisé dans le corps de la méthode.|
|[CA1802 : Utilisez des littéraux où c’est approprié](../code-quality/ca1802-use-literals-where-appropriate.md)|Un champ est déclaré statique et en lecture seule (Shared et ReadOnly en [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) et est initialisé avec une valeur qui est calculable à la compilation. La valeur est assignée au champ ciblé étant calculable à la compilation, remplacez la déclaration pour une variable const (Const en [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) afin que la valeur est calculée au moment de la compilation plutôt qu’au moment de l’exécution.|
|[CA1804 : Supprimez les variables locales inutilisées](../code-quality/ca1804-remove-unused-locals.md)|Les variables locales inutilisées et les assignations inutiles augmentent la taille d'un assembly et font baisser les performances.|
|[CA1806 : Ne pas ignorer les résultats de méthode](../code-quality/ca1806-do-not-ignore-method-results.md)|Un nouvel objet est créé mais jamais utilisé, ou une méthode qui crée et retourne une nouvelle chaîne est appelée et la nouvelle chaîne n’est jamais utilisée, ou une méthode de modèle COM (Component Object) ou P/Invoke retourne un code HRESULT ou d’erreur qui n’est jamais utilisé.|
|[CA1809 : Évitez le surplus de variables locales](../code-quality/ca1809-avoid-excessive-locals.md)|Une méthode d'optimisation des performances courante consiste à stocker une valeur dans un registre de processeur au lieu de la mémoire ; cette méthode est appelée « enregistrement de la valeur ».  Pour augmenter le risque que toutes les variables locales sont enregistrées, limitez le nombre de variables locales à 64.|
|[CA1810 : Initialisez les champs statiques de type référence en ligne](../code-quality/ca1810-initialize-reference-type-static-fields-inline.md)|Lorsqu’un type déclare un constructeur statique explicite, le compilateur juste-à-temps (JIT, Just-In-Time) ajoute une vérification à chacun des méthodes statiques et constructeurs d’instances du type afin de garantir que le constructeur statique a été appelé précédemment. Les vérifications des constructeurs statiques peuvent diminuer les performances.|
|[CA1811 : Évitez le recours à du code privé non appelé](../code-quality/ca1811-avoid-uncalled-private-code.md)|Membre privé ou interne (de niveau assembly) n’a pas d’appelants dans l’assembly, il n’est pas appelée par le common language runtime, et il n’est pas appelée par un délégué.|
|[CA1812 : Évitez les classes internes non instanciées](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)|Une instance d'un type de niveau assembly n'est pas créée par le code au sein de l'assembly.|
|[CA1813 : Évitez les attributs unsealed](../code-quality/ca1813-avoid-unsealed-attributes.md)|La bibliothèque de classes du [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] fournit des méthodes pour récupérer des attributs personnalisés. Par défaut, ces méthodes recherchent la hiérarchie d'héritage des attributs. Le fait de sceller l'attribut élimine la recherche dans la hiérarchie d'héritage et peut améliorer les performances.|
|[CA1814 : Utilisez des tableaux en escalier à la place de tableaux multidimensionnels](../code-quality/ca1814-prefer-jagged-arrays-over-multidimensional.md)|Un tableau en escalier est un tableau dont les éléments sont des tableaux. Les tableaux qui composent les éléments peuvent être de différentes tailles, ce qui peuvent entraîner un gaspillage d’espace pour certains jeux de données.|
|[CA1815 : Remplacez Equals et l’opérateur égal à dans les types valeur](../code-quality/ca1815-override-equals-and-operator-equals-on-value-types.md)|Pour les types valeur, l'implémentation héritée de Equals utilise la bibliothèque Reflection et compare le contenu de tous les champs. Le processus de réflexion sollicite fortement les ressources informatiques et la comparaison de chaque champ à la recherche d'une égalité peut s'avérer inutile. Si des utilisateurs sont susceptibles de comparer ou de trier des instances, ou de les utiliser en tant que clés de table de hachage, votre type valeur doit implémenter Equals.|
|[CA1816 : Appelez GC.SuppressFinalize correctement](../code-quality/ca1816-call-gc-suppressfinalize-correctly.md)|Une méthode qui est une implémentation de Dispose n’appelle pas de catalogue global. SuppressFinalize, ou une méthode qui n’est pas une implémentation de Dispose appelle GC. SuppressFinalize, ou une méthode appelle GC. SuppressFinalize et passe un élément autre que celui-ci (Me en [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]).|
|[CA1819 : Les propriétés ne doivent pas retourner des tableaux](../code-quality/ca1819-properties-should-not-return-arrays.md)|Les tableaux retournés par les propriétés ne sont pas protégés en écriture, même si la propriété est en lecture seule. Pour protéger le tableau de toute falsification, la propriété doit retourner une copie du tableau. En général, les utilisateurs ne comprennent l'incidence négative en matière de performances de l'appel à une telle propriété.|
|[CA1820 : Vérifiez la présence de chaînes vides en utilisant la longueur de chaîne](../code-quality/ca1820-test-for-empty-strings-using-string-length.md)|La comparaison de chaînes à l'aide de la propriété String.Length ou de la méthode String.IsNullOrEmpty est nettement plus rapide que l'utilisation d'Equals.|
|[CA1821 : Supprimez les finaliseurs vides](../code-quality/ca1821-remove-empty-finalizers.md)|Évitez autant que possible d'utiliser des finaliseurs en raison de la surcharge supplémentaire des performances impliquée dans le suivi de la durée de vie de l'objet. Un finaliseur vide entraîne une charge supplémentaire sans aucun avantage.|
|[CA1822 : Marquez les membres comme statique](../code-quality/ca1822-mark-members-as-static.md)|Les membres qui n'accèdent pas aux données d'instance ou n'appellent pas de méthodes d'instance peuvent être marquées comme static (Shared en [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]). Une fois que les méthodes ont été marquées comme static, le compilateur émet des sites d'appel non virtuels vers ces membres. Cette opération se traduit par un gain de performances mesurable pour le code dépendant des performances.|
|[CA1823 : Évitez les champs privés inutilisés](../code-quality/ca1823-avoid-unused-private-fields.md)|Des champs privés qui ne sont pas accessibles dans l'assembly ont été détectés.|
|[CA1824 : Marquez les assemblys avec NeutralResourcesLanguageAttribute](../code-quality/ca1824-mark-assemblies-with-neutralresourceslanguageattribute.md)|L'attribut NeutralResourcesLanguage informe le ResourceManager de la langue qui a été utilisée pour afficher les ressources d'une culture neutre d'un assembly. Cela permet d'améliorer les performances de recherche de la première ressource chargée et de réduire votre jeu de travail.|