---
title: Accédez à l’objet DTE à partir d’une extension de l’éditeur
ms.date: 04/24/2019
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - getting the DTE object
ms.assetid: c1f40bab-c6ec-45b0-8333-ea5ceb02a39d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e37bdb21b7c8132f0dfb166d19e03d36e838245d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697659"
---
# <a name="walkthrough-access-the-dte-object-from-an-editor-extension"></a>Procédure pas à pas : Accédez à l’objet DTE à partir d’une extension de l’éditeur

Dans VSPackages, vous pouvez obtenir l’objet DTE en appelant la <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> méthode avec le type de l’objet DTE. Dans les extensions du Cadre d’Extégabilité Gérée (MEF), vous pouvez importer <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> puis appeler la <xref:Microsoft.VisualStudio.Shell.ServiceProvider.GetService%2A> méthode avec un type de <xref:EnvDTE.DTE>.

## <a name="prerequisites"></a>Prérequis

Pour suivre cette procédure pas à pas, vous devez installer le Kit de développement logiciel (SDK) Visual Studio. Pour plus d’informations, voir [Visual Studio SDK](../extensibility/visual-studio-sdk.md).

## <a name="get-the-dte-object"></a>Obtient l'objet DTE.

1. Créez un projet VSIX C ET nommez-le **DTETest**. Ajoutez un modèle d’élément **Classificateur d’éditeur** et nommez-le **DTETest**.

   Pour plus d’informations, voir [Créer une extension avec un modèle d’élément d’éditeur](../extensibility/creating-an-extension-with-an-editor-item-template.md).

::: moniker range=">=vs-2019"

2. Ajoutez les références d’assemblage suivantes au projet :

    - Microsoft.VisualStudio.Shell.Framework (en anglais seulement)
    - Microsoft.VisualStudio.Shell.Immutable.10.0

3. Dans le fichier *DTETestProvider.cs,* ajoutez `using` les directives suivantes :

    ```csharp
    using EnvDTE;
    using Microsoft.VisualStudio.Shell;
    ```

4. Dans `DTETestProvider` la classe, <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider>importer un .

    ```csharp
    [Import]
    internal SVsServiceProvider ServiceProvider = null;
    ```

5. Dans `GetClassifier()` la méthode, ajoutez le `return` code suivant avant la déclaration :

    ```csharp
   ThreadHelper.ThrowIfNotOnUIThread();
   DTE dte = (DTE)ServiceProvider.GetService(typeof(DTE));
   ```

::: moniker-end

::: moniker range="vs-2017"

2. Ajoutez les références d’assemblage suivantes au projet :

   - EnvDTE
   - Microsoft.VisualStudio.Shell.Framework (en anglais seulement)

3. Dans le fichier *DTETestProvider.cs,* ajoutez `using` les directives suivantes :

    ```csharp
    using EnvDTE;
    using Microsoft.VisualStudio.Shell;
    ```

4. Dans `DTETestProvider` la classe, <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider>importer un .

    ```csharp
    [Import]
    internal SVsServiceProvider ServiceProvider = null;
    ```

5. Dans `GetClassifier()` la méthode, ajoutez le `return` code suivant avant la déclaration :

    ```csharp
   DTE dte = (DTE)ServiceProvider.GetService(typeof(DTE));
   ```

::: moniker-end

## <a name="see-also"></a>Voir aussi

- [Service linguistique et points d’extension de l’éditeur](../extensibility/language-service-and-editor-extension-points.md)
- [Lancer Visual Studio à l’aide de DTE](launch-visual-studio-dte.md)
