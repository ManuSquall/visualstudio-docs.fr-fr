---
title: Pour les Packages de contrôle de code Source | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], model
ms.assetid: 6164b2d3-a622-4de8-bef3-a6de985e9ebd
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: fa0dcdd930412e4e53c59509848f0b7c1503c47b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31129441"
---
# <a name="model-for-source-control-packages"></a>Modèle pour les Packages de contrôle de code Source
Le modèle suivant représente un exemple d’une implémentation de contrôle de code source. Dans le modèle, vous consultez les interfaces que vous devez implémenter et les services de l’environnement que vous devez appeler. Comme tous les services, vous appelez réellement les méthodes d’une interface particulière que vous obtenez par le biais du service. Les noms des classes sont identifiées pour le rendre plus facile de déterminer la façon dont est effectuée contrôle de code source.  
  
 ![Contrôle de code source&#95;TUP exemples](../../extensibility/internals/media/scc_tup.gif "SCC_TUP")  
Exemple de projet de contrôle Source  
  
## <a name="interfaces"></a>Interfaces  
 Vous pouvez implémenter le contrôle de code source pour vos nouveaux types de projet dans Visual Studio à l’aide de la liste des interfaces indiqué dans le tableau suivant.  
  
|Interface|Utilisez|  
|---------------|---------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>|Appelée par les projets et les éditeurs avant leur enregistrement ou de fichiers de modification (« Dirty »). Cette interface est accessible à l’aide de la <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave> service.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>|Appelé par les projets pour demander l’autorisation d’ajouter, supprimer ou renommer un fichier ou répertoire. Cette interface est également appelée par les projets pour informer l’environnement lorsqu’un ajout approuvé, supprimer ou renommer l’action est terminée. Il est accessible à l’aide de la <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments> service.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>|Implémentée par une entité qui inscrit pour être averti lorsque des projets ajoutent, renommer ou supprimer un fichier ou répertoire. Pour inscrire la notification d’événement, appelez <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2.AdviseTrackProjectDocumentsEvents%2A>.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>|Appelé par les projets pour inscrire avec le package de contrôle de code source et pour obtenir des informations sur l’état de contrôle de code source. Cette interface est accessible à l’aide de la <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager> service.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>|Implémenté par le projet pour répondre aux demandes de contrôle de code source pour plus d’informations sur les fichiers et pour obtenir les paramètres de contrôle requis pour le fichier de projet de la source.|  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2.AdviseTrackProjectDocumentsEvents%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>   
 [Prise en charge du contrôle de code source](../../extensibility/internals/supporting-source-control.md)