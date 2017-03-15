---
title: "Inscription de pages d’options personnalis&#233;es | Microsoft Docs"
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
  - "inscription, pages Options Outils personnalisées"
  - "Options Outils (pages) [Kit de développement logiciel (SDK) Visual Studio], inscription"
ms.assetid: 0ac6377d-a679-4f7d-be80-451c829b56f2
caps.latest.revision: 28
caps.handback.revision: 28
manager: "douge"
---
# Inscription de pages d’options personnalis&#233;es
Pour qu'une page d' **options d'outils** soit disponible aux utilisateurs et à l'automation de stockage, elle doit être inscrite convenablement avec l'environnement de développement intégré d' [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] \(IDE\).  
  
 Les pages d'**options d'outils** en fonction de managed package sont stockées en appliquant une instance d' <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> au VSPackage fournissant la page.  La prise en charge d'automation est indiquée en définissant la propriété d' <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute.SupportsAutomation%2A> à `true`.  
  
## Inscription de la page d'options Outils  
 Intégrant une page personnalisée d' **options d'outils** avec [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] requiert la création d'une entrée du Registre à l'emplacement suivant : HKEY\_LOCAL\_MACHINE \\SOFTWARE\\Microsoft\\VisualStudio \\*\<version\>*\\ToolsOptionsPages, où *\<version\>* est la version d' [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], par exemple 8,0.  
  
 L'entrée a une clé primaire à la catégorie \(`<PageCategory>`\) de la page d' **options d'outils** , et une sous\-clé contenant le nom du sous\-catégorie de la page \(`<PageSubCategory>`\).  
  
 Par exemple, la page d' **options d'outils** marquée avec la chaîne, **TextEditor.Basic**, a un \=textEditor d' `<PageCategory>`de clé de Registre avec une sous\-clé d' `<PageSubCategory>`\=Basic.  
  
 La structure de l'entrée de Registre est ci\-dessous :  
  
 \\Software\\Microsoft\\VisualStudio HKLM \\*\<version\>*\\ToolsOptionsPages \\  
  
 `<PageCategory>` \= '\#12345'  
  
 Package \= « {} »  
  
 ResourcePackage \= « {YYYYYY AAAA AAAA AAAA YYYYYYYYY} »  
  
 \\Software\\Microsoft\\VisualStudio HKLM \\*\<version\>*\\ToolsOptionsPages \\`<PageCategory>`  
  
 `<PageSubCategory>>` \= '\#67890'  
  
 Page \= « {ZZZZZZ ZZZZ ZZZZ ZZZZ ZZZZZZZZZ} »  
  
 Package \= « {AAAAAA AAAA AAAA AAAA AAAAAAAAA} »  
  
 ResourcePackage \= « {BBBBBB BBBB BBBB BBBB BBBBBBBBB} »  
  
 NoShowAllView \= 0\/1  
  
 Le tableau suivant répertorie les valeurs sous \\Software\\Microsoft\\VisualStudio HKLM \\*\<version\>*\\ToolsOptionsPages \\`<PageCategory>`.  
  
