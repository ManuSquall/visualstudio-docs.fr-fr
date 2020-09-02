---
title: Modèle pour les packages de contrôle de code source | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], model
ms.assetid: 6164b2d3-a622-4de8-bef3-a6de985e9ebd
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 811cdfa2cbae85d6509e7cd883c5675b81639fa0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68198441"
---
# <a name="model-for-source-control-packages"></a>Modèle des packages de contrôle de code source
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Le modèle suivant représente un exemple d’implémentation de contrôle de code source. Dans le modèle, vous voyez les interfaces que vous devez implémenter et les services d’environnement que vous devez appeler. Comme tous les services, vous appelez en fait les méthodes d’une interface particulière que vous obtenez par le biais du service. Les noms des classes sont identifiés pour vous permettre de voir plus facilement comment le contrôle de code source est exécuté.  
  
 ![Exemples de tallation SCC&#95;](../../extensibility/internals/media/scc-tup.gif "SCC_TUP")  
Exemple de projet de contrôle de code source  
  
## <a name="interfaces"></a>Interfaces  
 Vous pouvez implémenter le contrôle de code source pour vos nouveaux types de projet dans Visual Studio à l’aide de la liste des interfaces répertoriées dans le tableau suivant.  
  
|Interface|Utilisation|  
|---------------|---------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>|Appelée par les projets et les éditeurs avant d’enregistrer ou de modifier les fichiers (modifiés). Cette interface est accessible à l’aide du <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave> service.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>|Appelée par les projets pour demander l’autorisation d’ajouter, de supprimer ou de renommer un fichier ou un répertoire. Cette interface est également appelée par les projets pour informer l’environnement lorsqu’une action d’ajout, de suppression ou de changement de nom approuvée est terminée. Elle est accessible à l’aide du <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments> service.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>|Implémenté par une entité qui s’inscrit pour être averti lorsque des projets ajoutent, renomment ou suppriment un fichier ou un répertoire. Pour vous inscrire à la notification d’événement, appelez <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2.AdviseTrackProjectDocumentsEvents%2A> .|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>|Appelé par les projets à inscrire auprès du package de contrôle de code source et pour obtenir des informations sur l’état du contrôle de code source. Cette interface est accessible à l’aide du <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager> service.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>|Implémenté par le projet pour répondre aux demandes de contrôle de code source pour les informations sur les fichiers et pour obtenir les paramètres de contrôle de code source requis pour le fichier projet.|  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2.AdviseTrackProjectDocumentsEvents%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>   
 [Prise en charge du contrôle de code source](../../extensibility/internals/supporting-source-control.md)
