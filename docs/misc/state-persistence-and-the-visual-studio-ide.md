---
title: "Persistance de l’&#233;tat et IDE Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "paramètres de l’IDE, persistance de l’état"
  - "paramètres utilisateur (SDK Visual Studio), persistance"
  - "Options Outils (SDK Visual Studio), paramètres de persistance des pages"
  - "IDE, persistance de l’état"
  - "persistance, paramètres utilisateur"
ms.assetid: fdd49bb1-ed3b-4428-b685-de65c3215c1c
caps.latest.revision: 24
caps.handback.revision: 24
manager: "douge"
---
# Persistance de l’&#233;tat et IDE Visual Studio
L'ordre de **paramètres d'importation\/exportation** dans le menu d' **Outils** de l'environnement de développement intégré \(IDE\) \(IDE\) importe et exporte les personnalisations de l'environnement de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .  Les API de paramètres de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] dans [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] permettent à un VSPackage pour définir une ou plusieurs catégories de paramètres \(groupes de variables de l'état\) à rendre lorsqu'un utilisateur sélectionne la commande de **paramètres d'importation\/exportation** .  
  
 GUID identifie uniquement chaque paramètre catégorie et est défini dans sa propre entrée du Registre, appelée comme *un point de paramètres personnalisés*.  
  
> [!NOTE]
>  Les implémentations standard des pages options d' **Outils**, du **boîte à outils**, et de l' `Microsoft.VisualStudio.Shell.DialogPage` fournissent automatiquement la prise en charge de la persistance.  L'API de paramètres peut substituer le mécanisme par défaut.  Pour plus d'informations, consultez [Extension de la boîte à outils](../misc/extending-the-toolbox.md), [Pages Options](../misc/options-pages.md) et <xref:Microsoft.VisualStudio.Shell.DialogPage>.  
  
## Dans cette section  
 [Prise en charge pour les paramètres utilisateur](../extensibility/internals/support-for-user-settings.md)  
 décrit les paramètres du Registre \(point de paramètres personnalisés\) et des attributs utilisés pour spécifier une implémentation de paramètres de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] utilisée par un VSPackage donné.  
  
 [Procédure : exportation de paramètres à l’aide des assemblys d’interopérabilité](../misc/how-to-export-settings-by-using-interop-assemblies.md)  
 Fournit une description détaillée de la manière d'implémenter la prise en charge de stocker des données de configuration à l'aide de le mécanisme de paramètres de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] pour les VSPackages basé sur un assembly d'interopérabilité.  
  
 [Procédure : utilisation des assemblys PIA pour importer des paramètres](../misc/how-to-use-interop-assemblies-to-import-settings.md)  
 Fournit une description détaillée de la manière d'implémenter une prise en charge de l'extraction des données de configuration à l'aide de le mécanisme de paramètres de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] pour les VSPackages basé sur un assembly d'interopérabilité.  
  
 [Exportation de paramètres](../misc/exporting-settings.md)  
 Inclut une description détaillée de la manière d'implémenter la prise en charge de stocker des données de configuration à l'aide de le mécanisme de paramètres de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] pour le package managé VSPackages basé sur une infrastructure.  
  
 [Importation des paramètres](/visual-cpp/misc/importing-settings)  
 Fournit une description détaillée de la manière d'implémenter une prise en charge de l'extraction des données de configuration à l'aide de le mécanisme de paramètres de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] pour le package managé VSPackages basé sur une infrastructure.  
  
## Rubriques connexes  
 [Working with Settings](http://msdn.microsoft.com/fr-fr/4c0a56ab-6091-4ebc-9dc7-52c40846bacb)  
 Décrit comment gérer des sections d'exportation et importation de l'IDE.  
  
 [Pages Options](../misc/options-pages.md)  
 Décrit la prise en charge que [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] fournit automatiquement pour gérer les nouvelles pages options existantes ou les création d' **Outils**.  
  
 [Extension de la boîte à outils](../misc/extending-the-toolbox.md)  
 Explique la prise en charge que [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] fournit automatiquement pour la gestion ou étendre **boîte à outils**.  
  
 [Options et paramètres d'extension utilisateur](../extensibility/extending-user-settings-and-options.md)  
 Décrit comment programmer votre VSPackage pour obtenir et conserver les préférences de l'utilisateur.