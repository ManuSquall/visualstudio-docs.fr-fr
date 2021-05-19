---
title: Supprimer les violations de l’analyse du code
ms.date: 05/10/2021
description: Découvrez comment supprimer les violations d’analyse du code dans Visual Studio. Comprendre comment utiliser l’attribut SuppressMessageAttribute pour la suppression en source.
ms.custom: SEO-VS-2020
ms.topic: conceptual
helpviewer_keywords:
- source suppression, code analysis
- code analysis, source suppression
author: mikadumont
ms.author: midumont
manager: jmartens
dev_langs:
- CSharp
- VB
- CPP
ms.workload:
- multiple
ms.openlocfilehash: fd177a96b8789760927933fad5c0320553a72f57
ms.sourcegitcommit: 162be102d2c22a1c4ad2c447685abd28e0e85d15
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2021
ms.locfileid: "109973336"
---
# <a name="suppress-code-analysis-violations"></a>Supprimer les violations de l’analyse du code

Il est souvent utile d’indiquer qu’un avertissement n’est pas applicable. Cela indique aux membres de l’équipe que le code a été révisé et que l’avertissement peut être supprimé. Cet article décrit les différentes façons de supprimer les violations d’analyse du code à l’aide de l’IDE de Visual Studio.

::: moniker range=">=vs-2019"

## <a name="suppress-violations-using-the-editorconfig-file"></a>Supprimer les violations à l’aide du fichier EditorConfig

