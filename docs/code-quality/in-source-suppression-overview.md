---
title: Supprimer les avertissements d’analyse du code
ms.date: 12/01/2018
ms.topic: conceptual
helpviewer_keywords:
- source suppression, code analysis
- code analysis, source suppression
author: mikejo5000
ms.author: mikejo
manager: jillfra
dev_langs:
- CSharp
- VB
- CPP
ms.workload:
- multiple
ms.openlocfilehash: 71d2fe83690e55d49bb23bffb09de91c8f7534b6
ms.sourcegitcommit: 1efb6b219ade7c35068b79fbdc573a8771ac608d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78167622"
---
# <a name="suppress-code-analysis-warnings"></a>Supprimer les avertissements d’analyse du code

Il est souvent utile d’indiquer qu’un avertissement n’est pas applicable. Cela indique aux membres de l’équipe que le code a été révisé et que l’avertissement peut être supprimé. La suppression en source (ISS) utilise l’attribut <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> pour supprimer un avertissement. L’attribut peut être placé à proximité du segment de code qui a généré l’avertissement. Vous pouvez ajouter l’attribut <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> au fichier source en le tapant dans, ou vous pouvez utiliser le menu contextuel sur un avertissement dans le **liste d’erreurs** pour l’ajouter automatiquement.

L’attribut <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> est un attribut conditionnel, qui est inclus dans les métadonnées IL de votre assembly de code managé, uniquement si le symbole CODE_ANALYSIS compilation est défini au moment de la compilation.

Dans C++/CLI, utilisez l’autorité de certification macros\_supprimer\_message ou l’autorité de certification\_GLOBAL\_SUPPRESS_MESSAGE dans le fichier d’en-tête pour ajouter l’attribut.

> [!NOTE]
> Vous ne devez pas utiliser de suppressions dans la source pour les versions release, afin d’éviter d’expédier accidentellement les métadonnées de suppression dans la source. En outre, en raison du coût de traitement de la suppression en source, les performances de votre application peuvent être dégradées.

::: moniker range="vs-2017"

> [!NOTE]
> Si vous migrez un projet vers Visual Studio 2017, vous serez peut-être confronté à un grand nombre d’avertissements d’analyse du code. Si vous n’êtes pas prêt à corriger les avertissements, vous pouvez les supprimer en choisissant **analyser** > **exécuter l’analyse du code et supprimer les problèmes actifs**.
>
> ![Exécuter l’analyse du code et supprimer les problèmes dans Visual Studio](media/suppress-active-issues.png)

::: moniker-end

::: moniker range=">=vs-2019"

> [!NOTE]
> Si vous migrez un projet vers Visual Studio 2019, vous serez peut-être confronté à un grand nombre d’avertissements d’analyse du code. Si vous n’êtes pas prêt à corriger les avertissements, vous pouvez les supprimer en choisissant **analyser** > **générer et supprimer les problèmes actifs**.

::: moniker-end

## <a name="suppressmessage-attribute"></a>SuppressMessage (attribut)

Quand vous choisissez **supprimer** dans le menu contextuel ou le menu contextuel d’un avertissement d’analyse du code dans la **liste d’erreurs**, un attribut <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> est ajouté dans votre code ou dans le fichier de suppression globale du projet.

L’attribut <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> a le format suivant :

```vb
<Scope:SuppressMessage("Rule Category", "Rule Id", Justification = "Justification", MessageId = "MessageId", Scope = "Scope", Target = "Target")>
```

```csharp
[Scope:SuppressMessage("Rule Category", "Rule Id", Justification = "Justification", MessageId = "MessageId", Scope = "Scope", Target = "Target")]
```

```cpp
CA_SUPPRESS_MESSAGE("Rule Category", "Rule Id", Justification = "Justification", MessageId = "MessageId", Scope = "Scope", Target = "Target")
```

Les propriétés de l’attribut sont les suivantes :

- **Category** : catégorie dans laquelle la règle est définie. Pour plus d’informations sur les catégories de règle d’analyse du code, consultez [avertissements de code managé](../code-quality/code-analysis-for-managed-code-warnings.md).

- **CheckId** : identificateur de la règle. La prise en charge comprend un nom abrégé et un nom long pour l’identificateur de règle. Le nom abrégé est CAXXXX ; le nom long est CAXXXX : FriendlyTypeName.

- **Justification** : texte utilisé pour documenter la raison de la suppression du message.

- **MessageID** -identificateur unique d’un problème pour chaque message.

