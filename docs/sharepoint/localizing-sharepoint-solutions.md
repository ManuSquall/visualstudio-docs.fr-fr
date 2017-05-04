---
title: "Localisation de solutions SharePoint | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.SharePointTools.Project.GlobalAndFeatureResource"
  - "VS.SharePoint.Project.AddResourceDialog"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "globaliser (développement SharePoint dans Visual Studio)"
  - "localiser (développement SharePoint dans Visual Studio)"
  - "développement SharePoint dans Visual Studio, localiser"
ms.assetid: 0d4cfa2b-8b48-45c7-bbee-ece9b0baffaf
caps.latest.revision: 18
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 17
---
# Localisation de solutions SharePoint
  Le processus consistant à préparer vos applications afin qu'elles puissent être utilisées mondialement est appelé localisation.  La localisation est la traduction de ressources pour une culture spécifique.  Pour plus d'informations, consultez [Globalisation et localisation d'applications](../ide/globalizing-and-localizing-applications.md).  Cette rubrique fournit une vue d'ensemble de la localisation d'une solution SharePoint.  
  
 Pour localiser une solution, vous supprimez du code les chaînes codées en dur et les rendez abstraites dans des fichiers de ressources.  Un fichier de ressources est un fichier basé sur [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] avec une extension .resx.  Le fichier de ressources contient les versions traduites des chaînes utilisées dans votre solution.  Pour plus d'informations, consultez [Ressources dans les applications](http://go.microsoft.com/fwlink/?LinkID=155844).  
  
> [!NOTE]  
>  Ajoutez uniquement des ressources de type chaîne aux fichiers de ressources de solution SharePoint.  Bien que l'Éditeur de ressources vous permette d'ajouter des ressources qui ne sont pas des chaînes, ce type de ressources n'est pas déployé sur SharePoint.  
  
## Fichiers de ressources  
 Il existe trois genres de fichiers de ressources : par défaut, indépendant de la langue et spécifique à une langue.  
  
|Type de fichier de ressources|Description|  
|-----------------------------------|-----------------|  
|Par défaut|Également appelés ressource de secours, les fichiers de ressources par défaut contiennent des chaînes localisées pour la culture par défaut, par exemple l'anglais.  Ils sont utilisés s'il n'existe aucun fichier de ressources localisé pour la langue spécifiée.  Les ressources par défaut n'ont pas de fichiers séparés ; leur stockage s'effectue dans l'assembly d'application principal.|  
|Indépendant de la langue|Fichier de ressources qui contient des chaînes localisées pour une langue, mais pas une culture spécifique.  Par exemple, "fr" pour français.|  
|Spécifique à une langue|Fichier de ressources qui contient des chaînes localisées pour une langue et une culture.  Par exemple, "fr\-CA" pour français canadien.|  
  
 Pour plus d'informations, consultez [Organisation hiérarchique des ressources pour la localisation](http://go.microsoft.com/fwlink/?LinkId=178360).  
  
 Pour spécifier des fichiers de ressources par défaut dans les projets SharePoint que vous développez dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], choisissez **Langue indifférente \(Pays indifférent\)** dans la liste de cultures de la boîte de dialogue **Ajouter une ressource** lorsque vous ajoutez un fichier de ressources.  
  
