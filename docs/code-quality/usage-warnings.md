---
title: avertissements liés à l’utilisation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.codeanalysis.usagerules
helpviewer_keywords:
- warnings, usage
- managed code analysis warnings, usage warnings
- usage warnings
ms.assetid: fe7dc2a3-289d-4bf7-a1e4-0947a81287c4
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e607da01d160212eea03b1fe81dfb2fbf4ede3f6
ms.sourcegitcommit: 034c503ae04e22cf840ccb9770bffd012e40fb2d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/14/2019
ms.locfileid: "72305689"
---
# <a name="usage-warnings"></a>avertissements liés à l’utilisation

Les avertissements d’utilisation prennent en charge l’utilisation correcte de .NET.

## <a name="in-this-section"></a>Dans cette section

|Règle|Description|
|----------|-----------------|
|@NO__T 0CA1801 : Passer en revue les paramètres inutilisés @ no__t-0|Une signature de méthode inclut un paramètre qui n'est pas utilisé dans le corps de la méthode.|
|@NO__T 0CA1806 : Ne pas ignorer les résultats de la méthode @ no__t-0|Un nouvel objet est créé mais jamais utilisé ; ou une méthode qui crée et retourne une nouvelle chaîne est appelée et la nouvelle chaîne n'est jamais utilisée ; ou une méthode COM ou P/Invoke retourne un code HRESULT ou d'erreur qui n'est jamais utilisé.|
|@NO__T 0CA1816 : Appelez GC. SuppressFinalize correctement @ no__t-0|Une méthode qui est une implémentation de Dispose n’appelle pas de catalogue global. SuppressFinalize ; ou une méthode qui n’est pas une implémentation de Dispose appelle GC. SuppressFinalize ; ou une méthode appelle GC. SuppressFinalize et passe un élément autre que cette (Me en Visual Basic).|
|@NO__T 0CA2200 : Lever à nouveau pour conserver les détails de la pile @ no__t-0|Une exception est à nouveau levée et est spécifiée explicitement dans l'instruction throw. Si une exception est à nouveau levée par sa spécification dans l'instruction throw, la liste des appels de méthode présents entre la méthode d'origine qui a levé l'exception et la méthode actuelle est perdue.|
|@NO__T 0CA2201 : Ne levez pas les types d’exceptions réservés @ no__t-0|Cela rend l’erreur d’origine difficile à détecter et à déboguer.|
|@NO__T 0CA2202 : Ne pas supprimer les objets plusieurs fois @ no__t-0|Une implémentation de méthode contient des chemins d’accès de code qui peuvent provoquer des appels multiples à System.IDisposable.Dispose ou un Dispose équivalent (par exemple, une méthode Close() sur certains types) sur le même objet.|
|@NO__T 0CA2204 : Les littéraux doivent être orthographiés correctement @ no__t-0|Une chaîne littéral dans un corps de méthode contient un ou plusieurs mots qui ne sont pas reconnus par la bibliothèque de vérificateur d'orthographe Microsoft.|
|@NO__T 0CA2205 : Utiliser des équivalents managés de l’API Win32 @ no__t-0|Une méthode d’appel de code non managé est définie et une méthode .NET avec les fonctionnalités équivalentes est disponible.|
|@NO__T 0CA2207 : Initialiser les champs statiques de type valeur Inline @ no__t-0|Un type valeur déclare un constructeur statique explicite. Pour corriger une violation de cette règle, initialisez toutes les données statiques lorsqu’elles sont déclarées et supprimez le constructeur statique.|
|@NO__T 0CA2208 : Instancier les exceptions d’argument correctement @ no__t-0|Un appel est passé au constructeur par défaut (sans paramètre) d’un type d’exception qui est ou dérive d’ArgumentException, ou un argument string incorrect est passé à un constructeur paramétrable d’un type d’exception qui est ou dérive d’ArgumentException.|
|@NO__T 0CA2211 : Les champs non constants ne doivent pas être visibles @ no__t-0|Les champs statiques qui ne sont pas des constantes ou en lecture seule ne sont pas thread-safe. L’accès à ce champ doit être contrôlé avec soin et nécessite des techniques de programmation avancées pour la synchronisation de l’accès à l’objet de classe.|
|@NO__T 0CA2212 : Ne Marquez pas les composants pris en service avec WebMethod @ no__t-0|Une méthode d’un type qui hérite de System. EnterpriseServices. ServicedComponent est marquée avec System. Web. services. WebMethodAttribute. Sachant que WebMethodAttribute et une méthode ServicedComponent ont des comportements incompatibles et des exigences en matière de contexte et de flux de transactions, le comportement de la méthode est incorrect dans certains scénarios.|
|[CA2213 : Les champs pouvant être supprimés doivent l’être](../code-quality/ca2213-disposable-fields-should-be-disposed.md)|Un type qui implémente System.IDisposable déclare des champs de types qui implémentent également IDisposable. La méthode Dispose du champ n’est pas appelée par la méthode Dispose du type déclarant.|
|@NO__T 0CA2214 : N’appelez pas de méthodes substituables dans les constructeurs @ no__t-0|Quand un constructeur appelle une méthode virtuelle, il est possible que le constructeur de l’instance qui appelle la méthode n’ait pas été exécuté.|
|@NO__T 0CA2215 : Les méthodes dispose doivent appeler la classe de base dispose @ no__t-0|Si un type hérite d'un type pouvant être supprimé, il doit appeler la méthode Dispose du type de base issu de sa propre méthode Dispose.|
|@NO__T 0CA2216 : Les types jetables doivent déclarer un finaliseur @ no__t-0|Un type qui implémente System. IDisposable et a des champs qui suggèrent l’utilisation de ressources non managées, n’implémente pas de finaliseur comme décrit par Object. Finalize.|
|@NO__T 0CA2217 : Ne Marquez pas les enums avec FlagsAttribute @ no__t-0|Une énumération visible de l’extérieur est marquée avec FlagsAttribute et comporte une ou plusieurs valeurs qui ne sont pas des puissances de deux ou une combinaison des autres valeurs définies sur l’énumération.|
|@NO__T 0CA2218 : Substituez GetHashCode lors du remplacement de est égal à @ no__t-0|GetHashCode retourne une valeur fondée sur l’instance actuelle adaptée aux algorithmes de hachage et aux structures de données telles qu’une table de hachage. Deux objets de même type et égaux doivent retourner le même code de hachage.|
|@NO__T 0CA2219 : Ne levez pas d’exceptions dans les clauses d’exception @ no__t-0|Lorsqu'une exception est levée dans une clause finally ou fault, la nouvelle exception masque l'exception active. Lorsqu'une exception est levée dans une clause filter, le runtime l'intercepte en silence. Cela rend l’erreur d’origine difficile à détecter et à déboguer.|
|@NO__T 0CA2220 : Les finaliseurs doivent appeler le finaliseur de la classe de base @ no__t-0|La finalisation doit être propagée par le biais de la hiérarchie d'héritage. Pour garantir ce procédé, les types doivent appeler leur méthode Finalize de classe de base à partir de leur propre méthode Finalize.|
|@NO__T 0CA2221 : Les finaliseurs doivent être protégés @ no__t-0|Les finaliseurs doivent utiliser le modificateur d’accès family.|
|@NO__T 0CA2222 : Ne pas réduire la visibilité des membres hérités @ no__t-0|Ne modifiez pas le modificateur d’accès pour les membres hérités. La modification d'un membre hérité au profit d'un état privé n'empêche pas les appelants d'accéder à l'implémentation de classe de base de la méthode.|
|@NO__T 0CA2223 : Les membres doivent différer par plus que le type de retour @ no__t-0|Bien que le Common Language Runtime autorise l’utilisation de types de retour pour différencier des membres autrement identiques, cette fonctionnalité ne figure pas dans la Common Language Specification, et n’est pas une fonctionnalité courante des langages de programmation .NET.|
|@NO__T 0CA2224 : Remplacer Equals lors de la surcharge de l’opérateur est égal à @ no__t-0|Un type public implémente l’opérateur d’égalité, mais ne se substitue pas à Object. Equals.|
|@NO__T 0CA2225 : Les surcharges d’opérateur ont des alternatives nommées @ no__t-0|Une surcharge d'opérateur a été détectée, et la méthode de substitution nommée attendue n'a pas été trouvée. Le membre de substitution nommé fournit l’accès aux mêmes fonctionnalités que l’opérateur et est fourni aux développeurs qui programment dans des langages qui ne prennent pas en charge les opérateurs surchargés.|
|@NO__T 0CA2226 : Les opérateurs doivent avoir des surcharges symétriques @ no__t-0|Un type implémente l’opérateur d’égalité ou d’inégalité et n’implémente pas l’opérateur opposé.|
|@NO__T 0CA2227 : Les propriétés de collection doivent être en lecture seule @ no__t-0|Une propriété de collection accessible en écriture permet à un utilisateur de remplacer la collection par une collection différente. Une propriété en lecture seule empêche le remplacement de la collection, mais permet quand même aux membres individuels d’être définis.|
|@NO__T 0CA2228 : Ne fournissez pas de formats de ressources non commercialisés @ no__t-0|Les fichiers de ressources générés à l’aide des versions préliminaires du .NET peuvent ne pas être utilisables par les versions prises en charge de .NET.|
|[CA2229 : Implémentez des constructeurs de sérialisation](../code-quality/ca2229-implement-serialization-constructors.md)|Pour corriger une violation de cette règle, implémentez le constructeur de sérialisation. Dans le cas d'une classe sealed, rendez le constructeur privé ; sinon, attribuez-lui l'état protégé.|
|@NO__T 0CA2230 : Utiliser des paramètres pour les arguments de variable @ no__t-0|Un type public ou protégé contient une méthode publique ou protégée qui utilise la convention d’appel VarArgs au lieu du mot clé params.|
|[CA2231 : Surchargez l’opérateur égal (equals) en remplaçant ValueType.Equals](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)|Un type valeur se substitue à `Object.Equals`, mais n’implémente pas l’opérateur d’égalité.|
|@NO__T 0CA2232 : Marquer Windows Forms points d’entrée avec STAThread @ no__t-0|STAThreadAttribute indique que le modèle de thread COM pour l'application est un thread cloisonné (STA, Single-Threaded Apartment). Cet attribut doit être présent au point d'entrée de toute application qui utilise des Windows Forms ; s'il est omis, les composants Windows peuvent ne pas fonctionner correctement.|
|@NO__T 0CA2233 : Les opérations ne doivent pas dépasser @ no__t-0|Les opérations arithmétiques ne doivent pas être effectuées sans valider au préalable les opérandes, pour s’assurer que le résultat de l’opération n’est pas en dehors de la plage des valeurs possibles pour les types de données impliqués.|
|@NO__T 0CA2234 : Passer des objets System. URI à la place de Strings @ no__t-0|Un appel est passé à une méthode qui a un paramètre de chaîne dont le nom contient « uri », « URI », « urn », « URN », « url » ou « URL ».  Le type déclarant de la méthode contient une surcharge de méthode correspondante qui a un paramètre System.Uri.|
|[CA2235 : Marquez tous les champs non sérialisés](../code-quality/ca2235-mark-all-non-serializable-fields.md)|Un champ d'instance d'un type non sérialisable est déclaré dans un type sérialisable.|
|@NO__T 0CA2236 : Appeler les méthodes de la classe de base sur les types ISerializable @ no__t-0|Pour corriger une violation de cette règle, appelez la méthode GetObjectData ou le constructeur de sérialisation du type de base issu du constructeur ou de la méthode du type dérivé correspondant.|
|[CA2237 : Marquer les types ISerializable avec SerializableAttribute @ no__t-0|Pour être reconnus par le common language runtime comme sérialisable, les types doivent être marqués avec l’attribut SerializableAttribute même si le type utilise une routine de sérialisation personnalisée par le biais de l’implémentation de l’interface ISerializable.|
|@NO__T 0CA2238 : Implémentez correctement les méthodes de sérialisation @ no__t-0|Une méthode qui gère un événement de sérialisation n’a pas la signature, le type de retour ou la visibilité appropriée.|
|@NO__T 0CA2239 : Fournir des méthodes de désérialisation pour les champs facultatifs @ no__t-0|Un type a un champ qui est marqué avec l’attribut System. Runtime. Serialization. OptionalFieldAttribute, et le type ne fournit pas de méthodes de gestion des événements de désérialisation.|
|@NO__T 0CA2240 : Implémentez ISerializable correctement @ no__t-0|Pour corriger une violation de cette règle, rendez la méthode GetObjectData visible et substituable, et assurez-vous que tous les champs d’instance sont inclus dans le processus de sérialisation ou explicitement marqués avec l’attribut NonSerializedAttribute.|
|@NO__T 0CA2241 : Fournir des arguments corrects aux méthodes de mise en forme @ no__t-0|L’argument de format passé à System. String. format ne contient pas d’élément de mise en forme qui correspond à chaque argument d’objet, ou vice versa.|
|@NO__T 0CA2242 : Test de NaN correctement @ no__t-0|Cette expression teste une valeur par rapport à Single.Nan ou Double.Nan. Utilisez Single.IsNan(Single) ou Double.IsNan(Double) pour tester la valeur.|
|@NO__T 0CA2243 : Les littéraux de chaîne d’attribut doivent être analysés correctement @ no__t-0|Le paramètre de littéral de chaîne d’un attribut n’est pas analysé correctement pour une URL, un GUID ou une version.|