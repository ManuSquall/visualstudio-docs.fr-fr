---
title: La mise à niveau des éléments de projet | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- upgrading project items
- projects [Visual Studio SDK], upgrading items
- project items [Visual Studio], upgrading
ms.assetid: 8af29dd4-eaf1-4b3c-b602-198e1a3dff23
caps.latest.revision: 14
manager: douge
ms.openlocfilehash: a9bf5307e2eabc2ba15c8e2dc8e1b1e0fadb11a0
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49224092"
---
# <a name="upgrading-project-items"></a>Mise à niveau d’éléments de projet
Si vous ajoutez ou gérez les éléments à l’intérieur des systèmes de projet que vous n’implémentez pas, vous devrez peut-être participer au processus de mise à niveau du projet. Crystal Reports est un exemple d’un élément qui peut être ajouté au système de projet.  
  
 En général, les implémenteurs d’élément de projet souhaitent tirer parti d’un projet déjà entièrement instancié et mis à niveau, car ils ont besoin de savoir quelles le projet sont des références et les autres propriétés de projet il à prendre une décision de mise à niveau.  
  
### <a name="to-get-the-project-upgrade-notification"></a>Pour obtenir la notification de mise à niveau du projet  
  
1.  Définir le <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80.SolutionOrProjectUpgrading> indicateur (défini dans vsshell80.idl) dans votre implémentation d’élément de projet. Cela provoque votre élément de projet VSPackage automatiquement charger lorsque le [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] shell détermine qu’un système de projet est en cours de la mise à niveau.  
  
2.  Informez le <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade> interface via la <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution2.AdviseSolutionEvents%2A> (méthode).  
  
3.  Le <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade> interface est déclenchée une fois l’implémentation de système de projet a terminé ses opérations de mise à niveau et le nouveau projet mis à niveau est créé. Selon le scénario, le <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade> interface est déclenchée après le <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenSolution%2A>, le <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A>, ou le <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterLoadProject%2A> méthodes.  
  
### <a name="to-upgrade-the-project-item-files"></a>Pour mettre à niveau les fichiers d’élément de projet  
  
1.  Vous devez gérer soigneusement le processus de sauvegarde de fichier dans votre implémentation d’élément de projet. Cela s’applique en particulier pour une sauvegarde côte à côte, où le `fUpgradeFlag` paramètre de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> méthode est définie sur <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS>, où les fichiers qui avaient été sauvegardées sont placés le long de fichiers côté qui sont désignés comme « .old ». Les fichiers sauvegardés antérieures à l’heure système lorsque le projet a été mis à niveau peuvent être désignées comme obsolètes. En outre, ils peuvent être remplacés, sauf si vous prenez des mesures spécifiques pour éviter ce problème.  
  
2.  Au moment où votre élément de projet reçoit une notification de la mise à niveau du projet, le **Assistant Conversion de Visual Studio** est toujours affichée. Par conséquent, vous devez utiliser les méthodes de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUpgradeLogger> interface pour fournir des messages de mise à niveau à l’interface utilisateur de l’Assistant.  
  
## <a name="see-also"></a>Voir aussi  
 [Assistant Conversion de Visual Studio](http://msdn.microsoft.com/en-us/4acfd30e-c192-4184-a86f-2da5e4c3d83c)   
 [Mise à niveau de projets personnalisés](../misc/upgrading-custom-projects.md)