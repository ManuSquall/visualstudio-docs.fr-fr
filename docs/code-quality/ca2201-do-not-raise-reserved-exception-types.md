---
title: "CA2201 : Ne levez pas des types d&#39;exceptions r&#233;serv&#233;s | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DoNotRaiseReservedExceptionTypes"
  - "CA2201"
helpviewer_keywords: 
  - "CA2201"
  - "DoNotRaiseReservedExceptionTypes"
ms.assetid: dd14ef5c-80e6-41a5-834e-eba8e2eae75e
caps.latest.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 16
---
# CA2201 : Ne levez pas des types d&#39;exceptions r&#233;serv&#233;s
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotRaiseReservedExceptionTypes|  
|CheckId|CA2201|  
|Catégorie|Microsoft.Usage|  
|Modification avec rupture|Oui|  
  
## Cause  
 Une méthode lève un type d'exception trop général ou réservé par l'exécution.  
  
## Description de la règle  
 Les types d'exception suivants sont trop généraux pour fournir des informations suffisantes à l'utilisateur :  
  
-   <xref:System.Exception?displayProperty=fullName>  
  
-   <xref:System.ApplicationException?displayProperty=fullName>  
  
-   <xref:System.SystemException?displayProperty=fullName>  
  
 Les types d'exception suivants sont réservés et doivent être levés uniquement par le Common Language Runtime :  
  
-   <xref:System.ExecutionEngineException?displayProperty=fullName>  
  
-   <xref:System.IndexOutOfRangeException?displayProperty=fullName>  
  
-   <xref:System.NullReferenceException?displayProperty=fullName>  
  
-   <xref:System.OutOfMemoryException?displayProperty=fullName>  
  
 **Ne levez pas d'exceptions générales**  
  
 Si vous levez un type d'exception générale, tel que <xref:System.Exception> ou <xref:System.SystemException> dans une bibliothèque ou infrastructure, cela force les consommateurs à intercepter toutes les exceptions, y compris des exceptions inconnues qu'ils ne savent pas gérer.  
  
 Levez plutôt un type plus dérivé qui existe déjà dans l'infrastructure ou créez votre propre type qui dérive de <xref:System.Exception>.  
  
 **Levez des exceptions spécifiques**  
  
 La table suivante indique des paramètres et les exceptions à lever lorsque vous validez le paramètre, y compris le paramètre de valeur dans l'accesseur set d'une propriété :  
  
|Description des paramètres|Exception|  
|--------------------------------|---------------|  
|Référence `null`|<xref:System.ArgumentNullException?displayProperty=fullName>|  
|À l'extérieur de la plage de valeurs autorisée \(telle qu'un index pour une collection ou liste\)|<xref:System.ArgumentOutOfRangeException?displayProperty=fullName>|  
|Valeur `enum` non valide|<xref:System.ComponentModel.InvalidEnumArgumentException?displayProperty=fullName>|  
|Contient un format qui ne répond pas aux caractéristiques de paramètre d'une méthode \(telles que la chaîne de format pour `ToString(String)`\)|<xref:System.FormatException?displayProperty=fullName>|  
|Sinon non valide|<xref:System.ArgumentException?displayProperty=fullName>|  
  
 Lorsqu'une opération n'est pas valide pour l'état actuel d'un objet levez <xref:System.InvalidOperationException?displayProperty=fullName>  
  
 Lorsqu'une opération est exécutée sur un objet qui a été supprimé levez <xref:System.ObjectDisposedException?displayProperty=fullName>  
  
 Lorsqu'une opération n'est pas prise en charge \(comme dans un **Stream.Write** substitué dans un Flux de données ouvert en lecture\) levez <xref:System.NotSupportedException?displayProperty=fullName>  
  
 Lorsqu'une conversion provoquerait un dépassement de capacité \(tel que dans une surcharge explicite de l'opérateur de cast\) levez <xref:System.OverflowException?displayProperty=fullName>  
  
 Pour toutes les autres situations, envisagez de créer votre propre type qui dérive de <xref:System.Exception> et levez cette exception.  
  
## Comment corriger les violations  
 Pour corriger une violation de cette règle, changez le type de l'exception levée en un type spécifique qui ne fait pas partie des types réservés.  
  
## Quand supprimer les avertissements  
 Ne supprimez aucun avertissement de cette règle.  
  
## Règles connexes  
 [CA1031 : Ne pas intercepter des types d'exception générale](../Topic/CA1031:%20Do%20not%20catch%20general%20exception%20types.md)