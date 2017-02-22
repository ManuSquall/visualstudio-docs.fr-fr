---
title: "Avertissements li&#233;s &#224; l’affectation de noms | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.codeanalysis.namingrules"
helpviewer_keywords: 
  - "avertissements liés à l’analyse du code managé, avertissements liés à l’affectation de noms"
  - "avertissements liés à l’affectation de noms"
  - "avertissements, affecter des noms"
ms.assetid: f97223ce-1d39-4134-81c9-fff2c75d979b
caps.latest.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 19
---
# Avertissements li&#233;s &#224; l’affectation de noms
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Les avertissements d'affectation de nom prennent en charge l'adhésion aux conventions d'affectation de noms des règles de conception du [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  
  
## Dans cette section  
  
|Règle|Description|  
|-----------|-----------------|  
|[CA1700 : Ne nommez pas les valeurs enum 'Reserved'](../code-quality/ca1700-do-not-name-enum-values-reserved.md)|Cette règle suppose qu'un membre de l'énumération dont le nom contient le terme "reserved" n'est pas utilisé actuellement, mais constitue un espace réservé à renommer ou à supprimer dans une version ultérieure.  Renommer ou supprimer un membre constitue une modification avec rupture.|  
|[CA1713 : Les événements ne doivent pas être munis d'un préfixe Before ou After](../code-quality/ca1713-events-should-not-have-before-or-after-prefix.md)|Le nom d'un événement commence par « Before » ou « After ».  Pour nommer des événements associés déclenchés dans une séquence spécifique, utilisez le présent ou le passé pour indiquer la position relative dans la séquence d'actions.|  
|[CA1714 : Les énumérations d'indicateurs doivent avoir des noms au pluriel](../code-quality/ca1714-flags-enums-should-have-plural-names.md)|Une énumération publique comporte l'attribut System.FlagsAttribute et son nom ne se termine pas par « s ».  Les types marqués avec FlagsAttribute ont des noms au pluriel car l'attribut indique que plusieurs valeurs peuvent être spécifiées.|  
|[CA1704 : Les identificateurs doivent être correctement orthographiés](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)|Le nom d'un identificateur visible de l'extérieur contient un ou plusieurs mots qui ne sont pas reconnus par la bibliothèque du vérificateur d'orthographe Microsoft.|  
|[CA1708 : Les identificateurs ne doivent pas différer que par leur casse](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)|Les identificateurs des espaces de noms, types, membres et paramètres ne peuvent pas différer uniquement par la casse car les langages qui ciblent le Common Language Runtime ne sont pas tenus de respecter celle\-ci.|  
|[CA1715 : Les identificateurs doivent être dotés d'un préfixe correct](../code-quality/ca1715-identifiers-should-have-correct-prefix.md)|Le nom d'une interface extérieurement visible ne commence pas par un « I » majuscule.  Le nom d'un paramètre de type générique sur un type ou une méthode extérieurement visible ne commence pas par un « T » majuscule.|  
|[CA1720 : Les identificateurs ne doivent pas contenir de noms de types](../code-quality/ca1720-identifiers-should-not-contain-type-names.md)|Le nom d'un paramètre dans un membre extérieurement visible contient un nom de type de données, ou le nom d'un membre extérieurement visible contient un nom de type de données spécifique à une langue.|  
|[CA1722 : Les identificateurs ne doivent pas porter un préfixe incorrect](../code-quality/ca1722-identifiers-should-not-have-incorrect-prefix.md)|Par convention, seuls certains éléments de programmation présentent des noms qui commencent par un préfixe spécifique.|  
|[CA1711 : Les identificateurs ne doivent pas porter un suffixe incorrect](../code-quality/ca1711-identifiers-should-not-have-incorrect-suffix.md)|Par convention, seuls les noms des types qui étendent certains types de base ou qui implémentent certaines interfaces, ou les types dérivés de ces types, doivent se terminer par des suffixes réservés spécifiques.  Les autres noms de types ne doivent pas utiliser ces suffixes réservés.|  
|[CA1717 : Seuls les noms des enums FlagsAttribute doivent être au pluriel](../Topic/CA1717:%20Only%20FlagsAttribute%20enums%20should%20have%20plural%20names.md)|Selon les conventions d'attribution de nom, un nom au pluriel pour une énumération indique que plusieurs valeurs de l'énumération peuvent être spécifiées simultanément.|  
|[CA1725 : Les noms de paramètres doivent correspondre à la déclaration de base](../code-quality/ca1725-parameter-names-should-match-base-declaration.md)|La désignation cohérente des paramètres dans une hiérarchie de substitution augmente la facilité d'utilisation des substitutions de méthode.  Un nom de paramètre dans une méthode dérivée qui diffère du nom dans la déclaration de base peut créer une confusion pour déterminer si la méthode est une substitution de la méthode de base ou une nouvelle surcharge de la méthode.|  
|[CA1719 : Les noms des paramètres ne doivent pas être identiques aux noms des membres](../code-quality/ca1719-parameter-names-should-not-match-member-names.md)|Un nom de paramètre doit véhiculer la signification du paramètre et un nom de membre celle du membre.  Un design où ceux\-ci sont identiques est rare.  Donner à un paramètre le même que son membre n'est pas une méthode intuitive et rend la bibliothèque difficile à utiliser.|  
|[CA1701: La casse des mots composés de chaînes de ressources doit être correcte](../Topic/CA1701:%20Resource%20string%20compound%20words%20should%20be%20cased%20correctly.md)|Chaque mot de la chaîne de ressource est fractionné en jetons basés sur la casse.  Chaque combinaison de deux jetons contiguë est vérifiée par la bibliothèque du correcteur orthographique Microsoft.  S'il est reconnu, le mot produit une violation de la règle.|  
|[CA1703 : L'orthographe des chaînes de ressources doit être correcte](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)|Une chaîne de ressource contient un ou plusieurs mots qui ne sont pas reconnus par la bibliothèque du vérificateur d'orthographe Microsoft.|  
|[CA1724 : les noms de types ne doivent pas être identiques aux espaces de noms](../code-quality/ca1724-type-names-should-not-match-namespaces.md)|Les noms de types ne doivent pas correspondre aux noms d'espaces de noms définis dans la bibliothèque de classes [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  La violation de cette règle peut réduire la facilité d'utilisation de la bibliothèque.|  
|[CA1707 : Les identificateurs ne doivent pas contenir de traits de soulignement](../code-quality/ca1707-identifiers-should-not-contain-underscores.md)|Par convention, les noms d'identificateurs ne contiennent pas de trait de soulignement \(\_\).  Cette règle vérifie les espaces de noms, types, membres et paramètres.|  
|[CA1721 : Les noms des propriétés ne doivent pas être identiques à ceux des méthodes Get](../code-quality/ca1721-property-names-should-not-match-get-methods.md)|Le nom d'un membre public ou protégé commence par « Get ». Sinon, il correspond au nom d'une propriété publique ou protégée. "Get" doivent avoir des noms qui distinguent clairement leurs fonctions respectives.|  
|[CA1716 : Les identificateurs ne doivent pas correspondre à des mots clés](../code-quality/ca1716-identifiers-should-not-match-keywords.md)|Un nom d'espace de noms ou un nom de type correspond à un mot clé réservé dans un langage de programmation.  Les identificateurs des espaces de noms et des types ne doivent pas correspondre aux mots clés définis par les langages qui ciblent le Common Language Runtime.|  
|[CA1726 : Utilisez les termes par défaut](../code-quality/ca1726-use-preferred-terms.md)|Le nom d'un identificateur visible de l'extérieur contient un terme pour lequel un autre terme par défaut existe.  Le nom peut également inclure le terme « Indicateur » ou « Indicateurs ».|  
|[CA1709 : La casse des identificateurs doit être correcte](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)|Par convention, les noms de paramètres utilisent la casse mixte et les noms d'espaces de noms, de types et de membres utilisent la convention de casse Pascal.|  
|[CA1702 : La casse des mots composés doit être correcte](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)|Le nom d'un identificateur contient plusieurs mots et au moins l'un des mots semble être un mot composé qui ne présente pas une casse correcte.|  
|[CA1712 : N'ajoutez pas le nom de type en guise de préfixe à des valeurs enum](../code-quality/ca1712-do-not-prefix-enum-values-with-type-name.md)|Les noms des membres de l'énumération n'ont pas pour préfixe le nom de type car les informations de type sont censées être fournies par les outils de développement.|  
|[CA1710 : Les identificateurs doivent être dotés d'un suffixe correct](../Topic/CA1710:%20Identifiers%20should%20have%20correct%20suffix.md)|Par convention, les noms des types qui étendent certains types de base ou qui implémentent certaines interfaces, ou encore des types dérivés de ces types, présentent un suffixe associé au type de base ou à l'interface.|