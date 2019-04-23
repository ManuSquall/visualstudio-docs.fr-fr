---
title: La mise à niveau des projets | Microsoft Docs
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
ms.openlocfilehash: 7e97e21b2d08d7398a4372ac31cda63b5cfb9fe9
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60100597"
---
# <a name="upgrading-projects"></a>Mise à niveau des projets
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Modifie le modèle de projet d’une version de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] à l’autre peut nécessiter que les projets et solutions être mis à niveau afin qu’ils puissent exécuter sur la version plus récente. Le [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] fournit des interfaces qui peuvent être utilisées pour implémenter la mise à niveau de prise en charge dans vos propres projets.  
  
## <a name="upgrade-strategies"></a>Stratégies de mise à niveau  
 Pour prendre en charge une mise à niveau, votre implémentation de système de projet doit définir et implémenter une stratégie de mise à niveau. Pour déterminer votre stratégie, vous pouvez choisir de prendre en charge la sauvegarde de la côte à côte (SxS), sauvegarde de copie ou les deux.  
  
- Sauvegarde de la côte à côte signifie qu’un projet copie seulement les fichiers que vous avez besoin de la mise à niveau en place, ajout d’un suffixe de nom fichier approprié, par exemple, « .old ».  
  
- Sauvegarde de copie signifie qu’un projet copie tous les éléments de projet à un emplacement de sauvegarde fourni par l’utilisateur. Les fichiers appropriés à l’emplacement du projet d’origine sont ensuite mis à niveau.  
  
## <a name="how-upgrade-works"></a>Comment mettre à niveau Works  
 Lorsqu’une solution créée dans une version antérieure de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] est ouvert dans une version plus récente, les vérifications de l’IDE de fichier pour déterminer si elle doit être mis à niveau la solution. Si la mise à niveau est requise, le **Assistant Mise à niveau** est lancée automatiquement pour guider l’utilisateur au long du processus de mise à niveau.  
  
 Lorsqu’une solution a besoin de la mise à niveau, il interroge chaque fabrique de projet pour sa stratégie de mise à niveau. La stratégie détermine si la fabrique de projet prend en charge la sauvegarde de copie ou côte à côte. Les informations sont envoyées à la **Assistant Mise à niveau**, qui collecte les informations requises pour la sauvegarde et présente les options applicables à l’utilisateur.  
  
### <a name="multi-project-solutions"></a>Solutions à projets multiples  
 Si une solution contient plusieurs projets et les stratégies de mise à niveau sont différents, tels que lorsqu’un projet C++ qui prend uniquement en charge la sauvegarde de la côte à côte et un projet Web qui prennent uniquement en charge la sauvegarde de copie, les fabriques de projet doivent négocier la stratégie de mise à niveau.  
  
 La solution interroge chaque fabrique de projet pour <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory>. Il appelle ensuite <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject_CheckOnly%2A> pour vérifier si les fichiers de projets globale doivent être de la mise à niveau et à déterminer les stratégies de mise à niveau pris en charge. Le **Assistant Mise à niveau** est ensuite appelée.  
  
 Une fois que l’utilisateur a terminé l’Assistant, <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> est appelée sur chaque fabrique de projet pour effectuer la mise à niveau réelle. Pour faciliter les sauvegardes, les méthodes de IVsProjectUpgradeViaFactory fournissent la <xref:Microsoft.VisualStudio.Shell.Interop.SVsUpgradeLogger> service pour consigner les détails de la mise à niveau. Ce service ne peut pas être mis en cache.  
  
 Après la mise à jour tous les fichiers globales pertinents, chaque fabrique de projet peut choisir instancier un projet. L’implémentation de projet doit prendre en charge <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>. Le <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> méthode est ensuite appelée pour mettre à niveau tous les éléments de projet approprié.  
  
> [!NOTE]
>  Le <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> méthode ne fournit pas le service SVsUpgradeLogger. Ce service peut être obtenu en appelant <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A>.  
  
## <a name="best-practices"></a>Meilleures pratiques  
 Utilisez le <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave> service pour vérifier si vous pouvez modifier un fichier avant de le modifier et que vous pouvez l’enregistrer avant de l’enregistrer. Cela vous aidera votre sauvegarde et gérer les implémentations de mise à niveau des fichiers de projet sous contrôle de code source, les fichiers dotés d’autorisations suffisantes et ainsi de suite.  
  
 Utilisez le <xref:Microsoft.VisualStudio.Shell.Interop.SVsUpgradeLogger> service pendant toutes les phases de la sauvegarde et de mettre à niveau des informations sur la réussite ou l’échec de la mise à niveau.  
  
 Pour plus d’informations sur la sauvegarde et la mise à niveau des projets, consultez les commentaires pour IVsProjectUpgrade dans vsshell2.idl.  
  
## <a name="see-also"></a>Voir aussi  
 [Projets](../../extensibility/internals/projects.md)   
 [La mise à niveau de projets personnalisés](../../misc/upgrading-custom-projects.md)   
 [Mise à niveau d’éléments de projet](../../misc/upgrading-project-items.md)
