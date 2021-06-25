---
title: Accéder à l’objet DTE à partir d’une extension d’éditeur
description: Découvrez comment accéder à l’objet DTE à partir d’une extension d’éditeur à l’aide de l’exemple de code dans cette procédure pas à pas.
ms.custom: SEO-VS-2020
ms.date: 04/24/2019
ms.topic: tutorial
helpviewer_keywords:
- editors [Visual Studio SDK], new - getting the DTE object
ms.assetid: c1f40bab-c6ec-45b0-8333-ea5ceb02a39d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 094a37960fa5b32d018eebe3becee4fde43cc392
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112905122"
---
# <a name="walkthrough-access-the-dte-object-from-an-editor-extension"></a>Procédure pas à pas : accès à l’objet DTE à partir d’une extension d’éditeur

Dans les VSPackages, vous pouvez récupérer l’objet DTE en appelant la <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> méthode avec le type de l’objet DTE. Dans les extensions Managed Extensibility Framework (MEF), vous pouvez importer, <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> puis appeler la <xref:Microsoft.VisualStudio.Shell.ServiceProvider.GetService%2A> méthode avec un type <xref:EnvDTE.DTE> .

## <a name="prerequisites"></a>Prérequis

Pour suivre cette procédure pas à pas, vous devez installer le Kit de développement logiciel (SDK) Visual Studio. Pour plus d’informations, consultez [Kit de développement logiciel (SDK) Visual Studio](../extensibility/visual-studio-sdk.md).

## <a name="get-the-dte-object"></a>Obtient l'objet DTE.

1. Créez un projet VSIX C# et nommez-le **DTETest**. Ajoutez un modèle d’élément de **classifieur d’éditeur** et nommez-le **DTETest**.

   Pour plus d’informations, consultez [créer une extension avec un modèle d’élément d’éditeur](../extensibility/creating-an-extension-with-an-editor-item-template.md).

::: moniker range=">=vs-2019"

2. Ajoutez les références d’assembly suivantes au projet :

    - Microsoft. VisualStudio. Shell. Framework
    - Microsoft. VisualStudio. Shell. immuable. 10.0

3. Dans le fichier *DTETestProvider. cs* , ajoutez les `using` directives suivantes :

    ```csharp
    using EnvDTE;
    using Microsoft.VisualStudio.Shell;
    ```

4. Dans la `DTETestProvider` classe, importez un <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> .

    ```csharp
    [Import]
    internal SVsServiceProvider ServiceProvider = null;
    ```

5. Dans la `GetClassifier()` méthode, ajoutez le code suivant avant l' `return` instruction :

    ```csharp
   ThreadHelper.ThrowIfNotOnUIThread();
   DTE dte = (DTE)ServiceProvider.GetService(typeof(DTE));
   ```

::: moniker-end

::: moniker range="vs-2017"

2. Ajoutez les références d’assembly suivantes au projet :

   - EnvDTE
   - Microsoft. VisualStudio. Shell. Framework

3. Dans le fichier *DTETestProvider. cs* , ajoutez les `using` directives suivantes :

    ```csharp
    using EnvDTE;
    using Microsoft.VisualStudio.Shell;
    ```

4. Dans la `DTETestProvider` classe, importez un <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> .

    ```csharp
    [Import]
    internal SVsServiceProvider ServiceProvider = null;
    ```

5. Dans la `GetClassifier()` méthode, ajoutez le code suivant avant l' `return` instruction :

    ```csharp
   DTE dte = (DTE)ServiceProvider.GetService(typeof(DTE));
   ```

::: moniker-end

## <a name="see-also"></a>Voir aussi

- [Points d’extension du service de langage et de l’éditeur](../extensibility/language-service-and-editor-extension-points.md)
- [Lancer Visual Studio à l’aide de DTE](launch-visual-studio-dte.md)
