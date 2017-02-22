---
title: "La mise &#224; niveau de projets | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "la mise à niveau les packages VS"
  - "la mise à niveau des applications, des stratégies"
  - "VSPackages, mise à niveau de prise en charge"
ms.assetid: e01cb44a-8105-4cf4-8223-dfae65f8597a
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# La mise &#224; niveau de projets
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Les modifications apportées au modèle de projet d'une version de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] à mai prochain requièrent que les projets et les solutions soient mis à niveau afin qu'ils puissent s'exécuter sur la version plus récente.  [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] fournit des interfaces qui peuvent être utilisées pour implémenter la prise en charge de la mise à niveau dans vos propres projets.  
  
## stratégies de mise à niveau  
 Pour prendre en charge une mise à niveau, l'implémentation de votre système de projet doit définir et implémenter une stratégie de mise à niveau.  Lorsque vous déterminez votre stratégie, vous pouvez choisir de prendre en charge côte à côte de la sauvegarde, la sauvegarde de copie, ou les deux \(SxS\).  
  
-   La sauvegarde de SxS signifie qu'un projet copie uniquement les fichiers qui ont besoin de mettre à niveau sur place, en ajoutant un suffixe approprié de nom de fichier, par exemple, « .old ».  
  
-   La sauvegarde de copie signifie qu'un projet copie tous les éléments de projet à l'fournie par l'emplacement d'enregistrement.  Les fichiers appropriés à l'emplacement du projet d'origine sont ensuite mis à niveau.  
  
## Comment la mise à niveau s'exécute  
 Lorsqu'une solution créée dans une version antérieure de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] est ouverte dans une version plus récente, l'IDE active le fichier solution pour déterminer s'il doit être mis à niveau.  Si la mise à niveau est requis, **L'Assistant Mise à niveau** est automatiquement lancée pour parcourir l'utilisateur via la mise à niveau.  
  
 Lorsqu'une solution a besoin mettre à niveau, il interroge chaque fabrique de projet pour sa stratégie de mise à niveau.  La stratégie détermine si la fabrique de projet prend en charge la sauvegarde de copie ou la sauvegarde de SxS.  Les informations sont envoyées à **L'Assistant Mise à niveau**, qui collectent les informations requises pour la sauvegarde et répertorient les options applicables à l'utilisateur.  
  
### solutions à projets multiples  
 Si une solution contient plusieurs projets et les stratégies de mise à niveau diffèrent, par exemple lorsque le projet c\+\+ qui prend en charge uniquement la sauvegarde de SxS et un projet Web qui prennent uniquement en charge la sauvegarde de copie, les fabriques de projet doivent négocier la stratégie de mise à niveau.  
  
 la solution interroge chaque fabrique de projet pour <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory>.  Il appelle ensuite l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject_CheckOnly%2A> pour voir si les fichiers projet globaux ont besoin mettre à niveau et de déterminer les stratégies prises en charge par la mise à niveau.  **L'Assistant Mise à niveau** est ensuite appelé.  
  
 Une fois que l'utilisateur a terminé l'Assistant, l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> est appelé à chaque fabrique de projet pour effectuer la mise à niveau réelle.  Pour faciliter la sauvegarde, les méthodes d'IVsProjectUpgradeViaFactory fournissent le service d' <xref:Microsoft.VisualStudio.Shell.Interop.SVsUpgradeLogger> pour stocker les détails de la mise à niveau.  ce service ne peut pas être mis en cache.  
  
 Après avoir mis à jour tous les fichiers globaux appropriés, chaque fabrique de projet peut instancier un projet.  La mise en ? uvre de projet doit prendre en charge <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>.  La méthode d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> est ensuite appelée pour mettre à niveau tous les éléments de projet appropriés.  
  
> [!NOTE]
>  la méthode d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> ne fournit pas le service de SVsUpgradeLogger.  ce service peut être obtenu en appelant <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A>.  
  
## Meilleures pratiques  
 Utilisez le service d' <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave> pour vérifier si vous pouvez modifier un fichier avant de le modifier, et pouvez enregistrer avant de les stocker.  Cela permet à votre copie de sauvegarde et de mise à niveau des implémentations gérer les fichiers projet sous contrôle de code source, fichiers avec des autorisations insuffisantes, etc.  
  
 Utilisez le service d' <xref:Microsoft.VisualStudio.Shell.Interop.SVsUpgradeLogger> pendant toutes les phases de sauvegarde et le mettre à niveau pour fournir des informations sur la réussite ou l'échec de la mise à niveau.  
  
 Pour plus d'informations sur la sauvegarde et la mise à niveau des projets, consultez les commentaires pour IVsProjectUpgrade dans vsshell2.idl.  
  
## Voir aussi  
 [Projets](../../extensibility/internals/projects.md)   
 [Mise à niveau de projets personnalisés](../../misc/upgrading-custom-projects.md)   
 [Mise à niveau d’éléments de projet](../../misc/upgrading-project-items.md)