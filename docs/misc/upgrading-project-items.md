---
title: "Mise &#224; niveau d’&#233;l&#233;ments de projet | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "mise à niveau d’éléments de projet"
  - "projets [Kit de développement logiciel Visual Studio], mise à niveau d’éléments"
  - "éléments de projet [Visual Studio], mise à niveau"
ms.assetid: 8af29dd4-eaf1-4b3c-b602-198e1a3dff23
caps.latest.revision: 14
caps.handback.revision: 14
manager: "douge"
---
# Mise &#224; niveau d’&#233;l&#233;ments de projet
Si vous ajoutez ou gérer les éléments à l'intérieur de les systèmes de projet que vous n'implémentez pas, vous devrez peut\-être ajouter à la mise à niveau du projet.  Crystal Reports est un exemple d'un élément qui peut être ajouté au système de projet.  
  
 En général, les implémenteurs d'élément de projet souhaitent tirer parti d'un projet déjà entièrement instancié et mis à jour parce qu'ils doivent savoir que les références de projet et ce que sont là d'autres propriétés de projet pour prendre une décision de mise à niveau.  
  
### Pour obtenir la notification de mise à niveau du projet  
  
1.  Définissez l'indicateur d' <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80.SolutionOrProjectUpgrading> \(définie dans vsshell80.idl\) dans votre implémentation d'élément de projet.  Cela provoque votre élément de projet VSPackage à la charge automatique lorsque le shell de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] détermine qu'un système de projet est le processus de mise à niveau.  
  
2.  Recommandez l'interface d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade> via la méthode d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution2.AdviseSolutionEvents%2A> .  
  
3.  L'interface d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade> est levée après que l'implémentation du système de projet a terminé ses opérations de mise à niveau et le nouveau projet mis à jour.  Selon le scénario, l'interface d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade> est levée après <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenSolution%2A>, l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A>, ou les méthodes d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterLoadProject%2A> .  
  
### Pour mettre à niveau les fichiers d'élément de projet  
  
1.  vous devez soigneusement gérer le processus de sauvegarde de fichiers dans votre implémentation d'élément de projet.  Cela s'applique en particulier pour côte à côte de sauvegarde, où le paramètre d' `fUpgradeFlag` de la méthode d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> est défini à <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS>, dans lequel les fichiers qui avaient été sauvegardées sont placés sur des fichiers latéraux indiqués comme « .old ».  Les fichiers sauvegardés plus anciens que l'heure système lorsque le projet a été mis à niveau peuvent être désignés comme périmé.  En outre, ils peuvent être remplacés à moins que vous ne les mesures spécifiques pour empêcher cette situation.  
  
2.  Si votre élément de projet reçoit une notification de la mise à niveau de projet, **Assistant Conversion de Visual Studio** est encore affiché.  Par conséquent, vous devez utiliser les méthodes d'interface d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsUpgradeLogger> pour fournir des messages de mise à niveau vers l'interface utilisateur de l'Assistant.  
  
## Voir aussi  
 [Visual Studio Conversion Wizard](http://msdn.microsoft.com/fr-fr/4acfd30e-c192-4184-a86f-2da5e4c3d83c)   
 [Mise à niveau de projets personnalisés](../misc/upgrading-custom-projects.md)