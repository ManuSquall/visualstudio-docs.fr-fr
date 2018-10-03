---
title: Incorporation simplifiée | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], custom - simple view embedding
ms.assetid: f1292478-a57d-48ec-8c9e-88a23f04ffe5
caps.latest.revision: 17
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: de1ef1b6538c010a1428dfa54ea4296a870d7ad5
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47506585"
---
# <a name="simplified-embedding"></a>Incorporation simplifiée
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [simplifié incorporation](https://docs.microsoft.com/visualstudio/extensibility/simplified-embedding).  
  
Incorporation simplifiée est activée dans un éditeur lorsque son objet de vue de document est apparenté à (autrement dit, un enfant de) [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]et le <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> interface est implémentée pour prendre en charge ses commandes de fenêtre. Les éditeurs incorporation simplifiées ne peut pas héberger des contrôles actifs. Les objets utilisés pour créer un éditeur avec l’incorporation simplifiée sont affichés dans l’illustration suivante.  
  
 ![Graphique de l’éditeur d’incorporation simplifié](../extensibility/media/vssimplifiedembeddingeditor.gif "vsSimplifiedEmbeddingEditor")  
Éditeur avec l’incorporation simplifiée  
  
> [!NOTE]
>  Des objets dans cette illustration, uniquement le `CYourEditorFactory` objet est requis pour créer un éditeur de fichier standard. Si vous créez un éditeur personnalisé, vous ne devez pas implémenter <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2>, car votre éditeur possède probablement son propre mécanisme privé de persistance. Pour les éditeurs non personnalisées, toutefois, vous devez le faire.  
  
 Toutes les interfaces implémentées pour créer un éditeur avec l’incorporation simplifiée sont contenus dans le `CYourEditorDocument` objet. Toutefois, pour prendre en charge plusieurs vues de données de document, diviser les interfaces sur les objets de données et les vues distincts comme indiqué dans le tableau suivant.  
  
|Interface|Emplacement de l’interface|Utilisez|  
|---------------|---------------------------|---------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|Vue|Fournit la connexion à la fenêtre parente.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Vue|Gère les commandes.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser>|Vue|Permet la mise à jour de la barre d’état.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser>|Vue|Permet de **boîte à outils** éléments.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsFileChangeEvents>|Données|Envoie des notifications lorsque le fichier modifié.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>|Données|Active la fonctionnalité Enregistrer sous pour un type de fichier.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2>|Données|Active la persistance pour le document.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl>|Données|Permet la suppression des événements de changement de fichier, comme le déclenchement de rechargement.|

