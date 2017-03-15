---
title: "CA1700&#160;: Ne nommez pas les valeurs enum &#39;Reserved&#39; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1700"
  - "DoNotNameEnumValuesReserved"
helpviewer_keywords: 
  - "DoNotNameEnumValuesReserved"
  - "CA1700"
ms.assetid: 7a7e01c3-ae7d-4c82-a646-91b58864a749
caps.latest.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 17
---
# CA1700&#160;: Ne nommez pas les valeurs enum &#39;Reserved&#39;
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotNameEnumValuesReserved|  
|CheckId|CA1700|  
|Catégorie|Microsoft.Naming|  
|Modification avec rupture|Oui|  
  
## Cause  
 Le nom d'un membre de l'énumération contient le mot "reserved".  
  
## Description de la règle  
 Cette règle suppose qu'un membre de l'énumération dont le nom contient le terme "reserved" n'est pas utilisé actuellement, mais constitue un espace réservé à renommer ou à supprimer dans une version ultérieure.  Renommer ou supprimer un membre constitue une modification avec rupture.  Vous ne devez pas compter sur le fait que les utilisateurs ignorent un membre simplement parce que son nom contient le terme "reserved" ni sur le fait qu'ils lisent ou se conforment à la documentation.  En outre, sachant que les membres réservés apparaissent dans des explorateurs d'objets et des environnements de développement intégré intelligents, ils peuvent provoquer une confusion sur l'identité des membres réellement utilisés.  
  
 Au lieu d'utiliser un membre réservé, ajoutez un nouveau membre à l'énumération dans la version future.  Dans la plupart des cas, l'ajout du nouveau membre ne constitue pas une modification avec rupture, tant qu'il ne provoque aucune modification des valeurs des membres d'origine.  
  
 Dans un nombre restreint de cas, l'ajout d'un membre constitue une modification avec rupture et ce même si les membres d'origine conservent leurs valeurs d'origine.  À l'origine, le nouveau membre ne peut pas être retourné depuis les chemins d'accès d'un code existant sans arrêter les appelants qui utilisent une instruction `switch` \(`Select` en [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]\) sur la valeur de retour qui comprend la liste intégrale des membres et qui lève une exception dans le cas par défaut.  Un problème secondaire tient dans ce qu'un code client peut ne pas gérer la modification de comportement à partir de méthodes de réflexion telles que <xref:System.Enum.IsDefined%2A?displayProperty=fullName>.  Par conséquent, si le nouveau membre doit être retourné à partir des méthodes existantes ou si une incompatibilité d'application connue est due à une utilisation médiocre de la réflexion, la seule solution sans rupture consiste à :  
  
1.  Ajouter une nouvelle énumération qui contient les membres d'origine et nouveaux.  
  
2.  Marquez l'énumération d'origine avec l'attribut <xref:System.ObsoleteAttribute?displayProperty=fullName>.  
  
 Suivez la même procédure pour tout type ou membre visible de l'extérieur qui expose l'énumération d'origine.  
  
## Comment corriger les violations  
 Pour corriger une violation de cette règle, supprimez ou renommez le membre.  
  
## Quand supprimer les avertissements  
 Il est possible de supprimer sans risque un avertissement de cette règle pour un membre actuellement utilisé ou dans le cas de bibliothèques précédemment livrées.  
  
## Règles connexes  
 [CA2217 : Ne pas marquer les enums avec FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)  
  
 [CA1712 : N'ajoutez pas le nom de type en guise de préfixe à des valeurs enum](../code-quality/ca1712-do-not-prefix-enum-values-with-type-name.md)  
  
 [CA1028 : Enum Storage doit être Int32](../code-quality/ca1028-enum-storage-should-be-int32.md)  
  
 [CA1008 : Les enums doivent avoir la valeur zéro](../code-quality/ca1008-enums-should-have-zero-value.md)  
  
 [CA1027 : Marquer les enums avec FlagsAttribute](../code-quality/ca1027-mark-enums-with-flagsattribute.md)