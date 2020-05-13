---
title: Intégration simplifiée (fr) Microsoft Docs
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700071"
---
# <a name="simplified-embedding"></a>Incorporation simplifiée
L’intégration simplifiée est activée dans un éditeur lorsque son objet de vue [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]documentaire <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> est parenté à (c’est-à-dire, fait un enfant de) , et l’interface est implémentée pour gérer ses commandes de fenêtre. Les éditeurs d’intégration simplifiés ne peuvent pas héberger des contrôles actifs. Les objets utilisés pour créer un éditeur avec intégration simplifiée sont montrés dans l’illustration suivante.

 ![Graphique simplifié de l’éditeur d’intégration](../extensibility/media/vssimplifiedembeddingeditor.gif "vsSimplifiéEmbeddingEditor") Éditeur avec intégration simplifiée

> [!NOTE]
> Parmi les objets de cette `CYourEditorFactory` illustration, seul l’objet est nécessaire pour créer un éditeur standard basé sur le fichier. Si vous créez un éditeur personnalisé, vous <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2>n’êtes pas tenu de mettre en œuvre, parce que votre éditeur aura probablement son propre mécanisme de persistance privée. Pour les éditeurs non personnalisés, cependant, vous devez le faire.

 Toutes les interfaces mises en œuvre pour `CYourEditorDocument` créer un éditeur avec intégration simplifiée sont contenues dans l’objet. Toutefois, pour prendre en charge plusieurs vues des données documentaires, divisez les interfaces sur des données distinctes et affichez les objets tels qu’indiqués dans le tableau suivant.

|Interface|Emplacement de l’interface|Utilisation|
|---------------|---------------------------|---------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|Vue|Fournit un lien avec la fenêtre parente.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Vue|Gère les commandes.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser>|Vue|Permet la mise à jour de la barre d’état.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser>|Vue|Permet des articles **de boîte à** outils.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsFileChangeEvents>|Données|Envoie des notifications lorsque le fichier change.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>|Données|Permet la fonction Enregistrer comme pour un type de fichier.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2>|Données|Active la persistance pour le document.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl>|Données|Permet la suppression des événements de changement de fichier, tels que le déclenchement de rechargement.|
