---
title: 'Comment : Joindre les vues aux données documentaires ( Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - attach views to document data
ms.assetid: f92c0838-45be-42b8-9c55-713e9bb8df07
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1d8bd586a9d67996389f3cb6a2b0f13f0afec3bd
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711089"
---
# <a name="how-to-attach-views-to-document-data"></a>Comment : Joindre les vues pour documenter les données
Si vous avez une nouvelle vue de document, vous pouvez être en mesure de l’attacher à un objet de données de document existant.

## <a name="to-determine-if-you-can-attach-a-view-to-an-existing-document-data-object"></a>Pour déterminer si vous pouvez joindre une vue à un objet de données de document existant

1. Implémentez <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>.

2. Dans votre `IVsEditorFactory::CreateEditorInstance`implémentation , faites appel `QueryInterface` à l’objet de données de document existant lorsque l’IDE appelle votre `CreateEditorInstance` implémentation.

    L’appel `QueryInterface` vous permet d’examiner l’objet `punkDocDataExisting` de données de document existant, qui est spécifié dans le paramètre.

    Les interfaces exactes que vous devez interroger, cependant, dépend de l’éditeur qui ouvre le document, comme indiqué dans l’étape 4.

3. Si vous ne trouvez pas les interfaces appropriées sur l’objet de données de document existant, retournez un code d’erreur à votre éditeur indiquant que l’objet de données de document est incompatible avec votre éditeur.

    Dans la mise en <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>œuvre de l’IDE , une boîte de message vous informe que le document est ouvert dans un autre éditeur et demande si vous voulez le fermer.

4. Si vous fermez ce document, Visual Studio appelle votre usine d’éditeurs pour une deuxième fois. Sur cet appel, le `DocDataExisting` paramètre est égal à NULL. Votre implémentation d’usine d’éditeur peut alors ouvrir l’objet de données de document dans votre propre éditeur.

   > [!NOTE]
   > Pour déterminer si vous pouvez travailler avec un objet de données de document existant, vous [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] pouvez également utiliser la connaissance privée de la mise en œuvre de l’interface en jetant un pointeur à la classe réelle de votre implémentation privée. Par exemple, tous les `IVsPersistFileFormat`éditeurs standard <xref:Microsoft.VisualStudio.OLE.Interop.IPersist>implémenter , qui hérite de . Ainsi, vous `QueryInterface` pouvez <xref:Microsoft.VisualStudio.OLE.Interop.IPersist.GetClassID%2A>demander, et si l’ID de classe sur l’objet de données de document existant correspond à l’ID de classe de votre implémentation, alors vous pouvez travailler avec l’objet de données de document.

## <a name="robust-programming"></a>Programmation fiable
 Lorsque Visual Studio appelle <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> votre implémentation de la méthode, elle `punkDocDataExisting` transmet un pointeur à l’objet de données de document existant dans le paramètre, si l’on existe. Examinez l’objet `punkDocDataExisting` de données documentaires retournés pour déterminer si l’objet de données de document est approprié pour votre éditeur tel qu’indiqué dans la note à l’étape 4 de la procédure dans ce sujet. Si cela est approprié, alors votre usine d’éditeur devrait fournir une deuxième vue pour les données telles qu’elles sont décrites dans [Support plusieurs vues de documents](../extensibility/supporting-multiple-document-views.md). Si ce n’est pas le cas, il devrait afficher un message d’erreur approprié.

## <a name="see-also"></a>Voir aussi
- [Prendre en charge plusieurs vues de documents](../extensibility/supporting-multiple-document-views.md)
- [Données documentaires et vue de documents dans les éditeurs personnalisés](../extensibility/document-data-and-document-view-in-custom-editors.md)