- **Scope** : cible sur laquelle l’avertissement est supprimé. Si la cible n’est pas spécifiée, elle est définie sur la cible de l’attribut. Les [étendues](xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute.Scope) prises en charge sont les suivantes :

  - [`module`](#module-suppression-scope) : cette étendue supprime les avertissements sur un assembly. Il s’agit d’une suppression globale qui s’applique à l’ensemble du projet.

  - `resource`-([FxCop hérité](../code-quality/static-code-analysis-for-managed-code-overview.md) uniquement) cette étendue supprime les avertissements dans les informations de diagnostics écrits dans les fichiers de ressources qui font partie du module (Assembly). Cette étendue n’est pas lue/respectée dans C#les compilateurs/vb pour les diagnostics de l’analyseur Roslyn, qui analyse uniquement les fichiers sources.

  - `type` : cette étendue supprime les avertissements par rapport à un type.

  - `member` : cette étendue supprime les avertissements sur un membre.

  - `namespace` : cette étendue supprime les avertissements sur l’espace de noms lui-même. Elle ne supprime pas les avertissements relatifs aux types dans l’espace de noms.

  - `namespaceanddescendants`-(requiert la version du compilateur 3. x ou supérieure et Visual Studio 2019) cette portée supprime les avertissements dans un espace de noms et tous ses symboles descendants. La valeur `namespaceanddescendants` est ignorée par l’analyse héritée.

- **Cible** : identificateur utilisé pour spécifier la cible sur laquelle l’avertissement doit être supprimé. Il doit contenir un nom d’élément complet.

## <a name="suppressmessage-usage"></a>Utilisation de SuppressMessage

Les avertissements d’analyse du code sont supprimés au niveau auquel l’attribut <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> est appliqué. Par exemple, l’attribut peut être appliqué au niveau de l’assembly, du module, du type, du membre ou du paramètre. L’objectif est de coupler étroitement les informations de suppression au code où la violation se produit.

La forme générale de suppression inclut la catégorie de règle et un identificateur de règle, qui contient une représentation explicite facultative du nom de la règle. Par exemple :

`[SuppressMessage("Microsoft.Design", "CA1039:ListsAreStrongTyped")]`

S’il existe des raisons de performances strictes pour réduire les métadonnées de suppression dans la source, le nom de la règle peut être omis. La catégorie de règle et son ID de règle constituent ensemble un identificateur de règle suffisamment unique. Par exemple :

`[SuppressMessage("Microsoft.Design", "CA1039")]`

Pour des raisons de maintenabilité, l’omission du nom de la règle n’est pas recommandée.

## <a name="suppress-selective-violations-within-a-method-body"></a>Supprimer les violations sélectives dans un corps de méthode

Les attributs de suppression peuvent être appliqués à une méthode, mais ne peuvent pas être incorporés dans un corps de méthode. Cela signifie que toutes les violations d’une règle particulière sont supprimées si vous ajoutez l’attribut <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> à la méthode.

Dans certains cas, vous souhaiterez peut-être supprimer une instance particulière de la violation, par exemple afin que le code futur ne soit pas automatiquement exempté de la règle d’analyse du code. Certaines règles d’analyse du code vous permettent de le faire à l’aide de la propriété `MessageId` de l’attribut <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute>. En général, les règles héritées pour les violations sur un symbole particulier (une variable locale ou un paramètre) respectent la propriété `MessageId`. [Ca1500 : VariableNamesShouldNotMatchFieldNames](../code-quality/ca1500.md) est un exemple de cette règle. Toutefois, les règles héritées pour les violations sur du code exécutable (sans symbole) ne respectent pas la propriété `MessageId`. En outre, les analyseurs .NET Compiler Platform (« Roslyn ») ne respectent pas la propriété `MessageId`.

Pour supprimer une violation de symbole particulière d’une règle, spécifiez le nom de symbole de la propriété `MessageId` de l’attribut <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute>. L’exemple suivant montre le code avec deux violations de [ca1500 : VariableNamesShouldNotMatchFieldNames](../code-quality/ca1500.md)&mdash;une pour la variable `name` et une pour la variable `age`. Seule la violation pour le symbole `age` est supprimée.

```vb
Public Class Animal
    Dim age As Integer
    Dim name As String

    <CodeAnalysis.SuppressMessage("Microsoft.Maintainability", "CA1500:VariableNamesShouldNotMatchFieldNames", MessageId:="age")>
    Sub PrintInfo()
        Dim age As Integer = 5
        Dim name As String = "Charlie"

        Console.WriteLine("Age {0}, Name {1}", age, name)
    End Sub

End Class
```

```csharp
public class Animal
{
    int age;
    string name;

    [System.Diagnostics.CodeAnalysis.SuppressMessage("Microsoft.Maintainability", "CA1500:VariableNamesShouldNotMatchFieldNames", MessageId = "age")]
    private void PrintInfo()
    {
        int age = 5;
        string name = "Charlie";

        Console.WriteLine($"Age {age}, Name {name}");
    }
}
```

## <a name="generated-code"></a>Code généré

Les compilateurs de code managé et certains outils tiers génèrent du code pour faciliter le développement rapide de code. Le code généré par le compilateur qui apparaît dans les fichiers sources est généralement marqué avec l’attribut `GeneratedCodeAttribute`.

Vous pouvez choisir de supprimer les avertissements et les erreurs d’analyse du code pour le code généré. Pour plus d’informations sur la façon de supprimer de tels avertissements et erreurs, consultez [Comment : supprimer des avertissements pour le code généré](../code-quality/how-to-suppress-code-analysis-warnings-for-generated-code.md).

> [!NOTE]
> L’analyse du code ignore `GeneratedCodeAttribute` lorsqu’elle est appliquée à un assembly entier ou à un paramètre unique.

## <a name="global-level-suppressions"></a>Suppressions au niveau global

L’outil d’analyse du code managé examine `SuppressMessage` attributs appliqués au niveau de l’assembly, du module, du type, du membre ou du paramètre. Il déclenche également des violations sur les ressources et les espaces de noms. Ces violations doivent être appliquées au niveau global et sont étendues et ciblées. Par exemple, le message suivant supprime une violation d’espace de noms :

`[module: SuppressMessage("Microsoft.Design", "CA1020:AvoidNamespacesWithFewTypes", Scope = "namespace", Target = "MyNamespace")]`

> [!NOTE]
> Lorsque vous supprimez un avertissement avec la portée `namespace`, il supprime l’avertissement sur l’espace de noms lui-même. Elle ne supprime pas l’avertissement par rapport aux types dans l’espace de noms.

Toute suppression peut être exprimée en spécifiant une portée explicite. Ces suppressions doivent résider au niveau global. Vous ne pouvez pas spécifier la suppression au niveau du membre en décorant un type.

Les suppressions au niveau global sont le seul moyen de supprimer des messages qui font référence au code généré par le compilateur qui n’est pas mappé à une source utilisateur fournie explicitement. Par exemple, le code suivant supprime une violation par rapport à un constructeur émis par le compilateur :

`[module: SuppressMessage("Microsoft.Design", "CA1055:AbstractTypesDoNotHavePublicConstructors", Scope="member", Target="Microsoft.Tools.FxCop.Type..ctor()")]`

> [!NOTE]
> `Target` contient toujours le nom qualifié complet de l’élément.

### <a name="global-suppression-file"></a>Fichier de suppression globale

Le fichier de suppression globale conserve les suppressions qui sont des suppressions au niveau global ou des suppressions qui ne spécifient pas de cible. Par exemple, les suppressions pour les violations au niveau de l’assembly sont stockées dans ce fichier. En outre, certaines suppressions de ASP.NET sont stockées dans ce fichier, car les paramètres au niveau du projet ne sont pas disponibles pour le code-behind d’un formulaire. Un fichier de suppression globale est créé et ajouté à votre projet la première fois que vous sélectionnez l’option **dans le fichier de suppression du projet** de la commande **supprimer** de la fenêtre **liste d’erreurs** .

### <a name="module-suppression-scope"></a>Étendue de suppression de module

Vous pouvez supprimer les violations de qualité du code pour l’assembly entier à l’aide de la portée de **module** .

Par exemple, l’attribut suivant dans votre fichier projet _GlobalSuppressions_ supprime la violation ConfigureAwait pour un projet ASP.net Core :

`[assembly: System.Diagnostics.CodeAnalysis.SuppressMessage("Reliability", "CA2007:Consider calling ConfigureAwait on the awaited task", Justification = "ASP.NET Core doesn't use thread context to store request context.", Scope = "module")]`

## <a name="see-also"></a>Voir aussi

- <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute.Scope>
- <xref:System.Diagnostics.CodeAnalysis>
- [Utiliser des analyseurs de code](../code-quality/use-roslyn-analyzers.md)
