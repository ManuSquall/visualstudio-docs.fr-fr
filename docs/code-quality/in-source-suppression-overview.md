---
title: Supprimer les avertissements d’analyse du code dans Visual Studio
ms.date: 01/29/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- source suppression, code analysis
- code analysis, source suppression
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
- VB
- CPP
ms.workload:
- multiple
ms.openlocfilehash: aec11e54547f05e3ac7babae29e0c95737bc725e
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31924416"
---
# <a name="suppress-code-analysis-warnings"></a>Supprimer les avertissements d’analyse du code

Il est souvent utile d’indiquer qu’un avertissement n’est pas applicable. Cela indique à des membres de l’équipe que le code a été révisé et que l’avertissement peut être supprimé. Dans source suppression (ISS) utilise le <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> attribut pour supprimer un avertissement. L’attribut peut être placée à proximité du segment de code qui a généré l’avertissement. Vous pouvez ajouter la <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> d’attribut dans le fichier source en le tapant dans, ou vous pouvez utiliser le menu contextuel sur un avertissement dans le **liste d’erreurs** ajoute automatiquement.

Le <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> attribut est un attribut conditionnel qui est inclus dans les métadonnées de langage intermédiaire de votre assembly de code managé, uniquement si le symbole de compilation CODE_ANALYSIS est défini au moment de la compilation.

Dans C + c++ / CLI, utilisez les macros autorité de certification\_supprimer\_MESSAGE ou l’autorité de certification\_GLOBAL\_SUPPRESS_MESSAGE dans le fichier d’en-tête pour ajouter l’attribut.

> [!NOTE]
> Vous ne devez pas utiliser les suppressions dans la source sur les versions release, pour empêcher la copie les métadonnées de suppression à la source par inadvertance. En outre, en raison du coût de traitement de la suppression à la source, les performances de votre application peuvent être dégradé.

> [!NOTE]
> Si vous migrez un projet vers Visual Studio 2017, vous pouvez être confronté à avec un nombre considérable d’avertissements d’analyse du code. Si vous n’êtes pas prêt à résoudre les avertissements que vous souhaitez désactiver temporairement l’analyse du code, ouvrez les pages de propriétés du projet (**projet** > ***projet* propriétés...** ) et accédez à la **l’analyse du Code** onglet. Désélectionnez **activer l’analyse du Code sur la Build**, puis régénérez votre projet. Vous pouvez également sélectionner une règle différents, le plus petite configurée pour s’exécuter sur le code. N’oubliez pas d’activer l’analyse du code sur quand vous êtes prêt à résoudre les avertissements.

## <a name="suppressmessage-attribute"></a>SuppressMessage (attribut)

Lorsque vous choisissez **supprimer** dans le menu contextuel ou avec le bouton d’un avertissement d’analyse du code dans le **liste d’erreurs**, un <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> attribut est ajouté dans votre code ou de suppression globale du projet fichier.

Le <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> attribut a le format suivant :

```vb
<Scope:SuppressMessage("Rule Category", "Rule Id", Justification = "Justification", MessageId = "MessageId", Scope = "Scope", Target = "Target")>
```

```csharp
[Scope:SuppressMessage("Rule Category", "Rule Id", Justification = "Justification", MessageId = "MessageId", Scope = "Scope", Target = "Target")]
```

```cpp
CA_SUPPRESS_MESSAGE("Rule Category", "Rule Id", Justification = "Justification", MessageId = "MessageId", Scope = "Scope", Target = "Target")
```

Les propriétés de l’attribut incluent :

- **Catégorie de règle** -catégorie dans laquelle la règle est définie. Pour plus d’informations sur les catégories de règles analyse de code, consultez [gérés les avertissements du code](../code-quality/code-analysis-for-managed-code-warnings.md).

- **Id de règle** -l’identificateur de la règle. Prise en charge inclut à la fois un nom court et long de l’identificateur de la règle. Le nom court est CAXXXX ; le nom long est CAXXXX:FriendlyTypeName.

- **Justification** -le texte qui est utilisé pour documenter la raison de la suppression du message.

- **Id de message** -identificateur Unique d’un problème pour chaque message.

- **Étendue** -cible sur laquelle l’avertissement est supprimé. Si la cible n’est pas spécifiée, il est défini à la cible de l’attribut. Les étendues prises en charge sont les suivantes :

    - Module

    - Espace de noms

    - Ressource

    - Type

    - Membre

- **Cible** - un identificateur qui est utilisé pour spécifier la cible sur laquelle l’avertissement est supprimé. Il doit contenir un nom d’élément complet.

## <a name="suppressmessage-usage"></a>Utilisation de SuppressMessage

Avertissements d’analyse du code sont supprimés au niveau auquel le <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> attribut est appliqué. Par exemple, l’attribut peut être appliqué à l’assembly, un module, un type, un membre ou un au niveau du paramètre. L’objectif de ce est étroitement coupler les informations sur la suppression du code où la violation se produit.

La forme générale de la suppression inclut la catégorie de règle et un identificateur de règle, qui contient une représentation explicite facultative du nom de la règle. Par exemple :

`[SuppressMessage("Microsoft.Design", "CA1039:ListsAreStrongTyped")]`

