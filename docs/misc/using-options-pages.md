---
title: "Utilisation des pages d’options | Microsoft Docs"
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
  - "pages d’options des outils [Kit de développement logiciel (SDK) Visual Studio], utilisation"
ms.assetid: 5ae6b995-3aeb-43a7-9786-4cf69faa101c
caps.latest.revision: 36
caps.handback.revision: 36
manager: "douge"
---
# Utilisation des pages d’options
Le modèle Automation [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] fournit l’objet <xref:EnvDTE.DTE> pour permettre à des packages Visual Studio d’accéder à la boîte de dialogue **Options** du menu **Outils**  
  
 En général, les pages de la boîte de dialogue **Options** sont accessibles à l’aide du modèle Automation, que les pages soient fournies par l’environnement de développement intégré \(IDE\) [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ou par un VSPackage. Toutefois, il existe quelques exceptions, comme suit :  
  
-   Les paramètres de la page **Aide dynamique** ne sont pas accessibles par programmation. La fonctionnalité **Aide dynamique** peut être contrôlée à l’aide du modèle Automation, mais le contrôle doit être effectué directement dans le code. Pour plus d’informations, consultez [How to: Control the Dynamic Help Window](http://msdn.microsoft.com/fr-fr/7f5777aa-c270-4058-a175-8ce8a4ed25eb).  
  
-   Le contrôle des paramètres de la page **Polices et couleurs** est assuré via sa propre API, et non par le modèle Automation. Pour plus d’informations, consultez [Utilisation de polices et couleurs](../extensibility/using-fonts-and-colors.md).  
  
-   Impossible d’obtenir les propriétés spécifiques au langage via le modèle Automation.  
  
 Les pages **Options** ne prenant pas en charge le modèle Automation [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] peuvent ne pas retourner une collection de <xref:EnvDTE.Properties> Automation lors de l’interrogation. Si la collection est retournée, les fonctionnalités ne sont pas toutes présentes. Pour plus d’informations sur la gestion de ces fonctionnalités, consultez [Collections de propriétés DTE](../Topic/DTE%20Properties%20Collections.md).  
  
## Gestion des pages d’options  
 Pour gérer les pages **Options**, un VSPackage doit obtenir un objet <xref:EnvDTE.DTE> du modèle Automation.  
  
> [!NOTE]
>  Quand un VSPackage utilise le modèle Automation pour interroger et modifier les paramètres dans des pages **Options** installées, il n’étend pas les fonctionnalités de l’IDE. Par conséquent, le package n’a pas à implémenter un objet Automation.  
  
 Pour obtenir un objet <xref:EnvDTE.DTE> par le biais du modèle Automation, appelez la méthode <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A> et indiquez l’argument d’ID de service `SID_SDTE` et l’argument d’interface `IID__DTE`, comme suit.  
  
```  
pServiceProvider->QueryService(SID_SDTE, IID__DTE, (LPVOID*)pDTE);  
```  
  
 Pour obtenir un objet <xref:EnvDTE.DTE> à l’aide du MPF \(Managed Package Framework\), appelez la méthode <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> et indiquez un paramètre `serviceType` de type <xref:Microsoft.VisualStudio.Shell.Interop.SDTE>.  
  
 [!code-cs[UI_UserSettings_ToolsOptionPages#01](../misc/codesnippet/CSharp/using-options-pages_1.cs)]
 [!code-vb[UI_UserSettings_ToolsOptionPages#01](../misc/codesnippet/VisualBasic/using-options-pages_1.vb)]  
  
 Une page **Options** est définie par deux identificateurs. Le premier identificateur est une chaîne qui indique le dossier qui contient la page **Options**. Le deuxième identificateur est une chaîne qui indique l’élément spécifique dans ce dossier. Ils sont désignés comme catégorie et sous\-catégorie d’une page  **Options**, ou comme rubrique et sous\-rubrique.  
  
 Par exemple, les paramètres de l’éditeur de texte pour la gestion du code de base figurent dans le volet de navigation en tant que membre de **base** du dossier **Éditeur de texte**. L’identificateur de la catégorie est `TextEditor` et la sous\-catégorie est `Basic`, et la page **Options** elle\-même est appelée page `TextEditor.Basic`.  
  
> [!NOTE]
>  Pour, entre autres, des raisons de localisation, les noms affichés dans les pages **Options** peuvent différer des chaînes utilisées en tant qu’identificateurs de catégorie et sous\-catégorie. Vous devrez peut\-être utiliser le modèle Automation pour interroger l’IDE et obtenir les identificateurs corrects, s’ils ne sont pas documentés ailleurs. L’emplacement dans le Registre est HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VisualStudio\\*\<Version VS\>*\\AutomationProperties, où *\<Version VS\>* correspond au numéro de la version de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Pour plus d'informations, consultez [Inscription de pages d’options personnalisées](../misc/registering-custom-options-pages.md).  
  
 Vous pouvez obtenir les propriétés de la page `TextEditor.Basic` via le modèle Automation à l’aide de l’exemple suivant.  
  
```  
CComPtr<_DTE> srpDTE; CComPtr<Properties> srpDTEPropertiesList; hr = srpDTE->get_Properties("TextEditor", "Basic", &srpDTEPropertiesList);  
```  
  
 Pour obtenir les propriétés à l’aide du MPF, utilisez la méthode <xref:EnvDTE._DTE.Properties%2A>.  
  
 [!code-cs[UI_UserSettings_ToolsOptionPages#02](../misc/codesnippet/CSharp/using-options-pages_2.cs)]
 [!code-vb[UI_UserSettings_ToolsOptionPages#02](../misc/codesnippet/VisualBasic/using-options-pages_2.vb)]  
  
 La méthode <xref:EnvDTE.Properties.Item%2A> retourne les paramètres individuels de la collection de <xref:EnvDTE.Properties> comme un objet <xref:EnvDTE.Property>.  
  
 Comme avec les catégories et sous\-catégories, chaque paramètre a un identificateur qui est une chaîne unique. Par exemple, le paramètre **Taille des tabulations** de la page `TextEditor.Basic` est identifié par la chaîne `TabSize`.  
  
> [!NOTE]
>  Pour, entre autres, des raisons de localisation, les noms affichés dans les pages **Options** peuvent différer des chaînes utilisées en tant qu’identificateurs de paramètres. Vous devrez peut\-être utiliser le modèle Automation pour interroger l’IDE et obtenir les identificateurs corrects, s’ils ne sont pas documentés ailleurs.  
  
 Vous pouvez utiliser l’élément <xref:EnvDTE.Property.Value%2A> de l’objet <xref:EnvDTE.Property> qui est retourné par la méthode <xref:EnvDTE.Properties.Item%2A> de la collection de <xref:EnvDTE.Properties> pour interroger et modifier l’état des paramètres.  
  
 Par exemple, pour définir le paramètre **Taille des tabulations** de la page `TextEditor.Basic` via le modèle Automation, utilisez l’objet <xref:EnvDTE.Properties> retourné dans l’exemple suivant.  
  
```  
CComPtr<Property> srpProperty; hr = srpDTEPropertiesList->Item("TabSize", &srpProperty); hr= srpProperty.set_Value(4);  
```  
  
 L’exemple suivant montre comment mettre à jour le paramètre **Taille des tabulations** à l’aide du MPF.  
  
 [!code-cs[UI_UserSettings_ToolsOptionPages#03](../misc/codesnippet/CSharp/using-options-pages_3.cs)]
 [!code-vb[UI_UserSettings_ToolsOptionPages#03](../misc/codesnippet/VisualBasic/using-options-pages_3.vb)]  
  
 Pour plus d'informations, consultez [Contrôle des paramètres de la boîte de dialogue Options](../Topic/Controlling%20Options%20Settings.md).  
  
## Paramètres des pages d’options persistants  
 L’IDE implémente la persistance de l’état des pages **Options** qui prennent entièrement en charge le modèle Automation [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
 Les paramètres des pages qui figurent dans l’environnement IDE sont automatiquement enregistrés \(ou récupérés\) quand un utilisateur clique sur la commande **Paramètres d’importation\/exportation** dans le menu **Outils**.  
  
 Vous pouvez définir votre page **Options** personnalisée pour utiliser cette prise en charge de la persistance automatique en ajoutant l’indicateur `ProfileSave` à l’entrée de Registre de la page **Options** personnalisée sous HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VisualStudio\\*\<Version VS\>*\\AutomationProperties, où *\<Version VS\>* correspond au numéro de la version de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Pour plus d'informations, consultez [Inscription de pages d’options personnalisées](../misc/registering-custom-options-pages.md).  
  
## Voir aussi  
 [Création de pages d’options à l’aide des assemblys d’interopérabilité](/visual-cpp/misc/creating-options-pages-by-using-interop-assemblies)   
 [Création de Pages d'Options](../extensibility/internals/creating-options-pages.md)   
 [Création de pages d’options à l’aide d’Automation](../misc/creating-options-pages-by-using-automation.md)   
 [Contrôle des paramètres de la boîte de dialogue Options](../Topic/Controlling%20Options%20Settings.md)   
 [Inscription de pages d’options personnalisées](../misc/registering-custom-options-pages.md)   
 [Ouverture d’une page d’options](../misc/opening-an-options-page.md)   
 [Options et paramètres d'extension utilisateur](../extensibility/extending-user-settings-and-options.md)