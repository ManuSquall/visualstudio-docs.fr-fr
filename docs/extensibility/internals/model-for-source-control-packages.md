---
title: Modèle pour les Packages de contrôle de code Source | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], model
ms.assetid: 6164b2d3-a622-4de8-bef3-a6de985e9ebd
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1ad60503c9f7b15bd4665fb8f9552864debc381d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62909220"
---
# <a name="model-for-source-control-packages"></a>Modèle des packages de contrôle de code source
Le modèle suivant représente un exemple d’une implémentation de contrôle de code source. Dans le modèle, vous voyez les interfaces que vous devez implémenter et les services de l’environnement que vous devez appeler. Comme tous les services, vous appelez réellement les méthodes d’une interface particulière que vous obtenez par le biais du service. Les noms des classes sont identifiées pour le rendre plus facile de voir comment contrôle de code source est effectué.

 ![SCC&#95;TALLATION exemples](../../extensibility/internals/media/scc_tup.gif "SCC_TUP") exemple de projet de contrôle Source

## <a name="interfaces"></a>Interfaces
 Vous pouvez implémenter le contrôle de code source pour vos nouveaux types de projet dans Visual Studio à l’aide de la liste des interfaces indiqué dans le tableau suivant.

|Interface|Utilisez|
|---------------|---------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>|Appelé par les projets et les éditeurs avant leur enregistrement ou les fichiers de modification (« Dirty »). Cette interface est accessible à l’aide de la <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave> service.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>|Appelé par les projets pour demander l’autorisation d’ajouter, supprimer ou renommer un fichier ou répertoire. Cette interface est également appelée par les projets pour informer l’environnement lorsqu’un ajout approuvé, supprimer ou renommer l’action est terminée. Il est accessible à l’aide de la <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments> service.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>|Implémentée par toute entité qui inscrit pour être averti lorsque des projets à ajoutent, renommer ou supprimer un fichier ou répertoire. Pour vous inscrire pour la notification d’événement, appelez <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2.AdviseTrackProjectDocumentsEvents%2A>.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>|Appelé par les projets à inscrire avec le package de contrôle de code source et pour obtenir des informations sur l’état de contrôle de code source. Cette interface est accessible à l’aide de la <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager> service.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>|Implémenté par le projet pour répondre aux demandes de contrôle de code source pour plus d’informations sur les fichiers et pour obtenir la source des paramètres de contrôle requis pour le fichier projet.|

## <a name="see-also"></a>Voir aussi
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2.AdviseTrackProjectDocumentsEvents%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>
- [Prise en charge du contrôle de code source](../../extensibility/internals/supporting-source-control.md)