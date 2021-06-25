---
title: Ajout d’éléments aux boîtes de dialogue Ajouter un nouvel élément | Microsoft Docs
description: Découvrez comment ajouter des éléments à la boîte de dialogue Ajouter un nouvel élément dans Visual Studio, afin de pouvoir afficher des modèles et des éléments de projet à utiliser dans vos projets.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- Add New Item dialog box, adding items
ms.assetid: 2f70863b-425b-4e65-86b4-d6a898e29dc7
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 70bc1a0c4d90d8cab0b2193550773745fc2dd47e
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112904407"
---
# <a name="add-items-to-the-add-new-item-dialog-box"></a>Ajouter des éléments à la boîte de dialogue Ajouter un nouvel élément
Le processus d’ajout d’éléments à la boîte de dialogue **Ajouter un nouvel élément** démarre avec les clés de registre. Comme indiqué dans les entrées de Registre suivantes, la section **AddItemTemplates** contient le chemin d’accès et le nom du répertoire dans lequel les éléments rendus disponibles dans la boîte de dialogue **Ajouter un nouvel élément** sont placés.

> [!NOTE]
> La table qui suit immédiatement le segment de code contient des informations supplémentaires sur l’entrée de registre.

 Cette section se trouve sous **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0Exp\Projects**.

 Le premier GUID est le CLSID pour les projets de ce type ; le deuxième GUID indique le type de projet inscrit pour les modèles ajouter des éléments :

 **\\{C061DB26-5833-11D2-96F5-000000000000} \\ AddItemTemplates \\ TemplatesDir \\ {ACEF4EB2-57CF-11D2-96F4-000000000000} \\ 1**

 **@** = #6

   =  \\ TemplatesDir &lt; Chemin d’installation du kit de développement logiciel Visual Studio &gt; \\ VSIntegration \\ &lt; SomeFolder &gt; \\ &lt; SomePackage &gt; \\ &lt; SomeProject &gt; \\ &lt; SomeProjectItems&gt;

 **SortPriority** = DWORD : 00000064

| Nom | Type | Données (à partir du fichier *. RGS* ) | Description |
|------------------|-----------| - | - |
| @ (Valeur par défaut) | REG_SZ | #% IDS_ADDITEM_TEMPLATES_ENTRY% | ID de ressource pour ajouter des modèles d' **élément** . |
| Val TemplatesDir | REG_SZ | % TEMPLATE_PATH% \\ &lt; SomeProjectItems&gt; | Chemin d’accès aux éléments de projet affichés dans la boîte de dialogue de l’Assistant **Ajout d’un nouvel élément** . |
| Val SortPriority | REG_DWORD | 100 ( [!INCLUDE[vcprx64](../../extensibility/internals/includes/vcprx64_md.md)] ) | Détermine l’ordre de tri dans le nœud d’arbre des fichiers affichés dans la boîte de dialogue **Ajouter un nouvel élément** . |

> [!NOTE]
> Les GUID pour les types de projet Visual C# et Visual Basic sont les suivants :
> - [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]: {FAE04EC0-301F-11D3-BF4B-00C04F79EFBC}
> - [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]: {F184B08F-C81C-45F6-A57F-5ABD9991F28F}

 Le répertoire listé pour **TemplatesDir**, qui est *% TEMPLATE_PATH% \\ &lt; SomeProjectItems &gt;*, est le nœud sur le côté gauche de l’arborescence de la boîte de dialogue **Ajouter un nouvel élément** . Les éléments supplémentaires dans l’arborescence sont basés sur le sous-répertoire de ce répertoire racine. Les fichiers disponibles pour être ajoutés au projet sont les éléments du volet droit de la boîte de dialogue **Ajouter un nouvel élément** .

 En règle générale, ce dossier contient les fichiers de modèle de votre projet, tels qu’un fichier HTML de modèle ou *. cpp* , ainsi que tous les fichiers *. vsz* pour le démarrage des assistants. Pour contrôler la façon dont les éléments sont affichés, vous pouvez également inclure des fichiers *. vsdir* pour la localisation des noms de répertoires et des icônes. La chaîne localisée est la légende qui apparaît dans la boîte de dialogue qui représente ce nœud dans l’arborescence de la boîte de dialogue **Ajouter un nouvel élément** .

 Toutefois, vous n’avez pas besoin d’avoir tous les éléments dans un seul fichier *. vsdir* . Vous pouvez avoir un fichier *. vsdir* pour chaque élément de l’annuaire. Pour plus d’informations, consultez fichiers de l' [Assistant (. vsz)](../../extensibility/internals/wizard-dot-vsz-file.md) et [fichiers de description du répertoire de modèles (. vsdir)](../../extensibility/internals/template-directory-description-dot-vsdir-files.md).

