---
title: Mise à niveau d’éléments de projet | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- upgrading project items
- projects [Visual Studio SDK], upgrading items
- project items [Visual Studio], upgrading
ms.assetid: 8af29dd4-eaf1-4b3c-b602-198e1a3dff23
caps.latest.revision: 14
manager: jillfra
ms.openlocfilehash: eb3619e187c7856cf03ee60c8a04cbe527bf0a69
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65698686"
---
# <a name="upgrading-project-items"></a>Mise à niveau d’éléments de projet
Si vous ajoutez ou gérez des éléments dans des systèmes de projet que vous n’implémentez pas, vous devrez peut-être participer au processus de mise à niveau du projet. Crystal Reports est un exemple d’élément qui peut être ajouté au système de projet.  
  
 En règle générale, les implémenteurs d’éléments de projet souhaitent tirer parti d’un projet déjà entièrement instancié et mis à niveau, car ils ont besoin de savoir ce que sont les références de projet et les autres propriétés du projet pour prendre une décision de mise à niveau.  
  
### <a name="to-get-the-project-upgrade-notification"></a>Pour recevoir la notification de mise à niveau du projet  
  
1. Définissez l' <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80.SolutionOrProjectUpgrading> indicateur (défini dans vsshell80. idl) dans l’implémentation de l’élément de projet. Cela entraîne le chargement automatique de votre VSPackage d’élément de projet quand l' [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] interpréteur de commandes détermine qu’un système de projet est en cours de mise à niveau.  
  
2. Conseillez l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade> interface via la <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution2.AdviseSolutionEvents%2A> méthode.  
  
3. L' <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade> interface est déclenchée une fois que l’implémentation du système de projet a terminé ses opérations de mise à niveau et que le nouveau projet mis à niveau est créé. Selon le scénario, l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade> interface est déclenchée après <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenSolution%2A> , <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A> ou les <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterLoadProject%2A> méthodes.  
  
### <a name="to-upgrade-the-project-item-files"></a>Pour mettre à niveau les fichiers d’éléments de projet  
  
1. Vous devez soigneusement gérer le processus de sauvegarde de fichiers dans l’implémentation de l’élément de projet. Cela s’applique en particulier à une sauvegarde côte à côte, où le `fUpgradeFlag` paramètre de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> méthode a la valeur <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS> , où les fichiers qui ont été sauvegardés sont placés le long des fichiers désignés comme « . old ». Les fichiers sauvegardés antérieurs à l’heure système de la mise à niveau du projet peuvent être désignés comme obsolètes. En outre, elles peuvent être remplacées, sauf si vous prenez des mesures spécifiques pour éviter cela.  
  
2. Lorsque votre élément de projet reçoit une notification de la mise à niveau du projet, l' **Assistant Conversion de Visual Studio** s’affiche toujours. Par conséquent, vous devez utiliser les méthodes de l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsUpgradeLogger> interface pour fournir des messages de mise à niveau à l’interface utilisateur de l’Assistant.  
  
## <a name="see-also"></a>Voir aussi  
 [Assistant Conversion de Visual Studio](https://msdn.microsoft.com/4acfd30e-c192-4184-a86f-2da5e4c3d83c)   
 [Mise à niveau de projets personnalisés](../misc/upgrading-custom-projects.md)