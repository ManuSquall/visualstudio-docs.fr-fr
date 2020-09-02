---
title: Incorporation simplifiée | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - simple view embedding
ms.assetid: f1292478-a57d-48ec-8c9e-88a23f04ffe5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b9bc9619ae1ed75aed3656ff014296f7c7d88fa0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80700071"
---
# <a name="simplified-embedding"></a>Incorporation simplifiée
L’incorporation simplifiée est activée dans un éditeur lorsque son objet de vue de document est apparenté à (autrement dit, a rendu un enfant de) [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] et que l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> interface est implémentée pour gérer ses commandes de fenêtre. Les éditeurs d’incorporation simplifiés ne peuvent pas héberger des contrôles actifs. Les objets utilisés pour créer un éditeur avec incorporation simplifiée sont indiqués dans l’illustration suivante.

 ![Graphique de l’éditeur d’incorporation simplifié](../extensibility/media/vssimplifiedembeddingeditor.gif "vsSimplifiedEmbeddingEditor") Éditeur avec incorporation simplifiée

> [!NOTE]
> Parmi les objets de cette illustration, seul l' `CYourEditorFactory` objet est requis pour créer un éditeur standard basé sur des fichiers. Si vous créez un éditeur personnalisé, vous n’êtes pas obligé d’implémenter <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> , car votre éditeur aura probablement son propre mécanisme de persistance privée. Toutefois, pour les éditeurs non personnalisés, vous devez le faire.

 Toutes les interfaces implémentées pour créer un éditeur avec incorporation simplifiée sont contenues dans l' `CYourEditorDocument` objet. Toutefois, pour prendre en charge plusieurs vues de données de document, fractionnez les interfaces sur des données distinctes et affichez les objets comme indiqué dans le tableau suivant.

|Interface|Emplacement de l’interface|Utilisation|
|---------------|---------------------------|---------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|Affichage|Fournit la connexion à la fenêtre parente.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Affichage|Gère les commandes.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser>|Affichage|Permet la mise à jour de la barre d’état.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser>|Affichage|Active les éléments de **boîte à outils** .|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsFileChangeEvents>|Données|Envoie des notifications lorsque le fichier change.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>|Données|Active la fonctionnalité enregistrer sous pour un type de fichier.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2>|Données|Active la persistance pour le document.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl>|Données|Autorise la suppression des événements de modification de fichier, tels que le déclenchement du rechargement.|