> [!NOTE]
> Les fichiers *. vsdir* dans les répertoires de modèles sont facultatifs. Si vous souhaitez simplement placer un élément de projet dans le répertoire et l’afficher dans la boîte de dialogue **Ajouter un nouvel élément** , vous pouvez placer ce fichier dans le répertoire de modèles spécifié dans l’instruction **TemplatesDir** . Le fichier est ensuite affiché dans le volet droit de la boîte de dialogue **Ajouter un nouvel élément** pour ce projet. Toutefois, si vous souhaitez afficher une légende localisée pour le fichier ou une icône, vous devez inclure au moins un fichier *. vsdir* dans le répertoire des modèles.

## <a name="group-project-items"></a>Grouper les éléments de projet
 Si vous souhaitez inclure des groupes de modèles dans des dossiers de l’arborescence de la boîte de dialogue **Ajouter un nouvel élément** , vous devez avoir des sous-répertoires sous le répertoire de modèles racine avec les éléments qu’ils contiennent. Quand la boîte de dialogue **Ajouter un nouvel élément** s’affiche pour les utilisateurs, ceux-ci voient également les sous-dossiers et peuvent y sélectionner des éléments de projet.

 La priorité de tri dans le segment de code détermine où ce répertoire de modèles sera créé dans l’arborescence par rapport aux autres éléments du nœud d’arbre. Pour la boîte de dialogue **Ajouter un nouvel élément** , la priorité de tri est tout ce que vous devez inclure afin que vos éléments s’affichent à l’emplacement approprié dans la boîte de dialogue.

 Vous pouvez également implémenter l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2> interface pour filtrer ce qui est affiché dans la boîte de dialogue **Ajouter un nouvel élément** . En implémentant cette interface, vous pouvez configurer un répertoire de modèles sur le disque contenant, par exemple, des fichiers de modèle 50 et d’Assistant. De cette façon, vous pouvez avoir différents types de projets avec 20 fichiers qui appartiennent à un type de projet, les 30 autres fichiers appartenant à un autre type de projet et tous les fichiers disponibles dans un type général de projet. De cette manière, selon le modèle de projet créé, vous pouvez afficher un ensemble différent de fichiers de modèle.

 Par exemple, dans un projet Visual Basic, vous pouvez avoir des projets Web et des projets clients. Les Web Forms ne sont pas des éléments utiles à ajouter à un projet client, et les Windows Forms ne sont pas des éléments utiles à ajouter à un projet de serveur Web. Par conséquent, vous pouvez créer un répertoire de modèle qui contient tous les fichiers pour les deux types de projet. Ensuite, en implémentant <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2> , vous pouvez masquer les éléments qui ne doivent pas être affichés en fonction du type de paramètres de projet ou de projet dans le projet.

## <a name="filter-project-items"></a>Filtrer les éléments de projet
 `IVsFilterAddProjectItemDlg2` permet de filtrer les éléments dans l’arborescence (volet gauche) et les fichiers projet (volet droit) des manières suivantes :

- Par les noms localisés (sous-titres affichés dans la boîte de dialogue contenue dans le fichier *. vsdir* ) fournis par `IVsFilterAddProjectItemDlg` .

- Par les noms réels des fichiers et dossiers sur le disque (non localisé — aucun fichier *. vsdir* ) fourni par `IVsFilterAddProjectItemDlg` .

- Par catégorie, fourni par `IVsFilterAddProjectItemDlg2` .

  Pour filtrer par catégorie, fournissez une chaîne de catégorie à un élément dans le fichier *. vsdir* , tel que *formulaire Web* ou *élément client* dans Visual Basic. Le code de la boîte de dialogue récupère ensuite la classification des catégories à partir du fichier *. vsdir* et vous le transmet. Vous pouvez ensuite passer ces informations à votre implémentation de `IVsFilterAddProjectItemDlg2` pour filtrer la boîte de dialogue **Ajouter un nouvel élément** par catégories. Vous pouvez également filtrer les éléments pour les pages Web ou les cas d’application cliente Win32. En outre, vous pouvez identifier [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] les éléments avec balises en tant que Microsoft Foundation classes (MFC) ou éléments ATL (Active Template Library). Lorsque vous identifiez ces éléments, le système de projet peut définir ses propres classifications afin que le système puisse être filtré en fonction des catégories et des classifications.

  Si vous implémentez cette fonctionnalité de filtre, vous n’avez pas besoin de mapper une table de tous les éléments qui doivent être masqués. Vous pouvez simplement classer les éléments en types et placer les classifications dans le ou les fichiers *. vsdir* . Vous pouvez ensuite masquer tous les éléments qui ont une classification spécifique en implémentant l’interface. De cette façon, vous pouvez rendre les éléments de la boîte de dialogue **Ajouter un nouvel élément** dynamiques en fonction de l’État dans le projet.

## <a name="see-also"></a>Voir aussi
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>
- [Inscrire des modèles de projet et d’élément](../../extensibility/internals/registering-project-and-item-templates.md)
- [CATID des objets qui sont généralement utilisés pour étendre des projets](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)
- [Ajouter des modèles de projet et d’élément de projet](../../extensibility/internals/adding-project-and-project-item-templates.md)
- [Fichiers de description du répertoire de modèles (. vsdir)](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)
- [Fichier Assistant (. vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)
