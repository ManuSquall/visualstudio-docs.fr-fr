---
title: "Ajout d’éléments à l’ajouter un nouvel élément boîtes de dialogue | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Add New Item dialog box, adding items
ms.assetid: 2f70863b-425b-4e65-86b4-d6a898e29dc7
caps.latest.revision: "18"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5a16698863e92e5bbae4e888502788dd76b04f56
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="adding-items-to-the-add-new-item-dialog-boxes"></a>Ajout d’éléments à l’ajouter un nouvel élément boîtes de dialogue
Le processus d’ajout d’éléments à la **ajouter un nouvel élément** boîte de dialogue commence par les clés de Registre. Comme indiqué dans les entrées de Registre suivantes, la section AddItemTemplates contient le chemin d’accès et le nom du répertoire dans lequel les éléments mis à disposition dans le **ajouter un nouvel élément** boîte de dialogue sont placés.  
  
> [!NOTE]
>  Le tableau qui suit immédiatement le segment de code contient des informations supplémentaires sur l’entrée de Registre.  
  
 Cette section se trouve sous [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0Exp\Projects].  
  
 Le premier GUID est le CLSID pour les projets de ce type ; le second GUID indique le type de projet enregistré pour les modèles d’ajouter des éléments.  
  
 \\{C061DB26-5833-11D2-96F5-000000000000} \AddItemTemplates\TemplateDirs\ {ACEF4EB2-57CF-11D2-96F4-000000000000} \1  
  
 @="#6"  
  
 « TemplatesDir « = »\<chemin d’installation de Visual Studio SDK\\\VSIntegration\\\SomeFolder\\\SomePackage\\\SomeProject\\\SomeProjectItems »  
  
 « SortPriority » = dword:00000064  
  
|Nom|Type|Données (fichier .rgs)|Description|  
|----------|----------|-----------------------------|-----------------|  
|@ (Par défaut)|REG_SZ|#% IDS_ADDITEM_TEMPLATES_ENTRY %|ID de ressource pour **ajouter un élément** modèles.|  
|Val TemplatesDir|REG_SZ|%TEMPLATE_PATH%\ SomeProjectItems|Chemin d’accès des éléments de projet affichés dans la boîte de dialogue pour le **ajouter un nouvel élément** Assistant.|  
|Val SortPriority|REG_DWORD|100 ([!INCLUDE[vcprx64](../../extensibility/internals/includes/vcprx64_md.md)])|Détermine l’ordre de tri dans le nœud d’arborescence de fichiers affichés dans le **ajouter un nouvel élément** boîte de dialogue.|  
  
> [!NOTE]
>  Les GUID pour les types de projet Visual c# et Visual Basic sont les suivantes :[!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]: {FAE04EC0-301F-11D3-BF4B-00C04F79EFBC}[!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]: {F184B08F-C81C-45F6-A57F-5ABD9991F28F}  
  
 Le répertoire répertoriés pour TemplateDirs, qui est % TEMPLATE_PATH%\SomeProjectItems, est le nœud situé à gauche de la **ajouter un nouvel élément** arborescence de boîte de dialogue. Dans l’arborescence des éléments supplémentaires sont basées sur le sous-répertoire dans le répertoire racine. Les fichiers disponibles pour être ajoutés au projet sont les éléments dans le volet droit de la **ajouter un nouvel élément** boîte de dialogue.  
  
 En règle générale, ce dossier contient les fichiers de modèle pour votre projet comme un modèle HTML ou les fichiers .cpp et tous les fichiers .vsz pour les Assistants de démarrage. Pour contrôler la façon dont les éléments sont affichés, vous pouvez également inclure des fichiers .vsdir pour la localisation des icônes et des noms de répertoires. La chaîne localisée est la légende qui apparaît dans la boîte de dialogue qui représente ce nœud dans l’arborescence de la boîte de dialogue Ajouter un nouvel élément.  
  
 Toutefois, il est inutile d’avoir tous les éléments dans un seul fichier .vsdir. Vous pouvez avoir un seul fichier .vsdir pour chaque élément dans le répertoire. Pour plus d’informations, consultez [Assistant (. Fichier vsz)](../../extensibility/internals/wizard-dot-vsz-file.md) et [Description du modèle active (. Fichiers VSDir)](../../extensibility/internals/template-directory-description-dot-vsdir-files.md).  
  
> [!NOTE]
>  Les fichiers .vsdir dans les répertoires de modèle sont facultatifs. Si vous souhaitez simplement placer un élément de projet dans le répertoire et les afficher dans le **ajouter un nouvel élément** boîte de dialogue, vous pouvez placer ce fichier dans le répertoire de modèles spécifié dans l’instruction TemplatesDir. Le fichier puis apparaîtront dans le volet droit de la **ajouter un nouvel élément** boîte de dialogue pour ce projet. Toutefois, si vous souhaitez afficher une légende localisée pour le fichier ou d’une icône, vous devez inclure au moins un fichier .vsdir dans le répertoire de modèles.  
  
