---
title: Paramètres de contexte | Microsoft Docs
description: Découvrez les paramètres de contexte dans l’environnement de développement intégré (IDE) de Visual Studio qui définissent l’état d’un projet lorsque vous ajoutez ou implémentez un Assistant.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- wizards, context parameters
- context parameters
ms.assetid: 1a062dcb-8a8f-40dd-bea9-3d10f9448966
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 536e5abf92884c5c19399e73b4e1773e66919657
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112898225"
---
# <a name="context-parameters"></a>Paramètres de contexte
Dans l' [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] environnement de développement intégré (IDE), vous pouvez ajouter des assistants aux boîtes de dialogue **nouveau projet**, **Ajouter un nouvel élément** ou **Ajouter un sous-projet** . Les assistants ajoutés sont disponibles dans le menu **fichier** ou en cliquant avec le bouton droit sur un projet dans **Explorateur de solutions**. L’IDE transmet les paramètres de contexte à l’implémentation de l’Assistant. Les paramètres de contexte définissent l’état du projet lorsque l’IDE appelle l’Assistant.

 L’IDE démarre les assistants en définissant l' <xref:Microsoft.VisualStudio.Shell.Interop.VSADDITEMOPERATION> indicateur dans l’appel de l’IDE à la <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.AddItem%2A> méthode pour le projet. Quand il est défini, le projet doit faire en sorte `IVsExtensibility::RunWizardFile` que la méthode soit exécutée à l’aide du nom de l’Assistant inscrit ou du GUID et d’autres paramètres de contexte que l’environnement de développement intégré (IDE) lui transmet.

## <a name="context-parameters-for-new-project"></a>Paramètres de contexte pour le nouveau projet

| Paramètre | Description |
|-------------------------| - |
| `WizardType` | Type d’Assistant inscrit ( <xref:EnvDTE.Constants.vsWizardNewProject> ) ou GUID qui indique le type de l’Assistant. Dans l' [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] implémentation, le GUID de l’Assistant est {0F90E1D0-4999-11D1-B6D1-00A0C90F2744}. |
| `ProjectName` | Chaîne qui est le nom de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] projet unique. |
| `LocalDirectory` | Emplacement local des fichiers de projet de travail. |
| `InstallationDirectory` | Le chemin d’accès du répertoire de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] est l’installation de. |
| `FExclusive` | Indicateur booléen qui indique que le projet doit fermer les solutions ouvertes. |
| `SolutionName` | Nom du fichier solution sans la partie répertoire ou l’extension *. sln* . Le nom de fichier *. suo* est également créé à l’aide de `SolutionName` . Lorsque cet argument n’est pas une chaîne vide, l’Assistant utilise <xref:EnvDTE._Solution.Create%2A> avant d’ajouter le projet avec <xref:EnvDTE._Solution.AddFromTemplate%2A> . Si ce nom est une chaîne vide, utilisez <xref:EnvDTE._Solution.AddFromTemplate%2A> sans appeler <xref:EnvDTE._Solution.Create%2A> . |
| `Silent` | Valeur booléenne qui indique si l’Assistant doit s’exécuter en mode silencieux comme si l’utilisateur a cliqué sur **Terminer** ( `TRUE` ). |

## <a name="context-parameters-for-add-new-item"></a>Paramètres de contexte pour l’ajout d’un nouvel élément

| Paramètre | Description |
|-------------------------| - |
| `WizardType` | Type d’Assistant inscrit ( <xref:EnvDTE.Constants.vsWizardAddItem> ) ou GUID qui indique le type de l’Assistant. Dans l' [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] implémentation, le GUID de l’Assistant est {0F90E1D1-4999-11D1-B6D1-00A0C90F2744}. |
| `ProjectName` | Chaîne qui est le nom de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] projet unique. |
| `ProjectItems` | Emplacement local qui contient les fichiers de projet de travail. |
| `ItemName` | Nom de l’élément à ajouter. Ce nom est soit le nom de fichier par défaut, soit le nom de fichier que l’utilisateur tape dans la boîte de dialogue **Ajouter des éléments** . Le nom est basé sur les indicateurs définis dans le fichier *. vsdir* . Le nom peut être une valeur null. |
| `InstallationDirectory` | Le chemin d’accès du répertoire de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] est l’installation de. |
| `Silent` | Valeur booléenne qui indique si l’Assistant doit s’exécuter en mode silencieux comme si l’utilisateur a cliqué sur **Terminer** ( `TRUE` ). |

## <a name="context-parameters-for-add-sub-project"></a>Paramètres de contexte pour ajouter un sous-projet

| Paramètre | Description |
|-------------------------| - |
| `WizardType` | Type d’Assistant inscrit ( <xref:EnvDTE.Constants.vsWizardAddSubProject> ) ou GUID qui indique le type de l’Assistant. Dans l' [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] implémentation, le GUID de l’Assistant est {0F90E1D2-4999-11D1-B6D1-00A0C90F2744}. |
| `ProjectName` | Chaîne qui est le nom de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] projet unique. |
| `ProjectItems` | Pointeur vers la `ProjectItems` collection sur laquelle l’Assistant s’exécute. Ce pointeur est passé à l’Assistant en fonction de la sélection de la hiérarchie du projet. En général, un utilisateur sélectionne un dossier dans lequel placer l’élément, puis appelle la boîte de dialogue **Ajouter un élément** du projet. |
| `LocalDirectory` | Emplacement local des fichiers de projet de travail. |
| `ItemName` | Nom de l’élément à ajouter. Ce nom est soit le nom de fichier par défaut, soit le nom de fichier que l’utilisateur tape dans la boîte de dialogue **Ajouter des éléments** . Le nom est basé sur les indicateurs définis dans le fichier *. vsdir* . Le nom peut être une valeur null. |
| `InstallationDirectory` | Chemin d’accès du répertoire de l' [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] installation. |
| `Silent` | Valeur booléenne qui indique si l’Assistant doit s’exécuter en mode silencieux comme si l’utilisateur a cliqué sur **Terminer** ( `TRUE` ). |

## <a name="see-also"></a>Voir aussi
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject2>
- [Paramètres personnalisés](../../extensibility/internals/custom-parameters.md)
- [Assistants](../../extensibility/internals/wizards.md)
- [Fichier Assistant (. vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)
- [Paramètres de contexte pour le lancement des assistants](/previous-versions/tz690efs(v=vs.140))