---
title: FxCop règle statut port
ms.date: 05/21/2019
ms.topic: reference
helpviewer_keywords:
- fxcop rules
- fxcop analyzers, ported rules
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: fccd167bfafd4c27895b01927aaabc1e77eab91c
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79303210"
---
# <a name="fxcop-rule-port-status"></a>Statut de port de règle Fxcop

Si vous avez déjà utilisé l’analyse de code statique dans Visual Studio, vous vous demandez peut-être laquelle de ces règles sont disponibles dans la implémentation actuelle en tant [qu’analyseurs FxCop](install-fxcop-analyzers.md). Cette page énumère les règles qui sont portées ainsi que celles qui n’ont pas été portées et s’il est prévu de les porter.

## <a name="ported-rules"></a>Règles transférées

La [page de documentation autogénérée](https://github.com/dotnet/roslyn-analyzers/blob/master/src/Microsoft.CodeAnalysis.FxCopAnalyzers/Microsoft.CodeAnalysis.FxCopAnalyzers.md) dans le repo roslyn-analyseurs a la liste la plus à jour des règles qui ont été portés aux analyseurs FxCop. Cette page contient également des informations supplémentaires, telles que si la règle est activée par défaut et si elle a un *correctif de code*associé . ([Les correctifs de code](../ide/quick-actions.md) sont des corrections en un seul clic disponibles dans le menu d’icône d’ampoule dans Visual Studio.)

À la date de cette page, la liste des règles FxCop qui ont été portées aux [analyseurs FxCop](install-fxcop-analyzers.md) comprend :

ID de règle | Intitulé
--------|---------
[CA1000](ca1000-do-not-declare-static-members-on-generic-types.md) | Ne pas déclarer de membres statiques sur les types génériques
[CA1001](ca1001-types-that-own-disposable-fields-should-be-disposable.md) | Les types qui possèdent des champs supprimables doivent être supprimables
[CA1003](ca1003-use-generic-event-handler-instances.md) | Utiliser les instances du gestionnaire d'événements génériques
[CA1008](ca1008-enums-should-have-zero-value.md) | Les enums doivent avoir la valeur zéro
[CA1010](ca1010-collections-should-implement-generic-interface.md) | Les collections doivent implémenter une interface générique
[CA1012](ca1012-abstract-types-should-not-have-constructors.md) | Les types abstract ne doivent pas avoir de constructeurs
[CA1014](ca1014-mark-assemblies-with-clscompliantattribute.md) | Assemblages de marques avec CLSCompliant
[CA1016](ca1016-mark-assemblies-with-assemblyversionattribute.md) | Assemblées de marque avec la version d’assemblage
[CA1017](ca1017-mark-assemblies-with-comvisibleattribute.md) | Assemblées de marque avec ComVisible
[CA1018](ca1018-mark-attributes-with-attributeusageattribute.md) | Marquer les attributs avec AttributeUsageAttribute
[CA1019](ca1019-define-accessors-for-attribute-arguments.md) | Définir des accesseurs pour les arguments d'attribut
[CA1021](ca1021.md) | Éviter les paramètres out
[CA1024](ca1024-use-properties-where-appropriate.md) | Utiliser les propriétés lorsque cela est approprié
[CA1027](ca1027-mark-enums-with-flagsattribute.md) | Marquer les enums avec FlagsAttribute
[CA1028](ca1028-enum-storage-should-be-int32.md) | Enum Storage devrait être Int32
[CA1030](ca1030-use-events-where-appropriate.md) | Utiliser des événements lorsque cela est approprié
[CA1031](ca1031-do-not-catch-general-exception-types.md) | Ne pas intercepter des types d'exception générale
[CA1032](ca1032-implement-standard-exception-constructors.md) | Implémenter des constructeurs d'exception standard
[CA1033](ca1033-interface-methods-should-be-callable-by-child-types.md) | Les méthodes d'interface doivent pouvoir être appelées par les types enfants
[CA1034](ca1034-nested-types-should-not-be-visible.md) | Les types imbriqués ne doivent pas être visibles
[CA1036](ca1036-override-methods-on-comparable-types.md) | Substituer les méthodes sur les types Comparable
[CA1040](ca1040-avoid-empty-interfaces.md) | Éviter les interfaces vides
[CA1041](ca1041-provide-obsoleteattribute-message.md) | Fournir un message ObsoleteAttribute
[CA1043](ca1043-use-integral-or-string-argument-for-indexers.md) | Utiliser l’argument intégral ou à cordes pour les indexateurs
[CA1044](ca1044-properties-should-not-be-write-only.md) | Les propriétés ne doivent pas être en écriture seule
[CA1050](ca1050-declare-types-in-namespaces.md) | Déclarer les types dans des espaces de noms
[CA1051](ca1051-do-not-declare-visible-instance-fields.md) | Ne pas déclarer de champs d'instances visibles
[CA1052](ca1052-static-holder-types-should-be-sealed.md) | Les types de support statiques doivent être statiques ou non
[CA1053](ca1053-static-holder-types-should-not-have-constructors.md) | Les types de support statiques ne devraient pas avoir de constructeurs (CA1053 fait partie de [CA1052](ca1052-static-holder-types-should-be-sealed.md) pour les analyseurs FxCop)
[CA1054](ca1054-uri-parameters-should-not-be-strings.md) | Les paramètres Uri ne doivent pas être des chaînes
[CA1055](ca1055-uri-return-values-should-not-be-strings.md) | Les valeurs de retour d’Uri ne doivent pas être des ficelles
[CA1056](ca1056-uri-properties-should-not-be-strings.md) | Les propriétés Uri ne doivent pas être des chaînes
[CA1058](ca1058-types-should-not-extend-certain-base-types.md) | Les types ne doivent pas étendre certains types de base
[CA1060](ca1060-move-p-invokes-to-nativemethods-class.md) | Déplacer les pinvokes à la classe de méthodes indigènes
[CA1061](ca1061-do-not-hide-base-class-methods.md) | Ne pas masquer les méthodes de la classe de base
[CA1062](ca1062-validate-arguments-of-public-methods.md) | Valider les arguments de méthodes publiques
[CA1063](ca1063-implement-idisposable-correctly.md) | Implémentez IDisposable correctement
[CA1064](ca1064-exceptions-should-be-public.md) | Les exceptions doivent être publiques
[CA1065](ca1065-do-not-raise-exceptions-in-unexpected-locations.md) | Ne pas lever d'exceptions dans les emplacements inattendus
CA1066 | Type {0} devrait implémenter IEquatable\<T> parce qu’il l’emporte sur equals
CA1067 | Remplacer Object.Equals (objet) lors de la\<mise en œuvre de la> T IEquatable
[CA1068](ca1068.md) | Les paramètres CancellationToken doivent venir en dernier
CA1200 | Éviter d’utiliser des balises cref avec un préfixe
[CA1303](ca1303-do-not-pass-literals-as-localized-parameters.md) | Ne pas passer de littéraux en paramètres localisés
[CA1304](ca1304-specify-cultureinfo.md) | Spécifier CultureInfo
[CA1305](ca1305-specify-iformatprovider.md) | Spécifier IFormatProvider
[CA1307](ca1307-specify-stringcomparison.md) | Spécifier StringComparison
[CA1308](ca1308-normalize-strings-to-uppercase.md) | Normaliser les chaînes en majuscules
[CA1309](ca1309-use-ordinal-stringcomparison.md) | Utiliser la comparaison des cordes ordinaires
[CA1401](ca1401-p-invokes-should-not-be-visible.md) | Les P/Invoke ne doivent pas être visibles
[CA1501](ca1501-avoid-excessive-inheritance.md) | Éviter l'excès d'héritage
[CA1502](ca1502-avoid-excessive-complexity.md) | Éviter l'excès de complexité
[CA1505](ca1505-avoid-unmaintainable-code.md) | Éviter le code impossible à maintenir
[CA1506](ca1506-avoid-excessive-class-coupling.md) | Éviter les couplages de classe excessifs
[CA1507](ca1507.md) | Utilisez le nom pour exprimer des noms de symboles
CA1508 | Éviter le code conditionnel mort
CA1509 | Entrée invalide dans le fichier de spécification de règle de mesure de code
[CA1707](ca1707-identifiers-should-not-contain-underscores.md) | Les identificateurs ne doivent pas contenir de traits de soulignement
[CA1708](ca1708-identifiers-should-differ-by-more-than-case.md) | Les identificateurs ne doivent pas différer uniquement par leur casse
[CA1710](ca1710-identifiers-should-have-correct-suffix.md) | Les identificateurs doivent être dotés d'un suffixe correct
[CA1711](ca1711-identifiers-should-not-have-incorrect-suffix.md) | Les identificateurs ne doivent pas porter un suffixe incorrect
[CA1712](ca1712-do-not-prefix-enum-values-with-type-name.md) | N'ajoutez pas le nom de type en guise de préfixe à des valeurs enum
[CA1714](ca1714-flags-enums-should-have-plural-names.md) | Les noms des enums Flags doivent être au pluriel
[CA1715](ca1715-identifiers-should-have-correct-prefix.md) | Les identificateurs doivent être dotés d'un préfixe correct
[CA1716](ca1716-identifiers-should-not-match-keywords.md) | Les identificateurs ne doivent pas correspondre à des mots clés
[CA1717](ca1717-only-flagsattribute-enums-should-have-plural-names.md) | Seuls les noms des enums FlagsAttribute doivent être au pluriel
[CA1720](ca1720-identifiers-should-not-contain-type-names.md) | L’identifiant contient le nom de type
[CA1721](ca1721-property-names-should-not-match-get-methods.md) | Les noms des propriétés ne doivent pas être identiques à ceux des méthodes Get
[CA1724](ca1724-type-names-should-not-match-namespaces.md) | Les noms de type ne doivent pas correspondre aux espaces de nom
[CA1725](ca1725-parameter-names-should-match-base-declaration.md) | Les noms des paramètres doivent correspondre à la déclaration de base
[CA1801](ca1801.md) | Passez en revue les paramètres inutilisés
[CA1802](ca1802.md) | Utilisez des littérals le cas échéant
[CA1806](ca1806.md) | N'ignorez pas les résultats des méthodes
[CA1810](ca1810.md) | Initialisez les champs statiques de type référence en ligne
[CA1812](ca1812.md) | Évitez les classes internes non instanciées
[CA1813](ca1813.md) | Évitez les attributs unsealed
[CA1814](ca1814.md) | Utilisez des tableaux en escalier à la place de tableaux multidimensionnels
[CA1815](ca1815.md) | Remplacez Equals et l'opérateur égal à dans les types valeur
[CA1816](ca1816.md) | Disposer les méthodes doivent appeler SuppressFinalize
[CA1819](ca1819.md) | Les propriétés ne doivent pas retourner des tableaux
[CA1820](ca1820.md) | Vérifiez la présence de chaînes vides par la longueur de chaîne
[CA1821](ca1821.md) | Enlever les Finalizers vides
[CA1822](ca1822.md) | Marquez les membres comme static
[CA1823](ca1823.md) | Évitez les champs privés inutilisés
[CA1824](ca1824.md) | Marquer les assemblys avec NeutralResourcesLanguageAttribute
CA1825 | Évitez les allocations de tableau zéro longueur.
CA1826 | N’utilisez pas de méthodes enumérables sur les collections indexables. Utilisez plutôt la collection directement
[CA2000](ca2000.md) | Supprimer les objets avant la mise hors de portée
[CA2002](ca2002.md) | Ne définissez pas un verrou sur des objets à identité faible
[CA2007](ca2007.md) | Envisagez d’appeler ConfigureAwait sur la tâche attendue
CA2008 | Ne créez pas de tâches sans passer un TaskScheduler
CA2009 | N’appelez pas ToImmutableCollection sur une valeur ImmutableCollection
CA2010 | Toujours consommer la valeur retournée par des méthodes marquées avec PreserveSigAttribute
[CA2100](ca2100.md) | Vérifier si les requêtes SQL présentent des failles de sécurité
[CA2101](ca2101.md) | Spécifiez le marshaling pour les arguments de chaîne P/Invoke
[CA2119](ca2119.md) | Scellez les méthodes qui satisfont les interfaces privées
[CA2153](ca2153.md) | Ne pas attraper les exceptions corrompues de l’État
[CA2200](ca2200.md) | Rethrow pour préserver les détails de la pile.
[CA2201](ca2201.md) | Ne levez pas des types d'exceptions réservés
[CA2207](ca2207.md) | Initialisez les champs statiques des types valeur en ligne
[CA2208](ca2208.md) | Instanciez les exceptions d'argument comme il se doit
[CA2211](ca2211.md) | Les champs non constants ne doivent pas être visibles
[CA2213](ca2213.md) | Les champs pouvant être supprimés doivent l’être
[CA2214](ca2214.md) | N'appelez pas de méthodes substituables dans les constructeurs
[CA2216](ca2216.md) | Les types pouvant être supprimés doivent déclarer un finaliseur
[CA2217](ca2217.md) | Ne marquez pas les enums avec l'attribut FlagsAttribute
[CA2218](ca2218.md) | Remplacez GetHashCode au moment de remplacer Equals
[CA2219](ca2219.md) | Ne pas faire exception dans les clauses finales
[CA2224](ca2224.md) | Remplacement égal sur l’opérateur de surcharge égale
[CA2225](ca2225.md) | Les surcharges d'opérateur offrent d'autres méthodes nommées
[CA2226](ca2226.md) | Les opérateurs doivent contenir des surcharges symétriques
[CA2227](ca2227.md) | Les propriétés de collection doivent être en lecture seule
[CA2229](ca2229.md) | Implémentez des constructeurs de sérialisation
[CA2231](ca2231.md) | L’opérateur de surcharge est égal au type de valeur primordial égal
[CA2234](ca2234.md) | Passer les objets uri système de passage au lieu de cordes
[CA2235](ca2235.md) | Marquez tous les champs non sérialisés
[CA2237](ca2237.md) | Marquez les types ISerializable comme étant sérialisables
[CA2241](ca2241.md) | Indiquer le nombre correct d'arguments dans les méthodes de mise en forme
[CA2242](ca2242.md) | Effectuez correctement des tests NaN
[CA2243](ca2243.md) | Les littéraux de chaîne d'attribut doivent être analysés correctement
CA2244 | Ne pas reproduire les initialisations d’éléments indexés
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
CA3061 | N’ajoutez pas de schéma par URL
[CA3075](ca3075.md) | Traitement DTD non sécurisé dans le code XML
[CA3076](ca3076.md) | Traitement de script XSLT précaire.
[CA3077](ca3077.md) | Traitement non sécurisé dans la conception d’API, XmlDocument, et XmlTextReader
[CA3147](ca3147.md) | Mark Verb Handlers avec valide Antiforgery Token
[CA5350](ca5350.md) | N’utilisez pas d’algorithmes de chiffrement faibles
[CA5351](ca5351.md) | N’utilisez pas d’algorithmes cryptographiques cassés
CA5358 | Ne pas utiliser de modes de chiffrement non sécurisés
CA5359 | Ne pas désactiver la validation des certificats
CA5360 | N’appelez pas des méthodes dangereuses dans la désétérialisation
CA5361 | Ne pas désactiver l’utilisation de SChannel de Crypto forte
CA5362 | Ne vous référez pas dans la classe sérialisable
CA5363 | Ne pas désactiver la validation des demandes
CA5364 | N’utilisez pas de protocoles de sécurité dépréciés
CA5365 | Ne désactivez pas la vérification de l’en-tête HTTP
CA5366 | Utilisez XmlReader Pour DataSet Lire Xml
CA5367 | Ne pas sérialiser les types avec des champs pointeurs
CA5368 | Définir ViewStateUserKey pour les classes dérivées de la page
CA5369 | Utilisez XmlReader Pour déséialiser
CA5370 | Utilisez XmlReader pour valider le lecteur
CA5371 | Utilisez XmlReader pour Schema Read
CA5372 | Utilisez XmlReader pour XPathDocument
CA5373 | Ne pas utiliser la fonction de dérivation de clé obsolète
CA5374 | N’utilisez pas XslTransform
CA5375 | N’utilisez pas la signature d’accès partagé du compte
CA5376 | Utiliser SharedAccessProtocol HttpsOnly
CA5377 | Utiliser la politique d’accès au niveau des conteneurs
CA5378 | Ne pas désactiver ServicePointManagerSecurityProtocols
CA5379 | N’utilisez pas l’algorithme de fonction de dérivation des clés faibles
CA9999 | Décalage de version d’analyseur

## <a name="unported-rules"></a>Règles non-déportées

L’ensemble de règles qui n’a pas été porté aux [analyseurs FxCop](install-fxcop-analyzers.md) se compose de règles qui n’ont pas encore mais peuvent encore [être portées](#rules-that-may-be-ported), et ceux qui sont dépréciés et ne seront [pas portés](#deprecated-rules).

### <a name="rules-that-may-be-ported"></a>Règles qui peuvent être portées

Les règles d’analyse d’héritage FxCop suivantes n’ont pas encore été mises en œuvre en tant qu’analyseurs, mais peuvent encore l’être. Cela pourrait être en raison d’une raison technique de blocage ou tout simplement que la règle est moins prioritaire. Pour plus d’informations sur l’état du portage de chaque règle, cliquez sur le lien dans la colonne **de suivi des numéros.**

ID de règle | Problème de suivi
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
[CA1804](ca1804.md) | [https://github.com/dotnet/roslyn-analyzers/issues/461](https://github.com/dotnet/roslyn-analyzers/issues/461)
[CA1811](ca1811.md) | [https://github.com/dotnet/roslyn-analyzers/issues/464](https://github.com/dotnet/roslyn-analyzers/issues/464)
[CA1900](ca1900.md) | [https://github.com/dotnet/roslyn-analyzers/issues/474](https://github.com/dotnet/roslyn-analyzers/issues/474)
[CA2001](ca2001.md) | [https://github.com/dotnet/roslyn-analyzers/issues/477](https://github.com/dotnet/roslyn-analyzers/issues/477)
[CA2004](ca2004.md) | [https://github.com/dotnet/roslyn-analyzers/issues/479](https://github.com/dotnet/roslyn-analyzers/issues/479)
[CA2006](ca2006.md) | [https://github.com/dotnet/roslyn-analyzers/issues/480](https://github.com/dotnet/roslyn-analyzers/issues/480)
[CA2109](ca2109.md) | [https://github.com/dotnet/roslyn-analyzers/issues/488](https://github.com/dotnet/roslyn-analyzers/issues/488)
[CA2204](ca2204.md) | [https://github.com/dotnet/roslyn-analyzers/issues/529](https://github.com/dotnet/roslyn-analyzers/issues/529)
[CA2205](ca2205.md) | [https://github.com/dotnet/roslyn-analyzers/issues/530](https://github.com/dotnet/roslyn-analyzers/issues/530)
[CA2212](ca2212.md) | [https://github.com/dotnet/roslyn-analyzers/issues/534](https://github.com/dotnet/roslyn-analyzers/issues/534)
[CA2215](ca2215.md) | [https://github.com/dotnet/roslyn-analyzers/issues/535](https://github.com/dotnet/roslyn-analyzers/issues/535)
[CA2232](ca2232.md) | [https://github.com/dotnet/roslyn-analyzers/issues/545](https://github.com/dotnet/roslyn-analyzers/issues/545)
[CA2236](ca2236.md) | [https://github.com/dotnet/roslyn-analyzers/issues/548](https://github.com/dotnet/roslyn-analyzers/issues/548)
[CA2238](ca2238.md) | [https://github.com/dotnet/roslyn-analyzers/issues/549](https://github.com/dotnet/roslyn-analyzers/issues/549)
[CA2239](ca2239.md) | [https://github.com/dotnet/roslyn-analyzers/issues/550](https://github.com/dotnet/roslyn-analyzers/issues/550)
[CA2240](ca2240.md) | [https://github.com/dotnet/roslyn-analyzers/issues/551](https://github.com/dotnet/roslyn-analyzers/issues/551)

### <a name="deprecated-rules"></a>Règles dépréciées

Les règles d’analyse d’héritage FxCop suivantes sont dépréciées et ne seront pas implémentées en tant qu’analyseurs. Pour plus d’informations, vous pouvez rechercher par numéro ID (par exemple, **CA1009**) sur la [page des questions GitHub roslyn-analyseurs](https://github.com/dotnet/roslyn-analyzers/issues?utf8=%E2%9C%93&q=is:issue+label:FxCop-Port).

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
- [CA1702](ca1702.md)
- [CA1703](ca1703.md)
- [CA1800](ca1800.md)
- [CA1809](ca1809.md)
- [CA1901](ca1901.md)
- [CA1903](ca1903.md)
- [CA2003](ca2003.md)
- [CA2102](ca2102.md)
- [CA2103](ca2103.md)
- [CA2104](ca2104.md)
- [CA2105](ca2105.md)
- [CA2106](ca2106.md)
- [CA2107](ca2107.md)
- [CA2108](ca2108.md)
- [CA2111](ca2111.md)
- [CA2112](ca2112.md)
- [CA2114](ca2114.md)
- [CA2115](ca2115.md)
- [CA2116](ca2116.md)
- [CA2117](ca2117.md)
- [CA2118](ca2118.md)
- [CA2120](ca2120.md)
- [CA2121](ca2121.md)
- [CA2122](ca2122.md)
- [CA2123](ca2123.md)
- [CA2124](ca2124.md)
- [CA2126](ca2126.md)
- [CA2130](ca2130.md)
- [CA2131](ca2131.md)
- [CA2132](ca2132.md)
- [CA2133](ca2133.md)
- [CA2134](ca2134.md)
- [CA2135](ca2135.md)
- [CA2136](ca2136.md)
- [CA2137](ca2137.md)
- [CA2138](ca2138.md)
- [CA2139](ca2139.md)
- [CA2140](ca2140.md)
- [CA2141](ca2141.md)
- [CA2142](ca2142.md)
- [CA2143](ca2143.md)
- [CA2144](ca2144.md)
- [CA2145](ca2145.md)
- [CA2146](ca2146.md)
- [CA2147](ca2147.md)
- [CA2149](ca2149.md)
- [CA2151](ca2151.md)
- [CA2202](ca2202.md)
- [CA2210](ca2210.md)
- [CA2220](ca2220.md)
- [CA2221](ca2221.md)
- [CA2222](ca2222.md) ([justification](https://github.com/dotnet/roslyn-analyzers/issues/1378))
- [CA2223](ca2223.md)
- [CA2228](ca2228.md)
- [CA2230](ca2230.md)
- [CA2233](ca2233.md)
- [CA5122](ca5122.md)

## <a name="see-also"></a>Voir aussi

- [Règles de Microsoft.CodeAnalysis.FxCopAnalyzers](https://github.com/dotnet/roslyn-analyzers/blob/master/src/Microsoft.CodeAnalysis.FxCopAnalyzers/Microsoft.CodeAnalysis.FxCopAnalyzers.md)
