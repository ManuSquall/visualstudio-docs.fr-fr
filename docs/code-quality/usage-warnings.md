---
title: Règles d’utilisation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.codeanalysis.usagerules
helpviewer_keywords:
- rules, usage
- managed code analysis rules, usage rules
- usage rules
ms.assetid: fe7dc2a3-289d-4bf7-a1e4-0947a81287c4
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 45dd58978bb37dd66023d8a28b9babf017bec262
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2020
ms.locfileid: "90806185"
---
# <a name="usage-rules"></a>Règles d’utilisation

Les règles d’utilisation prennent en charge l’utilisation correcte de .NET.

## <a name="in-this-section"></a>Dans cette section

|Règle|Description|
|----------|-----------------|
|[CA1801 : Passez en revue les paramètres inutilisés](../code-quality/ca1801.md)|Une signature de méthode inclut un paramètre qui n'est pas utilisé dans le corps de la méthode.|
|[CA1816 : Appeler GC.SuppressFinalize correctement](../code-quality/ca1816.md)|Une méthode qui est une implémentation de Dispose n'appelle pas GC.SuppressFinalize ; ou une méthode qui n'est pas une implémentation de Dispose appelle GC.SuppressFinalize ; ou une méthode appelle GC.SuppressFinalize et passe un élément autre que celui-ci (Me en Visual Basic).|
|[CA2200 : Levez à nouveau une exception pour conserver les détails de la pile](../code-quality/ca2200.md)|Une exception est à nouveau levée et est spécifiée explicitement dans l'instruction throw. Si une exception est à nouveau levée par sa spécification dans l'instruction throw, la liste des appels de méthode présents entre la méthode d'origine qui a levé l'exception et la méthode actuelle est perdue.|
|[CA2201 : Ne levez pas des types d'exceptions réservés](../code-quality/ca2201.md)|Cela rend l’erreur d’origine difficile à détecter et à déboguer.|
|[CA2202 : Ne pas supprimer d'objets plusieurs fois](../code-quality/ca2202.md)|Une implémentation de méthode contient des chemins d’accès de code qui peuvent provoquer des appels multiples à System.IDisposable.Dispose ou un Dispose équivalent (par exemple, une méthode Close() sur certains types) sur le même objet.|
|[CA2207 : Initialisez les champs statiques des types valeur en ligne](../code-quality/ca2207.md)|Un type valeur déclare un constructeur statique explicite. Pour corriger une violation de cette règle, initialisez toutes les données statiques lorsqu’elles sont déclarées et supprimez le constructeur statique.|
|[CA2208 : Instanciez les exceptions d'argument comme il se doit](../code-quality/ca2208.md)|Un appel est passé au constructeur par défaut (sans paramètre) d'un type d'exception qui est ou dérive d'ArgumentException, ou un argument string incorrect est passé à un constructeur paramétrable d'un type d'exception qui est ou dérive d'ArgumentException.|
|[CA2211 : Les champs non constants ne doivent pas être visibles](../code-quality/ca2211.md)|Les champs statiques qui ne sont pas des constantes ou en lecture seule ne sont pas thread-safe. L’accès à ce champ doit être contrôlé avec soin et nécessite des techniques de programmation avancées pour la synchronisation de l’accès à l’objet de classe.|
|[CA2213 : Les champs pouvant être supprimés doivent l’être](../code-quality/ca2213.md)|Un type qui implémente System.IDisposable déclare des champs de types qui implémentent également IDisposable. La méthode Dispose du champ n'est pas appelée par la méthode Dispose du type déclarant.|
|[CA2214 : N'appelez pas de méthodes substituables dans les constructeurs](../code-quality/ca2214.md)|Quand un constructeur appelle une méthode virtuelle, il est possible que le constructeur de l’instance qui appelle la méthode n’ait pas été exécuté.|
|[CA2215 : Les méthodes Dispose doivent appeler la méthode Dispose de la classe de base](../code-quality/ca2215.md)|Si un type hérite d'un type pouvant être supprimé, il doit appeler la méthode Dispose du type de base issu de sa propre méthode Dispose.|
|[CA2216 : Les types pouvant être supprimés doivent déclarer un finaliseur](../code-quality/ca2216.md)|Un type qui implémente System. IDisposable et a des champs qui suggèrent l’utilisation de ressources non managées, n’implémente pas de finaliseur comme décrit par Object. Finalize.|
|[CA2217 : Ne marquez pas les enums avec l'attribut FlagsAttribute](../code-quality/ca2217.md)|Une énumération visible de l’extérieur est marquée avec FlagsAttribute et comporte une ou plusieurs valeurs qui ne sont pas des puissances de deux ou une combinaison des autres valeurs définies sur l’énumération.|
|[CA2219 : Ne pas lever d'exceptions dans les clauses d'exception](../code-quality/ca2219.md)|Lorsqu'une exception est levée dans une clause finally ou fault, la nouvelle exception masque l'exception active. Lorsqu'une exception est levée dans une clause filter, le runtime l'intercepte en silence. Cela rend l’erreur d’origine difficile à détecter et à déboguer.|
|[CA2225 : Les surcharges d'opérateur offrent d'autres méthodes nommées](../code-quality/ca2225.md)|Une surcharge d'opérateur a été détectée, et la méthode de substitution nommée attendue n'a pas été trouvée. Le membre de substitution nommé fournit l’accès aux mêmes fonctionnalités que l’opérateur et est fourni aux développeurs qui programment dans des langages qui ne prennent pas en charge les opérateurs surchargés.|
|[CA2226 : Les opérateurs doivent contenir des surcharges symétriques](../code-quality/ca2226.md)|Un type implémente l’opérateur d’égalité ou d’inégalité et n’implémente pas l’opérateur opposé.|
|[CA2227 : Les propriétés de collection doivent être en lecture seule](../code-quality/ca2227.md)|Une propriété de collection accessible en écriture permet à un utilisateur de remplacer la collection par une collection différente. Une propriété en lecture seule empêche le remplacement de la collection, mais permet quand même aux membres individuels d’être définis.|
|[CA2229 : Implémentez des constructeurs de sérialisation](../code-quality/ca2229.md)|Pour corriger une violation de cette règle, implémentez le constructeur de sérialisation. Dans le cas d'une classe sealed, rendez le constructeur privé ; sinon, attribuez-lui l'état protégé.|
|[CA2231 : Surchargez l’opérateur égal (equals) en remplaçant ValueType.Equals](../code-quality/ca2231.md)|Un type valeur se substitue à `Object.Equals` , mais n’implémente pas l’opérateur d’égalité.|
|[CA2232 : Marquez les points d'entrée Windows Forms avec STAThread](../code-quality/ca2232.md)|STAThreadAttribute indique que le modèle de thread COM pour l'application est un thread cloisonné (STA, Single-Threaded Apartment). Cet attribut doit être présent au point d'entrée de toute application qui utilise des Windows Forms ; s'il est omis, les composants Windows peuvent ne pas fonctionner correctement.|
|[CA2233 : Les opérations ne doivent pas déborder](../code-quality/ca2233.md)|Les opérations arithmétiques ne doivent pas être effectuées sans valider au préalable les opérandes, pour s’assurer que le résultat de l’opération n’est pas en dehors de la plage des valeurs possibles pour les types de données impliqués.|
|[CA2234 : Passez des objets System.Uri à la place de chaînes](../code-quality/ca2234.md)|Un appel est passé à une méthode qui a un paramètre de chaîne dont le nom contient « uri », « URI », « urn », « URN », « url » ou « URL ».  Le type déclarant de la méthode contient une surcharge de méthode correspondante qui a un paramètre System.Uri.|
|[CA2235 : Marquez tous les champs non sérialisés](../code-quality/ca2235.md)|Un champ d'instance d'un type non sérialisable est déclaré dans un type sérialisable.|
|[CA2236 : Appelez les méthodes de la classe de base sur les types ISerializable](../code-quality/ca2236.md)|Pour corriger une violation de cette règle, appelez la méthode GetObjectData ou le constructeur de sérialisation du type de base issu du constructeur ou de la méthode du type dérivé correspondant.|
|[CA2237 : Marquer les types ISerializable avec SerializableAttribute](../code-quality/ca2237.md)|Pour être reconnus par le common language runtime comme sérialisable, les types doivent être marqués avec l’attribut SerializableAttribute même si le type utilise une routine de sérialisation personnalisée par le biais de l’implémentation de l’interface ISerializable.|
|[CA2238 : Implémentez les méthodes de sérialisation comme il se doit](../code-quality/ca2238.md)|Une méthode qui gère un événement de sérialisation n’a pas la signature, le type de retour ou la visibilité appropriée.|
|[CA2239 : Spécifiez des méthodes de désérialisation pour les champs facultatifs](../code-quality/ca2239.md)|Un type a un champ qui est marqué avec l’attribut System. Runtime. Serialization. OptionalFieldAttribute, et le type ne fournit pas de méthodes de gestion des événements de désérialisation.|
|[CA2240 : Implémentez ISerializable comme il se doit](../code-quality/ca2240.md)|Pour corriger une violation de cette règle, rendez la méthode GetObjectData visible et substituable, et assurez-vous que tous les champs d’instance sont inclus dans le processus de sérialisation ou explicitement marqués avec l’attribut NonSerializedAttribute.|
|[CA2241 : Indiquer le nombre correct d'arguments dans les méthodes de mise en forme](../code-quality/ca2241.md)|L’argument de format passé à System. String. format ne contient pas d’élément de mise en forme qui correspond à chaque argument d’objet, ou vice versa.|
|[CA2242 : Effectuez correctement des tests NaN](../code-quality/ca2242.md)|Cette expression teste une valeur par rapport à Single.Nan ou Double.Nan. Utilisez Single.IsNan(Single) ou Double.IsNan(Double) pour tester la valeur.|
|[CA2243 : Les littéraux de chaîne d'attribut doivent être analysés correctement](../code-quality/ca2243.md)|Le paramètre de littéral de chaîne d’un attribut n’est pas analysé correctement pour une URL, un GUID ou une version.|
|[CA2244 : Ne pas dupliquer les initialisations d’éléments indexés](../code-quality/ca2244.md)|Un initialiseur d’objet a plus d’un initialiseur d’élément indexé avec le même index constant. Tout sauf le dernier initialiseur est redondant.|
|[CA2245 : Ne pas attribuer une propriété à elle-même](../code-quality/ca2245.md)|Une propriété a été accidentellement assignée à elle-même.|
|[CA2246 : Ne pas attribuer un symbole et son membre dans la même instruction](../code-quality/ca2246.md)|L’assignation d’un symbole et de son membre, autrement dit, un champ ou une propriété, dans la même instruction n’est pas recommandée. Il n’est pas évident de préciser si l’accès au membre était destiné à utiliser l’ancienne valeur du symbole avant l’assignation ou la nouvelle valeur de l’assignation dans cette instruction.|
|[CA2247 : L’argument passé au constructeur TaskCompletionSource doit être l’enum TaskCreationOptions au lieu de l’enum TaskContinuationOptions](../code-quality/ca2246.md)|TaskCompletionSource possède des constructeurs qui prennent des TaskCreationOptions qui contrôlent la tâche sous-jacente, et les constructeurs qui prennent l’état d’objet stocké dans la tâche.  Le passage accidentel d’un TaskContinuationOptions au lieu d’un TaskCreationOptions entraînera l’appel du traitement des options en tant qu’État.|
|[CA2248 : fournissez un argument « enum » correct à « Enum. HasFlag »](../code-quality/ca2248.md)|Le type enum passé comme argument à l' `HasFlag` appel de méthode est différent du type enum appelant.|
|[CA2249 : Utiliser de préférence String.Contains à la place de String.IndexOf](../code-quality/ca2249.md)|Les appels à `string.IndexOf` où le résultat est utilisé pour vérifier la présence ou l’absence d’une sous-chaîne peuvent être remplacés par `string.Contains` .|
