---
title: Données de document et vue de document dans les éditeurs personnalisés | Microsoft Docs
description: En savoir plus sur les composants d’un éditeur personnalisé, qui sont l’objet de données de document et l’objet de vue de document.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - document data and document view
ms.assetid: 71eea623-f566-4feb-84cd-ca1ba71bc493
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 391bec513f1f6d32d7ff2f87d70abdbf491ab8be
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105091238"
---
# <a name="document-data-and-document-view-in-custom-editors"></a>Données de document et vue de document dans les éditeurs personnalisés
Un éditeur personnalisé se compose de deux parties : un objet de données de document et un objet de vue de document. Comme les noms le suggèrent, l’objet de données de document représente les données textuelles à afficher. De même, l’objet de vue de document (ou « View ») représente une ou plusieurs fenêtres dans lesquelles afficher l’objet de données de document.

## <a name="document-data-object"></a>Objet de données de document
 Un objet de données de document est une représentation de données de texte dans la mémoire tampon de texte. Il s’agit d’un objet COM qui stocke le texte du document et d’autres informations. L’objet de données de document gère également la persistance des documents et active plusieurs vues de ses données. Pour plus d'informations, consultez la rubrique

 <xref:EnvDTE80.Window2.DocumentData%2A> et les [fenêtres de document](../extensibility/internals/document-windows.md).

 Les éditeurs et les concepteurs personnalisés peuvent choisir d’utiliser l' <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> objet ou leur propre mémoire tampon personnalisée. <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> suit le modèle d’incorporation simplifié pour un éditeur standard, prend en charge plusieurs vues et fournit des interfaces d’événements qui sont utilisées pour gérer plusieurs vues.

## <a name="document-view-object"></a>Objet de vue de document
 Une fenêtre qui affiche le code et un autre texte est appelée vue de document ou vue. Lorsque vous créez un éditeur, vous pouvez choisir une vue unique, dans laquelle le texte est affiché dans une seule fenêtre. Ou vous pouvez choisir une vue multiple, dans laquelle le texte est affiché dans plusieurs fenêtres. Votre choix dépend de votre application. Par exemple, si vous avez besoin d’une modification côte à côte, vous devez choisir affichage multiple. Chaque vue est associée à une entrée dans la table de documents en cours d’exécution de l’environnement de développement intégré (IDE) (RDT). Les fenêtres d’affichage appartiennent à un projet ou à un <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> objet.

 Si votre éditeur prend en charge plusieurs vues d’un objet de données de document, les données de votre document et les objets de vue de document doivent être séparés. Dans le cas contraire, ils peuvent être regroupés. Pour plus d’informations, consultez [prendre en charge plusieurs vues de documents](../extensibility/supporting-multiple-document-views.md).

 L’IDE avertit les affichages des événements (par exemple, lorsqu’une solution contenant un document est fermée) en faisant correspondre un identificateur d’élément (ItemID) pour chaque entrée dans la table de document en cours d’exécution. Pour plus d’informations, consultez exécution de la [table des documents](../extensibility/internals/running-document-table.md).

 Il existe deux options pour créer une vue d’un éditeur personnalisé. L’un est le modèle d’activation sur place, où la vue est hébergée dans une fenêtre à l’aide d’un contrôle ActiveX ou d’un objet de données de document. Le deuxième est le modèle d’incorporation simplifié, où la vue est hébergée par [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] et <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> est implémentée pour gérer les commandes de fenêtre. Pour plus d’informations sur le modèle d’activation sur place, consultez [activation sur place](/previous-versions/visualstudio/visual-studio-2015/misc/in-place-activation?preserve-view=true&view=vs-2015). Pour plus d’informations sur le modèle d’incorporation simplifié, consultez [incorporation simplifiée](../extensibility/simplified-embedding.md).

## <a name="see-also"></a>Voir aussi

- [Prendre en charge plusieurs vues de documents](../extensibility/supporting-multiple-document-views.md)
- [Incorporation simplifiée](../extensibility/simplified-embedding.md)
- [Comment : attacher des vues à des données de document](../extensibility/how-to-attach-views-to-document-data.md)
- [Gestion des titulaires de verrous de documents](../extensibility/document-lock-holder-management.md)
- [Vues à onglet unique et à plusieurs onglets](../extensibility/single-and-multi-tab-views.md)
- [Enregistrer un document standard](../extensibility/internals/saving-a-standard-document.md)
- [Persistance et table de document en cours d’exécution](../extensibility/internals/persistence-and-the-running-document-table.md)
- [Déterminer quel éditeur ouvre un fichier dans un projet](../extensibility/internals/determining-which-editor-opens-a-file-in-a-project.md)