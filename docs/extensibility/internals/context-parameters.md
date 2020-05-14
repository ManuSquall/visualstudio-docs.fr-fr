---
title: Paramètres de contexte Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- wizards, context parameters
- context parameters
ms.assetid: 1a062dcb-8a8f-40dd-bea9-3d10f9448966
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6673ad8f26c94165635b5f1bc652b91dcbbfd24f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709306"
---
# <a name="context-parameters"></a>Paramètres de contexte
Dans [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] l’environnement de développement intégré (IDE), vous pouvez ajouter des assistants au **nouveau projet,** **ajouter un nouvel élément**ou ajouter des boîtes de dialogue Sub **Project.** Les assistants ajoutés sont disponibles sur le menu **Fichier** ou en cliquant à droite sur un projet dans **Solution Explorer**. L’IDE transmet les paramètres de contexte à la mise en œuvre de l’assistant. Les paramètres de contexte définissent l’état du projet lorsque l’IDE appelle l’assistant.

 L’IDE commence les <xref:Microsoft.VisualStudio.Shell.Interop.VSADDITEMOPERATION> sorciers en plaçant le drapeau <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.AddItem%2A> dans l’appel de l’IDE à la méthode pour le projet. Lorsqu’il est défini, `IVsExtensibility::RunWizardFile` le projet doit faire exécuter la méthode en utilisant le nom d’assistant enregistré ou GUID et d’autres paramètres de contexte que l’IDE lui transmet.

## <a name="context-parameters-for-new-project"></a>Paramètres de contexte pour un nouveau projet

| Paramètre | Description |
|-------------------------| - |
| `WizardType` | Type d’assistant enregistré (<xref:EnvDTE.Constants.vsWizardNewProject>) ou le GUID qui indique le type d’assistant. Dans [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] la mise en œuvre, le GUID pour l’assistant est '0F90E1D0-4999-11D1-B6D1-00A0C90F2744'. |
| `ProjectName` | Une chaîne qui [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] est le nom unique du projet. |
| `LocalDirectory` | Emplacement local des dossiers de projet de travail. |
| `InstallationDirectory` | Itinéraire de l’installation [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] est. |
| `FExclusive` | Drapeau Boolean qui indique que le projet devrait fermer des solutions ouvertes. |
| `SolutionName` | Nom du fichier de solution sans la partie répertoire ou *l’extension .sln.* Le nom de fichier *.suo* est également créé en utilisant `SolutionName`. Lorsque cet argument n’est pas <xref:EnvDTE._Solution.Create%2A> une chaîne vide, l’assistant utilise avant d’ajouter le projet avec <xref:EnvDTE._Solution.AddFromTemplate%2A>. Si ce nom est une <xref:EnvDTE._Solution.AddFromTemplate%2A> chaîne <xref:EnvDTE._Solution.Create%2A>vide, utilisez sans appeler . |
| `Silent` | Boolean qui indique si l’assistant **Finish** doit courir en`TRUE`silence comme si Finish ont été cliqués ( ). |

## <a name="context-parameters-for-add-new-item"></a>Paramètres contextuelles pour ajouter un nouvel élément

| Paramètre | Description |
|-------------------------| - |
| `WizardType` | Type d’assistant enregistré (<xref:EnvDTE.Constants.vsWizardAddItem>) ou le GUID qui indique le type d’assistant. Dans [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] la mise en œuvre, le GUID pour l’assistant est '0F90E1D1-4999-11D1-B6D1-00A0C90F2744'. |
| `ProjectName` | Une chaîne qui [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] est le nom unique du projet. |
| `ProjectItems` | Emplacement local qui contient des fichiers de projet de travail. |
| `ItemName` | Nom de l’élément qui doit être ajouté. Ce nom est soit le nom de fichier par défaut ou le nom de fichier que l’utilisateur tape à partir de la boîte de dialogue **Add Items.** Le nom est basé sur les drapeaux qui sont définis dans le fichier *.vsdir.* Le nom peut être une valeur nulle. |
| `InstallationDirectory` | Itinéraire de l’installation [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] est. |
| `Silent` | Boolean qui indique si l’assistant **Finish** doit courir en`TRUE`silence comme si Finish ont été cliqués ( ). |

## <a name="context-parameters-for-add-sub-project"></a>Paramètres contextuelles pour Add Sub Project

| Paramètre | Description |
|-------------------------| - |
| `WizardType` | Type d’assistant enregistré (<xref:EnvDTE.Constants.vsWizardAddSubProject>) ou le GUID qui indique le type d’assistant. Dans [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] la mise en œuvre, le GUID pour l’assistant est '0F90E1D2-4999-11D1-B6D1-00A0C90F2744'. |
| `ProjectName` | Une chaîne qui [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] est le nom unique du projet. |
| `ProjectItems` | Pointeur `ProjectItems` à la collection sur laquelle l’assistant opère. Ce pointeur est transmis à l’assistant en fonction de la sélection de la hiérarchie du projet. Un utilisateur sélectionne généralement un dossier dans lequel mettre l’élément, puis appelle la boîte de dialogue **Add Item** du projet. |
| `LocalDirectory` | Emplacement local des dossiers de projet de travail. |
| `ItemName` | Nom de l’élément qui doit être ajouté. Ce nom est soit le nom de fichier par défaut ou le nom de fichier que l’utilisateur tape à partir de la boîte de dialogue **Add Items.** Le nom est basé sur les drapeaux qui sont définis dans le fichier *.vsdir.* Le nom peut être une valeur nulle. |
| `InstallationDirectory` | Parcours de l’installation. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] |
| `Silent` | Boolean qui indique si l’assistant **Finish** doit courir en`TRUE`silence comme si Finish ont été cliqués ( ). |

## <a name="see-also"></a>Voir aussi
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject2>
- [Paramètres personnalisés](../../extensibility/internals/custom-parameters.md)
- [Assistants](../../extensibility/internals/wizards.md)
- [Fichier Wizard (.vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)
- [Paramètres de contexte pour le lancement des assistants](https://msdn.microsoft.com/Library/051a10f4-9e45-4604-b344-123044f33a24)
