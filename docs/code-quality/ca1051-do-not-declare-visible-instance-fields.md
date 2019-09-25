---
title: "CA1051 : Ne pas déclarer de champs d'instances visibles"
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- CA1051
- DoNotDeclareVisibleInstanceFields
helpviewer_keywords:
- CA1051
- DoNotDeclareVisibleInstanceFields
ms.assetid: 2805376c-824c-462c-81d1-c51aaf7cabe7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 296e8cb4753d487573957de1108a8cb27778ef4c
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71235791"
---
# <a name="ca1051-do-not-declare-visible-instance-fields"></a>CA1051 : Ne pas déclarer de champs d'instances visibles

|||
|-|-|
|TypeName|DoNotDeclareVisibleInstanceFields|
|CheckId|CA1051|
|Category|Microsoft.Design|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause

Un type a un champ d’instance non privée.

Par défaut, cette règle recherche uniquement les types visibles de l’extérieur, mais elle peut [être configurée](#configurability).

## <a name="rule-description"></a>Description de la règle

Un champ s'utilise principalement en tant que détail d'implémentation. Les champs doivent `private` être `internal` ou et doivent être exposés à l’aide de propriétés. Il est aussi facile d’accéder à une propriété que d’accéder à un champ, et le code des accesseurs d’une propriété peut changer à mesure que les fonctionnalités du type se développent sans introduire de modifications avec rupture.

Les propriétés qui retournent simplement la valeur d’un champ privé ou interne sont optimisées pour s’exécuter sur les avec l’accès à un champ ; le gain de performance de l’utilisation de champs visibles de l’extérieur au lieu de propriétés est minime. *En externe* , fait référence `public`aux `protected`niveaux d’accessibilité, `Protected`, et `Protected Friend` `protected internal` (`Public`, et dans Visual Basic).

En outre, les champs publics ne peuvent pas être protégés par des [demandes de liaison](/dotnet/framework/misc/link-demands). Pour plus d’informations, [consultez CA2112 : Les types sécurisés ne doivent](../code-quality/ca2112-secured-types-should-not-expose-fields.md)pas exposer de champs. (Les demandes de liaison ne s’appliquent pas aux applications .NET Core.)

## <a name="how-to-fix-violations"></a>Comment corriger les violations

Pour corriger une violation de cette règle, définissez le champ `private` ou `internal` et exposez-le à l’aide d’une propriété visible de l’extérieur.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements

Supprimez cet avertissement uniquement si vous êtes certain que les consommateurs ont besoin d’un accès direct au champ. Pour la plupart des applications, les champs exposés ne fournissent pas d’avantages en matière de performances ou de facilité de maintenance par rapport aux propriétés.

Les consommateurs peuvent avoir besoin d’un accès à un champ dans les cas suivants :

- dans ASP.NET Web Forms contrôles de contenu
- Lorsque la plateforme cible utilise pour modifier `ref` des champs, tels que des frameworks MVVM (Model-View-ViewModel) pour WPF et UWP

## <a name="configurability"></a>Configurabilité

Si vous exécutez cette règle à partir d' [analyseurs FxCop](install-fxcop-analyzers.md) (et non avec l’analyse héritée), vous pouvez configurer les parties de votre code base sur lesquelles exécuter cette règle, en fonction de leur accessibilité. Par exemple, pour spécifier que la règle doit s’exécuter uniquement sur la surface d’API non publique, ajoutez la paire clé-valeur suivante à un fichier. editorconfig dans votre projet :

```ini
dotnet_code_quality.ca1051.api_surface = private, internal
```

Vous pouvez configurer cette option uniquement pour cette règle, pour toutes les règles ou pour toutes les règles de cette catégorie (conception). Pour plus d’informations, consultez [configurer les analyseurs FxCop](configure-fxcop-analyzers.md).

## <a name="example"></a>Exemple

L’exemple suivant montre un type (`BadPublicInstanceFields`) qui enfreint cette règle. `GoodPublicInstanceFields`affiche le code corrigé.

[!code-csharp[FxCop.Design.TypesPublicInstanceFields#1](../code-quality/codesnippet/CSharp/ca1051-do-not-declare-visible-instance-fields_1.cs)]

## <a name="related-rules"></a>Règles associées

- [CA2112 Les types sécurisés ne doivent pas exposer de champs](../code-quality/ca2112-secured-types-should-not-expose-fields.md)

## <a name="see-also"></a>Voir aussi

- [Demandes de liaison](/dotnet/framework/misc/link-demands)
