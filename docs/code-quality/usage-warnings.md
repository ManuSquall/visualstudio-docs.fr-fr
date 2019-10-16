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
ms.openlocfilehash: f58701cbebb4b738b635fac0c2805f07b4a5266f
ms.sourcegitcommit: 1507baf3a336bbb6511d4c3ce73653674831501b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72349553"
---
# <a name="usage-warnings"></a>avertissements liés à l’utilisation

Les avertissements d’utilisation prennent en charge l’utilisation correcte de .NET.

## <a name="in-this-section"></a>Dans cette section

|Règle|Description|
|----------|-----------------|
|[CA1801 : Passez en revue les paramètres inutilisés](../code-quality/ca1801.md)|Une signature de méthode inclut un paramètre qui n'est pas utilisé dans le corps de la méthode.|
|[CA1806 : Ne pas ignorer les résultats de méthode](../code-quality/ca1806.md)|Un nouvel objet est créé mais jamais utilisé ; ou une méthode qui crée et retourne une nouvelle chaîne est appelée et la nouvelle chaîne n'est jamais utilisée ; ou une méthode COM ou P/Invoke retourne un code HRESULT ou d'erreur qui n'est jamais utilisé.|
|[CA1816 : Appelez GC.SuppressFinalize correctement](../code-quality/ca1816.md)|Une méthode qui est une implémentation de dispose n’appelle pas GC. SuppressFinalize ou une méthode qui n’est pas une implémentation de dispose appelle GC. SuppressFinalize ou une méthode appelle GC. SuppressFinalize et passe autre chose que ce (moi dans Visual Basic).|
|[CA2200 : Levez à nouveau une exception pour conserver les détails de la pile](../code-quality/ca2200.md)|Une exception est à nouveau levée et est spécifiée explicitement dans l'instruction throw. Si une exception est à nouveau levée par sa spécification dans l'instruction throw, la liste des appels de méthode présents entre la méthode d'origine qui a levé l'exception et la méthode actuelle est perdue.|
|[CA2201 : Ne levez pas des types d’exceptions réservés](../code-quality/ca2201.md)|Cela rend l’erreur d’origine difficile à détecter et à déboguer.|
|[CA2202 : Ne pas supprimer des objets plusieurs fois](../code-quality/ca2202.md)|Une implémentation de méthode contient des chemins d’accès de code qui peuvent provoquer des appels multiples à System.IDisposable.Dispose ou un Dispose équivalent (par exemple, une méthode Close() sur certains types) sur le même objet.|
|[CA2204 : Les littéraux doivent être correctement orthographiés](../code-quality/ca2204.md)|Une chaîne littéral dans un corps de méthode contient un ou plusieurs mots qui ne sont pas reconnus par la bibliothèque de vérificateur d'orthographe Microsoft.|
|[CA2205 : Utilisez des équivalents managés de l’API Win32](../code-quality/ca2205.md)|Une méthode d’appel de code non managé est définie et une méthode .NET avec les fonctionnalités équivalentes est disponible.|
|[CA2207 : Initialisez les champs statiques des types de valeurs inline](../code-quality/ca2207.md)|Un type valeur déclare un constructeur statique explicite. Pour corriger une violation de cette règle, initialisez toutes les données statiques lorsqu’elles sont déclarées et supprimez le constructeur statique.|
|[CA2208 : Instanciez les exceptions d’argument correctement](../code-quality/ca2208.md)|Un appel est passé au constructeur par défaut (sans paramètre) d'un type d'exception qui est ou dérive d'ArgumentException, ou un argument string incorrect est passé à un constructeur paramétrable d'un type d'exception qui est ou dérive d'ArgumentException.|
|[CA2211 : Les champs non constants ne doivent pas être visibles](../code-quality/ca2211.md)|Les champs statiques qui ne sont pas des constantes ou en lecture seule ne sont pas thread-safe. L’accès à ce champ doit être contrôlé avec soin et nécessite des techniques de programmation avancées pour la synchronisation de l’accès à l’objet de classe.|
|[CA2212 : Ne marquez pas les composants pris en charge avec WebMethod](../code-quality/ca2212.md)|Une méthode d’un type qui hérite de System. EnterpriseServices. ServicedComponent est marquée avec System. Web. services. WebMethodAttribute. Sachant que WebMethodAttribute et une méthode ServicedComponent ont des comportements incompatibles et des exigences en matière de contexte et de flux de transactions, le comportement de la méthode est incorrect dans certains scénarios.|
|[CA2213 : Les champs pouvant être supprimés doivent l’être](../code-quality/ca2213.md)|Un type qui implémente System.IDisposable déclare des champs de types qui implémentent également IDisposable. La méthode Dispose du champ n'est pas appelée par la méthode Dispose du type déclarant.|
|[CA2214 : N’appelez pas de méthodes substituables dans les constructeurs](../code-quality/ca2214.md)|Quand un constructeur appelle une méthode virtuelle, il est possible que le constructeur de l’instance qui appelle la méthode n’ait pas été exécuté.|
|[CA2215 : Les méthodes Dispose doivent appeler la méthode Dispose de la classe de base](../code-quality/ca2215.md)|Si un type hérite d'un type pouvant être supprimé, il doit appeler la méthode Dispose du type de base issu de sa propre méthode Dispose.|
|[CA2216 : Les types supprimables doivent déclarer un finaliseur](../code-quality/ca2216.md)|Un type qui implémente System. IDisposable et a des champs qui suggèrent l’utilisation de ressources non managées, n’implémente pas de finaliseur comme décrit par Object. Finalize.|
|[CA2217 : Ne marquez pas les énumérations avec FlagsAttribute](../code-quality/ca2217.md)|Une énumération visible de l’extérieur est marquée avec FlagsAttribute et comporte une ou plusieurs valeurs qui ne sont pas des puissances de deux ou une combinaison des autres valeurs définies sur l’énumération.|
|[CA2218 : Remplacez GetHashCode lors du remplacement de Equals](../code-quality/ca2218.md)|GetHashCode retourne une valeur fondée sur l’instance actuelle adaptée aux algorithmes de hachage et aux structures de données telles qu’une table de hachage. Deux objets de même type et égaux doivent retourner le même code de hachage.|
|[CA2219 : Ne levez pas d’exceptions dans les clauses d’exception](../code-quality/ca2219.md)|Lorsqu'une exception est levée dans une clause finally ou fault, la nouvelle exception masque l'exception active. Lorsqu'une exception est levée dans une clause filter, le runtime l'intercepte en silence. Cela rend l’erreur d’origine difficile à détecter et à déboguer.|
|[CA2220 : Les finaliseurs doivent appeler le finaliseur de la classe de base](../code-quality/ca2220.md)|La finalisation doit être propagée par le biais de la hiérarchie d'héritage. Pour garantir ce procédé, les types doivent appeler leur méthode Finalize de classe de base à partir de leur propre méthode Finalize.|
|[CA2221 : Les finaliseurs doivent être protégés](../code-quality/ca2221.md)|Les finaliseurs doivent utiliser le modificateur d’accès family.|
|[CA2222 : Ne réduisez pas la visibilité des membres hérités](../code-quality/ca2222.md)|Ne modifiez pas le modificateur d’accès pour les membres hérités. La modification d'un membre hérité au profit d'un état privé n'empêche pas les appelants d'accéder à l'implémentation de classe de base de la méthode.|
|[CA2223 : Les membres ne doivent pas différer uniquement par leur type de retour](../code-quality/ca2223.md)|Bien que le Common Language Runtime autorise l’utilisation de types de retour pour différencier des membres autrement identiques, cette fonctionnalité ne figure pas dans la Common Language Specification, et n’est pas une fonctionnalité courante des langages de programmation .NET.|
|[CA2224 : Remplacez Equals lors de la surcharge de l’opérateur égal](../code-quality/ca2224.md)|Un type public implémente l’opérateur d’égalité, mais ne se substitue pas à Object. Equals.|
|[CA2225 : Les surcharges d’opérateur ont d’autres méthodes nommées](../code-quality/ca2225.md)|Une surcharge d'opérateur a été détectée, et la méthode de substitution nommée attendue n'a pas été trouvée. Le membre de substitution nommé fournit l’accès aux mêmes fonctionnalités que l’opérateur et est fourni aux développeurs qui programment dans des langages qui ne prennent pas en charge les opérateurs surchargés.|
|[CA2226 : Les opérateurs doivent avoir des surcharges symétriques](../code-quality/ca2226.md)|Un type implémente l’opérateur d’égalité ou d’inégalité et n’implémente pas l’opérateur opposé.|
|[CA2227 : Les propriétés de collection doivent être en lecture seule](../code-quality/ca2227.md)|Une propriété de collection accessible en écriture permet à un utilisateur de remplacer la collection par une collection différente. Une propriété en lecture seule empêche le remplacement de la collection, mais permet quand même aux membres individuels d’être définis.|
|[CA2228 : Ne distribuez pas des formats de ressources non commercialisés](../code-quality/ca2228.md)|Les fichiers de ressources générés à l’aide des versions préliminaires du .NET peuvent ne pas être utilisables par les versions prises en charge de .NET.|
|[CA2229 : Implémentez des constructeurs de sérialisation](../code-quality/ca2229.md)|Pour corriger une violation de cette règle, implémentez le constructeur de sérialisation. Dans le cas d'une classe sealed, rendez le constructeur privé ; sinon, attribuez-lui l'état protégé.|
|[CA2230 : Utilisez le mot clé params pour les arguments de variables](../code-quality/ca2230.md)|Un type public ou protégé contient une méthode publique ou protégée qui utilise la convention d’appel VarArgs au lieu du mot clé params.|
|[CA2231 : Surchargez l’opérateur égal (equals) en remplaçant ValueType.Equals](../code-quality/ca2231.md)|Un type valeur se substitue à `Object.Equals`, mais n’implémente pas l’opérateur d’égalité.|
|[CA2232 : Marquez les points d’entrée Windows Forms avec STAThread](../code-quality/ca2232.md)|STAThreadAttribute indique que le modèle de thread COM pour l'application est un thread cloisonné (STA, Single-Threaded Apartment). Cet attribut doit être présent au point d'entrée de toute application qui utilise des Windows Forms ; s'il est omis, les composants Windows peuvent ne pas fonctionner correctement.|
|[CA2233 : Les opérations ne doivent pas provoquer de dépassement de capacité](../code-quality/ca2233.md)|Les opérations arithmétiques ne doivent pas être effectuées sans valider au préalable les opérandes, pour s’assurer que le résultat de l’opération n’est pas en dehors de la plage des valeurs possibles pour les types de données impliqués.|
|[CA2234 : Passez des objets System.Uri au lieu de chaînes](../code-quality/ca2234.md)|Un appel est passé à une méthode qui a un paramètre de chaîne dont le nom contient « uri », « URI », « urn », « URN », « url » ou « URL ».  Le type déclarant de la méthode contient une surcharge de méthode correspondante qui a un paramètre System.Uri.|
|[CA2235 : Marquez tous les champs non sérialisables](../code-quality/ca2235.md)|Un champ d'instance d'un type non sérialisable est déclaré dans un type sérialisable.|
|[CA2236 : Appelez les méthodes de la classe de base sur les types ISerializable](../code-quality/ca2236.md)|Pour corriger une violation de cette règle, appelez la méthode GetObjectData ou le constructeur de sérialisation du type de base issu du constructeur ou de la méthode du type dérivé correspondant.|
|[CA2237 : Marquez les types ISerializable avec SerializableAttribute](../code-quality/ca2237.md)|Pour être reconnus par le common language runtime comme sérialisable, les types doivent être marqués avec l’attribut SerializableAttribute même si le type utilise une routine de sérialisation personnalisée par le biais de l’implémentation de l’interface ISerializable.|
|[CA2238 : Implémentez les méthodes de sérialisation correctement](../code-quality/ca2238.md)|Une méthode qui gère un événement de sérialisation n’a pas la signature, le type de retour ou la visibilité appropriée.|
|[CA2239 : Spécifiez des méthodes de désérialisation pour les champs facultatifs](../code-quality/ca2239.md)|Un type a un champ qui est marqué avec l’attribut System. Runtime. Serialization. OptionalFieldAttribute, et le type ne fournit pas de méthodes de gestion des événements de désérialisation.|
|[CA2240 : Implémentez ISerializable correctement](../code-quality/ca2240.md)|Pour corriger une violation de cette règle, rendez la méthode GetObjectData visible et substituable, et assurez-vous que tous les champs d’instance sont inclus dans le processus de sérialisation ou explicitement marqués avec l’attribut NonSerializedAttribute.|
|[CA2241 : Fournissez des arguments corrects aux méthodes de mise en forme](../code-quality/ca2241.md)|L’argument de format passé à System. String. format ne contient pas d’élément de mise en forme qui correspond à chaque argument d’objet, ou vice versa.|
|[CA2242 : Effectuez correctement des tests NaN](../code-quality/ca2242.md)|Cette expression teste une valeur par rapport à Single.Nan ou Double.Nan. Utilisez Single.IsNan(Single) ou Double.IsNan(Double) pour tester la valeur.|
|[CA2243 : Les littéraux de chaîne d’attribut doivent être analysés correctement](../code-quality/ca2243.md)|Le paramètre de littéral de chaîne d’un attribut n’est pas analysé correctement pour une URL, un GUID ou une version.|