S’il existe des raisons de performances strict pour réduire les métadonnées de suppression à la source, le nom de la règle peut être omis. La catégorie de règle et son ID de règle constituent un identificateur de règle unique suffisant. Par exemple :

`[SuppressMessage("Microsoft.Design", "CA1039")]`

Pour des raisons de facilité de maintenance, l’omission du nom de la règle n’est pas recommandée.

## <a name="suppress-selective-violations-within-a-method-body"></a>Supprimer des violations sélectives dans un corps de méthode

Attributs de suppression peuvent être appliqués à une méthode, mais il ne peut pas être incorporés dans un corps de méthode. Cela signifie que toutes les violations d’une règle particulière sont supprimées si vous ajoutez le <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> d’attribut à la méthode.

Dans certains cas, vous souhaiterez éventuellement supprimer une instance particulière de la violation, par exemple, afin que le code ultérieur n’est pas automatiquement exempté de la règle d’analyse du code. Certaines règles d’analyse du code permettent de procéder à l’aide de la `MessageId` propriété de la <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> attribut. En général, les règles hérité pour les violations d’un en ce qui concerne un symbole particulier (une variable locale ou un paramètre) la `MessageId` propriété. [CA1500:VariableNamesShouldNotMatchFieldNames](../code-quality/ca1500-variable-names-should-not-match-field-names.md) est un exemple de cette règle. Toutefois, les règles héritées de violations de code exécutable (pas un symbole) ne respectent pas la `MessageId` propriété. En outre, les analyseurs de plateforme des compilateurs .NET (« Roslyn ») ne respectent pas la `MessageId` propriété.

Pour supprimer une violation de symbole particulière d’une règle, spécifiez le nom de symbole pour le `MessageId` propriété de la <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> attribut. L’exemple suivant montre le code avec deux violations de [CA1500:VariableNamesShouldNotMatchFieldNames](../code-quality/ca1500-variable-names-should-not-match-field-names.md)&mdash;une pour le `name` variable et l’autre pour le `age` variable. Uniquement la violation de la `age` symbole est supprimé.

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

Les compilateurs de code managé et de certains des outils tiers génèrent du code pour faciliter le développement de code rapide. Code généré par le compilateur qui apparaît dans les fichiers sources est généralement signalé par le `GeneratedCodeAttribute` attribut.

Vous pouvez choisir s’il faut supprimer les avertissements d’analyse du code et les erreurs pour le code généré. Pour plus d’informations sur la façon de supprimer ces avertissements et les erreurs, consultez [Comment : supprimer les avertissements pour du Code généré](../code-quality/how-to-suppress-code-analysis-warnings-for-generated-code.md).

> [!NOTE]
> Analyse du code ignore `GeneratedCodeAttribute` lorsqu’il est appliqué à un assembly entier ou un paramètre unique.

## <a name="global-level-suppressions"></a>Suppressions au niveau global

L’outil d’analyse du code managé examine `SuppressMessage` attributs qui sont appliqués au niveau de l’assembly, module, type, membre ou paramètre. Il déclenche également des violations pour les ressources et les espaces de noms. Ces violations doivent être appliquées au niveau global d’une étendue et sont ciblées. Par exemple, le message suivant supprime une violation de l’espace de noms :

`[module: SuppressMessage("Microsoft.Design", "CA1020:AvoidNamespacesWithFewTypes", Scope = "namespace", Target = "MyNamespace")]`

> [!NOTE]
> Lorsque vous supprimez un avertissement avec la portée espace de noms, il supprime l’avertissement par rapport à l’espace de noms. Elle ne supprime pas l’avertissement par rapport aux types dans l’espace de noms.

Toute suppression peut être exprimée en spécifiant une portée explicite. Ces suppressions doivent exister au niveau global. Vous ne pouvez pas spécifier de suppression au niveau du membre en décorant un type.

Les suppressions au niveau global sont la seule façon de supprimer les messages qui font référence au code généré par le compilateur qui ne correspond pas à la source de l’utilisateur fournies explicitement. Par exemple, le code suivant supprime une violation sur un constructeur émis par le compilateur :

`[module: SuppressMessage("Microsoft.Design", "CA1055:AbstractTypesDoNotHavePublicConstructors", Scope="member", Target="Microsoft.Tools.FxCop.Type..ctor()")]`

> [!NOTE]
> `Target` contient toujours le nom qualifié complet.

## <a name="global-suppression-file"></a>Fichier de suppression globale

Le fichier de suppression globale conserve les suppressions qui sont soit au niveau global ou qui ne spécifient pas une cible. Par exemple, les suppressions de violations de niveau de l’assembly sont stockées dans ce fichier. En outre, certaines suppressions ASP.NET sont stockées dans ce fichier, car les paramètres au niveau du projet ne sont pas disponibles pour le code-behind d’un formulaire. Un fichier de suppression globale est créé et ajouté à votre projet la première fois que vous sélectionnez le **dans le fichier de Suppression de projet** option de le **supprimer** dans le **liste d’erreurs**fenêtre.

## <a name="see-also"></a>Voir aussi

- <xref:System.Diagnostics.CodeAnalysis>
- [Utilisez les analyseurs de Roslyn](../code-quality/use-roslyn-analyzers.md)