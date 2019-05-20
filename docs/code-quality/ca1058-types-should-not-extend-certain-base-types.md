---
title: 'CA1058 : Les types ne doivent pas étendre certains types de base'
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- TypesShouldNotExtendCertainBaseTypes
- CA1058
helpviewer_keywords:
- CA1058
- TypesShouldNotExtendCertainBaseTypes
ms.assetid: 8446ee40-beb1-49fa-8733-4d8e813471c0
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 44aaead9e00a1fb279666dfc55d4e9496e21139e
ms.sourcegitcommit: 2ee11676af4f3fc5729934d52541e9871fb43ee9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/17/2019
ms.locfileid: "65842106"
---
# <a name="ca1058-types-should-not-extend-certain-base-types"></a>CA1058 : Les types ne doivent pas étendre certains types de base

|||
|-|-|
|TypeName|TypesShouldNotExtendCertainBaseTypes|
|CheckId|CA1058|
|Category|Microsoft.Design|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause

Un type étend un des types de base suivants :

- <xref:System.ApplicationException?displayProperty=fullName>
- <xref:System.Xml.XmlDocument?displayProperty=fullName>
- <xref:System.Collections.CollectionBase?displayProperty=fullName>
- <xref:System.Collections.DictionaryBase?displayProperty=fullName>
- <xref:System.Collections.Queue?displayProperty=fullName>
- <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>
- <xref:System.Collections.SortedList?displayProperty=fullName>
- <xref:System.Collections.Stack?displayProperty=fullName>

Par défaut, cette règle examine uniquement les types visibles de l’extérieur, mais il s’agit de [configurable](#configurability).

## <a name="rule-description"></a>Description de la règle

Pour .NET Framework version 1, il était recommandé de dériver les nouvelles exceptions de <xref:System.ApplicationException>. La recommandation a changé et de nouvelles exceptions doivent dériver de <xref:System.Exception?displayProperty=fullName> ou une de ses sous-classes dans le <xref:System> espace de noms.

Ne créez pas une sous-classe de <xref:System.Xml.XmlDocument> si vous souhaitez créer une vue XML d’une source de données ou le modèle objet sous-jacent.

### <a name="non-generic-collections"></a>Collections non génériques

Utiliser et/ou étendre des collections génériques chaque fois que possible. N’étendez pas de collections non génériques dans votre code, à moins que vous ayez expédiées précédemment.

**Exemples d’utilisations incorrectes**

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

Pour corriger une violation de cette règle, dérivez le type d’un autre type de base ou une collection générique.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements

Ne supprimez pas un avertissement de cette règle pour les violations sur <xref:System.ApplicationException>. Il est possible de supprimer un avertissement de cette règle pour les violations sur <xref:System.Xml.XmlDocument>. Il est possible de supprimer un avertissement à propos d’une collection non générique si le code a été publié précédemment.

## <a name="configurability"></a>Possibilités de configuration

Si vous exécutez cette règle à partir de [analyseurs FxCop](install-fxcop-analyzers.md) (et non par le biais d’analyse statique du code), vous pouvez configurer les parties de votre codebase pour exécuter cette règle sur, en fonction de leur accessibilité. Par exemple, pour spécifier que la règle doit s’exécuter uniquement par rapport à la surface d’API non publics, ajoutez la paire clé-valeur suivante dans un fichier .editorconfig dans votre projet :

```ini
dotnet_code_quality.ca1058.api_surface = private, internal
```

Vous pouvez configurer cette option pour simplement cette règle, pour toutes les règles ou pour toutes les règles de cette catégorie (conception). Pour plus d’informations, consultez [analyseurs FxCop configurer](configure-fxcop-analyzers.md).