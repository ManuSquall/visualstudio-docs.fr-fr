---
title: Ajout d’éléments à l’ajouter un nouvel élément boîtes de dialogue | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Add New Item dialog box, adding items
ms.assetid: 2f70863b-425b-4e65-86b4-d6a898e29dc7
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3b1287bfe04a16c1e610aa9044399fa7b936d383
ms.sourcegitcommit: 1c2ed640512ba613b3bbbc9ce348e28be6ca3e45
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/03/2018
ms.locfileid: "39499862"
---
# <a name="add-items-to-the-add-new-item-dialog-box"></a>Ajouter des éléments à la boîte de dialogue Ajouter un nouvel élément
Le processus d’ajout d’éléments à la **ajouter un nouvel élément** boîte de dialogue commence par les clés de Registre. Comme indiqué dans les entrées de Registre suivantes, le **AddItemTemplates** section contient le chemin d’accès et le nom du répertoire dans lequel les éléments mis à disposition dans le **ajouter un nouvel élément** boîte de dialogue sont placés.  
  
> [!NOTE]
>  Le tableau qui suit immédiatement le segment de code contient des informations supplémentaires sur l’entrée de Registre.  
  
 Cette section se trouve sous **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0Exp\Projects**.
  
 Le premier GUID est le CLSID pour les projets de ce type ; le second GUID indique le type de projet enregistré pour les modèles d’ajouter des éléments :  
 
 **\\{C061DB26-5833-11D2-96F5-000000000000} \\AddItemTemplates\\TemplatesDir\\{ACEF4EB2-57CF-11D2-96F4-000000000000}\\1**
  
 **@** = #6 
  
 **TemplatesDir** = \\&lt;chemin d’installation de Visual Studio SDK&gt;\\VSIntegration\\&lt;SomeFolder&gt; \\ &lt;SomePackage&gt;\\&lt;SomeProject&gt;\\&lt;SomeProjectItems&gt;
  
 **SortPriority** = dword:00000064
  
|Name|Type|Données (à partir de *.rgs* fichier)|Description|  
|----------|----------|-----------------------------|-----------------|  
|@ (Par défaut)|REG_SZ|#% IDS_ADDITEM_TEMPLATES_ENTRY %|ID de ressource pour **ajouter un élément** modèles.|  
|Val TemplatesDir|REG_SZ|% TEMPLATE_PATH %\\&lt;SomeProjectItems&gt;|Chemin d’accès des éléments de projet affiché dans la boîte de dialogue pour le **ajouter un nouvel élément** Assistant.|  
|Val SortPriority|REG_DWORD|100 ([!INCLUDE[vcprx64](../../extensibility/internals/includes/vcprx64_md.md)])|Détermine l’ordre de tri dans le nœud d’arbre de fichiers affichés dans le **ajouter un nouvel élément** boîte de dialogue.|  
  
> [!NOTE]
>  Les GUID pour les types de projets Visual Basic et Visual c# sont les suivantes : 
- [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]: {FAE04EC0-301F-11D3-BF4B-00C04F79EFBC}
- [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]: {F184B08F-C81C-45F6-A57F-5ABD9991F28F}  
  
 Le répertoire répertorié pour **TemplatesDir**, qui est *TEMPLATE_PATH %\\&lt;SomeProjectItems&gt;*, est le nœud sur le côté gauche de la **ajouter Un nouvel élément** arborescence de boîte de dialogue. Dans l’arborescence des éléments supplémentaires sont basées sur le sous-répertoire dans le répertoire racine. Les fichiers disponibles à ajouter au projet sont les éléments dans le volet droit de la **ajouter un nouvel élément** boîte de dialogue.  
  
 En règle générale, ce dossier contient les fichiers de modèle pour votre projet comme un modèle HTML ou *.cpp* fichier et tout *.vsz* fichiers de démarrage d’Assistants. Pour contrôler la façon dont les éléments sont affichés, vous pouvez également inclure *.vsdir* fichiers pour la localisation des noms de répertoires et les icônes. La chaîne localisée est la légende qui apparaît dans la boîte de dialogue qui représente ce nœud dans le **ajouter un nouvel élément** arborescence de boîte de dialogue.  
  
 Toutefois, il est inutile d’avoir tous les éléments dans un *.vsdir* fichier. Vous pouvez avoir un *.vsdir* fichier pour chaque élément dans le répertoire. Pour plus d’informations, consultez [fichier Assistant (.vsz)](../../extensibility/internals/wizard-dot-vsz-file.md) et [fichiers de description (.vsdir) de répertoire de modèle](../../extensibility/internals/template-directory-description-dot-vsdir-files.md).  
  
> [!NOTE]
>  Le *.vsdir* fichiers dans les répertoires de modèle sont facultatifs. Si vous souhaitez simplement placer un élément de projet dans le répertoire et l’afficher dans le **ajouter un nouvel élément** boîte de dialogue, vous pouvez placer ce fichier dans le répertoire de modèles spécifié dans le **TemplatesDir** instruction. Le fichier puis apparaîtront dans le volet droit de la **ajouter un nouvel élément** boîte de dialogue pour ce projet. Toutefois, si vous souhaitez afficher une légende localisée pour le fichier ou une icône, vous devez inclure au moins un *.vsdir* fichier dans le répertoire de modèles.  
  
