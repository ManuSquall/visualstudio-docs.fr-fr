---
title: Nouveautés du contrôle de code source
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- what's new [Visual Studio SDK], source control
- source control [Visual Studio SDK], what's new
ms.assetid: bcf85418-18fb-4824-9dae-d14bf3d56a77
caps.latest.revision: 28
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 27623c22664e9d3c6b651615465e6abe812ea408
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2019
ms.locfileid: "59001489"
---
# <a name="what39s-new-in-source-control-in-visual-studio-2015"></a>Ce que&#39;nouveauté d’un contrôle de code Source dans Visual Studio 2015

[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Dans [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] vous pouvez fournir une solution de contrôle de code source profondément intégré en implémentant un VSPackage de contrôle de code source. Cette section décrit les fonctionnalités de contrôle de code source VSPackages et fournit une vue d’ensemble des étapes d’implémentation.  
  
## <a name="the-source-control-vspackage"></a>Le VSPackage de contrôle de code Source  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] prend en charge deux types de solutions de contrôle source. Dans toutes les versions de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], vous pouvez toujours intégrer basée sur une API de plug-in de contrôle de Source de plug-in. Vous pouvez également créer un VSPackage de contrôle de code source qui fournit une intégration approfondie, [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] chemin d’accès adéquat pour les solutions de contrôle de source qui requièrent un haut niveau de sophistication et d’autonomie.  
  
 Un VSPackage peut ajouter presque n’importe quel type de fonctionnalité à [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Un VSPackage de contrôle de code source fournit une fonctionnalité de contrôle de source complet pour [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], à partir de l’interface utilisateur présentée à l’utilisateur pour la communication serveur principal avec le système de contrôle de code source.  
  
 Implémentation d’un VSPackage de contrôle de code source nécessite une stratégie « tout ou rien ». Le créateur d’un VSPackage de contrôle de code source doit investir beaucoup d’efforts dans l’implémentation de plusieurs interfaces de contrôle de source et de nouveaux éléments d’interface utilisateur (boîtes de dialogue, les menus et barres d’outils) afin de couvrir les fonctionnalités de contrôle source entière, ainsi que des interfaces requis de n’importe quel package pour intégrer correctement à [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
 La procédure suivante donne une vue d’ensemble de ce qui est nécessaire pour implémenter un package de contrôle de code source. Pour plus d’informations, consultez [création d’un VSPackage de contrôle de code Source](../../extensibility/internals/creating-a-source-control-vspackage.md).  
  
1.  Créer un VSPackage qui offre un service de contrôle de source privée.  
  
2.  Implémenter les interfaces dans les services relatifs au contrôle de code source sont offerts par [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] (par exemple, le <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> et <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider> interface).  
  
3.  Inscrire votre VSPackage de contrôle de code source.  
  
4.  Implémenter le contrôle de code source toutes l’interface utilisateur, y compris les éléments de menu, des boîtes de dialogue, des barres d’outils et des menus contextuels.  
  
5.  Tous les événements relatifs au contrôle de source sont passés à votre contrôle de code source VSackage lorsqu’il est actif et doit être gérée par votre VSPackage.  
  
6.  Votre contrôle de code source VSPackage doit écouter les événements tels que ceux implémentation le <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3> interface ainsi que les événements de Document de projet de suivi (TPD) (implémenté par le <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> interface) et prendre les mesures nécessaires.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>   
 [Vue d’ensemble](../../extensibility/internals/source-control-integration-overview.md)   
 [Création d’un VSPackage de contrôle de code source](../../extensibility/internals/creating-a-source-control-vspackage.md)
