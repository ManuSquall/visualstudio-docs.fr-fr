---
title: "Ajout d&#39;&#233;l&#233;ments &#224; l&#39;ajouter un nouvel &#233;l&#233;ment bo&#238;tes de dialogue | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Ajouter la boîte de dialogue Nouvel élément, ajouter des éléments"
ms.assetid: 2f70863b-425b-4e65-86b4-d6a898e29dc7
caps.latest.revision: 18
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 18
---
# Ajout d&#39;&#233;l&#233;ments &#224; l&#39;ajouter un nouvel &#233;l&#233;ment bo&#238;tes de dialogue
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Le processus d'ajout d'éléments à la **Ajouter un nouvel élément** boîte de dialogue commence par les clés de Registre. Comme indiqué dans les entrées de Registre suivantes, la section AddItemTemplates contient le chemin d'accès et le nom du répertoire dans lequel les éléments mis à disposition dans le **Ajouter un nouvel élément** boîte de dialogue sont placés.  
  
> [!NOTE]
>  Le tableau qui suit immédiatement le segment de code contient des informations supplémentaires sur l'entrée de Registre.  
  
 Cette section se trouve sous \[HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VisualStudio\\14.0Exp\\Projects\].  
  
 Le premier GUID est le CLSID pour les projets de ce type ; le second GUID indique le type de projet enregistré pour les modèles d'ajouter des éléments.  
  
 \\{C061DB26\-5833\-11D2\-96F5\-000000000000}\\AddItemTemplates\\TemplateDirs\\ {ACEF4EB2\-57CF\-11D2\-96F4\-000000000000} \\1  
  
 @\="\#6"  
  
 « TemplatesDir « \= » \< path\\\\VSIntegration\\\\SomeFolder\\\\SomePackage\\\\SomeProject\\\\SomeProjectItems d'installation de Visual Studio SDK »  
  
 « SortPriority » \= dword:00000064  
  
|Nom|Type|Données \(fichier .rgs\)|Description|  
|---------|----------|------------------------------|-----------------|  
|@ \(Par défaut\)|REG\_SZ|\#% IDS\_ADDITEM\_TEMPLATES\_ENTRY %|ID de ressource pour **Ajouter un élément** modèles.|  
|Val TemplatesDir|REG\_SZ|%TEMPLATE\_PATH%\\ SomeProjectItems|Chemin d'accès des éléments de projet affiché dans la boîte de dialogue pour le **Ajouter un nouvel élément** Assistant.|  
|Val SortPriority|REG\_DWORD|100 \([!INCLUDE[vcprx64](../../extensibility/internals/includes/vcprx64_md.md)]\)|Détermine l'ordre de tri dans le nœud de l'arborescence des fichiers affichés dans le **Ajouter un nouvel élément** boîte de dialogue.|  
  
> [!NOTE]
>  Les GUID pour les types de projets Visual c\# et Visual Basic sont les suivants :[!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]: {FAE04EC0\-301F\-11D3\-BF4B\-00C04F79EFBC}[!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]: {F184B08F\-C81C\-45F6\-A57F\-5ABD9991F28F}  
  
 Le répertoire répertorié pour TemplateDirs, qui est de % TEMPLATE\_PATH%\\SomeProjectItems, est le nœud sur le côté gauche de la **Ajouter un nouvel élément** arborescence de boîte de dialogue. Dans l'arborescence des éléments supplémentaires sont basées sur le sous\-répertoire dans le répertoire racine. Les fichiers disponibles à ajouter au projet sont les éléments dans le volet droit de la **Ajouter un nouvel élément** boîte de dialogue.  
  
 En règle générale, ce dossier contient les fichiers de modèle pour votre projet comme un modèle HTML ou fichier .cpp et tous les fichiers .vsz pour démarrer des Assistants. Pour contrôler la façon dont les éléments sont affichés, vous pouvez également inclure les fichiers .vsdir pour la localisation des icônes et des noms de répertoire. La chaîne localisée est la légende qui apparaît dans la boîte de dialogue qui représente ce nœud dans l'arborescence de la boîte de dialogue Ajouter un nouvel élément.  
  
 Toutefois, il est inutile d'avoir tout dans un seul fichier .vsdir. Vous pouvez avoir un fichier .vsdir pour chaque élément dans le répertoire. Pour plus d’informations, consultez [Assistant \(. Fichier vsz\)](../../extensibility/internals/wizard-dot-vsz-file.md) et [Description du modèle active \(. Fichiers VSDir\)](../../extensibility/internals/template-directory-description-dot-vsdir-files.md).  
  
> [!NOTE]
>  Les fichiers .vsdir dans les répertoires de modèle sont facultatifs. Si vous souhaitez simplement placer un élément de projet dans le répertoire et les afficher dans le **Ajouter un nouvel élément** boîte de dialogue, vous pouvez placer ce fichier dans le répertoire de modèles spécifié dans l'instruction TemplatesDir. Le fichier puis apparaîtra dans le volet droit de la **Ajouter un nouvel élément** boîte de dialogue pour ce projet. Toutefois, si vous souhaitez afficher une légende pour le fichier ou une icône localisée, vous devez inclure au moins un fichier .vsdir dans le répertoire de modèles.  
  
