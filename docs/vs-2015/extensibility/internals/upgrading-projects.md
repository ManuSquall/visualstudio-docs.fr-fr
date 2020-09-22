---
title: Mise à niveau des projets | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- upgrading VSPackages
- upgrading applications, strategies
- VSPackages, upgrade support
ms.assetid: e01cb44a-8105-4cf4-8223-dfae65f8597a
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8e838cb02aa1a620356f96d9e77f1752797ac409
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90839397"
---
# <a name="upgrading-projects"></a>Mise à niveau des projets
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Les modifications apportées au modèle de projet d’une version de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] à la suivante peuvent nécessiter la mise à niveau des projets et des solutions afin qu’ils puissent s’exécuter sur la version plus récente. [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)]Fournit des interfaces qui peuvent être utilisées pour implémenter la prise en charge de la mise à niveau dans vos propres projets.  
  
## <a name="upgrade-strategies"></a>Stratégies de mise à niveau  
 Pour prendre en charge une mise à niveau, l’implémentation de votre système de projet doit définir et implémenter une stratégie de mise à niveau. Pour déterminer votre stratégie, vous pouvez choisir de prendre en charge la sauvegarde côte à côte (SxS), la sauvegarde de copie, ou les deux.  
  
- La sauvegarde SxS signifie qu’un projet copie uniquement les fichiers nécessitant une mise à niveau sur place, en ajoutant un suffixe de nom de fichier approprié, par exemple, « . old ».  
  
- La sauvegarde de copie signifie qu’un projet copie tous les éléments de projet vers un emplacement de sauvegarde fourni par l’utilisateur. Les fichiers appropriés à l’emplacement du projet d’origine sont ensuite mis à niveau.  
  
## <a name="how-upgrade-works"></a>Fonctionnement de la mise à niveau  
 Quand une solution créée dans une version antérieure de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] est ouverte dans une version plus récente, l’IDE vérifie le fichier solution pour déterminer s’il doit être mis à niveau. Si la mise à niveau est requise, l' **Assistant Mise à niveau** est automatiquement lancé pour guider l’utilisateur tout au long du processus de mise à niveau.  
  
 Quand une solution doit être mise à niveau, elle interroge chaque fabrique de projet pour sa stratégie de mise à niveau. La stratégie détermine si la fabrique de projets prend en charge la sauvegarde de copie ou la sauvegarde SxS. Les informations sont envoyées à l' **Assistant Mise à niveau**, qui collecte les informations requises pour la sauvegarde et présente les options applicables à l’utilisateur.  
  
### <a name="multi-project-solutions"></a>Solutions à projets multiples  
 Si une solution contient plusieurs projets et que les stratégies de mise à niveau diffèrent, par exemple quand un projet C++ qui prend uniquement en charge la sauvegarde SxS et un projet Web qui prend uniquement en charge la sauvegarde de copie, les fabriques de projet doivent négocier la stratégie de mise à niveau.  
  
 La solution interroge chaque fabrique de projet pour <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> . Il appelle ensuite <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject_CheckOnly%2A> pour voir si les fichiers projet globaux doivent être mis à niveau et pour déterminer les stratégies de mise à niveau prises en charge. L' **Assistant Mise à niveau** est alors appelé.  
  
 Une fois que l’utilisateur a terminé l’Assistant, <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> est appelé sur chaque fabrique de projet pour effectuer la mise à niveau réelle. Pour faciliter la sauvegarde, les méthodes IVsProjectUpgradeViaFactory fournissent au <xref:Microsoft.VisualStudio.Shell.Interop.SVsUpgradeLogger> service la journalisation des détails du processus de mise à niveau. Ce service ne peut pas être mis en cache.  
  
 Après la mise à jour de tous les fichiers globaux pertinents, chaque fabrique de projet peut choisir d’instancier un projet. L’implémentation du projet doit prendre en charge <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> . La <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> méthode est ensuite appelée pour mettre à niveau tous les éléments de projet pertinents.  
  
> [!NOTE]
> La <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> méthode ne fournit pas le service SVsUpgradeLogger. Ce service peut être obtenu en appelant <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A> .  
  
## <a name="best-practices"></a>Bonnes pratiques  
 Utilisez le <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave> service pour vérifier si vous pouvez modifier un fichier avant de le modifier et l’enregistrer avant de l’enregistrer. Cela aidera vos implémentations de sauvegarde et de mise à niveau à gérer les fichiers projet sous contrôle de code source, les fichiers avec des autorisations insuffisantes, etc.  
  
 Utilisez le <xref:Microsoft.VisualStudio.Shell.Interop.SVsUpgradeLogger> service pendant toutes les phases de la sauvegarde et de la mise à niveau pour fournir des informations sur la réussite ou l’échec du processus de mise à niveau.  
  
 Pour plus d’informations sur la sauvegarde et la mise à niveau des projets, consultez les commentaires pour IVsProjectUpgrade dans vsshell2. idl.  
  
## <a name="see-also"></a>Voir aussi  
 [Projet](../../extensibility/internals/projects.md)   
 [Mise à niveau de projets personnalisés](../../misc/upgrading-custom-projects.md)   
 [Mise à niveau d’éléments de projet](../../misc/upgrading-project-items.md)
