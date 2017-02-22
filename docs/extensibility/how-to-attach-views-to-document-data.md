---
title: "Comment&#160;: joindre des vues de donn&#233;es de document | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "éditeurs (Visual Studio SDK), personnalisés - joindre des vues à des données du document"
ms.assetid: f92c0838-45be-42b8-9c55-713e9bb8df07
caps.latest.revision: 22
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 22
---
# Comment&#160;: joindre des vues de donn&#233;es de document
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Si vous avez une nouvelle vue de document, vous pourrez attacher à un objet de données de document.  
  
### Pour déterminer si vous pouvez attacher un affichage à un objet de données de document  
  
1.  Implémentez <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>.  
  
2.  Dans votre implémentation de `IVsEditorFactory::CreateEditorInstance`, appelez `QueryInterface` sur l’objet de données de document existant lors de l’IDE appelle votre `CreateEditorInstance` mise en œuvre.  
  
     Appel de `QueryInterface` vous permet d’examiner l’objet de données de document existant, ce qui est spécifié dans le `punkDocDataExisting` paramètre.  
  
     Les interfaces exacts, vous devez interroger, dépend toutefois, l’éditeur qui ouvre le document, comme indiqué à l’étape 4.  
  
3.  Si vous ne trouvez pas les interfaces appropriées sur l’objet de données de document existant, puis renvoyer un code d’erreur dans votre éditeur indiquant que l’objet de données de document est incompatible avec votre éditeur.  
  
     Dans l’implémentation de l’IDE de <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>, une boîte de message vous informe que le document est ouvert dans un autre éditeur et vous demande si vous souhaitez fermer.  
  
4.  Si vous fermez ce document, Visual Studio appelle votre fabrique d’éditeur pour la deuxième fois. Dans cet appel, le `DocDataExisting` paramètre est égal à NULL. Votre implémentation de fabrique d’éditeur peut ensuite ouvrir l’objet de données de document dans votre propre éditeur.  
  
    > [!NOTE]
    >  Pour déterminer si vous pouvez travailler avec un objet de données de document, vous pouvez également utiliser des connaissances privé de l’implémentation d’interface en effectuant un cast d’un pointeur vers la valeur réelle [!INCLUDE[vcprvc](../debugger/includes/vcprvc_md.md)] classe de votre implémentation privée. Par exemple, tous les éditeurs standards implémentent `IVsPersistFileFormat`, qui hérite de <xref:Microsoft.VisualStudio.OLE.Interop.IPersist>. Par conséquent, vous pouvez appeler `QueryInterface` pour <xref:Microsoft.VisualStudio.OLE.Interop.IPersist.GetClassID%2A>, et si l’ID de classe sur l’objet de données de document existant correspond à votre mise en œuvre des ID de classe, puis vous pouvez travailler avec l’objet de données de document.  
  
## Programmation fiable  
 Lorsque Visual Studio appelle l’implémentation de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> \(méthode\), elle passe à nouveau un pointeur à l’objet de données de document existant dans le `punkDocDataExisting` paramètre, s’il en existe. Examiner l’objet de données de document renvoyé dans `punkDocDataExisting` pour déterminer si l’objet de données de document est appropriée pour votre éditeur, comme décrit dans la Remarque à l’étape 4 de la procédure dans cette rubrique. Si elle est appropriée, puis votre fabrique d’éditeur doit fournir une deuxième vue pour les données, comme indiqué dans [Prend en charge plusieurs vues de Document](../extensibility/supporting-multiple-document-views.md). Si ce n’est pas le cas, puis il doit afficher un message d’erreur.  
  
## Voir aussi  
 [Prend en charge plusieurs vues de Document](../extensibility/supporting-multiple-document-views.md)   
 [Données de documents et affichage de documents dans les éditeurs personnalisés](../extensibility/document-data-and-document-view-in-custom-editors.md)