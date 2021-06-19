---
title: 'Procédure pas à pas : déboguer des modèles de texte qui accèdent à un modèle'
description: Fournit des informations sur le débogage d’un modèle de texte qui accède à un modèle.
ms.date: 11/04/2016
ms.topic: how-to
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.custom: SEO-VS-2020
ms.workload:
- multiple
ms.openlocfilehash: d39b1ac72210145cc1efa1c513b7f3b76d8c2e36
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112388228"
---
# <a name="walkthrough-debugging-a-text-template-that-accesses-a-model"></a>Procédure pas à pas : débogage d'un modèle de texte accédant à un modèle
Lorsque vous modifiez ou ajoutez des modèles de texte dans une solution de langage spécifique à un domaine, vous pouvez recevoir des erreurs lorsque le moteur transforme le modèle en code source ou lors de la compilation du code généré. La procédure pas à pas suivante présente certaines des opérations que vous pouvez effectuer pour déboguer un modèle de texte.

> [!NOTE]
> Pour plus d’informations sur les modèles de texte en général, consultez [génération de code et modèles de texte T4](../modeling/code-generation-and-t4-text-templates.md). Pour plus d’informations sur le débogage des modèles de texte, consultez [procédure pas à pas : débogage d’un modèle de texte](debugging-a-t4-text-template.md).

## <a name="creating-a-domain-specific-language-solution"></a>Création d’une solution de langage Domain-Specific
 Dans cette procédure, vous créez une solution de langage spécifique à un domaine qui présente les caractéristiques suivantes :

- Nom : DebuggingTestLanguage

- Modèle de solution : langage minimal

- Extension de fichier :. ddd

- Nom de la société : fabrikam

  Pour plus d’informations sur la création d’une solution de langage spécifique à un domaine, consultez [How to : Create a Domain-Specific Language solution](../modeling/how-to-create-a-domain-specific-language-solution.md).

## <a name="creating-a-text-template"></a>Création d’un modèle de texte
 Ajoutez un modèle de texte à votre solution.

#### <a name="to-create-a-text-template"></a>Pour créer un modèle de texte

1. Générez la solution et commencez à l’exécuter dans le débogueur. (Dans le menu **générer** , cliquez sur **régénérer la solution**, puis, dans le menu **Déboguer** , cliquez sur Démarrer le **débogage**.) Une nouvelle instance de Visual Studio ouvre le projet de débogage.

2. Ajoutez un fichier texte nommé `DebugTest.tt` au projet de débogage.

3. Assurez-vous que la propriété **outil personnalisé** de DebugTest.TT a la valeur `TextTemplatingFileGenerator` .

## <a name="debugging-directives-that-access-a-model-from-a-text-template"></a>Directives de débogage qui accèdent à un modèle à partir d’un modèle de texte
 Avant de pouvoir accéder à un modèle à partir des instructions et des expressions d’un modèle de texte, vous devez d’abord appeler un processeur de directive généré. L’appel du processeur de directive généré rend les classes de votre modèle disponibles pour le code de modèle de texte sous forme de propriétés. Pour plus d’informations, consultez [accès aux modèles à partir de modèles de texte](../modeling/accessing-models-from-text-templates.md).

 Dans les procédures suivantes, vous allez déboguer un nom de directive incorrect et un nom de propriété incorrect.

#### <a name="to-debug-an-incorrect-directive-name"></a>Pour déboguer un nom de directive incorrect

1. Remplacez le code dans DebugTest.tt par le code suivant :

    > [!NOTE]
    > Le code contient une erreur. Vous introduisez l’erreur afin de la déboguer.

    ```csharp
    <#@ template language="C#" inherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation"#>
    <#@ output extension=".txt" #>
    <#@ modelRoot processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=ExampleModel" #>

    Model: <#= this.ExampleModel #>
    <#
    foreach (ExampleElement element in this.ExampleModel.Elements)
    {
    #>
        Element: <#= element.Name #>
    <#
    }
    #>
    ```

    ```vb
    <#@ template language="VB" inherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation"#>
    <#@ output extension=".txt" #>
    <#@ modelRoot processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=ExampleModel" #>

    Model: <#= Me.ExampleModel #>
    <#
    For Each element as ExampleElement in Me.ExampleModel.Elements
    #>
        Element: <#= element.Name #>
    <#
    Next
    #>
    ```

2. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur DebugTest.TT, puis cliquez sur **exécuter un outil personnalisé**.

     La fenêtre **liste d’erreurs** affiche cette erreur :

     **Le processeur nommé « DebuggingTestLanguageDirectiveProcessor » ne prend pas en charge la directive nommée « modelRoot ». La transformation ne sera pas exécutée.**

     Dans ce cas, l’appel de directive contient un nom de directive incorrect. Vous avez spécifié `modelRoot` comme nom de directive, mais le nom de directive correct est `DebuggingTestLanguage` .

3. Double-cliquez sur l’erreur dans la fenêtre **liste d’erreurs** pour accéder au code.

4. Pour corriger le code, remplacez le nom de la directive par `DebuggingTestLanguage` .

     La modification est mise en surbrillance.

    ```csharp
    <#@ DebuggingTestLanguage processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=ExampleModel" #>
    ```

    ```vb
    <#@ DebuggingTestLanguage processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=ExampleModel" #>
    ```

5. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur DebugTest.TT, puis cliquez sur **exécuter un outil personnalisé**.

     À présent, le système transforme le modèle de texte et génère le fichier de sortie correspondant. Aucune erreur ne s’affiche dans la fenêtre **liste d’erreurs** .

#### <a name="to-debug-an-incorrect-property-name"></a>Pour déboguer un nom de propriété incorrect

1. Remplacez le code dans DebugTest.tt par le code suivant :

    > [!NOTE]
    > Le code contient une erreur. Vous introduisez l’erreur afin de la déboguer.

    ```csharp
    <#@ template language="C#" inherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation"#>
    <#@ output extension=".txt" #>
    <#@ DebuggingTestLanguage processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=LibraryModel" #>

    Model: <#= this.ExampleModel #>
    <#
    foreach (ExampleElement element in this.ExampleModel.Elements)
    {
    #>
        Element: <#= element.Name #>
    <#
    }
    #>
    ```

    ```vb
    <#@ template language="VB" inherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation"#>
    <#@ output extension=".txt" #>
    <#@ DebuggingTestLanguage processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=LibraryModel" #>

    Model: <#= Me.ExampleModel #>
    <#
    For Each element as ExampleElement in Me.ExampleModel.Elements
    #>
        Element: <#= element.Name #>
    <#
    Next
    #>
    ```

2. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur DebugTest.TT, puis cliquez sur **exécuter un outil personnalisé**.

     La fenêtre **liste d’erreurs** apparaît et affiche l’une des erreurs suivantes :

     (C#)

     **Compilation de la transformation : Microsoft. VisualStudio. TextTemplating \<GUID> . GeneratedTextTransformation’ne contient pas de définition pour’ExampleModel'**

     (Visual Basic)

     **Compilation de la transformation : 'ExampleModel’n’est pas un membre de’Microsoft. VisualStudio. TextTemplating \<GUID> . GeneratedTextTransformation'.**

     Dans ce cas, le code de modèle de texte contient un nom de propriété incorrect. Vous avez spécifié `ExampleModel` en tant que nom de propriété, mais le nom de propriété correct est `LibraryModel` . Vous pouvez trouver le nom de propriété correct dans le paramètre fournit, comme indiqué dans le code suivant :

    ```
    <#@ DebuggingTestLanguage processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=LibraryModel" #>
    ```

3. Double-cliquez sur l’erreur dans la fenêtre Liste d’erreurs pour accéder au code.

4. Pour corriger le code, remplacez le nom de la propriété par `LibraryModel` dans le code du modèle de texte.

     Les modifications sont mises en surbrillance.

    ```csharp
    <#@ template language="C#" inherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation"#>
    <#@ output extension=".txt" #>
    <#@ DebuggingTestLanguage processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=LibraryModel" #>

    Model: <#= this.LibraryModel #>
    <#
    foreach (ExampleElement element in this.LibraryModel.Elements)
    {
    #>
        Element: <#= element.Name #>
    <#
    }
    #>
    ```

    ```vb
    <#@ template language="VB" inherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation"#>
    <#@ output extension=".txt" #>
    <#@ DebuggingTestLanguage processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=LibraryModel" #>

    Model: <#= Me.LibraryModel #>
    <#
    For Each element as ExampleElement in Me.LibraryModel.Elements
    #>
        Element: <#= element.Name #>
    <#
    Next
    #>
    ```

5. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur DebugTest.TT, puis cliquez sur **exécuter un outil personnalisé**.

     À présent, le système transforme le modèle de texte et génère le fichier de sortie correspondant. Aucune erreur ne s’affiche dans la fenêtre **liste d’erreurs** .
