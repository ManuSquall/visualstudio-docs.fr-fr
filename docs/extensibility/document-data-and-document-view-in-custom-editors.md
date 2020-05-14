---
title: Données de documents et vue de documents dans les éditeurs personnalisés ( Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - document data and document view
ms.assetid: 71eea623-f566-4feb-84cd-ca1ba71bc493
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 04e89194ff09bc273294246cc25718c999daf70f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712146"
---
# <a name="document-data-and-document-view-in-custom-editors"></a>Données documentaires et vue de documents dans les éditeurs personnalisés
Un éditeur personnalisé se compose de deux parties : un objet de données documentaire et un objet de vue de document. Comme les noms le suggèrent, l’objet de données de document représente les données de texte à afficher. De même, l’objet de vue de document (ou « vue ») représente une ou plusieurs fenêtres dans lesquelles afficher l’objet de données du document.

## <a name="document-data-object"></a>Objet de données documentaires
 Un objet de données de document est une représentation de données du texte dans le tampon de texte. Il s’agit d’un objet COM qui stocke le texte des documents et d’autres informations. L’objet de données de document gère également la persistance des documents et permet de multiples vues de ses données. Pour plus d'informations, consultez la rubrique

 <xref:EnvDTE80.Window2.DocumentData%2A>et [Document Windows](../extensibility/internals/document-windows.md).

 Les éditeurs et les concepteurs personnalisés peuvent choisir d’utiliser l’objet <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> ou leur propre tampon personnalisé. <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>suit le modèle d’intégration simplifié pour un éditeur standard, prend en charge plusieurs vues et fournit des interfaces événementiels qui sont utilisées pour gérer plusieurs vues.

## <a name="document-view-object"></a>Objet de vue de document
 Une fenêtre qui affiche le code et d’autres textes est connue sous le nom de vue ou de vue de document. Lorsque vous créez un éditeur, vous pouvez choisir une seule vue, dans laquelle le texte est affiché en une seule fenêtre. Ou vous pouvez choisir une vue multiple, dans laquelle le texte est affiché dans plus d’une fenêtre. Votre choix dépend de votre application. Par exemple, si vous avez besoin d’un montage côte à côte, vous choisissez une vue multiple. Chaque vue est associée à une entrée dans la table de documents en cours d’exécution (RDT) de l’environnement de développement intégré (RDT). Les fenêtres de vue <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> appartiennent à un projet ou à un objet.

 Si votre éditeur prend en charge plusieurs vues d’un objet de données documentaires, vos données de documents et vos objets de vue de document doivent être séparés. Sinon, ils peuvent être regroupés. Pour plus d’informations, voir [Support plusieurs vues de documents](../extensibility/supporting-multiple-document-views.md).

 L’IDE informe les points de vue sur les événements (par exemple, lorsqu’une solution contenant un document est fermée) en faisant correspondre un identifiant d’élément (ItemID) pour chaque entrée dans la table de document en cours d’exécution. Pour plus d’informations à ce sujet, voir [tableau de document Running](../extensibility/internals/running-document-table.md).

 Il existe deux options pour créer une vue pour un éditeur personnalisé. L’un est le modèle d’activation sur place, où la vue est hébergée dans une fenêtre à l’aide d’un contrôle ActiveX ou d’un objet de données de document. Le second est le modèle d’intégration simplifié, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] où la vue est hébergée par et <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> est implémentée pour gérer les commandes de fenêtre. Pour plus d’informations sur le modèle d’activation sur place, voir [activation sur place](/visualstudio/misc/in-place-activation?view=vs-2015). Pour plus d’informations sur le modèle d’intégration simplifiée, voir [l’intégration simplifiée](../extensibility/simplified-embedding.md).

## <a name="see-also"></a>Voir aussi

- [Prendre en charge plusieurs vues de documents](../extensibility/supporting-multiple-document-views.md)
- [Intégration simplifiée](../extensibility/simplified-embedding.md)
- [Comment : Joindre les vues pour documenter les données](../extensibility/how-to-attach-views-to-document-data.md)
- [Gestion des détenteurs de verrouillage de document](../extensibility/document-lock-holder-management.md)
- [Vues simples et multi-onglets](../extensibility/single-and-multi-tab-views.md)
- [Enregistrer un document standard](../extensibility/internals/saving-a-standard-document.md)
- [Persistance et tableau de document en cours d’exécution](../extensibility/internals/persistence-and-the-running-document-table.md)
- [Déterminer quel éditeur ouvre un fichier dans un projet](../extensibility/internals/determining-which-editor-opens-a-file-in-a-project.md)