|Nom|Type|Données|Description|  
|---------|----------|-------------|-----------------|  
|\(Valeur par défaut\)|REG\_SZ|Le nom canonique de catégorie de la page personnalisée d' **options d'outils**|Le nom de clé, `<PageCategory>`, est le nom non localisé canonique de catégorie de la page d' **options d'outils** . **Note:**  Si l'automatisation est prise en charge, une catégorie et les noms de sous\-catégorie non\-localisés canoniques sont utilisés pour obtenir la collection d' <xref:EnvDTE.Properties> d'une page d' **options d'outils** .  Pour plus d'informations, consultez [Utilisation des pages d’options](../misc/using-options-pages.md). <br /><br /> Pour les implémentations en fonction de managed package, le \> d' `<PageCategory`est obtenu à partir de l'argument d' `categoryName` au constructeur d' <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> .<br /><br /> La clé peut être vide, ou elle peut contenir l'ID de référence à la chaîne localisée dans la DLL du satellite d'implémentation de.<br /><br /> Pour les implémentations en fonction de managed package, cette valeur est obtenue à partir de l'argument d' `categoryResourceID` au constructeur d' <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> .|  
|Package|REG\_SZ|GUID|GUID du VSPackage implémentant la page personnalisée d' **options d'outils** .<br /><br /> Implémentations en fonction de managed package à l'aide de la réflexion d'utilisation d' <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> pour obtenir cette valeur.|  
|ResourcePackage|REG\_SZ|GUID|Facultatif.<br /><br /> Une DLL satellite contenant des chaînes localisées si le VSPackage implémentant les ne fournit pas.<br /><br /> Managed package utilise la réflexion pour obtenir le package approprié de ressource, ce <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> ne définit pas cet argument.|  
  
 Le tableau suivant répertorie les valeurs sous \\Software\\Microsoft\\VisualStudio HKLM \\*\<version\>*\\ToolsOptionsPages \\`<PageCategory>`\\`<PageSubCategory>`.  
  
|Nom|Type|Données|Description|  
|---------|----------|-------------|-----------------|  
|\(Valeur par défaut\)|REG\_SZ|Le nom de sous\-catégorie canonique de la page personnalisée d' **options d'outils**|Le nom de clé, \> d' `<PageSubCategory`, est le nom non localisé canonique de sous\-catégorie de page d' **options d'outils** . **Note:**  Si l'automatisation est prise en charge, une catégorie et les noms de sous\-catégorie non\-localisés canoniques sont utilisés pour obtenir la collection d' <xref:EnvDTE.Properties> d'une page d' **options d'outils** .  Pour plus d'informations, consultez [Utilisation des pages d’options](../misc/using-options-pages.md). <br /><br /> Pour les implémentations en fonction de managed package, le \> d' `<PageSubegory`est obtenu à partir de l'argument d' `pageName` au constructeur d' <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> .<br /><br /> La clé peut être vide, ou elle peut contenir l'ID de référence à la chaîne localisée dans une DLL satellite d'implémentation de.<br /><br /> Pour les implémentations en fonction de managed package, cette valeur est obtenue à partir de l'argument d' `pageNameResourceID` au constructeur d' <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> .|  
|Page|REG\_SZ|GUID|GUID de l'objet qui implémente la page personnalisée d' **options d'outils** .<br /><br /> Les implémentations en fonction de managed package à l'aide de <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> utilisent l'argument d' `pageType` du constructeur contenant <xref:System.Type> et la réflexion du VSPackage pour obtenir cette valeur.|  
|Package|REG\_SZ|GUID|Implémentations en fonction de managed package à l'aide de la réflexion d'utilisation d' <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> pour obtenir cette valeur.|  
|ResourcePackage|REG\_SZ|GUID|Facultatif.<br /><br /> Une DLL satellite contenant des chaînes localisées si le VSPackage implémentant les ne fournit pas.<br /><br /> Managed package utilise la réflexion pour obtenir la DLL de ressource correct, ce <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> ne définit pas cet argument.|  
|NoShowAllView|REG\_DWORD|0 ou 1 ;|Facultatif.<br /><br /> Indique si une page donnée d' **options d'outils** doit apparaître dans la vue \(par défaut\) complexe des pages d' **options d'outils** .  Prend en charge des environnements de programmation, tels que Visual Basic, qui comportent des pages d' **options d'outils** spéciale de regrouper les paramètres courants de fournir aux utilisateurs des vues simplifiées spécialisées d'options.<br /><br /> Si l'entrée de REG\_DWORD est non nulle, la page d' **options d'outils** n'apparaît pas dans une vue complexe.<br /><br /> Pour plus d'informations, consultez [Options, boîte de dialogue](../ide/reference/options-dialog-box-visual-studio.md).<br /><br /> Les implémentations en fonction de managed package pouvez définir cette valeur en définissant la propriété d' <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute.NoShowAllView%2A> à `true` dans le constructeur d' <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> .|  
  
 Un VSPackage ou un objet basé sur un assembly d'interopérabilité peut implémenter plusieurs pages d' **options d'outils** .  Chaque implémentation requiert une entrée dans \\Software\\Microsoft\\VisualStudio HKLM \\*\<version\>*\\ToolsOptionsPages.  
  
 Comme managed package instancie l'objet fournissant une page d' **options d'outils** , chaque page doit avoir son propre objet d'implémentation, indépendamment de l'implémentation d'un VSPackage d' <xref:Microsoft.VisualStudio.Shell.Package>.  
  
