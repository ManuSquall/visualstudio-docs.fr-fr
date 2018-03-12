---
title: Activation en Place | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], custom - in-place view activation
ms.assetid: 7d316945-06e0-4d8e-ba3a-0ef96fc75399
caps.latest.revision: 
manager: douge
ms.openlocfilehash: d1fe2c1dfe71923897836f803e3a9712b4dec0f1
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/09/2018
---
# <a name="in-place-activation"></a>Activation sur Place
Si votre mode Éditeur héberge ActiveX ou d’autres contrôles actifs, vous devez l’implémenter en tant que contrôle ActiveX ou en tant qu’objet de données de document actif à l’aide du modèle d’activation en place.  
  
## <a name="support-for-menus-toolbars-and-commands"></a>Prise en charge des menus, des barres d’outils et des commandes  
 Visual Studio permet à votre mode Éditeur d’utiliser les menus et les barres d’outils de l’IDE. Ces extensions sont appelées *composants OLE sur place*. Pour plus d’informations, consultez <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponent> et <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager>.  
  
 Si vous implémentez un contrôle ActiveX, vous pouvez héberger d’autres objets incorporés. Si vous implémentez un objet de données de document, le frame de fenêtre limite votre capacité à utiliser les contrôles ActiveX.  
  
> [!NOTE]
>  Les interfaces <xref:Microsoft.VisualStudio.OLE.Interop.IOleDocument> et <xref:Microsoft.VisualStudio.OLE.Interop.IOleDocumentView> permettent de séparer les données et les vues. Toutefois, Visual Studio ne prend pas en charge cette fonctionnalité, et ces interfaces sont utilisées uniquement pour représenter l’objet d’affichage de document.  
  
 Les éditeurs qui utilisent le service <xref:Microsoft.VisualStudio.Shell.Interop.SOleComponentUIManager> peuvent fournir l’intégration des menus, des barres d’outils et des commandes en appelant les méthodes de l’interface <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager> implémentée par le service <xref:Microsoft.VisualStudio.Shell.Interop.SOleComponentUIManager> . Les éditeurs peuvent également proposer d’autres fonctionnalités Visual Studio, telles que le suivi de sélection et la gestion des annulations. Pour plus d’informations, consultez [créer des éditeurs personnalisés et les concepteurs](../extensibility/creating-custom-editors-and-designers.md).  
  
## <a name="objects-and-interfaces-used"></a>Objets et interfaces utilisés  
 Les objets qui sont utilisés pour créer l’activation sur place sont affichés dans l’illustration suivante.  
  
 ![Dans &#45; Éditeur d’Activation sur place](../extensibility/media/vsinplaceactivationeditor.gif "vsInPlaceActivationEditor")  
Éditeur d’activation sur place  
  
> [!NOTE]
>  Parmi les objets de ce dessin, seul l’objet `CYourEditorFactory` est nécessaire pour créer un éditeur standard. Si vous créez un éditeur personnalisé, vous n’avez pas à implémenter <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> , car votre éditeur possède probablement son propre mécanisme privé de persistance. Pour plus d’informations, consultez [créer des éditeurs personnalisés et les concepteurs](../extensibility/creating-custom-editors-and-designers.md).  
  
 Toutes les interfaces qui sont implémentées pour créer un éditeur d’activation en place apparaissent dans l’objet `CYourEditorDocument` unique, mais cette configuration ne prend en charge qu’une seule vue pour vos données de document. Pour plus d’informations sur la prise en charge de plusieurs vues pour vos données de document, consultez [Supporting Multiple Document Views](../extensibility/supporting-multiple-document-views.md).  
  
|Interface|Type d’objet|Utilisez|  
|---------------|--------------------|---------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponent>|Vue|Permet aux objets VSPackage sur place de fonctionner comme des composants entièrement intégrés de l’IDE grâce au service <xref:Microsoft.VisualStudio.Shell.Interop.SOleComponentUIManager> . Ce service intègre les menus, les barres d’outils et les commandes de l’objet dans l’IDE, et émet des notifications concernant les changements d’état.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleObject>|Vue|Principaux moyens utilisés par un objet incorporé pour fournir des fonctionnalités de base à son conteneur et communiquer avec lui.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleInPlaceActiveObject>|Vue|Gère l’activation et la désactivation des objets sur place, et détermine quelle proportion de l’objet sur place doit être visible.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleInPlaceObject>|Vue|Fournit un canal de communication direct entre un objet sur place, la fenêtre frame la plus à l’extérieur dans l’application associée et la fenêtre de document de l’application qui contient l’objet incorporé.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleDocument>|Vue|Implémente un objet ActiveX. Notez que les méthodes de <xref:Microsoft.VisualStudio.OLE.Interop.IOleDocument> et <xref:Microsoft.VisualStudio.OLE.Interop.IOleDocumentView> qui séparent les données de document et les vues ne sont pas utilisées dans l’IDE.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Vue/Données|Permet à l’objet de données de document ou à l’objet de vue de document (ou aux deux) de participer à la gestion des commandes.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser>|Vue|Permet la mise à jour de la barre d’état.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser>|Vue|Permet d’ajouter des éléments à la boîte à outils.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsFileChangeEvents>|Données|Envoie une notification de modification au fichier modifié (cette interface est facultative).|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>|Données|Permet d’activer la fonctionnalité Enregistrer en tant que pour un type de fichier.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData>|Données|Active la persistance pour le document. Pour les fichiers en lecture seule, appelez <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.SetDocDataReadOnly%2A> pour fournir l’icône de verrou qui indique que les fichiers sont en lecture seule.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl>|Données|Détermine si les modifications apportées aux données de document doivent être ignorées.|