---
title: 'Comment : attacher des vues à des données de document | Microsoft Docs'
description: Vous pourrez peut-être attacher une nouvelle vue de document à un objet de données de document existant. Utilisez cette procédure pour déterminer si vous pouvez attacher la vue.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- editors [Visual Studio SDK], custom - attach views to document data
ms.assetid: f92c0838-45be-42b8-9c55-713e9bb8df07
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1e044ecbf2309d4d858c16afbdddc130b4661005
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "96994184"
---
# <a name="how-to-attach-views-to-document-data"></a>Comment : attacher des vues à des données de document
Si vous disposez d’une nouvelle vue de document, vous pouvez l’attacher à un objet de données de document existant.

## <a name="to-determine-if-you-can-attach-a-view-to-an-existing-document-data-object"></a>Pour déterminer si vous pouvez attacher une vue à un objet de données de document existant

1. Implémentez <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>.

2. Dans votre implémentation de `IVsEditorFactory::CreateEditorInstance` , appelez `QueryInterface` sur l’objet de données de document existant lorsque l’IDE appelle votre `CreateEditorInstance` implémentation.

    L’appel de `QueryInterface` vous permet d’examiner l’objet de données de document existant, qui est spécifié dans le `punkDocDataExisting` paramètre.

    Toutefois, les interfaces précises que vous devez interroger dépendent de l’éditeur qui ouvre le document, comme indiqué à l’étape 4.

3. Si vous ne trouvez pas les interfaces appropriées sur l’objet de données de document existant, renvoyez un code d’erreur à votre éditeur pour indiquer que l’objet de données de document est incompatible avec votre éditeur.

    Dans l’implémentation de l’IDE de <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> , une boîte de message vous informe que le document est ouvert dans un autre éditeur et vous demande si vous voulez le fermer.

4. Si vous fermez ce document, Visual Studio appelle la fabrique d’éditeur pour la deuxième fois. Sur cet appel, le `DocDataExisting` paramètre est égal à null. Votre implémentation de fabrique d’éditeur peut ensuite ouvrir l’objet de données de document dans votre propre éditeur.

   > [!NOTE]
   > Pour déterminer si vous pouvez utiliser un objet de données de document existant, vous pouvez également utiliser une connaissance privée de l’implémentation de l’interface en convertissant un pointeur vers la [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] classe réelle de votre implémentation privée. Par exemple, tous les éditeurs standard implémentent `IVsPersistFileFormat` , qui hérite de <xref:Microsoft.VisualStudio.OLE.Interop.IPersist> . Par conséquent, vous pouvez appeler `QueryInterface` pour <xref:Microsoft.VisualStudio.OLE.Interop.IPersist.GetClassID%2A> et, si l’ID de classe de l’objet de données de document existant correspond à l’ID de classe de votre implémentation, vous pouvez utiliser l’objet de données de document.

## <a name="robust-programming"></a>Programmation fiable
 Lorsque Visual Studio appelle votre implémentation de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> méthode, il passe un pointeur vers l’objet de données de document existant dans le `punkDocDataExisting` paramètre, s’il en existe un. Examinez l’objet de données de document retourné dans `punkDocDataExisting` pour déterminer si l’objet de données de document est approprié à votre éditeur, comme indiqué dans la remarque à l’étape 4 de la procédure de cette rubrique. Si cela est approprié, votre fabrique d’éditeur doit fournir une deuxième vue pour les données, comme indiqué dans [prendre en charge les vues de documents multiples](../extensibility/supporting-multiple-document-views.md). Si ce n’est pas le cas, il doit afficher un message d’erreur approprié.

## <a name="see-also"></a>Voir aussi
- [Prendre en charge plusieurs vues de documents](../extensibility/supporting-multiple-document-views.md)
- [Données de document et vue de document dans les éditeurs personnalisés](../extensibility/document-data-and-document-view-in-custom-editors.md)