Dans un **fichier EditorConfig**, définissez la gravité sur `none` , par exemple, `dotnet_diagnostic.CA1822.severity = none` . Pour ajouter un fichier EditorConfig, consultez [Ajouter un fichier EditorConfig à un projet](../ide/create-portable-custom-editor-options.md#add-and-remove-editorconfig-files).

::: moniker-end

## <a name="suppress-violations-in-source-code"></a>Supprimer les violations dans le code source

Vous pouvez supprimer des violations dans le code à l’aide d’une directive de préprocesseur, la [#pragma directive Warning (C#)](/dotnet/csharp/language-reference/preprocessor-directives.md#pragma-warning) ou [Disable (Visual Basic)](/dotnet/visual-basic/language-reference/directives/disable-enable.md) pour supprimer l’avertissement uniquement pour une ligne de code spécifique. Vous pouvez utiliser l' [attribut SuppressMessage](#in-source-suppression-and-the-suppressmessage-attribute).

- À partir de l' **éditeur de code**

  Placez le curseur dans la ligne de code avec la violation et appuyez sur **CTRL**+ + **point (.)** pour ouvrir le menu **actions rapides** . Sélectionnez **supprimer CAXXXX**, puis choisissez dans la **source** ou **dans la source (attribut)**.

  Si vous choisissez **dans la source**, vous voyez un aperçu de la directive de préprocesseur qui sera ajoutée à votre code.

  ::: moniker range="vs-2017"
  :::image type="content" source="media/suppress-diagnostic-from-editor.png" alt-text="Supprimer les diagnostics du menu actions rapides":::
  ::: moniker-end
  ::: moniker range=">=vs-2019"
  :::image type="content" source="media/vs-2019/suppress-diagnostic-from-editor.png" alt-text="Supprimer les diagnostics du menu actions rapides":::

  Si vous choisissez **dans source (attribut)**, vous voyez un aperçu de l' [attribut SuppressMessage](#in-source-suppression-and-the-suppressmessage-attribute) qui sera ajouté à votre code.

  :::image type="content" source="media/vs-2019/suppress-diagnostic-from-editor-attribute.png" alt-text="Supprimer le diagnostic du menu actions rapides à l’aide de l’attribut":::
  ::: moniker-end

- À partir de la **liste d’erreurs**

  Sélectionnez les règles que vous souhaitez supprimer, puis cliquez avec le bouton droit et sélectionnez **supprimer**  >  **dans la source**.

  - Si vous supprimez **dans la source**, la boîte de dialogue **aperçu des modifications** s’ouvre et affiche un aperçu de l' [avertissement #pragma](/dotnet/csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning) C# ou Visual Basic #Disable directive d' [Avertissement](/dotnet/visual-basic/language-reference/directives/directives) ajoutée au code source.

    ![Aperçu de l’ajout d' #pragma avertissement dans le fichier de code](media/pragma-warning-preview.png)

  Dans la boîte de dialogue **aperçu des modifications** , sélectionnez **appliquer**.

  > [!NOTE]
  > Si vous ne voyez pas l’option de menu **supprimer** dans **Explorateur de solutions**, la violation provient probablement de la génération et non de l’analyse en temps réel. Le **liste d’erreurs** affiche les diagnostics ou les violations de règle à partir de l’analyse du code en direct et de la Build. Comme les diagnostics de build peuvent être périmés, par exemple, si vous avez modifié le code pour corriger la violation mais que vous ne l’avez pas reconstruit, vous ne pouvez pas supprimer ces diagnostics du **liste d’erreurs**. Les diagnostics à partir de l’analyse en direct, ou IntelliSense, sont toujours à jour avec les sources actuelles et peuvent être supprimés du **liste d’erreurs**. Pour exclure les diagnostics de *Build* de votre sélection, basculez le filtre de source de **liste d’erreurs** de la **génération + IntelliSense** vers **IntelliSense uniquement**. Sélectionnez ensuite les diagnostics que vous souhaitez supprimer et procédez comme décrit précédemment.
  >
  > ![Filtre de source de Liste d’erreurs dans Visual Studio](media/error-list-filter.png)

## <a name="suppress-violations-using-a-global-suppression-file"></a>Supprimer les violations à l’aide d’un fichier de suppression global

Le [fichier de suppression globale](#global-level-suppressions) utilise l' [attribut SuppressMessage](#in-source-suppression-and-the-suppressmessage-attribute).

- Dans le **liste d’erreurs**, sélectionnez les règles que vous souhaitez supprimer, puis cliquez avec le bouton droit et sélectionnez **supprimer**  >  **dans le fichier de suppression**. La boîte de dialogue **aperçu des modifications** s’ouvre et affiche un aperçu de l' <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> attribut qui est ajouté au fichier de suppression globale.

  ![Aperçu de l’ajout de l’attribut SuppressMessage au fichier de suppression](media/preview-changes-in-suppression-file.png)

- Dans l' **éditeur de code**, placez le curseur dans la ligne de code avec la violation et appuyez sur **actions rapides et refactorisations** (ou appuyez sur **CTRL** + **point (.)**) pour ouvrir le menu **actions rapides** . Sélectionnez **supprimer CAXXXX**, puis choisissez **dans le fichier de suppression**. Vous voyez un aperçu du [fichier de suppression globale](#global-level-suppressions) qui sera créé ou modifié.

::: moniker range=">=vs-2019"

- Dans le menu **analyser** , sélectionnez **analyser**  >  la **Build et supprimer les problèmes actifs** dans la barre de menus pour supprimer toutes les violations en cours. Cette opération est parfois appelée « ligne de l’établissement ».

::: moniker-end
::: moniker range="vs-2017"

- Dans le menu **analyser** , sélectionnez **analyser**  >  **exécuter l’analyse du code et supprimer les problèmes actifs** dans la barre de menus pour supprimer toutes les violations en cours. Cette opération est parfois appelée « ligne de l’établissement ».
::: moniker-end

## <a name="suppress-violations-using-project-settings"></a>Supprimer les violations à l’aide des paramètres du projet

Dans **Explorateur de solutions**, ouvrez les propriétés du projet (cliquez avec le bouton droit sur le projet et choisissez **Propriétés** (ou appuyez sur **Alt + Entrée**) et utilisez l’onglet **analyse du code** pour configurer les options. Par exemple, vous pouvez désactiver l’analyse du code en direct ou désactiver les analyseurs .NET.

## <a name="suppress-violations-using-a-rule-set"></a>Supprimer les violations à l’aide d’un ensemble de règles

Dans l' **éditeur d’ensembles de règles**, désactivez la case à cocher en regard de son nom, ou définissez **action** sur **aucun**.

## <a name="in-source-suppression-and-the-suppressmessage-attribute"></a>Suppression en source et attribut SuppressMessage

La suppression en source (ISS) utilise l' <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> attribut pour supprimer un avertissement. L’attribut peut être placé à proximité du segment de code qui a généré l’avertissement. Vous pouvez ajouter l' <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> attribut au fichier source en le tapant dans, ou vous pouvez utiliser le menu contextuel sur un avertissement dans le **liste d’erreurs** pour l’ajouter automatiquement.

L' <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> attribut est un attribut conditionnel, qui est inclus dans les métadonnées il de votre assembly de code managé, uniquement si le CODE_ANALYSIS symbole de compilation est défini au moment de la compilation.

En C++/CLI, utilisez l’autorité de certification macros \_ supprimer le \_ message ou l' \_ \_ SUPPRESS_MESSAGE globale de l’autorité de certification dans le fichier d’en-tête pour ajouter l’attribut.

> [!NOTE]
> Vous ne devez pas utiliser de suppressions dans la source pour les versions release, afin d’éviter d’expédier accidentellement les métadonnées de suppression dans la source. En outre, en raison du coût de traitement de la suppression en source, les performances de votre application peuvent être dégradées.

::: moniker range="vs-2017"

> [!NOTE]
> Si vous migrez un projet vers Visual Studio 2017, vous serez peut-être confronté à un grand nombre d’avertissements d’analyse du code. Si vous n’êtes pas prêt à corriger les avertissements, vous pouvez les supprimer en sélectionnant **analyser**  >  **exécuter l’analyse du code et supprimer les problèmes actifs**.
>
> ![Exécuter l’analyse du code et supprimer les problèmes dans Visual Studio](media/suppress-active-issues.png)

::: moniker-end

::: moniker range=">=vs-2019"

> [!NOTE]
> Si vous migrez un projet vers Visual Studio 2019, vous serez peut-être confronté à un grand nombre d’avertissements d’analyse du code. Si vous n’êtes pas prêt à corriger les avertissements, vous pouvez les supprimer en sélectionnant **analyser** la  >  **Build et supprimer les problèmes actifs**.

::: moniker-end

### <a name="suppressmessage-attribute"></a>SuppressMessage (attribut)

Lorsque vous sélectionnez **supprimer** dans le menu contextuel ou le menu contextuel d’un avertissement d’analyse du code dans la **liste d’erreurs**, un <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> attribut est ajouté dans votre code ou dans le fichier de suppression globale du projet.

L' <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> attribut a le format suivant :

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

- **Category** : catégorie dans laquelle la règle est définie. Pour plus d’informations sur les catégories de règle d’analyse du code, consultez [avertissements de code managé](/dotnet/fundamentals/code-analysis/quality-rules/index).

- **CheckId** : identificateur de la règle. La prise en charge comprend un nom abrégé et un nom long pour l’identificateur de règle. Le nom abrégé est CAXXXX ; le nom long est CAXXXX : FriendlyTypeName.

- **Justification** : texte utilisé pour documenter la raison de la suppression du message.

- **MessageID** -identificateur unique d’un problème pour chaque message.

- **Scope** : cible sur laquelle l’avertissement est supprimé. Si la cible n’est pas spécifiée, elle est définie sur la cible de l’attribut. Les [étendues](xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute.Scope) prises en charge sont les suivantes :

  - [`module`](#module-suppression-scope) : Cette étendue supprime les avertissements sur un assembly. Il s’agit d’une suppression globale qui s’applique à l’ensemble du projet.

  - `resource` -([FxCop hérité](../code-quality/static-code-analysis-for-managed-code-overview.md) uniquement) cette étendue supprime les avertissements dans les informations de diagnostics écrits dans les fichiers de ressources qui font partie du module (Assembly). Cette étendue n’est pas lue/respectée dans les compilateurs C#/VB pour les diagnostics de l’analyseur Roslyn, qui analyse uniquement les fichiers sources.

  - `type` : Cette étendue supprime les avertissements par rapport à un type.

  - `member` : Cette étendue supprime les avertissements sur un membre.

  - `namespace` : Cette étendue supprime les avertissements sur l’espace de noms lui-même. Elle ne supprime pas les avertissements relatifs aux types dans l’espace de noms.

  - `namespaceanddescendants` -(Requiert le compilateur version 3. x ou supérieure et Visual Studio 2019) cette portée supprime les avertissements dans un espace de noms et tous ses symboles descendants. La `namespaceanddescendants` valeur est ignorée par l’analyse héritée.

- **Cible** : identificateur utilisé pour spécifier la cible sur laquelle l’avertissement doit être supprimé. Il doit contenir un nom d’élément complet.

Quand vous voyez des avertissements dans Visual Studio, vous pouvez afficher des exemples de `SuppressMessage` en [ajoutant une suppression au fichier de suppression globale](../code-quality/use-roslyn-analyzers.md#suppress-violations). L’attribut de suppression et ses propriétés requises s’affichent dans une fenêtre d’aperçu.

### <a name="suppressmessage-usage"></a>Utilisation de SuppressMessage

Les avertissements d’analyse du code sont supprimés au niveau auquel l' <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> attribut est appliqué. Par exemple, l’attribut peut être appliqué au niveau de l’assembly, du module, du type, du membre ou du paramètre. L’objectif est de coupler étroitement les informations de suppression au code où la violation se produit.

La forme générale de suppression inclut la catégorie de règle et un identificateur de règle, qui contient une représentation explicite facultative du nom de la règle. Par exemple :

`[SuppressMessage("Microsoft.Design", "CA1039:ListsAreStrongTyped")]`

S’il existe des raisons de performances strictes pour réduire les métadonnées de suppression dans la source, le nom de la règle peut être omis. La catégorie de règle et son ID de règle constituent ensemble un identificateur de règle suffisamment unique. Par exemple :

`[SuppressMessage("Microsoft.Design", "CA1039")]`

Pour des raisons de maintenabilité, l’omission du nom de la règle n’est pas recommandée.

### <a name="suppress-selective-violations-within-a-method-body"></a>Supprimer les violations sélectives dans un corps de méthode

Les attributs de suppression peuvent être appliqués à une méthode, mais ne peuvent pas être incorporés dans un corps de méthode. Cela signifie que toutes les violations d’une règle particulière sont supprimées si vous ajoutez l' <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> attribut à la méthode.

Dans certains cas, vous souhaiterez peut-être supprimer une instance particulière de la violation, par exemple afin que le code futur ne soit pas automatiquement exempté de la règle d’analyse du code. Certaines règles d’analyse du code vous permettent d’effectuer cette opération à l’aide `MessageId` de la propriété de l' <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> attribut. En général, les règles héritées pour les violations sur un symbole particulier (une variable locale ou un paramètre) respectent la `MessageId` propriété. [Ca1500 : VariableNamesShouldNotMatchFieldNames](../code-quality/ca1500.md) est un exemple de cette règle. Toutefois, les règles héritées pour les violations sur le code exécutable (sans symbole) ne respectent pas la `MessageId` propriété. En outre, les analyseurs .NET Compiler Platform (« Roslyn ») ne respectent pas la `MessageId` propriété.

Pour supprimer une violation de symbole particulière d’une règle, spécifiez le nom de symbole pour la `MessageId` propriété de l' <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> attribut. L’exemple suivant montre le code avec deux violations de [ca1500 : VariableNamesShouldNotMatchFieldNames](../code-quality/ca1500.md) &mdash; une pour la `name` variable et une pour la `age` variable. Seule la violation du `age` symbole est supprimée.

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

### <a name="global-level-suppressions"></a>Suppressions au niveau global

L’outil d’analyse du code managé examine les `SuppressMessage` attributs qui sont appliqués au niveau de l’assembly, du module, du type, du membre ou du paramètre. Il déclenche également des violations sur les ressources et les espaces de noms. Ces violations doivent être appliquées au niveau global et sont étendues et ciblées. Par exemple, le message suivant supprime une violation d’espace de noms :

`[module: SuppressMessage("Microsoft.Design", "CA1020:AvoidNamespacesWithFewTypes", Scope = "namespace", Target = "MyNamespace")]`

> [!NOTE]
> Lorsque vous supprimez un avertissement avec `namespace` la portée, il supprime l’avertissement sur l’espace de noms lui-même. Elle ne supprime pas l’avertissement par rapport aux types dans l’espace de noms.

Toute suppression peut être exprimée en spécifiant une portée explicite. Ces suppressions doivent résider au niveau global. Vous ne pouvez pas spécifier la suppression au niveau du membre en décorant un type.

Les suppressions au niveau global sont le seul moyen de supprimer des messages qui font référence au code généré par le compilateur qui n’est pas mappé à une source utilisateur fournie explicitement. Par exemple, le code suivant supprime une violation par rapport à un constructeur émis par le compilateur :

`[module: SuppressMessage("Microsoft.Design", "CA1055:AbstractTypesDoNotHavePublicConstructors", Scope="member", Target="Microsoft.Tools.FxCop.Type..ctor()")]`

> [!NOTE]
> `Target` contient toujours le nom complet de l’élément.

#### <a name="global-suppression-file"></a>Fichier de suppression globale

Le fichier de suppression globale conserve les suppressions qui sont des suppressions au niveau global ou des suppressions qui ne spécifient pas de cible. Par exemple, les suppressions pour les violations au niveau de l’assembly sont stockées dans ce fichier. En outre, certaines suppressions de ASP.NET sont stockées dans ce fichier, car les paramètres au niveau du projet ne sont pas disponibles pour le code-behind d’un formulaire. Un fichier de suppression globale est créé et ajouté à votre projet la première fois que vous sélectionnez l’option **dans le fichier de suppression du projet** de la commande **supprimer** de la fenêtre **liste d’erreurs** .

#### <a name="module-suppression-scope"></a>Étendue de suppression de module

Vous pouvez supprimer les violations de qualité du code pour l’assembly entier à l’aide de la portée de **module** .

Par exemple, l’attribut suivant dans votre fichier projet _GlobalSuppressions_ supprime la violation ConfigureAwait pour un projet ASP.net Core :

`[assembly: System.Diagnostics.CodeAnalysis.SuppressMessage("Reliability", "CA2007:Consider calling ConfigureAwait on the awaited task", Justification = "ASP.NET Core doesn't use thread context to store request context.", Scope = "module")]`

### <a name="generated-code"></a>Code généré

Les compilateurs de code managé et certains outils tiers génèrent du code pour faciliter le développement rapide de code. Le code généré par le compilateur qui apparaît dans les fichiers sources est généralement marqué avec l' `GeneratedCodeAttribute` attribut.

Pour l’analyse du code source, vous pouvez supprimer les messages du code généré dans un `.editorconfig` fichier. Pour plus d’informations, consultez [exclure le code généré](/dotnet/fundamentals/code-analysis/configuration-options#exclude-generated-code).

Pour l’analyse du code hérité, vous pouvez choisir de supprimer les avertissements et les erreurs d’analyse du code pour le code généré. Pour plus d’informations sur la façon de supprimer de tels avertissements et erreurs, consultez [Comment : supprimer des avertissements pour le code généré](../code-quality/how-to-suppress-code-analysis-warnings-for-generated-code.md).

> [!NOTE]
> L’analyse du code ignore `GeneratedCodeAttribute` quand elle est appliquée à un assembly entier ou à un paramètre unique.

## <a name="see-also"></a>Voir aussi

- <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute.Scope>
- <xref:System.Diagnostics.CodeAnalysis>
- [Utiliser des analyseurs de code](../code-quality/use-roslyn-analyzers.md)
