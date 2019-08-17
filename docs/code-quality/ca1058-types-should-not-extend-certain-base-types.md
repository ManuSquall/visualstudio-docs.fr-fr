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
ms.openlocfilehash: 38d92194a5aa2b46a0cb65a1525bc01d9de67b86
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/16/2019
ms.locfileid: "69547357"
---
# <a name="ca1058-types-should-not-extend-certain-base-types"></a>CA1058 : Les types ne doivent pas étendre certains types de base

|||
|-|-|
|TypeName|TypesShouldNotExtendCertainBaseTypes|
|CheckId|CA1058|
|Catégorie|Microsoft.Design|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause

Un type étend l’un des types de base suivants:

- <xref:System.ApplicationException?displayProperty=fullName>
- <xref:System.Xml.XmlDocument?displayProperty=fullName>
- <xref:System.Collections.CollectionBase?displayProperty=fullName>
- <xref:System.Collections.DictionaryBase?displayProperty=fullName>
- <xref:System.Collections.Queue?displayProperty=fullName>
- <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>
- <xref:System.Collections.SortedList?displayProperty=fullName>
- <xref:System.Collections.Stack?displayProperty=fullName>

Par défaut, cette règle recherche uniquement les types visibles de l’extérieur, mais elle peut [être configurée](#configurability).

## <a name="rule-description"></a>Description de la règle

Les exceptions doivent dériver de <xref:System.Exception?displayProperty=fullName> ou de l’une de ses sous-classes dans l' <xref:System> espace de noms.

Ne créez pas une sous-classe <xref:System.Xml.XmlDocument> de si vous souhaitez créer une vue XML d’un modèle d’objet ou d’une source de données sous-jacent.

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

Ne supprimez pas un avertissement de cette règle pour les <xref:System.ApplicationException>violations relatives à. Il est possible de supprimer sans risque un avertissement de cette règle pour <xref:System.Xml.XmlDocument>les violations relatives à. Il est possible de supprimer sans risque un avertissement concernant une collection non générique si le code a été libéré précédemment.

## <a name="configurability"></a>Configurabilité

Si vous exécutez cette règle à partir d' [analyseurs FxCop](install-fxcop-analyzers.md) (et non avec l’analyse héritée), vous pouvez configurer les parties de votre code base sur lesquelles exécuter cette règle, en fonction de leur accessibilité. Par exemple, pour spécifier que la règle doit s’exécuter uniquement sur la surface d’API non publique, ajoutez la paire clé-valeur suivante à un fichier. editorconfig dans votre projet:

```ini
dotnet_code_quality.ca1058.api_surface = private, internal
```

Vous pouvez configurer cette option uniquement pour cette règle, pour toutes les règles ou pour toutes les règles de cette catégorie (conception). Pour plus d’informations, consultez [configurer les analyseurs FxCop](configure-fxcop-analyzers.md).