## Prise en charge d'Automation  
 Si la prise en charge d'automation est utilisée pour implémenter une page d' **options d'outils** , elle doit stocker comme fournisseur d'automation.  Pour utiliser l'automation pour la gestion de propriété, et utiliser ses mécanismes de persistance d'enregistrer l'état de la page d' **options d'outils** , elle doit stocker comme fournisseur d' `AutomationProperty` .  
  
### Enregistrez un VSPackage en tant que fournisseur d'automation \(uniquement pour les pages options Outils en fonction de les assemblys d'interopérabilité\)  
 Les pages d'**options d'outils** sur un assembly d'interopérabilité sont implémentées dans le cadre de les classes de l'implémentation d'un VSPackage.  
  
 Dans ce cas, si une page d' **options d'outils** est de prendre en charge l'automation, le VSPackage basé sur un assembly d'interopérabilité doit être enregistré en tant que fournisseur d'automation.  
  
> [!NOTE]
>  La prise en charge d'automation dans managed package est fournie par un indépendant d'objet de l'implémentation du VSPackage.  Si cet objet prend en charge automation, cela est enregistré via la propriété d' <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute.SupportsAutomation%2A> du constructeur d' <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> .  
  
 L'entrée pour stocker un VSPackage en tant que fournisseur d'automatisation est du formulaire \\SOFTWARE\\Microsoft\\VisualStudio HKEY\_LOCAL\_MACHINE \\*\<version\>*\\Packages \\*\<PackageGUID\>*\\Automation, où *\<version\>* est la version d' [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] \(tel que 8,0\) et *\<PackageGUID\>* est un GUID du VSPackage qui implémente l'objet Automation.  
  
> [!NOTE]
>  Le chemin d'accès racine HKEY\_LOCAL\_MACHINE \\SOFTWARE\\Microsoft\\VisualStudio \\*\<version\>* peut être substitué par une autre racine lorsque le shell Visual Studio est initialisé.  Pour plus d'informations, consultez [Commutateurs de ligne de commande](../extensibility/command-line-switches-visual-studio-sdk.md).  
  
 La structure de l'entrée de Registre est :  
  
 HKEY\_LOCAL\_MACHINE \\SOFTWARE\\Microsoft\\VisualStudio \\*\<version\>*\\Packages \\*\<PackageGUID\>*\\Automation  
  
 `<AutomationObjectName>`  
  
|Nom|Type|Données|Description|  
|---------|----------|-------------|-----------------|  
|Automation|REG\_SZ|Non défini|Indéfini.<br /><br /> La présence de cette clé indique que le VSPackage référencé par *\<PackageGUID\>* prend en charge automation.<br /><br /> Le champ peut être utilisé pour stocker la documentation.<br /><br /> <xref:Microsoft.VisualStudio.Shell.ProvideAutomationObjectAttribute> crée automatiquement cette clé des applications basées sur managed package.|  
|`<AutomationObjectName>`|REG\_SZ|Le nom canonique de l'objet Automation fourni|Seul le nom de la clé est approprié.  Il est utilisé dans les opérations d'automation.<br /><br /> Le champ peut être utilisé pour stocker la documentation.<br /><br /> Pour les implémentations en fonction de managed package, le nom de cette clé est déterminé par l'argument d' `name` au constructeur d' <xref:Microsoft.VisualStudio.Shell.ProvideAutomationObjectAttribute> .<br /><br /> Si le constructeur d' <xref:Microsoft.VisualStudio.Shell.ProvideAutomationObjectAttribute> a une chaîne valide fournie à sa propriété d' <xref:Microsoft.VisualStudio.Shell.ProvideAutomationObjectAttribute.Description%2A> , cette valeur est insérée ici.|  
  
