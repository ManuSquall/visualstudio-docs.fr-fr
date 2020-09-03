---
title: 'Ca1058 : les types ne doivent pas étendre certains types de base | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- TypesShouldNotExtendCertainBaseTypes
- CA1058
helpviewer_keywords:
- CA1058
- TypesShouldNotExtendCertainBaseTypes
ms.assetid: 8446ee40-beb1-49fa-8733-4d8e813471c0
caps.latest.revision: 26
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: d8e267b1e6203759efc91936a3b13059368a3862
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85545390"
---
# <a name="ca1058-types-should-not-extend-certain-base-types"></a>CA1058 : Les types ne doivent pas étendre certains types de base
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Élément|Valeur|
|-|-|
|TypeName|TypesShouldNotExtendCertainBaseTypes|
|CheckId|CA1058|
|Category|Microsoft. Design|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause :
 Un type visible de l'extérieur étend certains types de base. Actuellement, cette règle signale des types qui dérivent des types suivants :

- <xref:System.ApplicationException?displayProperty=fullName>

- <xref:System.Xml.XmlDocument?displayProperty=fullName>

- <xref:System.Collections.CollectionBase?displayProperty=fullName>

- <xref:System.Collections.DictionaryBase?displayProperty=fullName>

- <xref:System.Collections.Queue?displayProperty=fullName>

- <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>

- <xref:System.Collections.SortedList?displayProperty=fullName>

- <xref:System.Collections.Stack?displayProperty=fullName>

## <a name="rule-description"></a>Description de la règle
 Pour la [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] version 1, il était recommandé de dériver de nouvelles exceptions de <xref:System.ApplicationException> . La recommandation a changé et les nouvelles exceptions doivent dériver de <xref:System.Exception?displayProperty=fullName> ou de l’une de ses sous-classes dans l' <xref:System> espace de noms.

 Ne créez pas une sous-classe de <xref:System.Xml.XmlDocument> si vous souhaitez créer une vue XML d’un modèle d’objet ou d’une source de données sous-jacent.

### <a name="non-generic-collections"></a>Collections non génériques
 Utilisez et/ou étendez les collections génériques dans la mesure du possible. N’étendez pas les collections non génériques dans votre code, sauf si vous les avez fournies précédemment.

 **Exemples d’utilisation incorrecte**

```csharp
public class MyCollection : CollectionBase
{
}

public class MyReadOnlyCollection : ReadOnlyCollectionBase
{
}
```

 **Exemples d’utilisation correcte**

```csharp
public class MyCollection : Collection<T>
{
}

public class MyReadOnlyCollection : ReadOnlyCollection<T>
{
}
```

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, dérivez le type d’un autre type de base ou d’une collection générique.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Ne supprimez pas un avertissement de cette règle pour les violations relatives à <xref:System.ApplicationException> . Il est possible de supprimer sans risque un avertissement de cette règle pour les violations relatives à <xref:System.Xml.XmlDocument> . Il est possible de supprimer sans risque un avertissement concernant une collection non générique si le code a été libéré précédemment.
