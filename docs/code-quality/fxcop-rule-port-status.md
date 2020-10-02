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
ms.openlocfilehash: 945b26158da4c4c7788570db0c565ebbcfc2b460
ms.sourcegitcommit: c025a5e2013c4955ca685092b13e887ce64aaf64
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2020
ms.locfileid: "91658579"
---
# <a name="fxcop-rule-port-status"></a>État du port de la règle FXCop

Si vous avez précédemment utilisé l’analyse statique du code dans Visual Studio, vous vous demandez peut-être laquelle de ces règles est disponible dans l’implémentation actuelle en tant qu' [analyseurs FxCop](install-fxcop-analyzers.md). Cette page répertorie les règles qui ont été portées. Consultez [règles non portées](fxcop-unported-rules.md) pour celles qui n’ont pas été portées et s’il est prévu de les porter.

## <a name="ported-rules"></a>Règles transférées

La [page de documentation générée automatiquement](https://github.com/dotnet/roslyn-analyzers/blob/master/src/Microsoft.CodeAnalysis.FxCopAnalyzers/Microsoft.CodeAnalysis.FxCopAnalyzers.md) dans Roslyn-Analyzers référentiel contient la liste la plus récente des règles qui ont été portées aux analyseurs FxCop. Cette page contient également des informations supplémentaires, par exemple si la règle est activée par défaut et si elle est associée à un *correctif de code*. (Les[correctifs de code](../ide/quick-actions.md) sont des correctifs accessibles en un clic dans le menu de l’icône d’ampoule dans Visual Studio.)

À partir de la date de cette page, la liste des règles FxCop qui ont été portées aux [analyseurs FxCop](install-fxcop-analyzers.md) comprend les éléments suivants :

Identificateur de la règle | Intitulé
--------|---------
[CA1000](/dotnet/fundamentals/code-analysis/quality-rules/ca1000) | Ne pas déclarer de membres statiques sur les types génériques
[CA1001](/dotnet/fundamentals/code-analysis/quality-rules/ca1001) | Les types qui possèdent des champs supprimables doivent être supprimables
[CA1002](/dotnet/fundamentals/code-analysis/quality-rules/ca1002) | Ne pas exposer de listes génériques
[CA1003](/dotnet/fundamentals/code-analysis/quality-rules/ca1003) | Utiliser les instances du gestionnaire d'événements génériques
[CA1005](/dotnet/fundamentals/code-analysis/quality-rules/ca1005) | Éviter les paramètres excessifs sur les types génériques
[CA1008](/dotnet/fundamentals/code-analysis/quality-rules/ca1008) | Les enums doivent avoir la valeur zéro
[CA1010](/dotnet/fundamentals/code-analysis/quality-rules/ca1010) | Les collections doivent implémenter une interface générique
[CA1012](/dotnet/fundamentals/code-analysis/quality-rules/ca1012) | Les types abstract ne doivent pas avoir de constructeurs
[CA1014](/dotnet/fundamentals/code-analysis/quality-rules/ca1014) | Marquer les assemblys avec CLSCompliant
[CA1016](/dotnet/fundamentals/code-analysis/quality-rules/ca1016) | Marquer les assemblys avec la version de l’assembly
[CA1017](/dotnet/fundamentals/code-analysis/quality-rules/ca1017) | Marquer les assemblys avec ComVisible
[CA1018](/dotnet/fundamentals/code-analysis/quality-rules/ca1018) | Marquer les attributs avec AttributeUsageAttribute
[CA1019](/dotnet/fundamentals/code-analysis/quality-rules/ca1019) | Définir des accesseurs pour les arguments d'attribut
[CA1021](/dotnet/fundamentals/code-analysis/quality-rules/ca1021) | Éviter les paramètres out
[CA1024](/dotnet/fundamentals/code-analysis/quality-rules/ca1024) | Utiliser les propriétés lorsque cela est approprié
[CA1027](/dotnet/fundamentals/code-analysis/quality-rules/ca1027) | Marquer les enums avec FlagsAttribute
[CA1028](/dotnet/fundamentals/code-analysis/quality-rules/ca1028) | Le stockage enum doit être Int32
[CA1030](/dotnet/fundamentals/code-analysis/quality-rules/ca1030) | Utiliser des événements lorsque cela est approprié
[CA1031](/dotnet/fundamentals/code-analysis/quality-rules/ca1031) | Ne pas intercepter des types d'exception générale
[CA1032](/dotnet/fundamentals/code-analysis/quality-rules/ca1032) | Implémenter des constructeurs d'exception standard
[CA1033](/dotnet/fundamentals/code-analysis/quality-rules/ca1033) | Les méthodes d'interface doivent pouvoir être appelées par les types enfants
[CA1034](/dotnet/fundamentals/code-analysis/quality-rules/ca1034) | Les types imbriqués ne doivent pas être visibles
[CA1036](/dotnet/fundamentals/code-analysis/quality-rules/ca1036) | Substituer les méthodes sur les types Comparable
[CA1040](/dotnet/fundamentals/code-analysis/quality-rules/ca1040) | Éviter les interfaces vides
[CA1041](/dotnet/fundamentals/code-analysis/quality-rules/ca1041) | Fournir un message ObsoleteAttribute
[CA1043](/dotnet/fundamentals/code-analysis/quality-rules/ca1043) | Utiliser un argument de chaîne ou intégral pour les indexeurs
[CA1044](/dotnet/fundamentals/code-analysis/quality-rules/ca1044) | Les propriétés ne doivent pas être en écriture seule
[CA1045](/dotnet/fundamentals/code-analysis/quality-rules/ca1045) | Ne pas passer de types par référence
[CA1046](/dotnet/fundamentals/code-analysis/quality-rules/ca1046) | Ne pas surcharger l'opérateur égal à sur les types référence
[CA1047](/dotnet/fundamentals/code-analysis/quality-rules/ca1047) | Ne pas déclarer les membres protégés dans les types sealed
[CA1050](/dotnet/fundamentals/code-analysis/quality-rules/ca1050) | Déclarer les types dans des espaces de noms
[CA1051](/dotnet/fundamentals/code-analysis/quality-rules/ca1051) | Ne pas déclarer de champs d'instances visibles
[CA1052](/dotnet/fundamentals/code-analysis/quality-rules/ca1052) | Les types de conteneurs statiques doivent être statiques ou NotInheritable
[CA1053](/dotnet/fundamentals/code-analysis/quality-rules/ca1053) | Les types de conteneurs statiques ne doivent pas avoir de constructeurs (ca1053 fait partie de [CA1052](/dotnet/fundamentals/code-analysis/quality-rules/ca1052) pour les analyseurs FxCop)
[CA1054](/dotnet/fundamentals/code-analysis/quality-rules/ca1054) | Les paramètres URI ne doivent pas être des chaînes
[CA1055](/dotnet/fundamentals/code-analysis/quality-rules/ca1055) | Les valeurs de retour URI ne doivent pas être des chaînes
[CA1056](/dotnet/fundamentals/code-analysis/quality-rules/ca1056) | Les propriétés URI ne doivent pas être des chaînes
[CA1058](/dotnet/fundamentals/code-analysis/quality-rules/ca1058) | Les types ne doivent pas étendre certains types de base
[CA1060](/dotnet/fundamentals/code-analysis/quality-rules/ca1060) | Déplacer pinvokes vers une classe de méthodes natives
[CA1061](/dotnet/fundamentals/code-analysis/quality-rules/ca1061) | Ne pas masquer les méthodes de la classe de base
[CA1062](/dotnet/fundamentals/code-analysis/quality-rules/ca1062) | Valider les arguments de méthodes publiques
[CA1063](/dotnet/fundamentals/code-analysis/quality-rules/ca1063) | Implémenter IDisposable correctement
[CA1064](/dotnet/fundamentals/code-analysis/quality-rules/ca1064) | Les exceptions doivent être publiques
[CA1065](/dotnet/fundamentals/code-analysis/quality-rules/ca1065) | Ne pas lever d'exceptions dans les emplacements inattendus
[CA1066](/dotnet/fundamentals/code-analysis/quality-rules/ca1066) | {0}Le type doit implémenter IEquatable \<T> , car il remplace égal à
[CA1067](/dotnet/fundamentals/code-analysis/quality-rules/ca1067) | Remplacer Object. Equals (Object) lors de l’implémentation de IEquatable\<T>
[CA1303](/dotnet/fundamentals/code-analysis/quality-rules/ca1303) | Ne pas passer de littéraux en paramètres localisés
[CA1304](/dotnet/fundamentals/code-analysis/quality-rules/ca1304) | Spécifier CultureInfo
[CA1305](/dotnet/fundamentals/code-analysis/quality-rules/ca1305) | Spécifier IFormatProvider
[CA1307](/dotnet/fundamentals/code-analysis/quality-rules/ca1307) | Spécifier StringComparison pour plus de clarté
[CA1308](/dotnet/fundamentals/code-analysis/quality-rules/ca1308) | Normaliser les chaînes en majuscules
[CA1309](/dotnet/fundamentals/code-analysis/quality-rules/ca1309) | Utiliser la comparaison de chaînes ordinale
[CA1401](/dotnet/fundamentals/code-analysis/quality-rules/ca1401) | Les P/Invoke ne doivent pas être visibles
[CA1501](/dotnet/fundamentals/code-analysis/quality-rules/ca1501) | Éviter l'excès d'héritage
[CA1502](/dotnet/fundamentals/code-analysis/quality-rules/ca1502) | Éviter l'excès de complexité
[CA1505](/dotnet/fundamentals/code-analysis/quality-rules/ca1505) | Éviter le code impossible à maintenir
[CA1506](/dotnet/fundamentals/code-analysis/quality-rules/ca1506) | Éviter les couplages de classe excessifs
[CA1700](/dotnet/fundamentals/code-analysis/quality-rules/ca1700) | Ne nommez pas les valeurs enum 'Reserved'
[CA1707](/dotnet/fundamentals/code-analysis/quality-rules/ca1707) | Les identificateurs ne doivent pas contenir de traits de soulignement
[CA1708](/dotnet/fundamentals/code-analysis/quality-rules/ca1708) | Les identificateurs ne doivent pas différer uniquement par leur casse
[CA1710](/dotnet/fundamentals/code-analysis/quality-rules/ca1710) | Les identificateurs doivent être dotés d'un suffixe correct
[CA1711](/dotnet/fundamentals/code-analysis/quality-rules/ca1711) | Les identificateurs ne doivent pas porter un suffixe incorrect
[CA1712](/dotnet/fundamentals/code-analysis/quality-rules/ca1712) | N'ajoutez pas le nom de type en guise de préfixe à des valeurs enum
[CA1713](/dotnet/fundamentals/code-analysis/quality-rules/ca1713) | Les événements ne doivent pas être munis d'un préfixe Before ou After
[CA1714](/dotnet/fundamentals/code-analysis/quality-rules/ca1714) | Les noms des enums Flags doivent être au pluriel
[CA1715](/dotnet/fundamentals/code-analysis/quality-rules/ca1715) | Les identificateurs doivent être dotés d'un préfixe correct
[CA1716](/dotnet/fundamentals/code-analysis/quality-rules/ca1716) | Les identificateurs ne doivent pas correspondre à des mots clés
[CA1717](/dotnet/fundamentals/code-analysis/quality-rules/ca1717) | Seuls les noms des enums FlagsAttribute doivent être au pluriel
[CA1720](/dotnet/fundamentals/code-analysis/quality-rules/ca1720) | L’identificateur contient le nom du type
[CA1721](/dotnet/fundamentals/code-analysis/quality-rules/ca1721) | Les noms des propriétés ne doivent pas être identiques à ceux des méthodes Get
[CA1724](/dotnet/fundamentals/code-analysis/quality-rules/ca1724) | Les noms de types ne doivent pas correspondre à des espaces de noms
[CA1725](/dotnet/fundamentals/code-analysis/quality-rules/ca1725) | Les noms des paramètres doivent correspondre à la déclaration de base
[CA1801](/dotnet/fundamentals/code-analysis/quality-rules/ca1801) | Passez en revue les paramètres inutilisés
[CA1802](/dotnet/fundamentals/code-analysis/quality-rules/ca1802) | Utiliser des littéraux quand cela est approprié
[CA1805](/dotnet/fundamentals/code-analysis/quality-rules/ca1805) | Ne pas initialiser inutilement
[CA1806](/dotnet/fundamentals/code-analysis/quality-rules/ca1806) | N'ignorez pas les résultats des méthodes
[CA1810](/dotnet/fundamentals/code-analysis/quality-rules/ca1810) | Initialisez les champs statiques de type référence en ligne
[CA1812](/dotnet/fundamentals/code-analysis/quality-rules/ca1812) | Évitez les classes internes non instanciées
[CA1813](/dotnet/fundamentals/code-analysis/quality-rules/ca1813) | Évitez les attributs unsealed
[CA1814](/dotnet/fundamentals/code-analysis/quality-rules/ca1814) | Utilisez des tableaux en escalier à la place de tableaux multidimensionnels
[CA1815](/dotnet/fundamentals/code-analysis/quality-rules/ca1815) | Remplacez Equals et l'opérateur égal à dans les types valeur
[CA1816](/dotnet/fundamentals/code-analysis/quality-rules/ca1816) | Les méthodes dispose doivent appeler SuppressFinalize
[CA1819](/dotnet/fundamentals/code-analysis/quality-rules/ca1819) | Les propriétés ne doivent pas retourner des tableaux
[CA1820](/dotnet/fundamentals/code-analysis/quality-rules/ca1820) | Vérifiez la présence de chaînes vides par la longueur de chaîne
[CA1821](/dotnet/fundamentals/code-analysis/quality-rules/ca1821) | Supprimer les finaliseurs vides
[CA1822](/dotnet/fundamentals/code-analysis/quality-rules/ca1822) | Marquez les membres comme static
[CA1823](/dotnet/fundamentals/code-analysis/quality-rules/ca1823) | Évitez les champs privés inutilisés
[CA1824](/dotnet/fundamentals/code-analysis/quality-rules/ca1824) | Marquer les assemblys avec NeutralResourcesLanguageAttribute
[CA1825](/dotnet/fundamentals/code-analysis/quality-rules/ca1825) | Évitez les allocations de tableau de longueur nulle.
[CA2000](/dotnet/fundamentals/code-analysis/quality-rules/ca2000) | Supprimer les objets avant la mise hors de portée
[CA2002](/dotnet/fundamentals/code-analysis/quality-rules/ca2002) | Ne définissez pas un verrou sur des objets à identité faible
[CA2100](/dotnet/fundamentals/code-analysis/quality-rules/ca2100) | Vérifier si les requêtes SQL présentent des failles de sécurité
[CA2101](/dotnet/fundamentals/code-analysis/quality-rules/ca2101) | Spécifiez le marshaling pour les arguments de chaîne P/Invoke
[CA2109](/dotnet/fundamentals/code-analysis/quality-rules/ca2109) | Passez en revue les gestionnaires d'événements visibles
[CA2119](/dotnet/fundamentals/code-analysis/quality-rules/ca2119) | Scellez les méthodes qui satisfont les interfaces privées
[CA2153](/dotnet/fundamentals/code-analysis/quality-rules/ca2153) | Ne pas intercepter les exceptions d’état endommagé
[CA2200](/dotnet/fundamentals/code-analysis/quality-rules/ca2200) | Levez à nouveau pour conserver les détails de la pile.
[CA2201](/dotnet/fundamentals/code-analysis/quality-rules/ca2201) | Ne levez pas des types d'exceptions réservés
[CA2207](/dotnet/fundamentals/code-analysis/quality-rules/ca2207) | Initialisez les champs statiques des types valeur en ligne
[CA2208](/dotnet/fundamentals/code-analysis/quality-rules/ca2208) | Instanciez les exceptions d'argument comme il se doit
[CA2211](/dotnet/fundamentals/code-analysis/quality-rules/ca2211) | Les champs non constants ne doivent pas être visibles
[CA2213](/dotnet/fundamentals/code-analysis/quality-rules/ca2213) | Les champs pouvant être supprimés doivent l’être
[CA2214](/dotnet/fundamentals/code-analysis/quality-rules/ca2214) | N'appelez pas de méthodes substituables dans les constructeurs
[CA2215](/dotnet/fundamentals/code-analysis/quality-rules/ca2215) | Les méthodes Dispose doivent appeler la méthode Dispose de la classe de base
[CA2216](/dotnet/fundamentals/code-analysis/quality-rules/ca2216) | Les types pouvant être supprimés doivent déclarer un finaliseur
[CA2217](/dotnet/fundamentals/code-analysis/quality-rules/ca2217) | Ne marquez pas les enums avec l'attribut FlagsAttribute
[CA2219](/dotnet/fundamentals/code-analysis/quality-rules/ca2219) | Ne levez pas d’exceptions dans les clauses finally
[CA2225](/dotnet/fundamentals/code-analysis/quality-rules/ca2225) | Les surcharges d'opérateur offrent d'autres méthodes nommées
[CA2226](/dotnet/fundamentals/code-analysis/quality-rules/ca2226) | Les opérateurs doivent contenir des surcharges symétriques
[CA2227](/dotnet/fundamentals/code-analysis/quality-rules/ca2227) | Les propriétés de collection doivent être en lecture seule
[CA2229](/dotnet/fundamentals/code-analysis/quality-rules/ca2229) | Implémentez des constructeurs de sérialisation
[CA2231](/dotnet/fundamentals/code-analysis/quality-rules/ca2231) | Surchargez l’opérateur égal en cas de substitution de type valeur égal à
[CA2234](/dotnet/fundamentals/code-analysis/quality-rules/ca2234) | Passer des objets URI système à la place de chaînes
[CA2235](/dotnet/fundamentals/code-analysis/quality-rules/ca2235) | Marquez tous les champs non sérialisés
[CA2237](/dotnet/fundamentals/code-analysis/quality-rules/ca2237) | Marquez les types ISerializable comme étant sérialisables
[CA2241](/dotnet/fundamentals/code-analysis/quality-rules/ca2241) | Indiquer le nombre correct d'arguments dans les méthodes de mise en forme
[CA2242](/dotnet/fundamentals/code-analysis/quality-rules/ca2242) | Effectuez correctement des tests NaN
[CA2243](/dotnet/fundamentals/code-analysis/quality-rules/ca2243) | Les littéraux de chaîne d'attribut doivent être analysés correctement
[CA2300](/dotnet/fundamentals/code-analysis/quality-rules/ca2300) | N’utilisez pas le désérialiseur non sécurisé BinaryFormatter
[CA2301](/dotnet/fundamentals/code-analysis/quality-rules/ca2301) | N’appelez pas BinaryFormatter.Deserialize sans définir BinaryFormatter.Binder au préalable
[CA2302](/dotnet/fundamentals/code-analysis/quality-rules/ca2302) | Vérifiez que BinaryFormatter.Binder est défini avant d’appeler BinaryFormatter.Deserialize
[CA2305](/dotnet/fundamentals/code-analysis/quality-rules/ca2305) | N’utilisez pas le désérialiseur non sécurisé LosFormatter
[CA2310](/dotnet/fundamentals/code-analysis/quality-rules/ca2310) | N’utilisez pas le désérialiseur non sécurisé NetDataContractSerializer
[CA2311](/dotnet/fundamentals/code-analysis/quality-rules/ca2311) | Ne désérialisez pas sans définir d’abord NetDataContractSerializer.Binder
[CA2312](/dotnet/fundamentals/code-analysis/quality-rules/ca2312) | Vérifiez que NetDataContractSerializer.Binder est défini avant la désérialisation
[CA2315](/dotnet/fundamentals/code-analysis/quality-rules/ca2315) | N’utilisez pas le désérialiseur non sécurisé ObjectStateFormatter
[CA2321](/dotnet/fundamentals/code-analysis/quality-rules/ca2321) | Ne désérialisez avec JavaScriptSerializer à l’aide de SimpleTypeResolver
[CA2322](/dotnet/fundamentals/code-analysis/quality-rules/ca2322) | Assurez-vous que JavaScriptSerializer n’est pas initialisé avec SimpleTypeResolver avant la désérialisation
[CA3001](/dotnet/fundamentals/code-analysis/quality-rules/ca3001) | Passez en revue le code pour détecter les vulnérabilités de l’injection SQL
[CA3002](/dotnet/fundamentals/code-analysis/quality-rules/ca3002) | Passez en revue le code pour détecter les vulnérabilités des scripts XSS
[CA3003](/dotnet/fundamentals/code-analysis/quality-rules/ca3003) | Passez en revue le code pour détecter les vulnérabilités de l’injection de chemin de fichier
[CA3004](/dotnet/fundamentals/code-analysis/quality-rules/ca3004) | Passez en revue le code pour détecter les vulnérabilités sur la divulgation d’informations
[CA3005](/dotnet/fundamentals/code-analysis/quality-rules/ca3005) | Passez en revue le code pour détecter les vulnérabilités de l’injection LDAP
[CA3006](/dotnet/fundamentals/code-analysis/quality-rules/ca3006) | Passez en revue le code pour détecter les vulnérabilités de l’injection de commande de processus
[CA3007](/dotnet/fundamentals/code-analysis/quality-rules/ca3007) | Passez en revue le code pour détecter les vulnérabilités de la redirection ouverte
[CA3008](/dotnet/fundamentals/code-analysis/quality-rules/ca3008) | Passez en revue le code pour détecter les vulnérabilités de l’injection XPath
[CA3009](/dotnet/fundamentals/code-analysis/quality-rules/ca3009) | Passez en revue le code pour détecter les vulnérabilités de l’injection XML
[CA3010](/dotnet/fundamentals/code-analysis/quality-rules/ca3010) | Passez en revue le code pour détecter les vulnérabilités de l’injection XAML
[CA3011](/dotnet/fundamentals/code-analysis/quality-rules/ca3011) | Passez en revue le code pour détecter les vulnérabilités de l’injection de DLL
[CA3012](/dotnet/fundamentals/code-analysis/quality-rules/ca3012) | Passez en revue le code pour détecter les vulnérabilités de l’injection regex
[CA3061](/dotnet/fundamentals/code-analysis/quality-rules/ca3061) | Ne pas ajouter de schéma par URL
[CA3075](/dotnet/fundamentals/code-analysis/quality-rules/ca3075) | Traitement DTD non sécurisé dans le code XML
[CA3076](/dotnet/fundamentals/code-analysis/quality-rules/ca3076) | Le traitement des scripts XSLT n’est pas sécurisé.
[CA3077](/dotnet/fundamentals/code-analysis/quality-rules/ca3077) | Traitement non sécurisé dans la conception d’API, XmlDocument et XmlTextReader
[CA3147](/dotnet/fundamentals/code-analysis/quality-rules/ca3147) | Marquer les gestionnaires de verbe avec valider le jeton anti-contrefaçon
[CA5350](/dotnet/fundamentals/code-analysis/quality-rules/ca5350) | N’utilisez pas d’algorithmes de chiffrement faibles
[CA5351](/dotnet/fundamentals/code-analysis/quality-rules/ca5351) | Ne pas utiliser les algorithmes de chiffrement rompus
[CA5358](/dotnet/fundamentals/code-analysis/quality-rules/ca5358) | Ne pas utiliser de modes de chiffrement non sécurisés
CA5359 | Ne pas désactiver la validation de certificat
CA5360 | N’appelez pas de méthodes dangereuses dans la désérialisation
[CA5361](/dotnet/fundamentals/code-analysis/quality-rules/ca5361) | Ne pas désactiver l’utilisation de SChannel de chiffrement fort
CA5362 | Ne pas faire référence à une classe sérialisable autonome
[CA5363](/dotnet/fundamentals/code-analysis/quality-rules/ca5363) | Ne pas désactiver la validation de la demande
[CA5364](/dotnet/fundamentals/code-analysis/quality-rules/ca5364) | Ne pas utiliser les protocoles de sécurité déconseillés
CA5365 | Ne désactivez pas la vérification d’en-tête HTTP
CA5366 | Utiliser XmlReader pour lire le jeu de données XML
CA5367 | Ne sérialisez pas les types avec des champs de pointeur
CA5368 | Définir ViewStateUserKey pour les classes dérivées de page
[CA5369](/dotnet/fundamentals/code-analysis/quality-rules/ca5369) | Utiliser XmlReader pour la désérialisation
[CA5370](/dotnet/fundamentals/code-analysis/quality-rules/ca5370) | Utiliser XmlReader pour valider le lecteur
[CA5371](/dotnet/fundamentals/code-analysis/quality-rules/ca5371) | Utiliser XmlReader pour la lecture de schéma
[CA5372](/dotnet/fundamentals/code-analysis/quality-rules/ca5372) | Utiliser XmlReader pour XPathDocument
[CA5373](/dotnet/fundamentals/code-analysis/quality-rules/ca5373) | Ne pas utiliser la fonction de dérivation de clé obsolète
CA5374 | Ne pas utiliser XslTransform
CA5375 | Ne pas utiliser la signature d’accès partagé du compte
CA5376 | Utiliser SharedAccessProtocol HttpsOnly
CA5377 | Utiliser la stratégie d’accès au niveau du conteneur
[CA5378](/dotnet/fundamentals/code-analysis/quality-rules/ca5378) | Ne pas désactiver ServicePointManagerSecurityProtocols
CA5379 | Ne pas utiliser l’algorithme de fonction de dérivation de clé faible
Ca9999 | Incompatibilité des versions de l’analyseur

## <a name="see-also"></a>Voir aussi

- [Règles Microsoft. CodeAnalysis. FxCopAnalyzers](https://github.com/dotnet/roslyn-analyzers/blob/master/src/Microsoft.CodeAnalysis.FxCopAnalyzers/Microsoft.CodeAnalysis.FxCopAnalyzers.md)
