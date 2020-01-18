---
title: Accéder à l’objet DTE à partir d’une extension d’éditeur
ms.date: 04/24/2019
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - getting the DTE object
ms.assetid: c1f40bab-c6ec-45b0-8333-ea5ceb02a39d
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d023359412b423c9c12d7c7d8a37e79571cbc11a
ms.sourcegitcommit: e3c3d2b185b689c5e32ab4e595abc1ac60b6b9a8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/18/2020
ms.locfileid: "76269084"
---
# <a name="walkthrough-access-the-dte-object-from-an-editor-extension"></a>Procédure pas à pas : accès à l’objet DTE à partir d’une extension d’éditeur

Dans les VSPackages, vous pouvez récupérer l’objet DTE en appelant la méthode <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> avec le type de l’objet DTE. Dans les extensions Managed Extensibility Framework (MEF), vous pouvez importer des <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider>, puis appeler la méthode <xref:Microsoft.VisualStudio.Shell.ServiceProvider.GetService%2A> à l’aide d’un type de <xref:EnvDTE.DTE>.

## <a name="prerequisites"></a>Prerequisites

Pour suivre cette procédure pas à pas, vous devez installer le Kit de développement logiciel (SDK) Visual Studio. Pour plus d’informations, consultez [Kit de développement logiciel (SDK) Visual Studio](../extensibility/visual-studio-sdk.md).

## <a name="get-the-dte-object"></a>Obtient l'objet DTE.

1. Créez un C# projet VSIX et nommez-le **DTETest**. Ajoutez un modèle d’élément de **classifieur d’éditeur** et nommez-le **DTETest**.

   Pour plus d’informations, consultez [créer une extension avec un modèle d’élément d’éditeur](../extensibility/creating-an-extension-with-an-editor-item-template.md).

::: moniker range=">=vs-2019"

2. Ajoutez les références d’assembly suivantes au projet :

    - Microsoft.VisualStudio.Shell.Framework
    - Microsoft.VisualStudio.Shell.Immutable.10.0

3. Dans le fichier *DTETestProvider.cs* , ajoutez les directives `using` suivantes :

    ```csharp
    using EnvDTE;
    using Microsoft.VisualStudio.Shell;
    ```

4. Dans la classe `DTETestProvider`, importez un <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider>.

    ```csharp
    [Import]
    internal SVsServiceProvider ServiceProvider = null;
    ```

5. Dans la méthode `GetClassifier()`, ajoutez le code suivant avant l’instruction `return` :

    ```csharp
   ThreadHelper.ThrowIfNotOnUIThread();
   DTE dte = (DTE)ServiceProvider.GetService(typeof(DTE));
   ```

::: moniker-end

::: moniker range="vs-2017"

2. Ajoutez les références d’assembly suivantes au projet :

   - EnvDTE
   - Microsoft.VisualStudio.Shell.Framework

3. Dans le fichier *DTETestProvider.cs* , ajoutez les directives `using` suivantes :

    ```csharp
    using EnvDTE;
    using Microsoft.VisualStudio.Shell;
    ```

4. Dans la classe `DTETestProvider`, importez un <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider>.

    ```csharp
    [Import]
    internal SVsServiceProvider ServiceProvider = null;
    ```

5. Dans la méthode `GetClassifier()`, ajoutez le code suivant avant l’instruction `return` :

    ```csharp
   DTE dte = (DTE)ServiceProvider.GetService(typeof(DTE));
   ```

::: moniker-end

## <a name="see-also"></a>Voir aussi

- [Points d’extension du service de langage et de l’éditeur](../extensibility/language-service-and-editor-extension-points.md)
- [Lancer Visual Studio à l’aide de DTE](launch-visual-studio-dte.md)
