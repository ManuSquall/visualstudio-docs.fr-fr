---
title: "Proc&#233;dure pas &#224; pas&#160;: Acc&#232;s &#224; l’objet DTE &#224; partir d’une Extension de l’&#233;diteur | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "éditeurs (Visual Studio SDK), nouvelles - mise en route de l’objet DTE"
ms.assetid: c1f40bab-c6ec-45b0-8333-ea5ceb02a39d
caps.latest.revision: 22
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 22
---
# Proc&#233;dure pas &#224; pas&#160;: Acc&#232;s &#224; l’objet DTE &#224; partir d’une Extension de l’&#233;diteur
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Dans les packages VS, vous pouvez obtenir l’objet DTE en appelant le <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> méthode avec le type de l’objet DTE. Dans les extensions de Managed Extensibility Framework \(MEF\), vous pouvez importer <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> puis appelez le <xref:Microsoft.VisualStudio.Shell.ServiceProvider.GetService%2A> méthode avec un type de <xref:EnvDTE.DTE>.  
  
## Composants requis  
 Pour suivre cette procédure pas à pas, vous devez installer le Kit de développement logiciel \(SDK\) Visual Studio. Pour plus d'informations, consultez [Kit de développement logiciel Visual Studio](../extensibility/visual-studio-sdk.md).  
  
## Obtention de l’objet DTE  
  
#### Pour obtenir l’objet DTE à partir du fournisseur  
  
1.  Créez un projet VSIX c\# nommé `DTETest`. Ajouter un modèle d’élément éditeur classifieur et nommez\-le `DTETest`. Pour plus d'informations, consultez [Création d'une Extension avec un éditeur de modèle d'élément](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
2.  Ajoutez les références d’assembly suivantes au projet :  
  
    -   EnvDTE  
  
    -   EnvDTE80  
  
    -   Microsoft.VisualStudio.Shell.Immutable.10.0  
  
3.  Accédez au fichier DTETest.cs et ajoutez le code suivant `using` directives :  
  
    ```c#  
    using EnvDTE;  
    using EnvDTE80;  
    using Microsoft.VisualStudio.Shell;  
  
    ```  
  
4.  Dans la `GetDTEProvider` classe, importez une <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider>.  
  
    ```c#  
    [Import]  
    internal SVsServiceProvider ServiceProvider = null;  
  
    ```  
  
5.  Dans la méthode `GetClassifier()`, ajoutez le code suivant.  
  
    ```c#  
    DTE dte = (DTE)ServiceProvider.GetService(typeof(DTE));  
  
    ```  
  
6.  Si vous devez utiliser le <xref:EnvDTE80.DTE2> interface, vous pouvez effectuer un cast de l’objet DTE.  
  
## Voir aussi  
 [Service de langage et les Points d’Extension Éditeur](../extensibility/language-service-and-editor-extension-points.md)