## Regrouper les éléments de projet  
 Si vous souhaitez contiennent des groupes de modèles dans les dossiers dans le **Ajouter un nouvel élément** arborescence de boîte de dialogue, vous devez disposer des sous\-répertoires sous le répertoire racine du modèle avec les éléments dans les. Lors de la **Ajouter un nouvel élément** boîte de dialogue s'affiche pour les utilisateurs, qu'ils également voir les sous\-dossiers et être en mesure de sélectionner des éléments de projet à partir de ceux\-ci.  
  
 L'ordre de priorité dans le segment de code détermine où ce répertoire de modèle sera créé dans l'arborescence par rapport aux autres éléments du nœud d'arbre. Pour le **Ajouter un nouvel élément** boîte de dialogue, l'ordre de priorité est tout ce que vous devez inclure afin que vos éléments apparaît dans l'emplacement approprié dans la boîte de dialogue.  
  
 Vous pouvez également implémenter le <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2> interface pour filtrer les informations figurant dans le **Ajouter un nouvel élément** boîte de dialogue. En implémentant cette interface, vous pouvez configurer Active d'un modèle sur le disque qui contient, par exemple, 50 fichiers modèle et l'Assistant. De cette façon, vous pouvez avoir différents types de projets avec 20 fichiers qui appartiennent à un type de projet, les 30 autres fichiers qui appartiennent à un autre type de projet et tous les fichiers dans un type de projet général. De cette manière, selon lequel le projet de modèle est créé, vous pouvez afficher un ensemble de fichiers de modèle différent.  
  
 Par exemple, dans un projet Visual Basic, vous devrez les projets Web et client. Les Web forms ne sont pas des éléments utiles à ajouter à un projet client, et les formulaires windows ne sont pas des éléments utiles à ajouter à un projet de serveur Web. Par conséquent, vous pouvez créer un répertoire de modèle qui contient tous les fichiers pour les deux types de projet. Puis en implémentant <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>, vous pouvez masquer les éléments qui ne doivent pas être affichées en fonction du type de projet ou les paramètres du projet dans le projet.  
  
## Filtrage des éléments de projet  
 `IVsFilterAddProjectItemDlg2` fournit du filtrage d'éléments dans l'arborescence \(volet gauche\), les fichiers projet \(volet droit\) comme suit :  
  
-   Par des noms localisés \(légendes affichées dans la boîte de dialogue qui est contenue dans le fichier .vsdir\) fournie par `IVsFilterAddProjectItemDlg`.  
  
-   Par les noms réels des fichiers et dossiers sur le disque \(non localisée, aucun fichier .vsdir\) fournie par `IVsFilterAddProjectItemDlg`.  
  
-   Par catégorie, fournie par `IVsFilterAddProjectItemDlg2`.  
  
 Pour filtrer par catégorie, fournissez une chaîne de catégorie pour un article dans le fichier .vsdir, tels que « Web form » ou « Client » dans Visual Basic. Le code de la boîte de dialogue puis récupère la classification de la catégorie à partir du fichier .vsdir et le transmet à vous. Vous pouvez ensuite passer ces informations à votre implémentation de `IVsFilterAddProjectItemDlg2` pour filtrer le **Ajouter un nouvel élément** boîte de dialogue catégories. Vous pouvez également filtrer les éléments pour les pages Web ou en cas d'application client Win32. En outre, vous pouvez identifier [!INCLUDE[vcprvc](../../debugger/includes/vcprvc_md.md)] des éléments étiquetés comme Microsoft Foundation Classes \(MFC\) ou des éléments de bibliothèque \(ATL\) de modèle actif. Lorsque vous identifiez ces éléments, le système de projet peut définir ses propres classifications afin que le système peut être filtré en fonction des catégories et classifications.  
  
 Si vous implémentez cette fonctionnalité de filtre, il est inutile de mapper une table de chaque élément doit être masqué. Vous pouvez simplement classer les éléments dans les types et placer les classifications dans l'ou les fichiers .vsdir. Vous pouvez masquer les éléments qui ont une classification spécifique en implémentant l'interface. Dans cette façon, vous pouvez rendre les éléments dans le **Ajouter un nouvel élément** dynamique de boîte de dialogue en fonction de l'état dans le projet.  
  
## Voir aussi  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>   
 [L’inscription de projet et modèles d’élément](../../extensibility/internals/registering-project-and-item-templates.md)   
 [CATID des objets qui sont généralement utilisés pour étendre des projets](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)   
 [Ajout de projet et modèles d'élément de projet](../../extensibility/internals/adding-project-and-project-item-templates.md)   
 [Description du modèle active \(. Fichiers VSDir\)](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)   
 [Assistant \(. Fichier vsz\)](../../extensibility/internals/wizard-dot-vsz-file.md)