## Localisation de solutions Visual Studio SharePoint  
 Lorsque vous localisez une solution, vous devez prendre en compte toutes les informations textuelles que votre solution affiche aux utilisateurs.  Les messages d'information, les messages d'erreur et les chaînes [!INCLUDE[TLA2#tla_ui](../sharepoint/includes/tla2sharptla-ui-md.md)] doivent être traduits et ces traductions placées dans les fichiers de ressources.  
  
 Chaque chaîne dans un fichier de ressources a un identificateur unique.  Utilisez le même identificateur pour la chaîne traduite dans chaque fichier de ressources.  Par exemple, si "String1" est l'identificateur de la première chaîne dans le fichier de ressources par défaut, utilisez le même identificateur pour la première chaîne dans les fichiers de ressources spécifiques à une langue.  
  
 En général, vous localisez trois types d'éléments dans les applications [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint : les fonctionnalités, le balisage de page ASPX et le code.  À des fins d'illustration, les sections suivantes supposent que vous disposez d'une solution SharePoint que vous souhaitez localiser en allemand et en japonais.  La langue par défaut est l'anglais.  
  
### Localisation des fonctionnalités  
 Pour localiser une fonctionnalité, vous devez remplacer le titre codé en dur et la description de la fonctionnalité par une expression qui référence le titre et la chaîne traduits dans le fichier de ressources localisé.  Vous effectuez cette modification dans le **Concepteur de fonctionnalités** de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  Pour plus d'informations, consultez [Comment : localiser une fonctionnalité](../sharepoint/how-to-localize-a-feature.md).  
  
 Pour localiser votre fonctionnalité anglaise en allemand et en japonais, vous ajoutez trois éléments de projet de fichier de ressources à votre projet : un pour l'anglais, un pour l'allemand et un pour le japonais.  Les fichiers de ressources de fonctionnalité ne peuvent pas être utilisés pour localiser le balisage ASPX ou le code ; des fichiers de ressources séparés sont nécessaires.  
  
 Une fois que vous avez créé les fichiers de ressources de fonctionnalité, ajoutez\-leur les chaînes traduites.  Accédez aux chaînes localisées avec une expression au format suivant :  
  
```  
$Resources:String ID  
```  
  
 Les ressources de fonctionnalité dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] sont toujours nommées Resources.  Si vous sélectionnez une langue autre que Langue indifférente, un [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)] de culture est ajouté au nom de fichier de ressources.  Par exemple, si vous ajoutez un fichier de ressources de fonctionnalités de langage \(par défaut\) invariant, il est appelé Resources.resx.  Si vous ajoutez une ressource de fonctionnalité spécifique à une langue en sélectionnant la culture Japonais \(Japon\), le fichier est appelé Resources.ja\-JP.resx.  Les noms de fichiers de ressources de fonctionnalité sont automatiquement assignés et ne peuvent pas être modifiés.  
  
 La portée des ressources de fonctionnalité est locale à la fonctionnalité à laquelle elles sont ajoutées.  Pour créer des ressources qui peuvent être utilisées par tout fichier de fonctionnalité ou d'élément dans la solution, ajoutez un élément de projet **Fichiers de ressources globales** plutôt qu'un fichier de ressources de fonctionnalité.  L'élément de projet **Fichier de ressources global** se trouve dans le dossier **2010** sous **SharePoint** dans la boîte de dialogue **Ajouter un nouvel élément**.  Les fichiers de ressources globaux se déploient vers le dossier \\Resources du dossier racine SharePoint.  
  
### Localisation du balisage de page ASPX  
 Pour localiser des pages d'[!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)], ajoutez trois éléments de projet Fichier de ressources à votre projet : un pour l'anglais, un pour l'allemand et un pour le japonais.  S'il n'est pas nécessaire de localiser le code en plus du balisage, vous pouvez ajouter à la place des fichiers de ressources globaux.  
  
 Attribuez un nom au fichier de ressources de langue par défaut.  Attribuez aux fichiers de ressources localisés le même nom, auquel est ajouté l'[!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)] de culture spécifique à une langue.  Par exemple, MyAppResources.de\-DE.resx pour l'allemand et MyAppResources.ja\-JP.resx pour le japonais.  
  
 Affectez à la propriété **Deployment Type** de chaque fichier de ressources la valeur **AppGlobalResource**.  Les fichiers de ressources sont alors déployés vers le dossier App\_GlobalResources, dans lequel ils sont disponibles pour l'ensemble des contrôles et des pages ASPX de la solution.  Le dossier App\_GlobalResources se trouve sous C:\\inetpub\\wwwroot\\wss\\VirtualDirectories\\\\\<numéro\_port\>\\App\_GlobalResources.  
  
> [!NOTE]  
>  Si vous utilisez des fichiers de ressources non globales, déplacez\-les vers le dossier d'éléments de projet pour activer la propriété Deployment Type et d'autres propriétés spécifiques à SharePoint.  
  
 Les fichiers de ressources de balisage ASPX permettent également de localiser le code.  Si vous utilisez les ressources pour localiser le code en plus du balisage ASPX, conservez la valeur Ressource incorporée pour la propriété Build Action afin que la ressource soit compilée dans un assembly satellite.  Toutefois, si vous utilisez uniquement les fichiers de ressources pour localiser le balisage, vous pouvez éventuellement remplacer la valeur de la propriété Build Action par Contenu pour empêcher la compilation du fichier dans l'assembly d'application principal.  
  
 Remplacez toutes les chaînes de propriété codées en dur dans le balisage des pages et contrôles ASPX par une expression au format suivant :  
  
```  
<asp:<class> runat="server" Text="<%$Resources:<Resource File Name>, <String ID>%>" />  
```  
  
 Par exemple :  
  
```  
<asp:Button ID="btn1" runat="server" onclick="btn1_Click" Text="<%$Resources:Resource1,String7%>"></asp:Button>  
```  
  
 Pour ASPX comme texte, utilisez une expression au format suivant :  
  
```  
<asp:literal ID="<ID>" runat="server" Text="<%$Resources:<Resource File Name>, <String ID>%>" />  
```  
  
 Par exemple :  
  
