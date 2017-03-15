---
title: "Cr&#233;ation de pages d’options &#224; l’aide d’Automation | Microsoft Docs"
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
  - "pages Outils Options [Kit de développement logiciel (SDK) Visual Studio], créer"
  - "automation [Kit de développement logiciel (SDK) Visual Studio], créer des pages Outils Options"
ms.assetid: 05ec0337-58fe-4746-8e85-7fb97f285522
caps.latest.revision: 12
caps.handback.revision: 12
manager: "douge"
---
# Cr&#233;ation de pages d’options &#224; l’aide d’Automation
VSPackages managé peut utiliser l'automation pour étendre l'environnement de développement intégré \(IDE\) de \(IDE\) [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] en ajoutant des pages **options** au menu d' **Outils** .  
  
 Une page d' **options d'outils** est un contrôle utilisateur, et est écrite comme n'importe quel autre contrôle utilisateur.  En général, vous utiliseriez un des générateurs de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] l'IDE pour créer l'objet et pour ajouter des contrôles utilisateur.  
  
> [!NOTE]
>  les pages d'**options d'outils** implémentées en tant que boîte de dialogue, à l'aide de `DialogProc` pour traiter les messages windows, doivent être des boîtes de dialogue non modale, et ne doivent pas appeler la fonction d' `EndDialog` .  
  
 Vous devez utiliser l'objet Automation que le VSPackage fournit à l'environnement aux propriétés de contrôle utilisateur de stockage.  
  
## Prise en charge de l'automation des pages options Outils implémentées avec les assemblys d'interopérabilité  
 Pour prendre en charge le modèle Automation, un VSPackage doit créer et stocker un objet Automation.  Consultez [Grâce à l’automatisation pour les packages VS](../extensibility/internals/providing-automation-for-vspackages.md) pour plus d'informations.  
  
 Lorsque le code qui utilise le modèle Automation appelle `DTE.Properties` pour la collection de propriétés d'une page donnée d' **options d'outils** , l'IDE utilise l'objet Automation fourni par l'implémentation du VSPackage d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> pour retourner la collection et permettre l'accès à ses objets constituants d' <xref:EnvDTE.Property> .  
  
 **Remarque** l'objet Automation retourné par <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> dépend du GUID fourni \(comme un VSPackage peut prendre en charge plusieurs objets Automation\).  Pour plus d'informations sur l'implémentation des objets Automation, consultez l' [Prise en charge d'Automation pour les Pages d'Options](../extensibility/internals/automation-support-for-options-pages.md).  
  
 une page d' **options d'outils** est spécifiée par deux identificateurs.  Le premier identificateur est une chaîne qui indique le dossier qui contient l'élément de la section d' **Options** le menu pour **Outils** .  le deuxième identificateur est une chaîne qui indique l'élément spécifique dans le dossier.  Pour plus d'informations, consultez [Utilisation des pages d’options](../misc/using-options-pages.md).  
  
 Deux entrées du Registre sont requises pour stocker un objet Automation :  
  
-   Sous HKEY\_LOCAL\_MACHINE  \\SOFTWARE\\Microsoft\\VisualStudio\\ *version* \\Packages \\ *PackageGUID* \\Automation  
  
-   sous HKEY\_LOCAL\_MACHINE \\SOFTWARE\\Microsoft\\VisualStudio \\ *\<Version\>* \\AutomationProperties  
  
     où  *\<Version\>*  est la version de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] \(tel que 8,0\) et  *\<PackageGUID\>*  est un GUID du VSPackage qui implémente l'objet Automation.  
  
 Selon la configuration sous l'entrée du Registre AutomationProperties, l'état d'une page d' **options d'outils** peut être enregistré automatiquement et restauré via le mécanisme de paramètres de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] lorsqu'un utilisateur sélectionne la commande de **paramètres d'importation\/exportation** dans le menu d' **Outils** .  Pour plus d'informations sur l'inscription des paramètres de la page d' **options d'outils** , consultez [Inscription de pages d’options personnalisées](../misc/registering-custom-options-pages.md).  
  
 Une application peut ne pas utiliser le modèle Automation pour implémenter la prise en charge des propriétés et des paramètres d'une page d' **options d'outils** .  
  
 Cela peut être souhaitable pour plusieurs raisons :  
  
-   Les paramètres gérés par la page d' **options d'outils** sont plus complexes en structure que le modèle relativement plat de propriété automation prend en charge.  
  
-   Il existe un besoin d'empêcher d'autres applications du programme gérant sa page d' **options d'outils** .  
  
-   Les contrôles d'accès ou les fonctionnalités de sécurité spéciaux sont obligatoires.  
  
 Dans ces cas, les VSPackages peut implémenter la prise en charge de la page d' **options d'outils** d'une manière appropriée.  Toutefois, ils doivent :  
  
-   Gérez la définition des propriétés de la page d' **options d'outils** .  
  
-   Gérez la persistance de l'état de la page d' **options d'outils** via les paramètres de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .  
  
-   fournissez une API, si vous le souhaitez, pour que d'autres applications utilisent la page d' **options d'outils** .  
  
 Les propriétés de la boîte de dialogue de **Polices et couleurs** est un exemple d'une page d' **options d'outils** qui ne peut pas être modifiée par le biais de le modèle Automation.  À la place, une API séparée est fournie, selon l'interface d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults> pour permettre la manipulation de programmation de la page de **Polices et couleursoptions d'outils** .  Pour plus d'informations sur le contrôle de la page de **Polices et couleursoptions d'outils** , consultez [Utilisation de polices et couleurs](../extensibility/using-fonts-and-colors.md).  
  
## Prise en charge de l'automation des pages options Outils dans managed package  
 Définissez la propriété d' <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute.SupportsAutomation%2A> de l'instance s'stockage d' <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> d'une implémentation pour indiquer qu'une implémentation managée d'Infrastructure\-base de package d'une page d' **options d'outils** prend en charge automation.  
  
 les pages d'**options d'outils** dérivées d' <xref:Microsoft.VisualStudio.Shell.DialogPage> sont fournies avec un objet Automation par défaut, qui peut être substituée.  
  
 Si une implémentation de page d' **options d'outils** ne prend pas en charge l'automation, l'implémentation doit fournir sa propre API pour permettre l'accès par programme à la page d' **options d'outils** .  
  
> [!NOTE]
>  La page de **Polices et couleurs** de l'IDE est un exemple d'une page d' **options d'outils** qui ne prend pas en charge l'automation, mais permet d'accéder à la page d' **options d'outils** via sa propre API.  Pour plus d'informations, consultez [Utilisation de polices et couleurs](../extensibility/using-fonts-and-colors.md).  
  
## Voir aussi  
 [Extension de l'environnement Visual Studio](../Topic/Extending%20the%20Visual%20Studio%20Environment.md)   
 [Création de pages d’options à l’aide des assemblys d’interopérabilité](/visual-cpp/misc/creating-options-pages-by-using-interop-assemblies)   
 [Création de Pages d'Options](../extensibility/internals/creating-options-pages.md)   
 [Comment : créer des pages d'options personnalisées](../Topic/How%20to:%20Create%20Custom%20Options%20Pages.md)   
 [Creating Registrar Scripts](/visual-cpp/atl/creating-registrar-scripts)   
 [Prise en charge d'Automation pour les Pages d'Options](../extensibility/internals/automation-support-for-options-pages.md)   
 [Utilisation des pages d’options](../misc/using-options-pages.md)