## <a name="group-project-items"></a>Regrouper des éléments de projet  
 Si vous souhaitez contiennent des groupes de modèles dans les dossiers dans le **ajouter un nouvel élément** arborescence de boîte de dialogue, vous devez disposer des sous-répertoires du répertoire de modèle racine avec les éléments dans les. Lorsque le **ajouter un nouvel élément** boîte de dialogue s’affiche aux utilisateurs, ils seront également voir les sous-dossiers et être en mesure de sélectionner des éléments de projet à partir de celles-ci.  
  
 La priorité de tri dans le segment de code détermine où ce répertoire de modèle sera créé dans l’arborescence par rapport aux autres éléments du nœud d’arbre. Pour le **ajouter un nouvel élément** boîte de dialogue, la priorité de tri est tout ce que vous devez inclure afin que vos éléments seront affichera à l’emplacement approprié dans la boîte de dialogue.  
  
 Vous pouvez également implémenter le <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2> interface pour filtrer ce qui est affiché dans le **ajouter un nouvel élément** boîte de dialogue. En implémentant cette interface, vous pouvez configurer un modèle directory sur le disque qui contient, par exemple, 50 fichiers de modèle et l’Assistant. De cette façon, vous pouvez avoir différents types de projets avec 20 fichiers qui appartiennent à un type de projet, les autres 30 fichiers qui appartiennent à un autre type de projet et tous les fichiers disponibles dans un type de projet général. De cette manière, en fonction du projet auquel le modèle est créé, vous pouvez afficher un autre ensemble de fichiers de modèle.  
  
 Par exemple, dans un projet Visual Basic, vous pouvez avoir les projets Web et client. Les Web forms ne sont pas des éléments utiles à ajouter à un projet client, et windows forms n’est pas utiles éléments à ajouter à un projet de serveur Web. Par conséquent, vous pouvez créer un répertoire de modèle qui contient tous les fichiers pour les deux types de projet. Ensuite, en implémentant <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>, vous pouvez masquer des éléments qui ne doivent pas être affichées en fonction du type de projet ou les paramètres du projet dans le projet.  
  
## <a name="filter-project-items"></a>Filtrer les éléments de projet  
 `IVsFilterAddProjectItemDlg2` fournit de filtrage d’éléments dans l’arborescence (volet gauche) et les fichiers de projet (volet droit) comme suit :  
  
-   En fonction des noms localisés (légendes affichées dans la boîte de dialogue qui est contenue dans le *.vsdir* fichier) fourni par `IVsFilterAddProjectItemDlg`.  
  
-   Par les noms réels des fichiers et dossiers sur le disque (non localisé — aucune *.vsdir* fichier) fourni par `IVsFilterAddProjectItemDlg`.  
  
-   Par catégorie, fourni par `IVsFilterAddProjectItemDlg2`.  
  
 Pour filtrer par catégorie, fournissez une chaîne de catégorie à un élément dans le *.vsdir* fichier, telles que *formulaire Web* ou *élément Client* en Visual Basic. Le code de la boîte de dialogue récupère ensuite la classification de la catégorie à partir de la *.vsdir* de fichier et le transmet à vous. Vous pouvez ensuite passer ces informations à votre implémentation de `IVsFilterAddProjectItemDlg2` pour filtrer le **ajouter un nouvel élément** boîte de dialogue par catégories. Vous pouvez également filtrer les éléments pour les pages Web ou comme des cas d’application client Win32. En outre, vous pouvez identifier [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] des éléments étiquetés comme Microsoft Foundation Classes (MFC) ou des éléments de modèle active de la bibliothèque (ATL). Lorsque vous identifiez ces éléments, le système de projet peut définir ses propres classifications afin que le système peut être filtré en fonction de catégories et classifications.  
  
 Si vous implémentez cette fonctionnalité de filtre, il est inutile mapper une table de chaque élément doit être masqué. Vous pouvez simplement classer des éléments dans les types et placer les classifications dans le *.vsdir* ou les fichiers. Vous pouvez masquer les éléments qui ont une classification spécifique en implémentant l’interface. Dans cette façon, vous pouvez rendre les éléments dans le **ajouter un nouvel élément** dynamique de boîte de dialogue en fonction de l’état au sein du projet.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>   
 [Inscrire les modèles de projet et d’élément](../../extensibility/internals/registering-project-and-item-templates.md)   
 [CATID des objets qui sont généralement utilisés pour étendre des projets](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)   
 [Ajouter le projet et les modèles d’élément de projet](../../extensibility/internals/adding-project-and-project-item-templates.md)   
 [Fichiers de description (.vsdir) de répertoire de modèle](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)   
 [Fichier de l’Assistant (.vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)