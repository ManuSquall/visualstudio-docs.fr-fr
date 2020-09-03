---
title: 'Procédure pas à pas : accès à l’objet DTE à partir d’une extension d’éditeur | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - getting the DTE object
ms.assetid: c1f40bab-c6ec-45b0-8333-ea5ceb02a39d
caps.latest.revision: 23
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4b14b59465b94ddd0a09748f0e309166bf3d4114
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68148873"
---
# <a name="walkthrough-accessing-the-dte-object-from-an-editor-extension"></a>Procédure pas à pas : accès à l’objet DTE à partir d’une extension de l’éditeur
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dans les VSPackages, vous pouvez récupérer l’objet DTE en appelant la <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> méthode avec le type de l’objet DTE. Dans les extensions Managed Extensibility Framework (MEF), vous pouvez importer, <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> puis appeler la <xref:Microsoft.VisualStudio.Shell.ServiceProvider.GetService%2A> méthode avec un type <xref:EnvDTE.DTE> .  
  
## <a name="prerequisites"></a>Prérequis  
 Pour suivre cette procédure pas à pas, vous devez installer le Kit de développement logiciel (SDK) Visual Studio. Pour plus d’informations, consultez [Kit de développement logiciel (SDK) Visual Studio](../extensibility/visual-studio-sdk.md).  
  
## <a name="getting-the-dte-object"></a>Obtention de l’objet DTE  
  
#### <a name="to-get-the-dte-object-from-the-serviceprovider"></a>Pour récupérer l’objet DTE à partir du ServiceProvider  
  
1. Créez un projet VSIX C# nommé `DTETest` . Ajoutez un modèle d’élément de classifieur d’éditeur et nommez-le `DTETest` . Pour plus d’informations, consultez [création d’une extension avec un modèle d’élément d’éditeur](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
2. Ajoutez les références d’assembly suivantes au projet :  
  
    - EnvDTE  
  
    - EnvDTE80  
  
    - Microsoft. VisualStudio. Shell. immuable. 10.0  
  
3. Accédez au fichier DTETest.cs et ajoutez les `using` directives suivantes :  
  
    ```csharp  
    using EnvDTE;  
    using EnvDTE80;  
    using Microsoft.VisualStudio.Shell;  
  
    ```  
  
4. Dans la `GetDTEProvider` classe, importez un <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> .  
  
    ```csharp  
    [Import]  
    internal SVsServiceProvider ServiceProvider = null;  
  
    ```  
  
5. Dans la méthode `GetClassifier()`, ajoutez le code suivant.  
  
    ```csharp  
    DTE dte = (DTE)ServiceProvider.GetService(typeof(DTE));  
  
    ```  
  
6. Si vous devez utiliser l' <xref:EnvDTE80.DTE2> interface, vous pouvez effectuer un cast de l’objet DTE vers celui-ci.  
  
## <a name="see-also"></a>Voir aussi  
 [Points d’extension du service de langage et de l’éditeur](../extensibility/language-service-and-editor-extension-points.md)
