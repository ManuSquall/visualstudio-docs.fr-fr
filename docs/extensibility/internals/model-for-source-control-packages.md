---
title: Modèle pour les paquets de contrôle des sources (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], model
ms.assetid: 6164b2d3-a622-4de8-bef3-a6de985e9ebd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 46845be1bc22a67d6703af12933945bdfcfa7f4b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707068"
---
# <a name="model-for-source-control-packages"></a>Modèle des packages de contrôle de code source
Le modèle suivant représente un exemple de mise en œuvre d’un contrôle source. Dans le modèle, vous voyez les interfaces que vous devez implémenter et les services d’environnement que vous devez appeler. Comme tous les services, vous appelez en fait les méthodes d’une interface particulière que vous obtenez par le service. Les noms des classes sont identifiés pour faciliter la mise en œt de l’image du contrôle des sources.

 ![SCC&#95;TUP Exemples](../../extensibility/internals/media/scc_tup.gif "SCC_TUP") Exemple Source Control Project

## <a name="interfaces"></a>Interfaces
 Vous pouvez implémenter le contrôle source de vos nouveaux types de projets dans Visual Studio à l’aide de la liste des interfaces affichées dans le tableau suivant.

|Interface|Utilisation|
|---------------|---------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>|Appelé par des projets et des éditeurs avant qu’ils n’enregistrent ou changent (sale) fichiers. Cette interface est accessible <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave> à l’aide du service.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>|Appelé par des projets pour demander la permission d’ajouter, de supprimer ou de renommer un fichier ou un répertoire. Cette interface est également appelée par des projets pour informer l’environnement lorsqu’une action approuvée d’ajout, de suppression ou de changement de nom est terminée. Il est accessible <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments> à l’aide du service.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>|Mise en œuvre par toute entité qui s’inscrit pour être notifiée lorsque les projets ajoutent, renomment ou suppriment un fichier ou un répertoire. Pour vous inscrire à <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2.AdviseTrackProjectDocumentsEvents%2A>la notification de l’événement, appelez .|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>|Appelé par les projets de s’inscrire avec le paquet de contrôle source et d’obtenir des informations sur l’état de contrôle des sources. Cette interface est accessible <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager> à l’aide du service.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>|Mise en œuvre par le projet pour répondre aux demandes de contrôle des sources pour obtenir des informations sur les fichiers et pour obtenir les paramètres de contrôle source requis pour le dossier du projet.|

## <a name="see-also"></a>Voir aussi
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2.AdviseTrackProjectDocumentsEvents%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>
- [Prise en charge du contrôle de code source](../../extensibility/internals/supporting-source-control.md)
