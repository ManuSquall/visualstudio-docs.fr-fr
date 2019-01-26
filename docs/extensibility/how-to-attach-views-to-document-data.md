---
title: 'Procédure : Joindre des vues de données de document | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - attach views to document data
ms.assetid: f92c0838-45be-42b8-9c55-713e9bb8df07
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1e9aa7b4a36f1d3a073bb13188954a1159012797
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "55010036"
---
# <a name="how-to-attach-views-to-document-data"></a>Procédure : Joindre des vues de données de document
Si vous avez une nouvelle vue de document, vous pourrez peut-être joindre à un objet de données de document existant.  
  
## <a name="to-determine-if-you-can-attach-a-view-to-an-existing-document-data-object"></a>Pour déterminer si vous pouvez attacher une vue à un objet de données de document existant  
  
1. Implémentez <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>.  
  
2. Dans votre implémentation de `IVsEditorFactory::CreateEditorInstance`, appelez `QueryInterface` sur l’objet de données de document existant lors de l’IDE appelle votre `CreateEditorInstance` implémentation.  
  
    Appel `QueryInterface` vous permet d’examiner l’objet de données de document existant, ce qui est spécifié dans le `punkDocDataExisting` paramètre.  
  
    Les interfaces exacts, vous devez interroger, dépend toutefois, l’éditeur qui s’ouvre le document, comme indiqué à l’étape 4.  
  
3. Si vous ne trouvez pas les interfaces appropriées sur l’objet de données de document existant, puis renvoie le code d’erreur dans votre éditeur indiquant que l’objet de données est incompatible avec votre éditeur.  
  
    Dans l’implémentation de l’IDE de <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>, une boîte de message vous informe que le document est ouvert dans un autre éditeur et vous demande si vous souhaitez fermer.  
  
4. Si vous fermez ce document, Visual Studio appelle votre fabrique d’éditeur pour une deuxième fois. Sur cet appel, le `DocDataExisting` paramètre est égal à NULL. Votre implémentation de fabrique d’éditeur permettre ensuite ouvrir l’objet de données dans votre propre éditeur.  
  
   > [!NOTE]
   >  Pour déterminer si vous pouvez travailler avec un objet de données de document existant, vous pouvez également utiliser une connaissance privée de l’implémentation d’interface en effectuant un cast d’un pointeur vers le texte réel [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] classe de votre implémentation privée. Par exemple, tous les éditeurs standards implémentent `IVsPersistFileFormat`, qui hérite de <xref:Microsoft.VisualStudio.OLE.Interop.IPersist>. Par conséquent, vous pouvez appeler `QueryInterface` pour <xref:Microsoft.VisualStudio.OLE.Interop.IPersist.GetClassID%2A>, et si l’ID de classe sur l’objet de données de document existant correspond à votre mise en œuvre des ID de classe, puis vous pouvez travailler avec l’objet de données de document.  
  
## <a name="robust-programming"></a>Programmation fiable  
 Lorsque Visual Studio appelle votre implémentation de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> (méthode), il passe à nouveau un pointeur à l’objet de données de document existant dans le `punkDocDataExisting` paramètre, s’il en existe. Examiner l’objet de données de document renvoyé dans `punkDocDataExisting` pour déterminer si l’objet de données est appropriée pour votre éditeur, comme indiqué dans la Remarque à l’étape 4 de la procédure décrite dans cette rubrique. Si c’est approprié, puis votre fabrique d’éditeur doit fournir une deuxième vue pour les données, comme indiqué dans [prendre en charge plusieurs vues de document](../extensibility/supporting-multiple-document-views.md). Si ce n’est pas le cas, puis il doit afficher un message d’erreur approprié.  
  
## <a name="see-also"></a>Voir aussi  
 [Prendre en charge plusieurs vues de document](../extensibility/supporting-multiple-document-views.md)   
 [Données de document et les vues de document dans les éditeurs personnalisés](../extensibility/document-data-and-document-view-in-custom-editors.md)