---
title: Paramètres de contexte | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- wizards, context parameters
- context parameters
ms.assetid: 1a062dcb-8a8f-40dd-bea9-3d10f9448966
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2efdbe1027bc3a85ed9eef02db9cec3d10504fca
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58952930"
---
# <a name="context-parameters"></a>Paramètres de contexte
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Dans le [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] l’environnement de développement intégré (IDE), vous pouvez ajouter des Assistants pour le **nouveau projet**, **ajouter un nouvel élément**, ou **ajouter un projet Sub** boîtes de dialogue. Les Assistants d’ajout sont disponibles sur le **fichier** menu ou en double-cliquant sur un projet dans **l’Explorateur de solutions**. L’IDE transmet les paramètres de contexte à l’implémentation de l’Assistant. Les paramètres de contexte définissent l’état du projet lors de l’IDE appelle l’Assistant.  
  
 Assistants de démarrage de l’IDE en définissant le <xref:Microsoft.VisualStudio.Shell.Interop.VSADDITEMOPERATION> indicateur dans l’appel de l’IDE à la <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.AddItem%2A> méthode pour le projet. Lorsque la valeur, le projet doit provoquer la `IVsExtensibility::RunWizardFile` méthode à exécuter à l’aide du nom de l’Assistant inscrit ou GUID et autres paramètres de contexte qui lui passe l’IDE.  
  
## <a name="context-parameters-for-new-project"></a>Paramètres de contexte pour le nouveau projet  
  
|Paramètre|Description|  
|---------------|-----------------|  
|`WizardType`|Inscrit le type d’Assistant (<xref:EnvDTE.Constants.vsWizardNewProject>) ou le GUID qui indique le type d’Assistant. Dans le [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] implémentation, le GUID de l’Assistant est {0F90E1D0-4999-11D1-B6D1-00A0C90F2744}.|  
|`ProjectName`|Chaîne qui est l’unique [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] nom du projet.|  
|`LocalDirectory`|Emplacement local de l’utilisation des fichiers projet.|  
|`InstallationDirectory`|Chemin du répertoire de le [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] est l’installation.|  
|`FExclusive`|Indicateur booléen qui indique que le projet doit fermer les solutions ouvertes.|  
|`SolutionName`|Nom du fichier de solution sans la partie répertoire ou de l’extension .sln. Le nom de fichier .suo est également créé à l’aide de `SolutionName`. Si cet argument n’est pas une chaîne vide, l’Assistant utilise <xref:EnvDTE._Solution.Create%2A> avant d’ajouter le projet avec <xref:EnvDTE._Solution.AddFromTemplate%2A>. Si ce nom est une chaîne vide, utilisez <xref:EnvDTE._Solution.AddFromTemplate%2A> sans appeler <xref:EnvDTE._Solution.Create%2A>.|  
|`Silent`|Valeur booléenne qui indique si l’Assistant doit s’exécuter en mode silencieux comme si **Terminer** premier clic (`TRUE`).|  
  
## <a name="context-parameters-for-add-new-item"></a>Paramètres de contexte pour ajoutent un nouvel élément  
  
|Paramètre|Description|  
|---------------|-----------------|  
|`WizardType`|Inscrit le type d’Assistant (<xref:EnvDTE.Constants.vsWizardAddItem>) ou le GUID qui indique le type d’Assistant. Dans le [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] implémentation, le GUID de l’Assistant est {0F90E1D1-4999-11D1-B6D1-00A0C90F2744}.|  
|`ProjectName`|Chaîne qui est l’unique [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] nom du projet.|  
|`ProjectItems`|Emplacement local qui contient les fichiers de projet de travail.|  
|`ItemName`|Nom de l’élément qui doit être ajouté. Ce nom est le nom de fichier par défaut ou le nom de fichier que l’utilisateur tape à partir de la **ajouter les éléments** boîte de dialogue. Le nom est basé sur les indicateurs sont définis dans le fichier .vsdir. Le nom peut être une valeur null.|  
|`InstallationDirectory`|Chemin du répertoire de le [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] est l’installation.|  
|`Silent`|Valeur booléenne qui indique si l’Assistant doit s’exécuter en mode silencieux comme si **Terminer** premier clic (`TRUE`).|  
  
## <a name="context-parameters-for-add-sub-project"></a>Paramètres de contexte pour ajouter un projet Sub  
  
|Paramètre|Description|  
|---------------|-----------------|  
|`WizardType`|Inscrit le type d’Assistant (<xref:EnvDTE.Constants.vsWizardAddSubProject>) ou le GUID qui indique le type d’Assistant. Dans le [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] implémentation, le GUID de l’Assistant est {0F90E1D2-4999-11D1-B6D1-00A0C90F2744}.|  
|`ProjectName`|Chaîne qui est l’unique [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] nom du projet.|  
|`ProjectItems`|Pointeur vers le `ProjectItems` regroupement sur lequel fonctionne l’Assistant. Ce pointeur est passé à l’Assistant selon la sélection de hiérarchie de projet. Un utilisateur sélectionne généralement un dossier dans lequel placer l’élément, puis appelle le projet **ajouter un élément** boîte de dialogue.|  
|`LocalDirectory`|Emplacement local de l’utilisation des fichiers projet.|  
|`ItemName`|Nom de l’élément qui doit être ajouté. Ce nom est le nom de fichier par défaut ou le nom de fichier que l’utilisateur tape à partir de la **ajouter les éléments** boîte de dialogue. Le nom est basé sur les indicateurs sont définis dans le fichier .vsdir. Le nom peut être une valeur null.|  
|`InstallationDirectory`|Chemin du répertoire de le [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] est l’installation.|  
|`Silent`|Valeur booléenne qui indique si l’Assistant doit s’exécuter en mode silencieux comme si **Terminer** premier clic (`TRUE`).|  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject2>   
 [Paramètres personnalisés](../../extensibility/internals/custom-parameters.md)   
 [Assistants](../../extensibility/internals/wizards.md)   
 [Assistant (. Fichier vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)   
 [Paramètres de contexte pour le lancement d’Assistants](http://msdn.microsoft.com/library/051a10f4-9e45-4604-b344-123044f33a24)
