---
title: 'Procédure pas à pas : Accès à l’objet DTE à partir d’une Extension de l’éditeur | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - getting the DTE object
ms.assetid: c1f40bab-c6ec-45b0-8333-ea5ceb02a39d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8ed4343139b3e59dfba7adc71b1c91cdf01c13db
ms.sourcegitcommit: 56ae5032d99d948aae0548ae318ca2bae97ea962
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/07/2018
ms.locfileid: "39586246"
---
# <a name="walkthrough-accessing-the-dte-object-from-an-editor-extension"></a>Procédure pas à pas : Accès à l’objet DTE à partir d’une extension de l’éditeur
Dans les VSPackages, vous pouvez obtenir l’objet DTE en appelant le <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> méthode avec le type de l’objet DTE. Dans les extensions Managed Extensibility Framework (MEF), vous pouvez importer <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> , puis appelez le <xref:Microsoft.VisualStudio.Shell.ServiceProvider.GetService%2A> méthode avec un type de <xref:EnvDTE.DTE>.  
  
## <a name="prerequisites"></a>Prérequis  
 Pour suivre cette procédure pas à pas, vous devez installer le Kit de développement logiciel (SDK) Visual Studio. Pour plus d’informations, consultez [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
## <a name="getting-the-dte-object"></a>Obtention de l’objet DTE  
  
### <a name="to-get-the-dte-object-from-the-serviceprovider"></a>Pour obtenir de l’objet DTE à partir de ServiceProvider  
  
1.  Créez un projet VSIX c# nommé `DTETest`. Ajouter un modèle d’élément de classifieur d’éditeur et nommez-le `DTETest`. Pour plus d’informations, consultez [créer une extension avec un éditeur de modèle d’élément](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
2.  Ajoutez les références d’assembly suivantes au projet :  
  
    -   EnvDTE  
  
    -   EnvDTE80  
  
    -   Microsoft.VisualStudio.Shell.Immutable.10.0  
  
3.  Accédez à la *DTETest.cs* de fichiers et ajoutez le code suivant `using` directives :  
  
    ```csharp  
    using EnvDTE;  
    using EnvDTE80;  
    using Microsoft.VisualStudio.Shell;  
  
    ```  
  
4.  Dans le `GetDTEProvider` class, importer un <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider>.  
  
    ```csharp  
    [Import]  
    internal SVsServiceProvider ServiceProvider = null;  
  
    ```  
  
5.  Dans la méthode `GetClassifier()`, ajoutez le code suivant.  
  
    ```csharp  
    DTE dte = (DTE)ServiceProvider.GetService(typeof(DTE));  
  
    ```  
  
6.  Si vous devez utiliser le <xref:EnvDTE80.DTE2> interface, vous pouvez effectuer un cast de l’objet DTE.  
  
## <a name="see-also"></a>Voir aussi  
 [Points d’extension éditeur et le service de langage](../extensibility/language-service-and-editor-extension-points.md)