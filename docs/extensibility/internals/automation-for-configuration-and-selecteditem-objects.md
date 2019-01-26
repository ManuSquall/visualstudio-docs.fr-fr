---
title: Automatisation de la Configuration et des objets SelectedItem | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], SelectedItem object
- automation [Visual Studio SDK], builds
ms.assetid: 120377f1-51aa-4445-b2f7-06ab7fc2b47f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 60efbb25b0b5b52e1392ce84c16710a78dde7b16
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54919276"
---
# <a name="automation-for-configuration-and-selecteditem-objects"></a>Automation pour les objets de Configuration et SelectedItem
Vous pouvez automatiser la génération et le processus de l’élément sélectionné dans [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
## <a name="automation-for-builds"></a>Automation pour les builds  
 Build ou la configuration dispose d’un modèle automation qui est fourni lorsque vous implémentez <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider>. Pour plus d’informations, consultez [Présentation des configurations de build](../../ide/understanding-build-configurations.md).  
  
 Si vous créez un VSPackage et que vous souhaitez contrôler les options de configuration, vous devez utiliser le modèle automation.  
  
## <a name="automation-for-selecteditem"></a>Automatisation de la propriété SelectedItem  
 Vous n’êtes pas obligé de fournir une implémentation pour le `SelectedItem` , car Visual Studio contient une implémentation standard de l’objet. Toutefois, vous pouvez implémenter le `SelectedItem` de l’objet si vous préférez. Vous devez implémenter un objet qui contient le `SelectedItem` interface et renvoie une réponse à un appel à la <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> méthode avec `VSITEMID` défini sur <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A>   
 [Contribuer au modèle automation](../../extensibility/internals/contributing-to-the-automation-model.md)   
 [Présentation des configurations de build](../../ide/understanding-build-configurations.md)