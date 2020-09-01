---
title: État du port de la règle FxCop
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
ms.openlocfilehash: c3d9c1dfa45251d0f64a93bb9a5142dcec76b7c7
ms.sourcegitcommit: 26178b116cbf7353fee6ca989b8d872114f7b405
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/31/2020
ms.locfileid: "89219723"
---
# <a name="fxcop-rule-port-status"></a>État du port de la règle FXCop

Si vous avez précédemment utilisé l’analyse statique du code dans Visual Studio, vous vous demandez peut-être laquelle de ces règles est disponible dans l’implémentation actuelle en tant qu' [analyseurs FxCop](install-fxcop-analyzers.md). Cette page répertorie les règles qui sont portées, ainsi que celles qui n’ont pas été portées et s’il est prévu de les porter.

## <a name="ported-rules"></a>Règles transférées

La [page de documentation générée automatiquement](https://github.com/dotnet/roslyn-analyzers/blob/master/src/Microsoft.CodeAnalysis.FxCopAnalyzers/Microsoft.CodeAnalysis.FxCopAnalyzers.md) dans Roslyn-Analyzers référentiel contient la liste la plus récente des règles qui ont été portées aux analyseurs FxCop. Cette page contient également des informations supplémentaires, par exemple si la règle est activée par défaut et si elle est associée à un *correctif de code*. (Les[correctifs de code](../ide/quick-actions.md) sont des correctifs accessibles en un clic dans le menu de l’icône d’ampoule dans Visual Studio.)

À partir de la date de cette page, la liste des règles FxCop qui ont été portées aux [analyseurs FxCop](install-fxcop-analyzers.md) comprend les éléments suivants :

Identificateur de la règle | Titre
--------|---------
[CA1000](ca1000.md) | Ne pas déclarer de membres statiques sur les types génériques
[CA1001](ca1001.md) | Les types qui possèdent des champs supprimables doivent être supprimables
[CA1003](ca1003.md) | Utiliser les instances du gestionnaire d'événements génériques
[CA1008](ca1008.md) | Les enums doivent avoir la valeur zéro
[CA1010](ca1010.md) | Les collections doivent implémenter une interface générique
[CA1012](ca1012.md) | Les types abstract ne doivent pas avoir de constructeurs
[CA1014](ca1014.md) | Marquer les assemblys avec CLSCompliant
[CA1016](ca1016.md) | Marquer les assemblys avec la version de l’assembly
[CA1017](ca1017.md) | Marquer les assemblys avec ComVisible
[CA1018](ca1018.md) | Marquer les attributs avec AttributeUsageAttribute
[CA1019](ca1019.md) | Définir des accesseurs pour les arguments d'attribut
[CA1021](ca1021.md) | Éviter les paramètres out
[CA1024](ca1024.md) | Utiliser les propriétés lorsque cela est approprié
[CA1027](ca1027.md) | Marquer les enums avec FlagsAttribute
[CA1028](ca1028.md) | Le stockage enum doit être Int32
[CA1030](ca1030.md) | Utiliser des événements lorsque cela est approprié
[CA1031](ca1031.md) | Ne pas intercepter des types d'exception générale
[CA1032](ca1032.md) | Implémenter des constructeurs d'exception standard
[CA1033](ca1033.md) | Les méthodes d'interface doivent pouvoir être appelées par les types enfants
[CA1034](ca1034.md) | Les types imbriqués ne doivent pas être visibles
[CA1036](ca1036.md) | Substituer les méthodes sur les types Comparable
[CA1040](ca1040.md) | Éviter les interfaces vides
[CA1041](ca1041.md) | Fournir un message ObsoleteAttribute
[CA1043](ca1043.md) | Utiliser un argument de chaîne ou intégral pour les indexeurs
[CA1044](ca1044.md) | Les propriétés ne doivent pas être en écriture seule
[CA1050](ca1050.md) | Déclarer les types dans des espaces de noms
[CA1051](ca1051.md) | Ne pas déclarer de champs d'instances visibles
[CA1052](ca1052.md) | Les types de conteneurs statiques doivent être statiques ou NotInheritable
[CA1053](ca1053.md) | Les types de conteneurs statiques ne doivent pas avoir de constructeurs (ca1053 fait partie de [CA1052](ca1052.md) pour les analyseurs FxCop)
[CA1054](ca1054.md) | Les paramètres URI ne doivent pas être des chaînes
[CA1055](ca1055.md) | Les valeurs de retour URI ne doivent pas être des chaînes
[CA1056](ca1056.md) | Les propriétés URI ne doivent pas être des chaînes
[CA1058](ca1058.md) | Les types ne doivent pas étendre certains types de base
[CA1060](ca1060.md) | Déplacer pinvokes vers une classe de méthodes natives
[CA1061](ca1061.md) | Ne pas masquer les méthodes de la classe de base
[CA1062](ca1062.md) | Valider les arguments de méthodes publiques
[CA1063](ca1063.md) | Implémenter IDisposable correctement
[CA1064](ca1064.md) | Les exceptions doivent être publiques
[CA1065](ca1065.md) | Ne pas lever d'exceptions dans les emplacements inattendus
[Ca1066](ca1066.md) | {0}Le type doit implémenter IEquatable \<T> , car il remplace égal à
[Ca1067](ca1067.md) | Remplacer Object. Equals (Object) lors de l’implémentation de IEquatable\<T>
[Ca1068](ca1068.md) | Les paramètres CancellationToken doivent venir en dernier
Ca1200 | Éviter d’utiliser des balises cref avec un préfixe
[CA1303](ca1303.md) | Ne pas passer de littéraux en paramètres localisés
[CA1304](ca1304.md) | Spécifier CultureInfo
[CA1305](ca1305.md) | Spécifier IFormatProvider
[CA1307](ca1307.md) | Spécifier StringComparison pour plus de clarté
[CA1308](ca1308.md) | Normaliser les chaînes en majuscules
[CA1309](ca1309.md) | Utiliser la comparaison de chaînes ordinale
[CA1401](ca1401.md) | Les P/Invoke ne doivent pas être visibles
[CA1501](ca1501.md) | Éviter l'excès d'héritage
[CA1502](ca1502.md) | Éviter l'excès de complexité
[CA1505](ca1505.md) | Éviter le code impossible à maintenir
[CA1506](ca1506.md) | Éviter les couplages de classe excessifs
[Ca1507](ca1507.md) | Utiliser nameof pour exprimer des noms de symboles
[CA1508](ca1508.md) | Éviter le code conditionnel mort
Ca1509 | Entrée non valide dans le fichier de spécification de règle de métrique du code
[CA1707](ca1707.md) | Les identificateurs ne doivent pas contenir de traits de soulignement
[CA1708](ca1708.md) | Les identificateurs ne doivent pas différer uniquement par leur casse
[CA1710](ca1710.md) | Les identificateurs doivent être dotés d'un suffixe correct
[CA1711](ca1711.md) | Les identificateurs ne doivent pas porter un suffixe incorrect
[CA1712](ca1712.md) | N'ajoutez pas le nom de type en guise de préfixe à des valeurs enum
[CA1714](ca1714.md) | Les noms des enums Flags doivent être au pluriel
[CA1715](ca1715.md) | Les identificateurs doivent être dotés d'un préfixe correct
[CA1716](ca1716.md) | Les identificateurs ne doivent pas correspondre à des mots clés
[CA1717](ca1717.md) | Seuls les noms des enums FlagsAttribute doivent être au pluriel
[CA1720](ca1720.md) | L’identificateur contient le nom du type
[CA1721](ca1721.md) | Les noms des propriétés ne doivent pas être identiques à ceux des méthodes Get
[CA1724](ca1724.md) | Les noms de types ne doivent pas correspondre à des espaces de noms
[CA1725](ca1725.md) | Les noms des paramètres doivent correspondre à la déclaration de base
[CA1801](ca1801.md) | Passez en revue les paramètres inutilisés
[CA1802](ca1802.md) | Utiliser des littéraux quand cela est approprié
[CA1806](ca1806.md) | N'ignorez pas les résultats des méthodes
[CA1810](ca1810.md) | Initialisez les champs statiques de type référence en ligne
[CA1812](ca1812.md) | Évitez les classes internes non instanciées
[CA1813](ca1813.md) | Évitez les attributs unsealed
[CA1814](ca1814.md) | Utilisez des tableaux en escalier à la place de tableaux multidimensionnels
[CA1815](ca1815.md) | Remplacez Equals et l'opérateur égal à dans les types valeur
[CA1816](ca1816.md) | Les méthodes dispose doivent appeler SuppressFinalize
[CA1819](ca1819.md) | Les propriétés ne doivent pas retourner des tableaux
[CA1820](ca1820.md) | Vérifiez la présence de chaînes vides par la longueur de chaîne
[CA1821](ca1821.md) | Supprimer les finaliseurs vides
[CA1822](ca1822.md) | Marquez les membres comme static
[CA1823](ca1823.md) | Évitez les champs privés inutilisés
[CA1824](ca1824.md) | Marquer les assemblys avec NeutralResourcesLanguageAttribute
[CA1825](ca1825.md) | Évitez les allocations de tableau de longueur nulle.
CA1826 | N’utilisez pas de méthodes énumérables sur des collections indexables. Utilisez plutôt la collection directement
[CA2000](ca2000.md) | Supprimer les objets avant la mise hors de portée
[CA2002](ca2002.md) | Ne définissez pas un verrou sur des objets à identité faible
[Ca2007](ca2007.md) | Envisagez d’appeler ConfigureAwait sur la tâche attendue
[CA2008](ca2008.md) | Ne pas créer de tâches sans passer un TaskScheduler
Ca2009 | N’appelez pas ToImmutableCollection sur une valeur ImmutableCollection
CA2010 | Consomme toujours la valeur retournée par les méthodes marquées avec PreserveSigAttribute
[CA2100](ca2100.md) | Vérifier si les requêtes SQL présentent des failles de sécurité
[CA2101](ca2101.md) | Spécifiez le marshaling pour les arguments de chaîne P/Invoke
[CA2119](ca2119.md) | Scellez les méthodes qui satisfont les interfaces privées
[CA2153](ca2153.md) | Ne pas intercepter les exceptions d’état endommagé
[CA2200](ca2200.md) | Levez à nouveau pour conserver les détails de la pile.
[CA2201](ca2201.md) | Ne levez pas des types d'exceptions réservés
[CA2207](ca2207.md) | Initialisez les champs statiques des types valeur en ligne
[CA2208](ca2208.md) | Instanciez les exceptions d'argument comme il se doit
[CA2211](ca2211.md) | Les champs non constants ne doivent pas être visibles
[CA2213](ca2213.md) | Les champs pouvant être supprimés doivent l’être
[CA2214](ca2214.md) | N'appelez pas de méthodes substituables dans les constructeurs
[CA2216](ca2216.md) | Les types pouvant être supprimés doivent déclarer un finaliseur
[CA2217](ca2217.md) | Ne marquez pas les enums avec l'attribut FlagsAttribute
[CA2218](ca2218.md) | Remplacez GetHashCode au moment de remplacer Equals
[CA2219](ca2219.md) | Ne levez pas d’exceptions dans les clauses finally
[CA2224](ca2224.md) | Remplacer Equals lors de la surcharge de l’opérateur égal
[CA2225](ca2225.md) | Les surcharges d'opérateur offrent d'autres méthodes nommées
[CA2226](ca2226.md) | Les opérateurs doivent contenir des surcharges symétriques
[CA2227](ca2227.md) | Les propriétés de collection doivent être en lecture seule
[CA2229](ca2229.md) | Implémentez des constructeurs de sérialisation
[CA2231](ca2231.md) | Surchargez l’opérateur égal en cas de substitution de type valeur égal à
[CA2234](ca2234.md) | Passer des objets URI système à la place de chaînes
[CA2235](ca2235.md) | Marquez tous les champs non sérialisés
[CA2237](ca2237.md) | Marquez les types ISerializable comme étant sérialisables
[CA2241](ca2241.md) | Indiquer le nombre correct d'arguments dans les méthodes de mise en forme
[CA2242](ca2242.md) | Effectuez correctement des tests NaN
[CA2243](ca2243.md) | Les littéraux de chaîne d'attribut doivent être analysés correctement
CA2244 | Ne pas dupliquer les initialisations d’éléments indexés
[Ca2300](ca2300.md) | N’utilisez pas le désérialiseur non sécurisé BinaryFormatter
[Ca2301](ca2301.md) | N’appelez pas BinaryFormatter.Deserialize sans définir BinaryFormatter.Binder au préalable
[Ca2302](ca2302.md) | Vérifiez que BinaryFormatter.Binder est défini avant d’appeler BinaryFormatter.Deserialize
[CA2305](ca2305.md) | N’utilisez pas le désérialiseur non sécurisé LosFormatter
[CA2310](ca2310.md) | N’utilisez pas le désérialiseur non sécurisé NetDataContractSerializer
[CA2311](ca2311.md) | Ne désérialisez pas sans définir d’abord NetDataContractSerializer.Binder
[CA2312](ca2312.md) | Vérifiez que NetDataContractSerializer.Binder est défini avant la désérialisation
[CA2315](ca2315.md) | N’utilisez pas le désérialiseur non sécurisé ObjectStateFormatter
[CA2321](ca2321.md) | Ne désérialisez avec JavaScriptSerializer à l’aide de SimpleTypeResolver
[CA2322](ca2322.md) | Assurez-vous que JavaScriptSerializer n’est pas initialisé avec SimpleTypeResolver avant la désérialisation
[CA3001](ca3001.md) | Passez en revue le code pour détecter les vulnérabilités de l’injection SQL
[Ca3002](ca3002.md) | Passez en revue le code pour détecter les vulnérabilités des scripts XSS
[Ca3003](ca3003.md) | Passez en revue le code pour détecter les vulnérabilités de l’injection de chemin de fichier
[Ca3004](ca3004.md) | Passez en revue le code pour détecter les vulnérabilités sur la divulgation d’informations
[Ca3005](ca3005.md) | Passez en revue le code pour détecter les vulnérabilités de l’injection LDAP
[Ca3006](ca3006.md) | Passez en revue le code pour détecter les vulnérabilités de l’injection de commande de processus
[CA3007](ca3007.md) | Passez en revue le code pour détecter les vulnérabilités de la redirection ouverte
[CA3008](ca3008.md) | Passez en revue le code pour détecter les vulnérabilités de l’injection XPath
[CA3009](ca3009.md) | Passez en revue le code pour détecter les vulnérabilités de l’injection XML
[Ca3010](ca3010.md) | Passez en revue le code pour détecter les vulnérabilités de l’injection XAML
[CA3011](ca3011.md) | Passez en revue le code pour détecter les vulnérabilités de l’injection de DLL
[CA3012](ca3012.md) | Passez en revue le code pour détecter les vulnérabilités de l’injection regex
[CA3061](ca3061.md) | Ne pas ajouter de schéma par URL
[CA3075](ca3075.md) | Traitement DTD non sécurisé dans le code XML
[CA3076](ca3076.md) | Le traitement des scripts XSLT n’est pas sécurisé.
[CA3077](ca3077.md) | Traitement non sécurisé dans la conception d’API, XmlDocument et XmlTextReader
[CA3147](ca3147.md) | Marquer les gestionnaires de verbe avec valider le jeton anti-contrefaçon
[CA5350](ca5350.md) | N’utilisez pas d’algorithmes de chiffrement faibles
[CA5351](ca5351.md) | Ne pas utiliser les algorithmes de chiffrement rompus
[CA5358](ca5358.md) | Ne pas utiliser de modes de chiffrement non sécurisés
CA5359 | Ne pas désactiver la validation de certificat
CA5360 | N’appelez pas de méthodes dangereuses dans la désérialisation
[CA5361](ca5361.md) | Ne pas désactiver l’utilisation de SChannel de chiffrement fort
CA5362 | Ne pas faire référence à une classe sérialisable autonome
[CA5363](ca5363.md) | Ne pas désactiver la validation de la demande
[CA5364](ca5364.md) | Ne pas utiliser les protocoles de sécurité déconseillés
CA5365 | Ne désactivez pas la vérification d’en-tête HTTP
CA5366 | Utiliser XmlReader pour lire le jeu de données XML
CA5367 | Ne sérialisez pas les types avec des champs de pointeur
CA5368 | Définir ViewStateUserKey pour les classes dérivées de page
[CA5369](ca5369.md) | Utiliser XmlReader pour la désérialisation
[CA5370](ca5370.md) | Utiliser XmlReader pour valider le lecteur
[CA5371](ca5371.md) | Utiliser XmlReader pour la lecture de schéma
[CA5372](ca5372.md) | Utiliser XmlReader pour XPathDocument
[CA5373](ca5373.md) | Ne pas utiliser la fonction de dérivation de clé obsolète
CA5374 | Ne pas utiliser XslTransform
CA5375 | Ne pas utiliser la signature d’accès partagé du compte
CA5376 | Utiliser SharedAccessProtocol HttpsOnly
CA5377 | Utiliser la stratégie d’accès au niveau du conteneur
[CA5378](ca5378.md) | Ne pas désactiver ServicePointManagerSecurityProtocols
CA5379 | Ne pas utiliser l’algorithme de fonction de dérivation de clé faible
Ca9999 | Incompatibilité des versions de l’analyseur

## <a name="unported-rules"></a>Règles désutilisées

L’ensemble des règles qui n’ont pas été déplacées vers les [analyseurs FxCop](install-fxcop-analyzers.md) se composent de règles qui n’ont pas encore [pu être portées](#rules-that-may-be-ported), et celles qui sont dépréciées et qui [ne seront pas portées](#deprecated-rules).

### <a name="rules-that-may-be-ported"></a>Règles qui peuvent être reportées

Les règles d’analyse héritées FxCop suivantes n’ont pas encore été implémentées en tant qu’analyseurs, mais peuvent toujours être. Cela peut être dû à une raison technique de blocage ou simplement que la règle est moins prioritaire. Pour plus d’informations sur l’état de portage de chaque règle, cliquez sur le lien dans la colonne **problème de suivi** .

Identificateur de la règle | Suivi du problème
--- | ---
[CA1002](ca1002.md) | [https://github.com/dotnet/roslyn-analyzers/issues/369](https://github.com/dotnet/roslyn-analyzers/issues/369)
[CA1004](ca1004.md) | [https://github.com/dotnet/roslyn-analyzers/issues/370](https://github.com/dotnet/roslyn-analyzers/issues/370)
[CA1005](ca1005.md) | [https://github.com/dotnet/roslyn-analyzers/issues/371](https://github.com/dotnet/roslyn-analyzers/issues/371)
[CA1006](ca1006.md) | [https://github.com/dotnet/roslyn-analyzers/issues/372](https://github.com/dotnet/roslyn-analyzers/issues/372)
[CA1007](ca1007.md) | [https://github.com/dotnet/roslyn-analyzers/issues/373](https://github.com/dotnet/roslyn-analyzers/issues/373)
[CA1011](ca1011.md) | [https://github.com/dotnet/roslyn-analyzers/issues/375](https://github.com/dotnet/roslyn-analyzers/issues/375)
[CA1021](ca1021.md) | [https://github.com/dotnet/roslyn-analyzers/issues/377](https://github.com/dotnet/roslyn-analyzers/issues/377)
[CA1023](ca1023.md) | [https://github.com/dotnet/roslyn-analyzers/issues/378](https://github.com/dotnet/roslyn-analyzers/issues/378)
[CA1045](ca1045.md) | [https://github.com/dotnet/roslyn-analyzers/issues/391](https://github.com/dotnet/roslyn-analyzers/issues/391)
[CA1046](ca1046.md) | [https://github.com/dotnet/roslyn-analyzers/issues/392](https://github.com/dotnet/roslyn-analyzers/issues/392)
[CA1047](ca1047.md) | [https://github.com/dotnet/roslyn-analyzers/issues/393](https://github.com/dotnet/roslyn-analyzers/issues/393)
[CA1048](ca1048.md) | [https://github.com/dotnet/roslyn-analyzers/issues/394](https://github.com/dotnet/roslyn-analyzers/issues/394)
[CA1049](ca1049.md) | [https://github.com/dotnet/roslyn-analyzers/issues/395](https://github.com/dotnet/roslyn-analyzers/issues/395)
[CA1057](ca1057.md) | [https://github.com/dotnet/roslyn-analyzers/issues/401](https://github.com/dotnet/roslyn-analyzers/issues/401)
[CA1300](ca1300.md) | [https://github.com/dotnet/roslyn-analyzers/issues/408](https://github.com/dotnet/roslyn-analyzers/issues/408)
[CA1301](ca1301.md) | [https://github.com/dotnet/roslyn-analyzers/issues/409](https://github.com/dotnet/roslyn-analyzers/issues/409)
[CA1306](ca1306.md) | [https://github.com/dotnet/roslyn-analyzers/issues/414](https://github.com/dotnet/roslyn-analyzers/issues/414)
[CA1402](ca1402.md) | [https://github.com/dotnet/roslyn-analyzers/issues/418](https://github.com/dotnet/roslyn-analyzers/issues/418)
[CA1403](ca1403.md) | [https://github.com/dotnet/roslyn-analyzers/issues/419](https://github.com/dotnet/roslyn-analyzers/issues/419)
[CA1404](ca1404.md) | [https://github.com/dotnet/roslyn-analyzers/issues/420](https://github.com/dotnet/roslyn-analyzers/issues/420)
[CA1405](ca1405.md) | [https://github.com/dotnet/roslyn-analyzers/issues/421](https://github.com/dotnet/roslyn-analyzers/issues/421)
[CA1407](ca1407.md) | [https://github.com/dotnet/roslyn-analyzers/issues/423](https://github.com/dotnet/roslyn-analyzers/issues/423)
[CA1408](ca1408.md) | [https://github.com/dotnet/roslyn-analyzers/issues/424](https://github.com/dotnet/roslyn-analyzers/issues/424)
[CA1409](ca1409.md) | [https://github.com/dotnet/roslyn-analyzers/issues/425](https://github.com/dotnet/roslyn-analyzers/issues/425)
[CA1410](ca1410.md) | [https://github.com/dotnet/roslyn-analyzers/issues/426](https://github.com/dotnet/roslyn-analyzers/issues/426)
[CA1411](ca1411.md) | [https://github.com/dotnet/roslyn-analyzers/issues/427](https://github.com/dotnet/roslyn-analyzers/issues/427)
[CA1412](ca1412.md) | [https://github.com/dotnet/roslyn-analyzers/issues/428](https://github.com/dotnet/roslyn-analyzers/issues/428)
[CA1413](ca1413.md) | [https://github.com/dotnet/roslyn-analyzers/issues/429](https://github.com/dotnet/roslyn-analyzers/issues/429)
[CA1414](ca1414.md) | [https://github.com/dotnet/roslyn-analyzers/issues/430](https://github.com/dotnet/roslyn-analyzers/issues/430)
[CA1415](ca1415.md) | [https://github.com/dotnet/roslyn-analyzers/issues/431](https://github.com/dotnet/roslyn-analyzers/issues/431)
[CA1500](ca1500.md) | [https://github.com/dotnet/roslyn-analyzers/issues/432](https://github.com/dotnet/roslyn-analyzers/issues/432)
[CA1600](ca1600.md) | [https://github.com/dotnet/roslyn-analyzers/issues/438](https://github.com/dotnet/roslyn-analyzers/issues/438)
[CA1601](ca1601.md) | [https://github.com/dotnet/roslyn-analyzers/issues/439](https://github.com/dotnet/roslyn-analyzers/issues/439)
[CA1700](ca1700.md) | [https://github.com/dotnet/roslyn-analyzers/issues/440](https://github.com/dotnet/roslyn-analyzers/issues/440)
[CA1704](ca1704.md) | [https://github.com/dotnet/roslyn-analyzers/issues/443](https://github.com/dotnet/roslyn-analyzers/issues/443)
[CA1709](ca1709.md) | [https://github.com/dotnet/roslyn-analyzers/issues/445](https://github.com/dotnet/roslyn-analyzers/issues/445)
[CA1713](ca1713.md) | [https://github.com/dotnet/roslyn-analyzers/issues/449](https://github.com/dotnet/roslyn-analyzers/issues/449)
[CA1719](ca1719.md) | [https://github.com/dotnet/roslyn-analyzers/issues/453](https://github.com/dotnet/roslyn-analyzers/issues/453)
[CA1722](ca1722.md) | [https://github.com/dotnet/roslyn-analyzers/issues/455](https://github.com/dotnet/roslyn-analyzers/issues/455)
[CA1726](ca1726.md) | [https://github.com/dotnet/roslyn-analyzers/issues/458](https://github.com/dotnet/roslyn-analyzers/issues/458)
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

### <a name="deprecated-rules"></a>Règles déconseillées

Les règles d’analyse héritées FxCop suivantes sont déconseillées et ne sont pas implémentées en tant qu’analyseurs. Pour plus d’informations, vous pouvez effectuer une recherche par ID de règle (par exemple, **CA1009**) sur la [page des problèmes de GitHub Roslyn-Analyzer](https://github.com/dotnet/roslyn-analyzers/issues?utf8=%E2%9C%93&q=is:issue+label:FxCop-Port).

- [CA1009](ca1009.md)
- [CA1020](ca1020.md)
- [CA1025](ca1025.md)
- [CA1026](ca1026.md)
- [CA1035](ca1035.md)
- [CA1038](ca1038.md)
- [CA1039](ca1039.md)
- [CA1059](ca1059.md)
- [CA1302](ca1302.md)
- [CA1400](ca1400.md)
- [CA1406](ca1406.md)
- [CA1504](ca1504.md)
- [CA1701](ca1701.md)
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
- [Ca2222](ca2222.md) ([Justification](https://github.com/dotnet/roslyn-analyzers/issues/1378))
- [CA2223](ca2223.md)
- [CA2228](ca2228.md)
- [CA2230](ca2230.md)
- [CA2233](ca2233.md)
- [CA5122](ca5122.md)

## <a name="see-also"></a>Voir aussi

- [Règles Microsoft. CodeAnalysis. FxCopAnalyzers](https://github.com/dotnet/roslyn-analyzers/blob/master/src/Microsoft.CodeAnalysis.FxCopAnalyzers/Microsoft.CodeAnalysis.FxCopAnalyzers.md)
