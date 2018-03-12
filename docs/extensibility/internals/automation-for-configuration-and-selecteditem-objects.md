---
title: Automatisation de la Configuration et les objets SelectedItem | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- automation [Visual Studio SDK], SelectedItem object
- automation [Visual Studio SDK], builds
ms.assetid: 120377f1-51aa-4445-b2f7-06ab7fc2b47f
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 8a9446a5c63df7f20d6e4dbdc3cb60bf20183bb5
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="automation-for-configuration-and-selecteditem-objects"></a>Automatisation de la Configuration et les objets SelectedItem
Vous pouvez automatiser la génération et le processus de l’élément sélectionné dans [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
## <a name="automation-for-builds"></a>Automation pour les Builds  
 Build ou la configuration dispose d’un modèle automation fourni lors de l’implémentation <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider>. Pour plus d’informations, consultez [Présentation des configurations de build](../../ide/understanding-build-configurations.md).  
  
 Si vous créez un VSPackage et que vous souhaitez contrôler les options de configuration, vous devez utiliser le modèle automation.  
  
## <a name="automation-for-selecteditem"></a>Automatisation de SelectedItem  
 Vous n’êtes pas obligé de fournir une implémentation pour la `SelectedItem` , car Visual Studio contient une implémentation standard de l’objet. Toutefois, vous pouvez implémenter la `SelectedItem` de l’objet si vous préférez. Vous devez implémenter un objet qui contient le `SelectedItem` de l’interface et renvoie une réponse à un appel à la <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> méthode de VSITEMID <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A>   
 [Qui contribuent au modèle Automation](../../extensibility/internals/contributing-to-the-automation-model.md)   
 [Présentation des configurations de build](../../ide/understanding-build-configurations.md)