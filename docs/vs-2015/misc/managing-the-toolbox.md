---
title: La gestion de la boîte à outils | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- Toolbox [Visual Studio SDK], automatic tab selection
- Toolbox [Visual Studio SDK], managing
ms.assetid: 3b052047-f6db-46dd-b3bf-da1c348ee410
caps.latest.revision: 33
manager: jillfra
ms.openlocfilehash: ba4b166cc409dd2c50c258a9b82ee34c22e9b084
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62838675"
---
# <a name="managing-the-toolbox"></a>Managing the Toolbox
Le [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] permet à un VSPackage, tel qu’un éditeur ou un concepteur, de gérer l’appartenance et l’apparence de la **boîte à outils**.  
  
 De plus, la **boîte à outils** peut être gérée de manière automatisée. Pour plus d’informations sur la gestion d’une boîte à outils grâce à l’automatisation, consultez [Comment : Contrôler la boîte à outils](http://msdn.microsoft.com/library/c9d8a18a-d2bc-43d4-a803-601bfc6a6599).  
  
## <a name="automatic-toolbox-tab-selection"></a>Sélection automatique d’onglets dans la boîte à outils  
 Vous pouvez activer automatiquement un onglet ou une catégorie de la **boîte à outils** en fonction de l’éditeur ou du concepteur actuellement actif. Par exemple, si un concepteur de formulaires est activé, vous pouvez souhaiter sélectionner l’onglet **Tous les Windows Forms** .  
  
 Cette prise en charge est limitée aux éditeurs et concepteurs nécessitant ce qui suit :  
  
1. L’implémentation d’un objet usine pour fournir des instances de l’éditeur ou du concepteur. Pour plus d’informations sur l’implémentation d’un objet usine pour un concepteur ou un éditeur, consultez [Editor Factories](../extensibility/editor-factories.md).  
  
2. Inscription de l’onglet de boîte à outils qui est activé automatiquement si l’éditeur ou le concepteur est ouvert.  
  
## <a name="controlling-the-toolbox"></a>Contrôle de la boîte à outils  
 En complément de la prise en charge de l’automatisation, le [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] fournit les interfaces suivantes qui permettent aux VSPackages un plus grand contrôle sur la gestion de la **boîte à outils** .  
  
|Interface|Description|  
|---------------|-----------------|  
|<xref:System.Drawing.Design.IToolboxService>|Permet aux applications de gérer, ajouter et supprimer <xref:System.Drawing.Design.ToolboxItem> objets à partir de la **boîte à outils**. Permet également la configuration de l’apparence et des catégories de la **boîte à outils** .|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2>|Permet de gérer, ajouter et supprimer des contrôles ActiveX de la **boîte à outils** , ainsi que de configurer l’apparence et les catégories de la **boîte à outils** .|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox3>|Étend les fonctionnalités de <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2> en fournissant une prise en charge complète pour la persistance et la localisation.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox4>||  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox5>||  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox6>||  
  
 Plusieurs points importants sont à prendre en compte quand vous utilisez ces interfaces :  
  
- <xref:System.Drawing.Design.IToolboxService> est disponible uniquement pour les VSPackages MPF (Managed Package Framework).  
  
- Contrôles ne peuvent pas être ajoutés directement à la **boîte à outils** à l’aide de <xref:System.Drawing.Design.IToolboxService>.  
  
- Un VSPackage doit utiliser <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2> pour ajouter des contrôles ou héberger le contrôle dans un contrôle wrapper dérivé de <xref:System.Windows.Forms.AxHost>.  
  
   Visual Studio fournit l’outil `Aximp.exe` pour l’automatisation de l’encapsulation des contrôles ActiveX dans un contrôle dérivé de <xref:System.Windows.Forms.AxHost>. Pour plus d’informations, consultez [Aximp.exe (importateur de contrôles ActiveX Windows Forms)](http://msdn.microsoft.com/library/482c0d83-7144-4497-b626-87d2351b78d0).  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox>, <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2> et <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox3> sont des interfaces COM disponibles via les assemblys PIA.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2> dérive de <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox> et implémente toutes ses méthodes.  
  
   Les objets obtiennent uniquement une instance de <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2>.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox3> ne dérive pas de <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2> et n’implémente pas ses méthodes.  
  
   Les objets nécessitant des fonctionnalités dans les deux interfaces doivent obtenir des instances des deux interfaces depuis l’environnement.  
  
- Quand vous utilisez <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2> et <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox3>, les informations concernant les noms canoniques (non localisés) des onglets sont gérées par les méthodes <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox3.GetIDOfTab%2A> et <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox3.SetIDOfTab%2A>.  
  
- Quand vous utilisez <xref:System.Drawing.Design.IToolboxService>, c’est à l’implémenteur de gérer les informations localisées, telles que les noms des catégories.  
  
  Utilisez le mécanisme de paramètres pour permettre aux utilisateurs d’enregistrer les paramètres de la **boîte à outils** auxquels ils peuvent accéder à l’aide de la commande **Paramètres d’importation/exportation** , située dans le menu **Outils** de l’IDE. Pour plus d’informations sur l’utilisation des paramètres, consultez [Extending User Settings and Options](../extensibility/extending-user-settings-and-options.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Extension de la boîte à outils](../misc/extending-the-toolbox.md)