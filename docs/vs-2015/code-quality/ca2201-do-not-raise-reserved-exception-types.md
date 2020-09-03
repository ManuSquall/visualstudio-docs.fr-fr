---
title: 'CA2201 : ne levez pas de types d’exceptions réservés | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotRaiseReservedExceptionTypes
- CA2201
helpviewer_keywords:
- CA2201
- DoNotRaiseReservedExceptionTypes
ms.assetid: dd14ef5c-80e6-41a5-834e-eba8e2eae75e
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 9533a597a33deaed17ff2a73d56ef306ea7b5613
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85546339"
---
# <a name="ca2201-do-not-raise-reserved-exception-types"></a>CA2201 : Ne levez pas des types d'exceptions réservés
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Élément|Valeur|
|-|-|
|TypeName|DoNotRaiseReservedExceptionTypes|
|CheckId|CA2201|
|Category|Microsoft. usage|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause :
 Une méthode lève un type d’exception qui est trop général ou qui est réservé par le Runtime.

## <a name="rule-description"></a>Description de la règle
 Les types d’exception suivants sont trop généraux pour fournir des informations suffisantes à l’utilisateur :

- <xref:System.Exception?displayProperty=fullName>

- <xref:System.ApplicationException?displayProperty=fullName>

- <xref:System.SystemException?displayProperty=fullName>

  Les types d’exception suivants sont réservés et doivent être levés uniquement par l’common language runtime :

- <xref:System.ExecutionEngineException?displayProperty=fullName>

- <xref:System.IndexOutOfRangeException?displayProperty=fullName>

- <xref:System.NullReferenceException?displayProperty=fullName>

- <xref:System.OutOfMemoryException?displayProperty=fullName>

  **Ne pas lever d’exceptions générales**

  Si vous levez un type d’exception générale, tel que <xref:System.Exception> ou <xref:System.SystemException> dans une bibliothèque ou une infrastructure, il oblige les consommateurs à intercepter toutes les exceptions, y compris les exceptions inconnues qu’ils ne savent pas gérer.

  Au lieu de cela, vous pouvez soit lever un type plus dérivé qui existe déjà dans le Framework, soit créer votre propre type qui dérive de <xref:System.Exception> .

  **Lever des exceptions spécifiques**

  Le tableau suivant présente les paramètres et les exceptions à lever lorsque vous validez le paramètre, y compris le paramètre de valeur dans l’accesseur Set d’une propriété :

|Description du paramètre|Exception|
|---------------------------|---------------|
|`null` faire|<xref:System.ArgumentNullException?displayProperty=fullName>|
|En dehors de la plage de valeurs autorisée (par exemple, un index pour une collection ou une liste)|<xref:System.ArgumentOutOfRangeException?displayProperty=fullName>|
|Valeur non valide `enum`|<xref:System.ComponentModel.InvalidEnumArgumentException?displayProperty=fullName>|
|Contient un format qui ne respecte pas les spécifications de paramètres d’une méthode (telle que la chaîne de format pour `ToString(String)` )|<xref:System.FormatException?displayProperty=fullName>|
|Sinon non valide|<xref:System.ArgumentException?displayProperty=fullName>|

 Lorsqu’une opération n’est pas valide pour l’état actuel d’un objet Throw <xref:System.InvalidOperationException?displayProperty=fullName>

 Lorsqu’une opération est effectuée sur un objet qui a été supprimé Throw <xref:System.ObjectDisposedException?displayProperty=fullName>

 Lorsqu’une opération n’est pas prise en charge (par exemple, dans un **flux substitué. écrire** dans un flux ouvert pour la lecture) throw <xref:System.NotSupportedException?displayProperty=fullName>

 Lorsqu’une conversion génère un dépassement de capacité (par exemple, dans une surcharge d’opérateur de cast explicite), lève <xref:System.OverflowException?displayProperty=fullName>

 Pour toutes les autres situations, envisagez de créer votre propre type qui dérive de <xref:System.Exception> et qui lève cette exception.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, remplacez le type de l’exception levée par un type spécifique qui ne fait pas partie des types réservés.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Ne supprimez aucun avertissement de cette règle.

## <a name="related-rules"></a>Règles associées
 [CA1031 : Ne pas intercepter des types d'exception générale](../code-quality/ca1031-do-not-catch-general-exception-types.md)