### Enregistrez une page d'options Outils comme automation de prise en charge  
 Les deux des implémentations d'interopérabilité de contexte de package et basé sur un assembly gérées des pages d' **options d'outils** doivent s'inscrire pour permettre l'accès d'automation dans une page d' **options d'outils** .  Cela inclut les mécanismes et l'accès de persistance de propriété automation à la page via <xref:EnvDTE>.  C'est indépendant de l'alignement de VSPackage lui\-même au fournisseur de services d'automation.  
  
 Comme avec l'alignement de page d' **options d'outils** mentionné ci\-dessus, l'entrée a une clé primaire à la catégorie \(`<PageCategory>`\) de la page d' **options d'outils** , et une sous\-clé contenant le nom du sous\-catégorie de la page \(`<PageSubcategory>`\).  
  
 Si vous utilisez managed package, utilisez <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> pour enregistrer une classe comme fourniture d'une page d' **options d'outils** et définir la propriété d' <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute.SupportsAutomation%2A> à `true` pour indiquer que la page prend en charge automation.  
  
 L'entrée du Registre est trouvée dans \\SOFTWARE\\Microsoft\\VisualStudio HKEY\_LOCAL\_MACHINE \\*\<version\>*\\AutomationProperties, où *\<version\>* est la version d' [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], par exemple 8,0.  
  
> [!NOTE]
>  Le chemin d'accès racine HKEY\_LOCAL\_MACHINE \\SOFTWARE\\Microsoft\\VisualStudio \\*\<version\>* peut être substitué par une autre racine lorsque le shell Visual Studio est initialisé, car plus d'informations, consultez [Commutateurs de ligne de commande](../extensibility/command-line-switches-visual-studio-sdk.md).  
  
 La structure de l'entrée de Registre est ci\-dessous :  
  
 HKEY\_LOCAL\_MACHINE \\SOFTWARE\\Microsoft\\VisualStudio \\*\<version\>\\*AutomationProperties  
  
 `<PageCategory>` \= ‘\#456’  
  
 ResourcePackage \= « {} »  
  
 `<PageSubCategory>` \= ‘\#789’  
  
 Package \= « {YYYYYY AAAA AAAA AAAA YYYYYYYYY} »  
  
 Nom \= « `<PageCategory>` .`<PageSubcategory>` »  
  
 « ProfileSave » \= 1\/0  
  
 Le tableau suivant répertorie les valeurs sous HKEY\_LOCAL\_MACHINE \\SOFTWARE\\Microsoft\\VisualStudio \\*\<version\>*\\AutomationProperties \\`<PageCategory>`.  
  
