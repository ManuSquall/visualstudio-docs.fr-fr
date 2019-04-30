---
title: 'Procédure pas à pas : Débogage d’un modèle de texte qui accède à un modèle | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: af46a7fe-6b98-4d3d-b816-0bbf8e81e220
caps.latest.revision: 8
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: b589050c156e4c3d1e322bfa5996364016cbe38e
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63446724"
---
# <a name="walkthrough-debugging-a-text-template-that-accesses-a-model"></a>Procédure pas à pas : Débogage d’un modèle de texte accédant à un modèle
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Lorsque vous modifiez ou ajoutez des modèles de texte dans une solution de langage spécifique à un domaine, vous obtiendrez des erreurs lorsque le moteur transforme le modèle de code source ou lors de la compilation du code généré. La procédure suivante montre quelques opérations que vous pouvez faire pour déboguer un modèle de texte.  
  
> [!NOTE]
> Pour plus d’informations sur le texte modèles en général, consultez [génération de Code et modèles de texte T4](../modeling/code-generation-and-t4-text-templates.md). Pour plus d’informations sur le débogage des modèles de texte, consultez [procédure pas à pas : Débogage d’un modèle de texte](http://msdn.microsoft.com/library/5c3fd3b7-c110-4e86-a22f-d5756be6b94f).  
  
## <a name="creating-a-domain-specific-language-solution"></a>Création d’une Solution de langage spécifique à un domaine  
 Dans cette procédure, vous créez une solution de langage spécifique à un domaine qui présente les caractéristiques suivantes :  
  
- Nom : DebuggingTestLanguage  
  
- Modèle de solution : Langage minimal  
  
- Extension de fichier : .ddd  
  
- Nom de la société : Fabrikam  
  
  Pour plus d’informations sur la création d’une solution de langage spécifique à un domaine, consultez [Comment : Créer une solution de langage spécifique à un domaine](../modeling/how-to-create-a-domain-specific-language-solution.md).  
  
## <a name="creating-a-text-template"></a>Création d’un modèle de texte  
 Ajouter un modèle de texte à votre solution.  
  
#### <a name="to-create-a-text-template"></a>Pour créer un modèle de texte  
  
1. Générez la solution et commencer à l’exécuter dans le débogueur. (Sur le **Build** menu, cliquez sur **régénérer la Solution**, puis, dans le **déboguer** menu, cliquez sur **démarrer le débogage**.) Une nouvelle instance de Visual Studio ouvre le projet de débogage.  
  
2. Ajoutez un fichier texte nommé `DebugTest.tt` au projet de débogage.  
  
3. Assurez-vous que le **un outil personnalisé** a la valeur de propriété de DebugTest.tt `TextTemplatingFileGenerator`.  
  
## <a name="debugging-directives-that-access-a-model-from-a-text-template"></a>Débogage des directives qui accèdent à un modèle à partir d’un modèle de texte  
 Avant que vous pouvez accéder à un modèle à partir des instructions et expressions dans un modèle de texte, vous devez d’abord appeler un processeur de directive généré. Appeler le processeur de directive généré rend les classes dans votre modèle disponibles pour le code de modèle de texte en tant que propriétés. Pour plus d’informations, consultez [l’accès à des modèles à partir de modèles de texte](../modeling/accessing-models-from-text-templates.md).  
  
 Dans les procédures suivantes, vous allez déboguer un nom de directive incorrect et un nom de propriété incorrecte.  
  
#### <a name="to-debug-an-incorrect-directive-name"></a>Pour déboguer un nom de directive incorrect  
  
1. Remplacez le code dans DebugTest.tt par le code suivant :  
  
    > [!NOTE]
    > Le code contient une erreur. Vous risquez d’introduire l’erreur pour la déboguer.  
  
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
  
2. Dans **l’Explorateur de solutions**, DebugTest.tt d’avec le bouton droit, puis cliquez sur **exécuter un outil personnalisé**.  
  
     Le **liste d’erreurs** fenêtre affiche cette erreur :  
  
     **Le processeur nommé 'DebuggingTestLanguageDirectiveProcessor' ne prend pas en charge la directive nommée 'modelRoot'. La transformation ne sera pas exécutée.**  
  
     Dans ce cas, l’appel de directive contient un nom de directive incorrect. Vous avez spécifié `modelRoot` comme le nom de la directive, mais le nom de directive correct est `DebuggingTestLanguage`.  
  
3. Double-cliquez sur l’erreur dans le **liste d’erreurs** fenêtre pour accéder au code.  
  
4. Pour corriger le code, remplacez le nom de la directive par `DebuggingTestLanguage`.  
  
     La modification est mis en surbrillance.  
  
    ```csharp  
    <#@ DebuggingTestLanguage processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=ExampleModel" #>  
    ```  
  
    ```vb  
    <#@ DebuggingTestLanguage processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=ExampleModel" #>  
    ```  
  
5. Dans **l’Explorateur de solutions**, DebugTest.tt d’avec le bouton droit, puis cliquez sur **exécuter un outil personnalisé**.  
  
     Maintenant, le système transforme le modèle de texte et génère le fichier de sortie correspondant. Vous ne verrez pas toutes les erreurs dans le **liste d’erreurs** fenêtre.  
  
#### <a name="to-debug-an-incorrect-property-name"></a>Pour déboguer un nom de propriété incorrecte  
  
1. Remplacez le code dans DebugTest.tt par le code suivant :  
  
    > [!NOTE]
    > Le code contient une erreur. Vous risquez d’introduire l’erreur pour la déboguer.  
  
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
  
2. Dans le **l’Explorateur de solutions**, DebugTest.tt d’avec le bouton droit, puis cliquez sur **exécuter un outil personnalisé**.  
  
     Le **liste d’erreurs** fenêtre apparaît et affiche l’un de ces erreurs :  
  
     (C#)  
  
     **Compilation de la transformation : Microsoft.VisualStudio.TextTemplating\<GUID>. GeneratedTextTransformation' ne contient pas d’une définition pour 'ExampleModel'**  
  
     (Visual Basic)  
  
     **Compilation de la transformation : 'ExampleModel' n’est pas un membre de ' Microsoft.VisualStudio.TextTemplating\<GUID >. GeneratedTextTransformation'.**  
  
     Dans ce cas, le code de modèle de texte contient un nom de propriété incorrecte. Vous avez spécifié `ExampleModel` en tant que le nom de propriété, mais la propriété correcte est nom `LibraryModel`. Vous pouvez rechercher le nom de la propriété appropriée dans l’offre de paramètre, comme indiqué dans le code suivant :  
  
    ```  
    <#@ DebuggingTestLanguage processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=LibraryModel" #>  
    ```  
  
3. Double-cliquez sur l’erreur dans la fenêtre liste d’erreurs pour accéder au code.  
  
4. Pour corriger le code, remplacez le nom de propriété par `LibraryModel` dans le code de modèle de texte.  
  
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
  
5. Dans **l’Explorateur de solutions**, DebugTest.tt d’avec le bouton droit, puis cliquez sur **exécuter un outil personnalisé**.  
  
     Maintenant, le système transforme le modèle de texte et génère le fichier de sortie correspondant. Vous ne verrez pas toutes les erreurs dans le **liste d’erreurs** fenêtre.
