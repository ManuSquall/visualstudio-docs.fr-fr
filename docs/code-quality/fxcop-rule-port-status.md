---
title: État du port de la règle FxCop
ms.date: 05/21/2019
ms.topic: reference
helpviewer_keywords:
- fxcop rules
- fxcop analyzers, ported rules
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 04a4738181c579617711150da4eb99e08aeb039c
ms.sourcegitcommit: 535ef05b1e553f0fc66082cd2e0998817eb2a56a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72018426"
---
# <a name="fxcop-rule-port-status"></a>État du port de la règle FXCop

Si vous avez précédemment utilisé l’analyse statique du code dans Visual Studio, vous vous demandez peut-être laquelle de ces règles est disponible dans l’implémentation actuelle en tant qu' [analyseurs FxCop](install-fxcop-analyzers.md). Cette page répertorie les règles qui sont portées, ainsi que celles qui n’ont pas été portées et s’il est prévu de les porter.

## <a name="ported-rules"></a>Règles transférées

La [page de documentation générée automatiquement](https://github.com/dotnet/roslyn-analyzers/blob/master/src/Microsoft.CodeAnalysis.FxCopAnalyzers/Microsoft.CodeAnalysis.FxCopAnalyzers.md) dans Roslyn-Analyzers référentiel contient la liste la plus récente des règles qui ont été portées aux analyseurs FxCop. Cette page contient également des informations supplémentaires, par exemple si la règle est activée par défaut et si elle est associée à un *correctif de code*. (Les[correctifs de code](../ide/quick-actions.md) sont des correctifs accessibles en un clic dans le menu de l’icône d’ampoule dans Visual Studio.)

À partir de la date de cette page, la liste des règles FxCop qui ont été portées aux [analyseurs FxCop](install-fxcop-analyzers.md) comprend les éléments suivants :

ID de règle | Titre
--------|---------
[CA1000](ca1000-do-not-declare-static-members-on-generic-types.md) | Ne pas déclarer de membres statiques sur les types génériques
[CA1001](ca1001-types-that-own-disposable-fields-should-be-disposable.md) | Les types qui possèdent des champs supprimables doivent être supprimables
[CA1003](ca1003-use-generic-event-handler-instances.md) | Utiliser les instances du gestionnaire d'événements génériques
[CA1008](ca1008-enums-should-have-zero-value.md) | Les enums doivent avoir la valeur zéro
[CA1010](ca1010-collections-should-implement-generic-interface.md) | Les collections doivent implémenter une interface générique
[CA1012](ca1012-abstract-types-should-not-have-constructors.md) | Les types abstract ne doivent pas avoir de constructeurs
[CA1014](ca1014-mark-assemblies-with-clscompliantattribute.md) | Marquer les assemblys avec CLSCompliant
[CA1016](ca1016-mark-assemblies-with-assemblyversionattribute.md) | Marquer les assemblys avec la version de l’assembly
[CA1017](ca1017-mark-assemblies-with-comvisibleattribute.md) | Marquer les assemblys avec ComVisible
[CA1018](ca1018-mark-attributes-with-attributeusageattribute.md) | Marquer les attributs avec AttributeUsageAttribute
[CA1019](ca1019-define-accessors-for-attribute-arguments.md) | Définir des accesseurs pour les arguments d'attribut
[CA1024](ca1024-use-properties-where-appropriate.md) | Utiliser les propriétés lorsque cela est approprié
[CA1027](ca1027-mark-enums-with-flagsattribute.md) | Marquer les enums avec FlagsAttribute
[CA1028](ca1028-enum-storage-should-be-int32.md) | Le stockage enum doit être Int32
[CA1030](ca1030-use-events-where-appropriate.md) | Utiliser des événements lorsque cela est approprié
[CA1031](ca1031-do-not-catch-general-exception-types.md) | Ne pas intercepter des types d'exception générale
[CA1032](ca1032-implement-standard-exception-constructors.md) | Implémenter des constructeurs d'exception standard
[CA1033](ca1033-interface-methods-should-be-callable-by-child-types.md) | Les méthodes d'interface doivent pouvoir être appelées par les types enfants
[CA1034](ca1034-nested-types-should-not-be-visible.md) | Les types imbriqués ne doivent pas être visibles
[CA1036](ca1036-override-methods-on-comparable-types.md) | Substituer les méthodes sur les types Comparable
[CA1040](ca1040-avoid-empty-interfaces.md) | Éviter les interfaces vides
[CA1041](ca1041-provide-obsoleteattribute-message.md) | Fournir un message ObsoleteAttribute
[CA1043](ca1043-use-integral-or-string-argument-for-indexers.md) | Utiliser un argument de chaîne ou intégral pour les indexeurs
[CA1044](ca1044-properties-should-not-be-write-only.md) | Les propriétés ne doivent pas être en écriture seule
[CA1050](ca1050-declare-types-in-namespaces.md) | Déclarer les types dans des espaces de noms
[CA1051](ca1051-do-not-declare-visible-instance-fields.md) | Ne pas déclarer de champs d'instances visibles
[CA1052](ca1052-static-holder-types-should-be-sealed.md) | Les types de conteneurs statiques doivent être statiques ou NotInheritable
[CA1053](ca1053-static-holder-types-should-not-have-constructors.md) | Les types de conteneurs statiques ne doivent pas avoir de constructeurs (ca1053 fait partie de [CA1052](ca1052-static-holder-types-should-be-sealed.md) pour les analyseurs FxCop)
[CA1054](ca1054-uri-parameters-should-not-be-strings.md) | Les paramètres URI ne doivent pas être des chaînes
[CA1055](ca1055-uri-return-values-should-not-be-strings.md) | Les valeurs de retour URI ne doivent pas être des chaînes
[CA1056](ca1056-uri-properties-should-not-be-strings.md) | Les propriétés URI ne doivent pas être des chaînes
[CA1058](ca1058-types-should-not-extend-certain-base-types.md) | Les types ne doivent pas étendre certains types de base
[CA1060](ca1060-move-p-invokes-to-nativemethods-class.md) | Déplacer pinvokes vers une classe de méthodes natives
[CA1061](ca1061-do-not-hide-base-class-methods.md) | Ne pas masquer les méthodes de la classe de base
[CA1062](ca1062-validate-arguments-of-public-methods.md) | Valider les arguments de méthodes publiques
[CA1063](ca1063-implement-idisposable-correctly.md) | Implémenter IDisposable correctement
[CA1064](ca1064-exceptions-should-be-public.md) | Les exceptions doivent être publiques
[CA1065](ca1065-do-not-raise-exceptions-in-unexpected-locations.md) | Ne pas lever d'exceptions dans les emplacements inattendus
CA1066 | Le @no__t de type-0 doit implémenter IEquatable @ no__t-1T >, car il remplace égal à
CA1067 | Remplace Object. Equals (Object) lors de l’implémentation de IEquatable @ no__t-0T >
[CA1068](ca1068.md) | Les paramètres CancellationToken doivent venir en dernier
CA1200 | Éviter d’utiliser des balises cref avec un préfixe
[CA1303](ca1303-do-not-pass-literals-as-localized-parameters.md) | Ne pas passer de littéraux en paramètres localisés
[CA1304](ca1304-specify-cultureinfo.md) | Spécifier CultureInfo
[CA1305](ca1305-specify-iformatprovider.md) | Spécifier IFormatProvider
[CA1307](ca1307-specify-stringcomparison.md) | Spécifier StringComparison
[CA1308](ca1308-normalize-strings-to-uppercase.md) | Normaliser les chaînes en majuscules
[CA1309](ca1309-use-ordinal-stringcomparison.md) | Utiliser la comparaison de chaînes ordinale
[CA1401](ca1401-p-invokes-should-not-be-visible.md) | Les P/Invoke ne doivent pas être visibles
[CA1501](ca1501-avoid-excessive-inheritance.md) | Éviter l'excès d'héritage
[CA1502](ca1502-avoid-excessive-complexity.md) | Éviter l'excès de complexité
[CA1505](ca1505-avoid-unmaintainable-code.md) | Éviter le code impossible à maintenir
[CA1506](ca1506-avoid-excessive-class-coupling.md) | Éviter les couplages de classe excessifs
[CA1507](ca1507.md) | Utiliser nameof pour exprimer des noms de symboles
CA1508 | Éviter le code conditionnel mort
CA1509 | Entrée non valide dans le fichier de spécification de règle de métrique du code
[CA1707](ca1707-identifiers-should-not-contain-underscores.md) | Les identificateurs ne doivent pas contenir de traits de soulignement
[CA1708](ca1708-identifiers-should-differ-by-more-than-case.md) | Les identificateurs ne doivent pas différer uniquement par leur casse
[CA1710](ca1710-identifiers-should-have-correct-suffix.md) | Les identificateurs doivent être dotés d'un suffixe correct
[CA1711](ca1711-identifiers-should-not-have-incorrect-suffix.md) | Les identificateurs ne doivent pas porter un suffixe incorrect
[CA1712](ca1712-do-not-prefix-enum-values-with-type-name.md) | N'ajoutez pas le nom de type en guise de préfixe à des valeurs enum
[CA1714](ca1714-flags-enums-should-have-plural-names.md) | Les noms des enums Flags doivent être au pluriel
[CA1715](ca1715-identifiers-should-have-correct-prefix.md) | Les identificateurs doivent être dotés d'un préfixe correct
[CA1716](ca1716-identifiers-should-not-match-keywords.md) | Les identificateurs ne doivent pas correspondre à des mots clés
[CA1717](ca1717-only-flagsattribute-enums-should-have-plural-names.md) | Seuls les noms des enums FlagsAttribute doivent être au pluriel
[CA1720](ca1720-identifiers-should-not-contain-type-names.md) | L’identificateur contient le nom du type
[CA1721](ca1721-property-names-should-not-match-get-methods.md) | Les noms des propriétés ne doivent pas être identiques à ceux des méthodes Get
[CA1724](ca1724-type-names-should-not-match-namespaces.md) | Les noms de types ne doivent pas correspondre à des espaces de noms
[CA1725](ca1725-parameter-names-should-match-base-declaration.md) | Les noms des paramètres doivent correspondre à la déclaration de base
[CA1801](ca1801-review-unused-parameters.md) | Passez en revue les paramètres inutilisés
[CA1802](ca1802-use-literals-where-appropriate.md) | Utiliser des littéraux quand cela est approprié
[CA1806](ca1806-do-not-ignore-method-results.md) | N'ignorez pas les résultats des méthodes
[CA1810](ca1810-initialize-reference-type-static-fields-inline.md) | Initialisez les champs statiques de type référence en ligne
[CA1812](ca1812-avoid-uninstantiated-internal-classes.md) | Évitez les classes internes non instanciées
[CA1813](ca1813-avoid-unsealed-attributes.md) | Évitez les attributs unsealed
[CA1814](ca1814-prefer-jagged-arrays-over-multidimensional.md) | Utilisez des tableaux en escalier à la place de tableaux multidimensionnels
[CA1815](ca1815-override-equals-and-operator-equals-on-value-types.md) | Remplacez Equals et l'opérateur égal à dans les types valeur
[CA1816](ca1816-call-gc-suppressfinalize-correctly.md) | Les méthodes dispose doivent appeler SuppressFinalize
[CA1819](ca1819-properties-should-not-return-arrays.md) | Les propriétés ne doivent pas retourner des tableaux
[CA1820](ca1820-test-for-empty-strings-using-string-length.md) | Vérifiez la présence de chaînes vides par la longueur de chaîne
[CA1821](ca1821-remove-empty-finalizers.md) | Supprimer les finaliseurs vides
[CA1822](ca1822-mark-members-as-static.md) | Marquez les membres comme static
[CA1823](ca1823-avoid-unused-private-fields.md) | Évitez les champs privés inutilisés
[CA1824](ca1824-mark-assemblies-with-neutralresourceslanguageattribute.md) | Marquer les assemblys avec NeutralResourcesLanguageAttribute
CA1825 | Évitez les allocations de tableau de longueur nulle.
CA1826 | N’utilisez pas de méthodes énumérables sur des collections indexables. Utilisez plutôt la collection directement
[CA2000](ca2000-dispose-objects-before-losing-scope.md) | Supprimer les objets avant la mise hors de portée
[CA2002](ca2002-do-not-lock-on-objects-with-weak-identity.md) | Ne définissez pas un verrou sur des objets à identité faible
[CA2007](ca2007-do-not-directly-await-task.md) | Envisagez d’appeler ConfigureAwait sur la tâche attendue
CA2008 | Ne pas créer de tâches sans passer un TaskScheduler
CA2009 | N’appelez pas ToImmutableCollection sur une valeur ImmutableCollection
CA2010 | Consomme toujours la valeur retournée par les méthodes marquées avec PreserveSigAttribute
[CA2100](ca2100-review-sql-queries-for-security-vulnerabilities.md) | Vérifier si les requêtes SQL présentent des failles de sécurité
[CA2101](ca2101-specify-marshaling-for-p-invoke-string-arguments.md) | Spécifiez le marshaling pour les arguments de chaîne P/Invoke
[CA2119](ca2119-seal-methods-that-satisfy-private-interfaces.md) | Scellez les méthodes qui satisfont les interfaces privées
[CA2153](ca2153-avoid-handling-corrupted-state-exceptions.md) | Ne pas intercepter les exceptions d’état endommagé
[CA2200](ca2200-rethrow-to-preserve-stack-details.md) | Levez à nouveau pour conserver les détails de la pile.
[CA2201](ca2201-do-not-raise-reserved-exception-types.md) | Ne levez pas des types d'exceptions réservés
[CA2207](ca2207-initialize-value-type-static-fields-inline.md) | Initialisez les champs statiques des types valeur en ligne
[CA2208](ca2208-instantiate-argument-exceptions-correctly.md) | Instanciez les exceptions d'argument comme il se doit
[CA2211](ca2211-non-constant-fields-should-not-be-visible.md) | Les champs non constants ne doivent pas être visibles
[CA2213](ca2213-disposable-fields-should-be-disposed.md) | Les champs pouvant être supprimés doivent l’être
[CA2214](ca2214-do-not-call-overridable-methods-in-constructors.md) | N'appelez pas de méthodes substituables dans les constructeurs
[CA2216](ca2216-disposable-types-should-declare-finalizer.md) | Les types pouvant être supprimés doivent déclarer un finaliseur
[CA2217](ca2217-do-not-mark-enums-with-flagsattribute.md) | Ne marquez pas les enums avec l'attribut FlagsAttribute
[CA2218](ca2218-override-gethashcode-on-overriding-equals.md) | Remplacez GetHashCode au moment de remplacer Equals
[CA2219](ca2219-do-not-raise-exceptions-in-exception-clauses.md) | Ne levez pas d’exceptions dans les clauses finally
[CA2224](ca2224-override-equals-on-overloading-operator-equals.md) | Remplacer Equals lors de la surcharge de l’opérateur égal
[CA2225](ca2225-operator-overloads-have-named-alternates.md) | Les surcharges d'opérateur offrent d'autres méthodes nommées
[CA2226](ca2226-operators-should-have-symmetrical-overloads.md) | Les opérateurs doivent contenir des surcharges symétriques
[CA2227](ca2227-collection-properties-should-be-read-only.md) | Les propriétés de collection doivent être en lecture seule
[CA2229](ca2229-implement-serialization-constructors.md) | Implémentez des constructeurs de sérialisation
[CA2231](ca2231-overload-operator-equals-on-overriding-valuetype-equals.md) | Surchargez l’opérateur égal en cas de substitution de type valeur égal à
[CA2234](ca2234-pass-system-uri-objects-instead-of-strings.md) | Passer des objets URI système à la place de chaînes
[CA2235](ca2235-mark-all-non-serializable-fields.md) | Marquez tous les champs non sérialisés
[CA2237](ca2237-mark-iserializable-types-with-serializableattribute.md) | Marquez les types ISerializable comme étant sérialisables
[CA2241](ca2241-provide-correct-arguments-to-formatting-methods.md) | Indiquer le nombre correct d'arguments dans les méthodes de mise en forme
[CA2242](ca2242-test-for-nan-correctly.md) | Effectuez correctement des tests NaN
[CA2243](ca2243-attribute-string-literals-should-parse-correctly.md) | Les littéraux de chaîne d'attribut doivent être analysés correctement
CA2244 | Ne pas dupliquer les initialisations d’éléments indexés
[CA2300](ca2300.md) | N’utilisez pas le désérialiseur non sécurisé BinaryFormatter
[CA2301](ca2301.md) | N’appelez pas BinaryFormatter.Deserialize sans définir BinaryFormatter.Binder au préalable
[CA2302](ca2302.md) | Vérifiez que BinaryFormatter.Binder est défini avant d’appeler BinaryFormatter.Deserialize
[CA2305](ca2305.md) | N’utilisez pas le désérialiseur non sécurisé LosFormatter
[CA2310](ca2310.md) | N’utilisez pas le désérialiseur non sécurisé NetDataContractSerializer
[CA2311](ca2311.md) | Ne désérialisez pas sans définir d’abord NetDataContractSerializer.Binder
[CA2312](ca2312.md) | Vérifiez que NetDataContractSerializer.Binder est défini avant la désérialisation
[CA2315](ca2315.md) | N’utilisez pas le désérialiseur non sécurisé ObjectStateFormatter
[CA2321](ca2321.md) | Ne désérialisez avec JavaScriptSerializer à l’aide de SimpleTypeResolver
[CA2322](ca2322.md) | Assurez-vous que JavaScriptSerializer n’est pas initialisé avec SimpleTypeResolver avant la désérialisation
[CA3001](ca3001.md) | Passez en revue le code pour détecter les vulnérabilités de l’injection SQL
[CA3002](ca3002.md) | Passez en revue le code pour détecter les vulnérabilités des scripts XSS
[CA3003](ca3003.md) | Passez en revue le code pour détecter les vulnérabilités de l’injection de chemin de fichier
[CA3004](ca3004.md) | Passez en revue le code pour détecter les vulnérabilités sur la divulgation d’informations
[CA3005](ca3005.md) | Passez en revue le code pour détecter les vulnérabilités de l’injection LDAP
[CA3006](ca3006.md) | Passez en revue le code pour détecter les vulnérabilités de l’injection de commande de processus
[CA3007](ca3007.md) | Passez en revue le code pour détecter les vulnérabilités de la redirection ouverte
[CA3008](ca3008.md) | Passez en revue le code pour détecter les vulnérabilités de l’injection XPath
[CA3009](ca3009.md) | Passez en revue le code pour détecter les vulnérabilités de l’injection XML
[CA3010](ca3010.md) | Passez en revue le code pour détecter les vulnérabilités de l’injection XAML
[CA3011](ca3011.md) | Passez en revue le code pour détecter les vulnérabilités de l’injection de DLL
[CA3012](ca3012.md) | Passez en revue le code pour détecter les vulnérabilités de l’injection regex
CA3061 | Ne pas ajouter de schéma par URL
[CA3075](ca3075-insecure-dtd-processing.md) | Traitement DTD non sécurisé dans le code XML
[CA3076](ca3076-insecure-xslt-script-execution.md) | Le traitement des scripts XSLT n’est pas sécurisé.
[CA3077](ca3077-insecure-processing-in-api-design-xml-document-and-xml-text-reader.md) | Traitement non sécurisé dans la conception d’API, XmlDocument et XmlTextReader
[CA3147](ca3147-mark-verb-handlers-with-validateantiforgerytoken.md) | Marquer les gestionnaires de verbe avec valider le jeton anti-contrefaçon
[CA5350](ca5350-do-not-use-weak-cryptographic-algorithms.md) | N’utilisez pas d’algorithmes de chiffrement faibles
[CA5351](ca5351-do-not-use-broken-cryptographic-algorithms.md) | Ne pas utiliser les algorithmes de chiffrement rompus
CA5358 | Ne pas utiliser les modes de chiffrement non sécurisés
CA5359 | Ne pas désactiver la validation de certificat
CA5360 | N’appelez pas de méthodes dangereuses dans la désérialisation
CA5361 | Ne pas désactiver l’utilisation de SChannel de chiffrement fort
CA5362 | Ne pas faire référence à une classe sérialisable autonome
CA5363 | Ne pas désactiver la validation de la demande
CA5364 | Ne pas utiliser les protocoles de sécurité déconseillés
CA5365 | Ne désactivez pas la vérification d’en-tête HTTP
CA5366 | Utiliser XmlReader pour lire le jeu de données XML
CA5367 | Ne sérialisez pas les types avec des champs de pointeur
CA5368 | Définir ViewStateUserKey pour les classes dérivées de page
CA5369 | Utiliser XmlReader pour la désérialisation
CA5370 | Utiliser XmlReader pour valider le lecteur
CA5371 | Utiliser XmlReader pour la lecture de schéma
CA5372 | Utiliser XmlReader pour XPathDocument
CA5373 | Ne pas utiliser la fonction de dérivation de clé obsolète
CA5374 | Ne pas utiliser XslTransform
CA5375 | Ne pas utiliser la signature d’accès partagé du compte
CA5376 | Utiliser SharedAccessProtocol HttpsOnly
CA5377 | Utiliser la stratégie d’accès au niveau du conteneur
CA5378 | Ne pas désactiver ServicePointManagerSecurityProtocols
CA5379 | Ne pas utiliser l’algorithme de fonction de dérivation de clé faible
CA9999 | Incompatibilité des versions de l’analyseur

## <a name="unported-rules"></a>Règles désutilisées

L’ensemble des règles qui n’ont pas été déplacées vers les [analyseurs FxCop](install-fxcop-analyzers.md) se composent de règles qui n’ont pas encore [pu être portées](#rules-that-may-be-ported), et celles qui sont dépréciées et qui [ne seront pas portées](#deprecated-rules).

### <a name="rules-that-may-be-ported"></a>Règles qui peuvent être reportées

Les règles d’analyse héritées FxCop suivantes n’ont pas encore été implémentées en tant qu’analyseurs, mais peuvent toujours être. Cela peut être dû à une raison technique de blocage ou simplement que la règle est moins prioritaire. Pour plus d’informations sur l’état de portage de chaque règle, cliquez sur le lien dans la colonne **problème de suivi** .

ID de règle | Suivi du problème
--- | ---
[CA1002](ca1002-do-not-expose-generic-lists.md) | [https://github.com/dotnet/roslyn-analyzers/issues/369](https://github.com/dotnet/roslyn-analyzers/issues/369)
[CA1004](ca1004-generic-methods-should-provide-type-parameter.md) | [https://github.com/dotnet/roslyn-analyzers/issues/370](https://github.com/dotnet/roslyn-analyzers/issues/370)
[CA1005](ca1005-avoid-excessive-parameters-on-generic-types.md) | [https://github.com/dotnet/roslyn-analyzers/issues/371](https://github.com/dotnet/roslyn-analyzers/issues/371)
[CA1006](ca1006-do-not-nest-generic-types-in-member-signatures.md) | [https://github.com/dotnet/roslyn-analyzers/issues/372](https://github.com/dotnet/roslyn-analyzers/issues/372)
[CA1007](ca1007-use-generics-where-appropriate.md) | [https://github.com/dotnet/roslyn-analyzers/issues/373](https://github.com/dotnet/roslyn-analyzers/issues/373)
[CA1011](ca1011-consider-passing-base-types-as-parameters.md) | [https://github.com/dotnet/roslyn-analyzers/issues/375](https://github.com/dotnet/roslyn-analyzers/issues/375)
[CA1021](ca1021-avoid-out-parameters.md) | [https://github.com/dotnet/roslyn-analyzers/issues/377](https://github.com/dotnet/roslyn-analyzers/issues/377)
[CA1023](ca1023-indexers-should-not-be-multidimensional.md) | [https://github.com/dotnet/roslyn-analyzers/issues/378](https://github.com/dotnet/roslyn-analyzers/issues/378)
[CA1045](ca1045-do-not-pass-types-by-reference.md) | [https://github.com/dotnet/roslyn-analyzers/issues/391](https://github.com/dotnet/roslyn-analyzers/issues/391)
[CA1046](ca1046-do-not-overload-operator-equals-on-reference-types.md) | [https://github.com/dotnet/roslyn-analyzers/issues/392](https://github.com/dotnet/roslyn-analyzers/issues/392)
[CA1047](ca1047-do-not-declare-protected-members-in-sealed-types.md) | [https://github.com/dotnet/roslyn-analyzers/issues/393](https://github.com/dotnet/roslyn-analyzers/issues/393)
[CA1048](ca1048-do-not-declare-virtual-members-in-sealed-types.md) | [https://github.com/dotnet/roslyn-analyzers/issues/394](https://github.com/dotnet/roslyn-analyzers/issues/394)
[CA1049](ca1049-types-that-own-native-resources-should-be-disposable.md) | [https://github.com/dotnet/roslyn-analyzers/issues/395](https://github.com/dotnet/roslyn-analyzers/issues/395)
[CA1057](ca1057-string-uri-overloads-call-system-uri-overloads.md) | [https://github.com/dotnet/roslyn-analyzers/issues/401](https://github.com/dotnet/roslyn-analyzers/issues/401)
[CA1300](ca1300-specify-messageboxoptions.md) | [https://github.com/dotnet/roslyn-analyzers/issues/408](https://github.com/dotnet/roslyn-analyzers/issues/408)
[CA1301](ca1301-avoid-duplicate-accelerators.md) | [https://github.com/dotnet/roslyn-analyzers/issues/409](https://github.com/dotnet/roslyn-analyzers/issues/409)
[CA1306](ca1306-set-locale-for-data-types.md) | [https://github.com/dotnet/roslyn-analyzers/issues/414](https://github.com/dotnet/roslyn-analyzers/issues/414)
[CA1402](ca1402-avoid-overloads-in-com-visible-interfaces.md) | [https://github.com/dotnet/roslyn-analyzers/issues/418](https://github.com/dotnet/roslyn-analyzers/issues/418)
[CA1403](ca1403-auto-layout-types-should-not-be-com-visible.md) | [https://github.com/dotnet/roslyn-analyzers/issues/419](https://github.com/dotnet/roslyn-analyzers/issues/419)
[CA1404](ca1404-call-getlasterror-immediately-after-p-invoke.md) | [https://github.com/dotnet/roslyn-analyzers/issues/420](https://github.com/dotnet/roslyn-analyzers/issues/420)
[CA1405](ca1405-com-visible-type-base-types-should-be-com-visible.md) | [https://github.com/dotnet/roslyn-analyzers/issues/421](https://github.com/dotnet/roslyn-analyzers/issues/421)
[CA1407](ca1407-avoid-static-members-in-com-visible-types.md) | [https://github.com/dotnet/roslyn-analyzers/issues/423](https://github.com/dotnet/roslyn-analyzers/issues/423)
[CA1408](ca1408-do-not-use-autodual-classinterfacetype.md) | [https://github.com/dotnet/roslyn-analyzers/issues/424](https://github.com/dotnet/roslyn-analyzers/issues/424)
[CA1409](ca1409-com-visible-types-should-be-creatable.md) | [https://github.com/dotnet/roslyn-analyzers/issues/425](https://github.com/dotnet/roslyn-analyzers/issues/425)
[CA1410](ca1410-com-registration-methods-should-be-matched.md) | [https://github.com/dotnet/roslyn-analyzers/issues/426](https://github.com/dotnet/roslyn-analyzers/issues/426)
[CA1411](ca1411-com-registration-methods-should-not-be-visible.md) | [https://github.com/dotnet/roslyn-analyzers/issues/427](https://github.com/dotnet/roslyn-analyzers/issues/427)
[CA1412](ca1412-mark-comsource-interfaces-as-idispatch.md) | [https://github.com/dotnet/roslyn-analyzers/issues/428](https://github.com/dotnet/roslyn-analyzers/issues/428)
[CA1413](ca1413-avoid-non-public-fields-in-com-visible-value-types.md) | [https://github.com/dotnet/roslyn-analyzers/issues/429](https://github.com/dotnet/roslyn-analyzers/issues/429)
[CA1414](ca1414-mark-boolean-p-invoke-arguments-with-marshalas.md) | [https://github.com/dotnet/roslyn-analyzers/issues/430](https://github.com/dotnet/roslyn-analyzers/issues/430)
[CA1415](ca1415-declare-p-invokes-correctly.md) | [https://github.com/dotnet/roslyn-analyzers/issues/431](https://github.com/dotnet/roslyn-analyzers/issues/431)
[CA1500](ca1500-variable-names-should-not-match-field-names.md) | [https://github.com/dotnet/roslyn-analyzers/issues/432](https://github.com/dotnet/roslyn-analyzers/issues/432)
[CA1600](ca1600-do-not-use-idle-process-priority.md) | [https://github.com/dotnet/roslyn-analyzers/issues/438](https://github.com/dotnet/roslyn-analyzers/issues/438)
[CA1601](ca1601-do-not-use-timers-that-prevent-power-state-changes.md) | [https://github.com/dotnet/roslyn-analyzers/issues/439](https://github.com/dotnet/roslyn-analyzers/issues/439)
[CA1700](ca1700-do-not-name-enum-values-reserved.md) | [https://github.com/dotnet/roslyn-analyzers/issues/440](https://github.com/dotnet/roslyn-analyzers/issues/440)
[CA1704](ca1704-identifiers-should-be-spelled-correctly.md) | [https://github.com/dotnet/roslyn-analyzers/issues/443](https://github.com/dotnet/roslyn-analyzers/issues/443)
[CA1709](ca1709-identifiers-should-be-cased-correctly.md) | [https://github.com/dotnet/roslyn-analyzers/issues/445](https://github.com/dotnet/roslyn-analyzers/issues/445)
[CA1713](ca1713-events-should-not-have-before-or-after-prefix.md) | [https://github.com/dotnet/roslyn-analyzers/issues/449](https://github.com/dotnet/roslyn-analyzers/issues/449)
[CA1719](ca1719-parameter-names-should-not-match-member-names.md) | [https://github.com/dotnet/roslyn-analyzers/issues/453](https://github.com/dotnet/roslyn-analyzers/issues/453)
[CA1722](ca1722-identifiers-should-not-have-incorrect-prefix.md) | [https://github.com/dotnet/roslyn-analyzers/issues/455](https://github.com/dotnet/roslyn-analyzers/issues/455)
[CA1726](ca1726-use-preferred-terms.md) | [https://github.com/dotnet/roslyn-analyzers/issues/458](https://github.com/dotnet/roslyn-analyzers/issues/458)
[CA1804](ca1804-remove-unused-locals.md) | [https://github.com/dotnet/roslyn-analyzers/issues/461](https://github.com/dotnet/roslyn-analyzers/issues/461)
[CA1811](ca1811-avoid-uncalled-private-code.md) | [https://github.com/dotnet/roslyn-analyzers/issues/464](https://github.com/dotnet/roslyn-analyzers/issues/464)
[CA1900](ca1900-value-type-fields-should-be-portable.md) | [https://github.com/dotnet/roslyn-analyzers/issues/474](https://github.com/dotnet/roslyn-analyzers/issues/474)
[CA2001](ca2001-avoid-calling-problematic-methods.md) | [https://github.com/dotnet/roslyn-analyzers/issues/477](https://github.com/dotnet/roslyn-analyzers/issues/477)
[CA2004](ca2004-remove-calls-to-gc-keepalive.md) | [https://github.com/dotnet/roslyn-analyzers/issues/479](https://github.com/dotnet/roslyn-analyzers/issues/479)
[CA2006](ca2006-use-safehandle-to-encapsulate-native-resources.md) | [https://github.com/dotnet/roslyn-analyzers/issues/480](https://github.com/dotnet/roslyn-analyzers/issues/480)
[CA2109](ca2109-review-visible-event-handlers.md) | [https://github.com/dotnet/roslyn-analyzers/issues/488](https://github.com/dotnet/roslyn-analyzers/issues/488)
[CA2204](ca2204-literals-should-be-spelled-correctly.md) | [https://github.com/dotnet/roslyn-analyzers/issues/529](https://github.com/dotnet/roslyn-analyzers/issues/529)
[CA2205](ca2205-use-managed-equivalents-of-win32-api.md) | [https://github.com/dotnet/roslyn-analyzers/issues/530](https://github.com/dotnet/roslyn-analyzers/issues/530)
[CA2212](ca2212-do-not-mark-serviced-components-with-webmethod.md) | [https://github.com/dotnet/roslyn-analyzers/issues/534](https://github.com/dotnet/roslyn-analyzers/issues/534)
[CA2215](ca2215-dispose-methods-should-call-base-class-dispose.md) | [https://github.com/dotnet/roslyn-analyzers/issues/535](https://github.com/dotnet/roslyn-analyzers/issues/535)
[CA2232](ca2232-mark-windows-forms-entry-points-with-stathread.md) | [https://github.com/dotnet/roslyn-analyzers/issues/545](https://github.com/dotnet/roslyn-analyzers/issues/545)
[CA2236](ca2236-call-base-class-methods-on-iserializable-types.md) | [https://github.com/dotnet/roslyn-analyzers/issues/548](https://github.com/dotnet/roslyn-analyzers/issues/548)
[CA2238](ca2238-implement-serialization-methods-correctly.md) | [https://github.com/dotnet/roslyn-analyzers/issues/549](https://github.com/dotnet/roslyn-analyzers/issues/549)
[CA2239](ca2239-provide-deserialization-methods-for-optional-fields.md) | [https://github.com/dotnet/roslyn-analyzers/issues/550](https://github.com/dotnet/roslyn-analyzers/issues/550)
[CA2240](ca2240-implement-iserializable-correctly.md) | [https://github.com/dotnet/roslyn-analyzers/issues/551](https://github.com/dotnet/roslyn-analyzers/issues/551)

### <a name="deprecated-rules"></a>Règles déconseillées

Les règles d’analyse héritées FxCop suivantes sont déconseillées et ne sont pas implémentées en tant qu’analyseurs. Pour plus d’informations, vous pouvez effectuer une recherche par ID de règle (par exemple, **CA1009**) sur la [page des problèmes de GitHub Roslyn-Analyzer](https://github.com/dotnet/roslyn-analyzers/issues?utf8=%E2%9C%93&q=is:issue+label:FxCop-Port).

- [CA1009](ca1009-declare-event-handlers-correctly.md)
- [CA1020](ca1020-avoid-namespaces-with-few-types.md)
- [CA1025](ca1025-replace-repetitive-arguments-with-params-array.md)
- [CA1026](ca1026-default-parameters-should-not-be-used.md)
- [CA1035](ca1035-icollection-implementations-have-strongly-typed-members.md)
- [CA1038](ca1038-enumerators-should-be-strongly-typed.md)
- [CA1039](ca1039-lists-are-strongly-typed.md)
- [CA1059](ca1059-members-should-not-expose-certain-concrete-types.md)
- [CA1302](ca1302-do-not-hardcode-locale-specific-strings.md)
- [CA1400](ca1400-p-invoke-entry-points-should-exist.md)
- [CA1406](ca1406-avoid-int64-arguments-for-visual-basic-6-clients.md)
- [CA1504](ca1504-review-misleading-field-names.md)
- [CA1701](ca1701-resource-string-compound-words-should-be-cased-correctly.md)
- [CA1702](ca1702-compound-words-should-be-cased-correctly.md)
- [CA1703](ca1703-resource-strings-should-be-spelled-correctly.md)
- [CA1800](ca1800-do-not-cast-unnecessarily.md)
- [CA1809](ca1809-avoid-excessive-locals.md)
- [CA1901](ca1901-p-invoke-declarations-should-be-portable.md)
- [CA1903](ca1903-use-only-api-from-targeted-framework.md)
- [CA2003](ca2003-do-not-treat-fibers-as-threads.md)
- [CA2102](ca2102-catch-non-clscompliant-exceptions-in-general-handlers.md)
- [CA2103](ca2103-review-imperative-security.md)
- [CA2104](ca2104-do-not-declare-read-only-mutable-reference-types.md)
- [CA2105](ca2105-array-fields-should-not-be-read-only.md)
- [CA2106](ca2106-secure-asserts.md)
- [CA2107](ca2107-review-deny-and-permit-only-usage.md)
- [CA2108](ca2108-review-declarative-security-on-value-types.md)
- [CA2111](ca2111-pointers-should-not-be-visible.md)
- [CA2112](ca2112-secured-types-should-not-expose-fields.md)
- [CA2114](ca2114-method-security-should-be-a-superset-of-type.md)
- [CA2115](ca2115-call-gc-keepalive-when-using-native-resources.md)
- [CA2116](ca2116-aptca-methods-should-only-call-aptca-methods.md)
- [CA2117](ca2117-aptca-types-should-only-extend-aptca-base-types.md)
- [CA2118](ca2118-review-suppressunmanagedcodesecurityattribute-usage.md)
- [CA2120](ca2120-secure-serialization-constructors.md)
- [CA2121](ca2121-static-constructors-should-be-private.md)
- [CA2122](ca2122-do-not-indirectly-expose-methods-with-link-demands.md)
- [CA2123](ca2123-override-link-demands-should-be-identical-to-base.md)
- [CA2124](ca2124-wrap-vulnerable-finally-clauses-in-outer-try.md)
- [CA2126](ca2126-type-link-demands-require-inheritance-demands.md)
- [CA2130](ca2130-security-critical-constants-should-be-transparent.md)
- [CA2131](ca2131-security-critical-types-may-not-participate-in-type-equivalence.md)
- [CA2132](ca2132-default-constructors-must-be-at-least-as-critical-as-base-type-default-constructors.md)
- [CA2133](ca2133-delegates-must-bind-to-methods-with-consistent-transparency.md)
- [CA2134](ca2134-methods-must-keep-consistent-transparency-when-overriding-base-methods.md)
- [CA2135](ca2135-level-2-assemblies-should-not-contain-linkdemands.md)
- [CA2136](ca2136-members-should-not-have-conflicting-transparency-annotations.md)
- [CA2137](ca2137-transparent-methods-must-contain-only-verifiable-il.md)
- [CA2138](ca2138-transparent-methods-must-not-call-methods-with-the-suppressunmanagedcodesecurity-attribute.md)
- [CA2139](ca2139-transparent-methods-may-not-use-the-handleprocesscorruptingexceptions-attribute.md)
- [CA2140](ca2140-transparent-code-must-not-reference-security-critical-items.md)
- [CA2141](ca2141-transparent-methods-must-not-satisfy-linkdemands.md)
- [CA2142](ca2142-transparent-code-should-not-be-protected-with-linkdemands.md)
- [CA2143](ca2143-transparent-methods-should-not-use-security-demands.md)
- [CA2144](ca2144-transparent-code-should-not-load-assemblies-from-byte-arrays.md)
- [CA2145](ca2145-transparent-methods-should-not-be-decorated-with-the-suppressunmanagedcodesecurityattribute.md)
- [CA2146](ca2146-types-must-be-at-least-as-critical-as-their-base-types-and-interfaces.md)
- [CA2147](ca2147-transparent-methods-may-not-use-security-asserts.md)
- [CA2149](ca2149-transparent-methods-must-not-call-into-native-code.md)
- [CA2151](ca2151-fields-with-critical-types-should-be-security-critical.md)
- [CA2202](ca2202-do-not-dispose-objects-multiple-times.md)
- [CA2210](ca2210-assemblies-should-have-valid-strong-names.md)
- [CA2220](ca2220-finalizers-should-call-base-class-finalizer.md)
- [CA2221](ca2221-finalizers-should-be-protected.md)
- [Ca2222](ca2222-do-not-decrease-inherited-member-visibility.md) ([Justification](https://github.com/dotnet/roslyn-analyzers/issues/1378))
- [CA2223](ca2223-members-should-differ-by-more-than-return-type.md)
- [CA2228](ca2228-do-not-ship-unreleased-resource-formats.md)
- [CA2230](ca2230-use-params-for-variable-arguments.md)
- [CA2233](ca2233-operations-should-not-overflow.md)
- [CA5122](ca5122-p-invoke-declarations-should-not-be-safe-critical.md)

## <a name="see-also"></a>Voir aussi

- [Règles Microsoft. CodeAnalysis. FxCopAnalyzers](https://github.com/dotnet/roslyn-analyzers/blob/master/src/Microsoft.CodeAnalysis.FxCopAnalyzers/Microsoft.CodeAnalysis.FxCopAnalyzers.md)