---
title: 'CA1812 : Évitez les classes internes non instanciées'
ms.date: 05/16/2019
ms.topic: reference
f1_keywords:
- CA1812
- AvoidUninstantiatedInternalClasses
helpviewer_keywords:
- AvoidUninstantiatedInternalClasses
- CA1812
ms.assetid: 1bb92a42-322a-44cc-98a8-8858212c1e1f
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f924e9530a7ee43ec2222366141c3af6be2efc29
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71233608"
---
# <a name="ca1812-avoid-uninstantiated-internal-classes"></a>CA1812 : Évitez les classes internes non instanciées

|||
|-|-|
|TypeName|AvoidUninstantiatedInternalClasses|
|CheckId|CA1812|
|Category|Microsoft. performance|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause

Un type interne (au niveau de l’assembly) n’est jamais instancié.

## <a name="rule-description"></a>Description de la règle

Cette règle tente de localiser un appel à l’un des constructeurs du type et signale une violation si aucun appel n’est trouvé.

Les types suivants ne sont pas examinés par cette règle :

- Types de valeur

- Types abstraits

- Énumérations

- Délégués

- Types de tableau émis par le compilateur

- Types qui ne peuvent pas être instanciés et qui [`static`](/dotnet/csharp/language-reference/keywords/static) ne définissent que des méthodes ([ `Shared` dans Visual Basic](/dotnet/visual-basic/language-reference/modifiers/shared)).

Si vous appliquez à <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute?displayProperty=fullName> l’assembly en cours d’analyse, cette règle ne signale pas les types marqués comme [`internal`](/dotnet/csharp/language-reference/keywords/internal) ([ `Friend` dans Visual Basic](/dotnet/visual-basic/language-reference/modifiers/friend)), car un champ peut être utilisé par un assembly friend.

## <a name="how-to-fix-violations"></a>Comment corriger les violations

Pour corriger une violation de cette règle, supprimez le type ou ajoutez du code qui l’utilise. Si le type contient uniquement `static` des méthodes, ajoutez l’un des éléments suivants au type pour empêcher le compilateur d’émettre un constructeur d’instance public par défaut :

- Modificateur pour `static` C# les types qui ciblent .NET Framework 2,0 ou version ultérieure.

- Constructeur privé pour les types qui ciblent les versions de .NET Framework 1,0 et 1,1.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements

Il est possible de supprimer sans risque un avertissement de cette règle. Nous vous recommandons de supprimer cet avertissement dans les cas suivants :

- La classe est créée par le biais de méthodes de réflexion à <xref:System.Activator.CreateInstance%2A?displayProperty=fullName>liaison tardive, telles que.

- La classe est créée automatiquement par le runtime ou ASP.NET. Voici quelques exemples de classes créées automatiquement, qui <xref:System.Configuration.IConfigurationSectionHandler?displayProperty=fullName> implémentent <xref:System.Web.IHttpHandler?displayProperty=fullName>ou.

- La classe est passée en tant que paramètre de type qui a une [ `new` contrainte](/dotnet/csharp/language-reference/keywords/new-constraint). L’exemple suivant est signalé par la règle CA1812 :

    ```csharp
    internal class MyClass
    {
        public DoSomething()
        {
        }
    }
    public class MyGeneric<T> where T : new()
    {
        public T Create()
        {
            return new T();
        }
    }

    MyGeneric<MyClass> mc = new MyGeneric<MyClass>();
    mc.Create();
    ```

## <a name="related-rules"></a>Règles associées

- [CA1811 Éviter le code privé qui n’a pas été appelé](../code-quality/ca1811-avoid-uncalled-private-code.md)
- [CA1801 Passer en revue les paramètres inutilisés](../code-quality/ca1801-review-unused-parameters.md)
- [CA1804 Supprimer les variables locales inutilisées](../code-quality/ca1804-remove-unused-locals.md)