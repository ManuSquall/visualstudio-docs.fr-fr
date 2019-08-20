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
ms.openlocfilehash: 6946434708e38bde7f6efcfc8404da14f91b41ee
ms.sourcegitcommit: 12f2851c8c9bd36a6ab00bf90a020c620b364076
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2019
ms.locfileid: "66744698"
---
# <a name="ca1812-avoid-uninstantiated-internal-classes"></a>CA1812 : Évitez les classes internes non instanciées

|||
|-|-|
|TypeName|AvoidUninstantiatedInternalClasses|
|CheckId|CA1812|
|Category|Microsoft.Performance|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause

Un type (de niveau assembly) interne n’est jamais instancié.

## <a name="rule-description"></a>Description de la règle

Cette règle tente de localiser un appel à un des constructeurs de type et signale une violation si aucun appel n’est trouvé.

Les types suivants ne sont pas examinés par cette règle :

- Types de valeur

- Types abstraits

- Énumérations

- Délégués

- Types de tableau émis par le compilateur

- Les types qui ne peut pas être instanciée et qui définissent uniquement [ `static` ](/dotnet/csharp/language-reference/keywords/static) ([ `Shared` en Visual Basic](/dotnet/visual-basic/language-reference/modifiers/shared)) méthodes.
Si vous appliquez <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute?displayProperty=fullName> à l’assembly qui est en cours d’analyse, cette règle ne sera pas vérifiée sur les constructeurs portant la mention `internal` parce que vous ne pouvez pas savoir si un champ est utilisé par une autre assembly `friend`.

Si vous appliquez le <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute?displayProperty=fullName> à l’assembly qui est en cours d’analyse, cette règle ne marquera pas les types qui sont marqués comme [ `internal` ](/dotnet/csharp/language-reference/keywords/internal) ([ `Friend` en Visual Basic](/dotnet/visual-basic/language-reference/modifiers/friend)), car un champ peut être utilisé par un assembly friend.
## <a name="how-to-fix-violations"></a>Comment corriger les violations

Pour corriger une violation de cette règle, supprimez le type ou ajouter du code qui l’utilise. Si le type contient uniquement `static` méthodes, ajoutez les valeurs suivantes au type pour empêcher le compilateur d’émettre un constructeur d’instance public par défaut :

- Le `static` modificateur pour C# types qui ciblent .NET Framework 2.0 ou version ultérieure.

- Un constructeur privé pour les types qui ciblent des versions 1.0 et 1.1 du .NET Framework.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements

Il est possible de supprimer un avertissement de cette règle. Nous vous recommandons de supprimer cet avertissement dans les situations suivantes :

- La classe est créée par le biais des méthodes de la réflexion à liaison tardive comme <xref:System.Activator.CreateInstance%2A?displayProperty=fullName>.

- La classe est créée automatiquement par le runtime ou ASP.NET. Quelques exemples de classes créées automatiquement sont ceux qui implémentent <xref:System.Configuration.IConfigurationSectionHandler?displayProperty=fullName> ou <xref:System.Web.IHttpHandler?displayProperty=fullName>.

- La classe est passée comme un paramètre de type a un [ `new` contrainte](/dotnet/csharp/language-reference/keywords/new-constraint). L’exemple suivant est signalé par règle CA1812 :

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

- [CA1811 : Évitez le recours à code privé non appelé](../code-quality/ca1811-avoid-uncalled-private-code.md)
- [CA1801 : Passez en revue les paramètres inutilisés](../code-quality/ca1801-review-unused-parameters.md)
- [CA1804 : Supprimez les variables locales inutilisées](../code-quality/ca1804-remove-unused-locals.md)
