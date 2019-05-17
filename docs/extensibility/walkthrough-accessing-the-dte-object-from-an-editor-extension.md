---
title: Accéder à l’objet DTE à partir d’une extension de l’éditeur
ms.date: 04/24/2019
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - getting the DTE object
ms.assetid: c1f40bab-c6ec-45b0-8333-ea5ceb02a39d
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9c3e21ea3d05350a59d62fc9da9e0387f072ec16
ms.sourcegitcommit: 62f42113ae4dae1ddfff1c4e02445acc09913445
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/29/2019
ms.locfileid: "64878198"
---
# <a name="walkthrough-access-the-dte-object-from-an-editor-extension"></a>Procédure pas à pas : Accéder à l’objet DTE à partir d’une extension de l’éditeur

Dans les VSPackages, vous pouvez obtenir l’objet DTE en appelant le <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> méthode avec le type de l’objet DTE. Dans les extensions Managed Extensibility Framework (MEF), vous pouvez importer <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> , puis appelez le <xref:Microsoft.VisualStudio.Shell.ServiceProvider.GetService%2A> méthode avec un type de <xref:EnvDTE.DTE>.

## <a name="prerequisites"></a>Prérequis

Pour suivre cette procédure pas à pas, vous devez installer le Kit de développement logiciel (SDK) Visual Studio. Pour plus d’informations, consultez [Visual Studio SDK](../extensibility/visual-studio-sdk.md).

## <a name="get-the-dte-object"></a>Obtient l’objet DTE

1. Créer un C# VSIX de projet et nommez-le **DTETest**. Ajouter un **classifieur d’éditeur** modèle d’élément et nommez-le **DTETest**.

   Pour plus d’informations, consultez [créer une extension avec un éditeur de modèle d’élément](../extensibility/creating-an-extension-with-an-editor-item-template.md).

::: moniker range=">=vs-2019"

2. Ajoutez la référence d’assembly suivantes au projet :

    - Microsoft.VisualStudio.Shell.Immutable.10.0

3. Dans le *DTETestProvider.cs* de fichier, ajoutez le code suivant `using` directives :

    ```csharp
    using EnvDTE;
    using Microsoft.VisualStudio.Shell;
    ```

4. Dans le `DTETestProvider` class, importer un <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider>.

    ```csharp
    [Import]
    internal SVsServiceProvider ServiceProvider = null;
    ```

5. Dans le `GetClassifier()` (méthode), ajoutez le code suivant avant la `return` instruction :

    ```csharp
   ThreadHelper.ThrowIfNotOnUIThread();
   DTE dte = (DTE)ServiceProvider.GetService(typeof(DTE));
   ```

::: moniker-end

::: moniker range="vs-2017"

2. Ajoutez les références d’assembly suivantes au projet :

   - EnvDTE
   - Microsoft.VisualStudio.Shell.Framework

3. Dans le *DTETestProvider.cs* de fichier, ajoutez le code suivant `using` directives :

    ```csharp
    using EnvDTE;
    using Microsoft.VisualStudio.Shell;
    ```

4. Dans le `DTETestProvider` class, importer un <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider>.

    ```csharp
    [Import]
    internal SVsServiceProvider ServiceProvider = null;
    ```

5. Dans le `GetClassifier()` (méthode), ajoutez le code suivant avant la `return` instruction :

    ```csharp
   DTE dte = (DTE)ServiceProvider.GetService(typeof(DTE));
   ```

::: moniker-end

## <a name="see-also"></a>Voir aussi

- [Points d’extension éditeur et le service de langage](../extensibility/language-service-and-editor-extension-points.md)
- [Lancez Visual Studio à l’aide de DTE](launch-visual-studio-dte.md)