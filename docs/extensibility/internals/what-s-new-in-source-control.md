---
title: "Quel &#39; s de contrôle de code Source | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- what's new [Visual Studio SDK], source control
- source control [Visual Studio SDK], what's new
ms.assetid: bcf85418-18fb-4824-9dae-d14bf3d56a77
caps.latest.revision: "27"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 946a3c9fb7d3f0ccd6a90383f6ca22d91c0009a4
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="what39s-new-in-source-control"></a>Quel &#39; s de contrôle de code Source
Dans [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] vous pouvez fournir une solution de contrôle de code source profondément intégré en implémentant un VSPackage de contrôle de code source. Cette section décrit les fonctionnalités de contrôle de code source VSPackages et fournit une vue d’ensemble des étapes d’implémentation.  
  
## <a name="the-source-control-vspackage"></a>Le VSPackage de contrôle de code Source  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]prend en charge deux types de solutions de contrôle de code source. Dans toutes les versions de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], vous pouvez toujours intégrer basée sur une API de plug-in de contrôle de Source de plug-in. Vous pouvez également créer un VSPackage pour le contrôle de code source qui fournit une intégration approfondie, [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] chemin d’accès approprié pour les solutions de contrôle de source qui nécessitent un niveau élevé de sophistication et d’autonomie.  
  
 Un VSPackage peut ajouter presque n’importe quel type de fonctionnalité à [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Un contrôle de code source VSPackage fournit une fonctionnalité de contrôle de source complet pour [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], à partir de l’interface utilisateur présentée à l’utilisateur pour les communications avec le système de contrôle de source.  
  
 Implémentation d’un contrôle de code source VSPackage nécessite une stratégie « tout ou rien ». Le créateur d’un contrôle de code source VSPackage doit investir une quantité importante de l’effort de mise en œuvre un certain nombre de nouveaux éléments d’interface utilisateur (boîtes de dialogue, les menus et barres d’outils) pour couvrir la fonctionnalité de contrôle source entière, les interfaces de contrôle de code source, ainsi que des interfaces requis d’un package pour intégrer correctement à [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 La procédure suivante donne une vue d’ensemble de ce qui est nécessaire pour implémenter un package de contrôle de code source. Pour plus d’informations, consultez [création d’un VSPackage de contrôle de Source](../../extensibility/internals/creating-a-source-control-vspackage.md).  
  
1.  Créer un VSPackage qui proffers un service de contrôle de source privée.  
  
2.  Implémenter les interfaces dans les services relatifs au contrôle de code source sont offerts par [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] (par exemple, le <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> et <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider> interface).  
  
3.  Inscrire votre contrôle de code source VSPackage.  
  
4.  Implémenter tous les contrôle de source de l’interface utilisateur, y compris les éléments de menu, des boîtes de dialogue, des barres d’outils et des menus contextuels.  
  
5.  Tous les événements relatifs au contrôle de code source sont passés à votre contrôle de code source VSackage lorsqu’il est actif et doit être gérée par votre VSPackage.  
  
6.  Votre contrôle de code source VSPackage doit écouter les événements, tels que ceux implémentation le <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3> , ainsi que les événements de Document de projet de suivi (TPD) de l’interface (implémenté par le <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> interface) et prenez les mesures nécessaires.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>   
 [Vue d’ensemble](../../extensibility/internals/source-control-integration-overview.md)   
 [Création d’un VSPackage de contrôle de code source](../../extensibility/internals/creating-a-source-control-vspackage.md)