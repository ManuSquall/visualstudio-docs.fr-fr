---
title: "CA1058&#160;: Les types ne doivent pas &#233;tendre certains types de base | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "TypesShouldNotExtendCertainBaseTypes"
  - "CA1058"
helpviewer_keywords: 
  - "CA1058"
  - "TypesShouldNotExtendCertainBaseTypes"
ms.assetid: 8446ee40-beb1-49fa-8733-4d8e813471c0
caps.latest.revision: 24
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 24
---
# CA1058&#160;: Les types ne doivent pas &#233;tendre certains types de base
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|TypesShouldNotExtendCertainBaseTypes|  
|CheckId|CA1058|  
|Catégorie|Microsoft.CSharp|  
|Modification avec rupture|Oui|  
  
## Cause  
 Un type visible de l'extérieur étend certains types de base.  Cette règle indique actuellement les types qui dérivent des types suivants :  
  
-   <xref:System.ApplicationException?displayProperty=fullName>  
  
-   <xref:System.Xml.XmlDocument?displayProperty=fullName>  
  
-   <xref:System.Collections.CollectionBase?displayProperty=fullName>  
  
-   <xref:System.Collections.DictionaryBase?displayProperty=fullName>  
  
-   <xref:System.Collections.Queue?displayProperty=fullName>  
  
-   <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>  
  
-   <xref:System.Collections.SortedList?displayProperty=fullName>  
  
-   <xref:System.Collections.Stack?displayProperty=fullName>  
  
## Description de la règle  
 Pour la version 1 de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], il était recommandé de dériver les nouvelles exceptions de <xref:System.ApplicationException>.  Cette recommandation a changé et les nouvelles exceptions doivent dériver de <xref:System.Exception?displayProperty=fullName> ou d'une de ses sous\-classes dans l'espace de noms <xref:System>.  
  
 Ne créez pas de sous\-classe de <xref:System.Xml.XmlDocument> si vous souhaitez créer un affichage XML d'un modèle objet ou d'une source de données sous\-jacent.  
  
### Collections non génériques  
 Utiliser et\/ou étendre des collections génériques chaque fois que possible.  N'étendez pas de collections non génériques dans votre code, à moins que vous ne les ayez expédiées précédemment.  
  
 **Exemples d'utilisations incorrectes**  
  
```c#  
public class MyCollection : CollectionBase  
{  
}  
  
public class MyReadOnlyCollection : ReadOnlyCollectionBase  
{  
}  
```  
  
 **Exemples d'utilisations correctes**  
  
```c#  
public class MyCollection : Collection<T>  
{  
}  
  
public class MyReadOnlyCollection : ReadOnlyCollection<T>  
{  
}  
```  
  
## Comment corriger les violations  
 Pour résoudre une violation de cette règle, dérivez le type d'un type de base différent ou d'une collection générique.  
  
## Quand supprimer les avertissements  
 Ne supprimez pas un avertissement de cette règle pour les violations concernant <xref:System.ApplicationException>.  Il est possible de supprimer sans risque un avertissement de cette règle pour les violations concernant <xref:System.Xml.XmlDocument>.  Il est possible de supprimer un avertissement à propos d'une collection non générique si le code a été diffusé précédemment.