---
title: Automatisation pour la configuration et les objets SelectedItem | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], SelectedItem object
- automation [Visual Studio SDK], builds
ms.assetid: 120377f1-51aa-4445-b2f7-06ab7fc2b47f
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 42faf8127c1ab70d3470aa497a0cdab6058060f8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68157263"
---
# <a name="automation-for-configuration-and-selecteditem-objects"></a>Automatisation de la configuration et des objets SelectedItem
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Vous pouvez automatiser les processus de génération et d’élément sélectionné dans [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
## <a name="automation-for-builds"></a>Automation pour les builds  
 La génération ou la configuration dispose d’un modèle Automation qui est fourni quand vous implémentez <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider> . Pour plus d’informations, consultez [Présentation des configurations de build](../../ide/understanding-build-configurations.md).  
  
 Si vous créez un VSPackage et souhaitez contrôler les options de configuration, vous devez utiliser le modèle Automation.  
  
## <a name="automation-for-selecteditem"></a>Automatisation pour SelectedItem  
 Vous n’avez pas besoin de fournir une implémentation pour l' `SelectedItem` objet, car Visual Studio contient une implémentation standard. Toutefois, vous pouvez implémenter l' `SelectedItem` objet si vous préférez. Vous devez implémenter un objet qui contient l' `SelectedItem` interface et retourner une réponse à un appel à la <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> méthode avec VSITEMID défini sur <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> .  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A>   
 [Contribution au modèle Automation](../../extensibility/internals/contributing-to-the-automation-model.md)   
 [Fonctionnement des configurations de build](../../ide/understanding-build-configurations.md)