```  
<asp:literal ID="Literal1" runat="server" Text="<%$Resources:Resource1, String9%>" />  
```  
  
 Pour plus d'informations, consultez [Comment : localiser le balisage ASPX](../sharepoint/how-to-localize-aspx-markup.md).  
  
### Localisation du code  
 Outre la localisation des chaînes de fonctionnalité et du balisage [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)], vous devez également localiser les chaînes de message et d'erreur qui s'affichent dans le code de la solution.  Les messages d'erreur et les messages d'information localisés sont contenus dans des assemblys satellites.  Les assemblys satellites contiennent des chaînes qui sont visibles par les utilisateurs, par exemple des messages de texte et de sortie [!INCLUDE[TLA2#tla_ui](../sharepoint/includes/tla2sharptla-ui-md.md)] comme les exceptions.  
  
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] utilise le modèle « hub and spoke » .NET Framework standard.  Le concentrateur \(hub\), ou assembly de programme principal, contient les ressources de langue par défaut.  Les spokes, ou assemblys satellites, contiennent les ressources spécifiques à une langue.  Pour plus d'informations, consultez [Empaquetage et déploiement de ressources](http://go.microsoft.com/fwlink/?LinkId=179280).  Les assemblys satellites sont compilés à partir de fichiers de ressources \(.resx\).  Lorsque vous ajoutez des fichiers de ressources spécifiques à une langue à votre projet et au package de solution, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] compile les fichiers de ressources dans des assemblys satellites nommés *Project Name*.resources.dll.  
  
 Comme avec le balisage ASPX, localisez le code d'application SharePoint en ajoutant des éléments de projet de fichier de ressources séparés à votre projet ; un pour la langue par défaut et un pour chaque langue localisée.  Toutefois, comme indiqué précédemment, si vous avez déjà des fichiers de ressources pour la localisation du balisage ASPX, vous pouvez les réutiliser pour la localisation du code.  Si vous devez créer des fichiers de ressources, attribuez au fichier de ressources de langue par défaut le nom de votre choix, avec l'extension .resx.  Attribuez aux fichiers de ressources localisés le même nom, auquel est ajouté l'[!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)] de culture spécifique à une langue.  Affectez à la propriété Build Action de chaque fichier de ressources la valeur Ressource incorporée pour permettre la création d'assemblys de ressources satellites.  
  
 Pour créer les assemblys satellites, générez le projet puis ajoutez les fichiers comme assemblys supplémentaires via l'onglet **Avancé** du **Concepteur de packages**.  Lorsque vous ajoutez les assemblys, ajoutez un dossier [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)] de culture au chemin d'accès, tel que de\-DE\\*Project Item Name*.resources.dll.  Cela permet au package de contenir des fichiers qui ont le même nom.  
  
 Dans votre code, remplacez les chaînes codées en dur par des appels à la méthode <xref:System.Web.HttpContext.GetGlobalResourceObject%2A> à l'aide de la syntaxe suivante :  
  
```  
HttpContext.GetGlobalResourceObject("<Resource File Name>", "<String ID>")  
```  
  
 Pour plus d'informations, consultez [Comment : localiser du code](../sharepoint/how-to-localize-code.md).  
  
#### Localisation du code du composant WebPart  
 Les composants WebPart fournissent une fonctionnalité d'éditeur de propriétés personnalisée qui inclut des attributs de code utilisant des chaînes codées en dur, par exemple WebDisplayName, Category et WebDescription.  Pour remplacer les valeurs de chaîne de ces attributs, créez une classe séparée qui dérive de la classe de l'attribut.  Dans ces classes, définissez la propriété de l'attribut.  La propriété de l'attribut dépend de la classe de base.  Par exemple, la propriété de l'attribut WebDisplayName est DisplayNameValue et la propriété de l'attribut WebDescription est DescriptionValue.  
  
 Dans la classe dérivée, référencez l'ID de chaîne à partir du fichier de ressources et de l'objet ResourceManager pour obtenir la valeur localisée de l'ID de chaîne.  Retournez cette valeur à l'attribut d'éditeur de propriétés.  
  
## Voir aussi  
 [Comment : localiser une fonctionnalité](../sharepoint/how-to-localize-a-feature.md)   
 [Comment : localiser le balisage ASPX](../sharepoint/how-to-localize-aspx-markup.md)   
 [Comment : localiser du code](../sharepoint/how-to-localize-code.md)   
 [Comment : ajouter un fichier de ressources](../sharepoint/how-to-add-a-resource-file.md)   
 [Comment : utiliser un fichier de ressources pour spécifier des noms localisés, propriétés et autorisations](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)  
  
  