|Nom|Type|Données|Description|  
|---------|----------|-------------|-----------------|  
|\(Valeur par défaut\)|REG\_SZ|Le nom canonique de catégorie de la page personnalisée d' **options d'outils**|Le nom de clé, \> d' `<PageCategory`, est le nom non localisé canonique de la classe de page d' **options d'outils** . **Note:**  Si l'automatisation est prise en charge, une catégorie et les noms de sous\-catégorie non\-localisés canoniques sont utilisés pour obtenir la collection d' <xref:EnvDTE.Properties> d'une page d' **options d'outils** .  Pour plus d'informations, consultez [Utilisation des pages d’options](../misc/using-options-pages.md). <br /><br /> La clé peut être vide, ou elle peut contenir l'ID de référence à la chaîne localisée dans la DLL du satellite d'implémentation de.<br /><br /> Pour les implémentations en fonction de managed package, le \> d' `<PageCategory`est obtenu à partir de l'argument d' `categoryName` au constructeur d' <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> .|  
|ResourcePackage|REG\_SZ|GUID|Facultatif.<br /><br /> Une DLL satellite contenant des chaînes localisées si le VSPackage implémentant les ne fournit pas.<br /><br /> Managed package utilise la réflexion pour obtenir la ressource appropriée VSPackage, ce <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> ne définit pas cet argument.|  
  
 Le tableau suivant répertorie les valeurs sous HKEY\_LOCAL\_MACHINE \\SOFTWARE\\Microsoft\\VisualStudio \\*\<version\>*\\AutomationProperties \\`<PageCategory>\<PageSubCategory>`.  
  
|Nom|Type|Données|Description|  
|---------|----------|-------------|-----------------|  
|\(Valeur par défaut\)|REG\_SZ|Le nom de sous\-catégorie de la page personnalisée d' **options d'outils**|Le nom de clé, \> d' `<PageSubCategory`, est le nom non localisé canonique de sous\-catégorie de page d' **options d'outils** . **Note:**  Si l'automatisation est prise en charge, une catégorie et les noms de sous\-catégorie non\-localisés canoniques sont utilisés pour obtenir la collection d' <xref:EnvDTE.Properties> d'une page d' **options d'outils** .  Pour plus d'informations, consultez [Utilisation des pages d’options](../misc/using-options-pages.md). <br /><br /> La clé peut être vide, ou elle peut contenir l'ID de référence à la chaîne localisée dans la DLL du satellite d'implémentation de.<br /><br /> Pour les implémentations en fonction de managed package, `<PageSubCategory>` est obtenu à partir de l'argument d' `pageName` au constructeur d' <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> .|  
|Package|REG\_SZ|GUID|GUID du VSPackage implémentant la page personnalisée d' **options d'outils** .<br /><br /> Implémentations en fonction de managed package à l'aide de la réflexion d'utilisation d' <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> pour obtenir cette valeur.|  
|Nom|REG\_SZ|Nom de la collection de propriétés de la page d' **options d'outils**|La chaîne d' `<PageCategory>.<PageSubCategory>` utilisée pour faire référence à la page d' **options d'outils** .  Pour plus d'informations, consultez [Utilisation des pages d’options](../misc/using-options-pages.md).<br /><br /> Pour les implémentations en fonction de managed package, le nom est obtenu à partir de les arguments au constructeur d' <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> et a la forme `categoryName.pageName`.|  
|ProfileSave|DWORD|1\/0|Facultatif.<br /><br /> Cette valeur indique si les paramètres de la page d' **options d'outils** sont stockés par le mécanisme de paramètres d' [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] lorsqu'un utilisateur clique sur la commande **paramètres d'importation\/exportation** dans le menu **Outils** .<br /><br /> Si la clé est présent et sa valeur est 1, la page d' **options d'outils** demande la prise en charge de paramètres.<br /><br /> Les implémentations en fonction de managed package définit cette valeur si le constructeur d' <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> est fourni avec le jeu de propriétés d' <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute.SupportsProfiles%2A> à `true`.|  
  
## Voir aussi  
 [Creating Registrar Scripts](/visual-cpp/atl/creating-registrar-scripts)   
 [Utilisation des pages d’options](../misc/using-options-pages.md)   
 [Création de pages d’options à l’aide des assemblys d’interopérabilité](/visual-cpp/misc/creating-options-pages-by-using-interop-assemblies)   
 [Comment : créer des pages d'options personnalisées](../Topic/How%20to:%20Create%20Custom%20Options%20Pages.md)   
 [Pages Options](../misc/options-pages.md)   
 [Prise en charge d'Automation pour les Pages d'Options](../extensibility/internals/automation-support-for-options-pages.md)