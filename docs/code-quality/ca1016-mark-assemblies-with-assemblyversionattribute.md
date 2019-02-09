---
title: 'CA1016 : Marquer les assemblys avec AssemblyVersionAttribute'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MarkAssembliesWithAssemblyVersion
- CA1016
helpviewer_keywords:
- CA1016
- MarkAssembliesWithAssemblyVersion
ms.assetid: 4340aed8-d92b-4cde-a398-cb6963c6da5a
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: a00c8e30e981794e69d4572e0a924438514780c7
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2019
ms.locfileid: "55917777"
---
# <a name="ca1016-mark-assemblies-with-assemblyversionattribute"></a>CA1016 : Marquer les assemblys avec AssemblyVersionAttribute

|||
|-|-|
|TypeName|MarkAssembliesWithAssemblyVersion|
|CheckId|CA1016|
|Category|Microsoft.Design|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause

L’assembly n’a pas un numéro de version.

## <a name="rule-description"></a>Description de la règle

L’identité d’un assembly est composée des informations suivantes :

- Nom de l'assembly

- Numéro de version

- culture

- Clé publique (pour les assemblys à nom fort).

Le .NET Framework utilise le numéro de version pour identifier de façon unique un assembly et à lier aux types dans les assemblys à nom fort. Le numéro de version est utilisé conjointement avec la version et la stratégie d'éditeur. Par défaut, les applications s'exécutent uniquement avec la version d'assembly avec laquelle elles ont été construites.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, ajoutez un numéro de version à l’assembly à l’aide de la <xref:System.Reflection.AssemblyVersionAttribute?displayProperty=fullName> attribut. Lisez l'exemple suivant.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Ne supprimez pas d’avertissement de cette règle pour les assemblys qui sont utilisés par des tiers, ou dans un environnement de production.

## <a name="example"></a>Exemple
 L’exemple suivant montre un assembly qui a le <xref:System.Reflection.AssemblyVersionAttribute> attribut appliqué.

 [!code-csharp[FxCop.Design.AssembliesVersion#1](../code-quality/codesnippet/CSharp/ca1016-mark-assemblies-with-assemblyversionattribute_1.cs)]
 [!code-vb[FxCop.Design.AssembliesVersion#1](../code-quality/codesnippet/VisualBasic/ca1016-mark-assemblies-with-assemblyversionattribute_1.vb)]
 [!code-cpp[FxCop.Design.AssembliesVersion#1](../code-quality/codesnippet/CPP/ca1016-mark-assemblies-with-assemblyversionattribute_1.cpp)]

## <a name="see-also"></a>Voir aussi

- [Contrôle de version des assemblys](/dotnet/framework/app-domains/assembly-versioning)
- [Guide pratique pour Créer une stratégie d’éditeur](/dotnet/framework/configure-apps/how-to-create-a-publisher-policy)