## <a name="grouping-project-items"></a>Regroupement des éléments de projet  
 Si vous souhaitez contiennent des groupes de modèles dans des dossiers de la **ajouter un nouvel élément** arborescence de boîte de dialogue, vous devez disposer des sous-répertoires sous le répertoire racine du modèle avec les éléments dans les. Lorsque le **ajouter un nouvel élément** boîte de dialogue est affichée aux utilisateurs, ils seront également voir les sous-dossiers et être en mesure de sélectionner des éléments de projet à partir de celles-ci.  
  
 L’ordre de priorité dans le segment de code détermine où ce répertoire modèle sera créé dans l’arborescence par rapport aux autres éléments du nœud d’arbre. Pour le **ajouter un nouvel élément** boîte de dialogue, l’ordre de priorité est tout ce dont vous devez inclure afin que vos éléments s’afficheront dans l’emplacement approprié dans la boîte de dialogue.  
  
 Vous pouvez également implémenter la <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2> interface pour filtrer ce qui est affiché dans le **ajouter un nouvel élément** boîte de dialogue. En implémentant cette interface, vous pouvez configurer Active d’un modèle sur le disque qui contient, par exemple, 50 fichiers de modèle et l’Assistant. De cette façon, vous pouvez avoir différents types de projets avec 20 fichiers qui appartiennent à un type de projet, les autres 30 fichiers qui appartiennent à un autre type de projet et tous les fichiers dans un type de projet général. De cette manière, selon le projet de modèle est créé, vous pouvez afficher un ensemble différent de fichiers de modèle.  
  
 Par exemple, supposons que vous avez des projets Web et projets de client dans un projet Visual Basic. Web forms ne sont pas des éléments utiles à ajouter à un projet client, et les formulaires windows ne sont pas des éléments utiles à ajouter à un projet de serveur Web. Par conséquent, vous pouvez créer un répertoire de modèle qui contient tous les fichiers pour les deux types de projet. Puis en implémentant <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>, vous pouvez masquer des éléments qui ne doivent pas être affichées en fonction du type de projet ou les paramètres du projet dans le projet.  
  
## <a name="filtering-project-items"></a>Le filtrage des éléments de projet  
 `IVsFilterAddProjectItemDlg2`fournit de filtrage d’éléments dans l’arborescence (volet gauche) et les fichiers de projet (volet droit), comme suit :  
  
-   En fonction des noms localisés (légendes affichées dans la boîte de dialogue qui est contenue dans le fichier .vsdir) fournie par `IVsFilterAddProjectItemDlg`.  
  
-   Par les noms réels des fichiers et dossiers sur le disque (non localisée, aucun fichier .vsdir) fournie par `IVsFilterAddProjectItemDlg`.  
  
-   Par catégorie, fournie par `IVsFilterAddProjectItemDlg2`.  
  
 Pour filtrer par catégorie, fournissez une chaîne de catégorie pour un article dans le fichier .vsdir, tels que « Web form » ou « Client » en Visual Basic. Ensuite, le code de la boîte de dialogue récupère la classification de la catégorie à partir du fichier .vsdir et passe à vous. Vous pouvez ensuite passer ces informations à votre implémentation de `IVsFilterAddProjectItemDlg2` pour filtrer le **ajouter un nouvel élément** boîte de dialogue catégories. Vous pouvez également filtrer les éléments pour les pages Web ou en cas d’application client Win32. En outre, vous pouvez identifier [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] des éléments en tant que Microsoft Foundation Classes (MFC) ou des éléments de modèle active de la bibliothèque (ATL). Lorsque vous identifiez ces éléments, le système de projet peut définir ses propres classifications afin que le système peut être filtré en fonction des catégories et classifications.  
  
 Si vous implémentez cette fonctionnalité de filtre, il est inutile de mapper une table de chaque élément doit être masqué. Vous pouvez simplement classer les éléments dans les types et placer les classifications dans l’ou les fichiers .vsdir. Ensuite, vous pouvez masquer tous les éléments qui ont une classification spécifique en implémentant l’interface. De cette façon, vous pouvez apporter les éléments de la **ajouter un nouvel élément** dynamique de boîte de dialogue en fonction de l’état dans le projet.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>   
 [L’inscription des modèles de projet et élément](../../extensibility/internals/registering-project-and-item-templates.md)   
 [CATID d’extendeurs pour les objets qui sont généralement utilisés pour étendre des projets](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)   
 [Ajout de projet et modèles d’élément de projet](../../extensibility/internals/adding-project-and-project-item-templates.md)   
 [Description du modèle active (. Fichiers VSDir)](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)   
 [Fichier Assistant (.Vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)