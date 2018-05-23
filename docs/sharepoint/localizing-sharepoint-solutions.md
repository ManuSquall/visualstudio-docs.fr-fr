---
title: Localisation de Solutions SharePoint | Documents Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.Project.GlobalAndFeatureResource
- VS.SharePoint.Project.AddResourceDialog
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- globalizing [SharePoint development in Visual Studio]
- localizing [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, localizing
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 89cc146a64e1e74c2682163ba3bebc16ed5a84e7
ms.sourcegitcommit: 1466ac0f49ebf7448ea4507ae3f79acb25d51d3e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/22/2018
---
# <a name="localizing-sharepoint-solutions"></a>Localisation de solutions SharePoint
  Le processus de préparation de vos applications afin qu’ils peuvent être utilisés dans le monde entier est appelé à la localisation. Localisation est traduction de ressources pour une culture spécifique. Pour plus d’informations, consultez [globalisation et localisation d’Applications](/visualstudio/ide/globalizing-and-localizing-applications). Cette rubrique fournit une vue d’ensemble de la localisation d’une solution SharePoint.  
  
 Pour localiser une solution, vous supprimez des chaînes codées en dur dans le code et d’abstraire les dans les fichiers de ressources. Un fichier de ressources est un [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)]-en fonction du fichier avec l’extension .resx. Le fichier de ressources contient les versions traduites des chaînes utilisées dans votre solution. Pour plus d’informations, consultez [ressources dans les Applications](http://go.microsoft.com/fwlink/?LinkID=155844).  
  
> [!NOTE]  
>  Ajoutez uniquement les ressources de chaîne aux fichiers de ressources de solution SharePoint. Bien que l’éditeur de ressources vous permet d’ajouter des ressources, des ressources ne déploient pas sur SharePoint.  
  
## <a name="resource-files"></a>Fichiers de ressources  
 Il existe trois types de fichiers de ressources : par défaut, indépendante du langage et spécifiques au langage.  
  
|Type de fichier de ressources|Description|  
|------------------------|-----------------|  
|Par défaut|Également appelé une ressource de secours, les fichiers de ressources par défaut contiennent des chaînes localisées pour la culture par défaut, tel que l’anglais. Ils sont utilisés si aucun fichier de ressource localisée pour la langue spécifiée peut être trouvé. Ressources de valeur par défaut n’ont pas de fichiers distincts, ils sont stockés dans l’assembly d’application principal.|  
|Indépendante du langage|Un fichier de ressources qui contient des chaînes localisées pour une langue, mais pas une culture spécifique. Par exemple, « fr » pour Français.|  
|Spécifique au langage|Un fichier de ressources qui contient des chaînes localisées pour une langue et une culture. Par exemple, « fr-CA » pour Français canadien.|  
  
 Pour plus d’informations, consultez [organisation hiérarchique des ressources pour la localisation](http://go.microsoft.com/fwlink/?LinkId=178360).  
  
 Pour spécifier les fichiers de ressources par défaut dans les projets SharePoint que vous développez dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], choisissez **langue indifférente (pays indifférent)** dans la liste de la culture de la **ajouter une ressource** boîte de dialogue lorsque vous Ajouter un fichier de ressources.  
  
## <a name="localizing-visual-studio-sharepoint-solutions"></a>Localisation de Solutions de Visual Studio SharePoint  
 Quand vous localisez une solution, vous devez envisager de toutes les informations textuelles que votre solution affiche aux utilisateurs. Messages d’information, messages d’erreur, et [!INCLUDE[TLA2#tla_ui](../sharepoint/includes/tla2sharptla-ui-md.md)] chaînes doivent être traduits et ces traductions placées dans les fichiers de ressources.  
  
 Chaque chaîne dans un fichier de ressources a un identificateur unique. Utiliser le même identificateur pour la chaîne traduite dans chaque fichier de ressources. Par exemple, si « String1 » est l’identificateur de la première chaîne dans le fichier de ressources par défaut, vous pouvez utiliser le même identificateur pour la première chaîne dans les fichiers de ressources spécifiques aux langues.  
  
 Il existe trois domaines vous localisez généralement dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] applications SharePoint : fonctionnalités, le balisage de page ASPX et le code. À des fins d’illustration, les sections suivantes vous possédez une solution SharePoint que vous souhaitez localiser en allemand et en japonais. La langue par défaut est l’anglaise.  
  
### <a name="localizing-features"></a>Localisation des fonctionnalités  
 Pour localiser une fonctionnalité, vous devez remplacer le codé en dur le titre et la description de la fonctionnalité avec une expression qui référence le titre traduit et la chaîne dans le fichier de ressources localisées. Vous effectuez cette modification dans le **Concepteur de fonctionnalités** dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Pour plus d’informations, consultez [Comment : localiser une fonctionnalité](../sharepoint/how-to-localize-a-feature.md).  
  
 Pour localiser votre fonctionnalité anglaise en allemand et en japonais, vous ajoutez trois éléments de projet de fichier de ressources à votre projet : un pour l’anglais, un pour l’allemand et un pour le japonais. Les fichiers de ressources de fonctionnalité ne peut pas être utilisés pour localiser le balisage ASPX ou le code ; fichiers de ressources séparés sont requis pour eux.  
  
 Après avoir créé la fonctionnalité fichiers de ressources, ajouter des chaînes traduites. Accédez aux chaînes localisées avec une expression au format suivant :  
  
```aspx-csharp  
$Resources:String ID  
```  
  
 Ressources de fonctionnalité dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] sont toujours nommées Resources. Si vous sélectionnez une langue autre que langue indifférente, puis une culture [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)] est ajouté au nom du fichier de ressources. Par exemple, si vous ajoutez un fichier de ressources de fonctionnalité de langue indifférente (par défaut), il est appelé Resources.resx. Si vous ajoutez une ressource de fonctionnalité de langage spécifiques en sélectionnant la culture Japonais (Japon), le fichier est appelé Resources.ja-JP.resx. Noms de fichiers de ressources de fonctionnalité sont automatiquement affectés et ne peut pas être modifiés.  
  
 L’étendue de ressources de fonctionnalité est locale à la fonctionnalité qu’ils sont ajoutés à. Pour créer des ressources qui peuvent être utilisées par n’importe quel fichier de fonctionnalité ou un élément de la solution, ajoutez un **fichier de ressources Global** élément de projet au lieu d’un fichier de ressources de fonctionnalité. Le **fichier de ressources Global** élément de projet se trouve dans le **2010** dossier sous **SharePoint** dans les **ajouter un nouvel élément** boîte de dialogue. Déploiement des fichiers de ressources globales dans le dossier \Resources du dossier racine SharePoint.  
  
### <a name="localizing-aspx-page-markup"></a>Localisation du balisage de Page ASPX  
 Pour localiser [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] pages, vous ajoutez trois éléments de projet de fichier de ressources à votre projet : un pour l’anglais, un pour l’allemand et un pour le japonais. Si vous n’avez pas à localiser le code en plus du balisage, vous pouvez ajouter à la place les fichiers de ressources globales.  
  
 Fournissez un nom pour le fichier de ressources de langue par défaut. Attribuer les fichiers de ressources localisés le même nom que celui ajouté avec la culture spécifique au langage [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)]. Par exemple, MyAppResources.de-de.resx pour l’allemand et MyAppResources.ja-JP.resx pour le japonais.  
  
 Définir le **Type de déploiement** propriété de chaque fichier de ressources à **par AppGlobalResource**. Cela entraîne des fichiers de ressources à déployer dans le dossier App_GlobalResources, où ils sont disponibles pour toutes les pages ASPX et les contrôles dans la solution. Le dossier App_GlobalResources se trouve dans C:\inetpub\wwwroot\wss\VirtualDirectories\\< numéro de port\>\App_GlobalResources.  
  
> [!NOTE]  
>  Si vous utilisez des fichiers de ressources globales, déplacez-les vers le dossier d’élément de projet pour activer la propriété Type de déploiement et autres propriétés spécifiques à SharePoint.  
  
 Fichiers de ressources de balisage ASPX peuvent également être utilisés pour localiser le code. Si vous utilisez les ressources pour localiser le code en plus du balisage ASPX, conservez le paramètre de propriété Action de génération de chaque fichier en tant que ressource incorporée afin que la ressource à compiler dans un assembly satellite. Toutefois, si vous utilisez les fichiers de ressources uniquement pour localiser le balisage, vous pouvez éventuellement modifier l’Action de génération au contenu pour empêcher que le fichier qui est compilé dans l’assembly d’application principal.  
  
 Remplacez toutes les chaînes de propriété codées en dur dans votre balisage de contrôles et les pages ASPX par une expression au format suivant :  
  
```aspx-csharp  
<asp:<class> runat="server" Text="<%$Resources:<Resource File Name>, <String ID>%>" />  
```  
  
 Par exemple :  
  
```aspx-csharp  
<asp:Button ID="btn1" runat="server" onclick="btn1_Click" Text="<%$Resources:Resource1,String7%>"></asp:Button>  
```  
  
 Pour ASPX sous forme de texte, utilisez une expression au format suivant :  
  
```aspx-csharp  
<asp:literal ID="<ID>" runat="server" Text="<%$Resources:<Resource File Name>, <String ID>%>" />  
```  
  
 Par exemple :  
  
```aspx-csharp  
<asp:literal ID="Literal1" runat="server" Text="<%$Resources:Resource1, String9%>" />  
```  
  
 Pour plus d’informations, consultez [Comment : localiser le balisage ASPX](../sharepoint/how-to-localize-aspx-markup.md).  
  
### <a name="localizing-code"></a>Localisation du Code  
 En plus de la localisation des chaînes de fonctionnalité et [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] balisage, vous devez également localiser les chaînes de message et les chaînes d’erreur qui s’affichent dans le code de votre solution. Localisés d’information et messages d’erreur sont contenus dans des assemblys satellites. Les assemblys satellites contiennent des chaînes qui sont visibles par les utilisateurs, tels que [!INCLUDE[TLA2#tla_ui](../sharepoint/includes/tla2sharptla-ui-md.md)] messages texte et de sortie comme les exceptions.  
  
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] utilise le modèle de hub et spoke .NET Framework standard. Le concentrateur ou un assembly de programme principal contient les ressources de langue par défaut. Les spokes, ou assemblys satellites, contiennent les ressources spécifiques à une langue. Pour plus d’informations, consultez [Empaquetage et déploiement de ressources](http://go.microsoft.com/fwlink/?LinkId=179280). Assemblys satellites sont compilés à partir de fichiers de ressources (.resx). Lorsque vous ajoutez des fichiers de ressources de langue spécifiques à votre projet et le package de solution, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] compile les fichiers de ressources dans des assemblys satellites nommés *nom du projet*. resources.dll.  
  
 Comme avec le balisage ASPX, localiser du code d’application SharePoint en ajoutant des éléments de projet de fichier de ressources distincts pour votre projet ; un pour la langue par défaut et un pour chaque langue est localisée. Toutefois, comme mentionné précédemment, si vous avez déjà des fichiers de ressources pour la localisation du balisage ASPX, vous pouvez les réutiliser pour localiser le code. Si vous avez besoin créer des fichiers de ressources, nommez le fichier de ressources de langue par défaut de votre choix, avec l’extension .resx. Affectez des fichiers de ressources localisés le même nom que celui ajouté avec la culture spécifique au langage [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)]. Définir la propriété Action de génération de chaque fichier de ressources pour la ressource incorporée pour permettre la création d’assemblys de ressources satellites.  
  
 Pour créer les assemblys satellites, générez le projet, puis ajoutez les fichiers comme assemblys supplémentaires via la **avancé** onglet de la **Concepteur de packages**. Lorsque vous ajoutez les assemblys, ajoutez une culture [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)] dossier pour le chemin d’accès, tel que fr-fr\\*nom d’élément de projet*. resources.dll. Cela permet au package de contenir des fichiers qui ont le même nom.  
  
 Dans votre code, remplacez les chaînes codées en dur avec des appels à la <xref:System.Web.HttpContext.GetGlobalResourceObject%2A> méthode à l’aide de la syntaxe suivante :  
  
```aspx-csharp  
HttpContext.GetGlobalResourceObject("<Resource File Name>", "<String ID>")  
```  
  
 Pour plus d’informations, consultez [Comment : localiser le Code](../sharepoint/how-to-localize-code.md).  
  
#### <a name="web-part-code-localization"></a>Localisation du Code Web Part  
 WebPart inclure une fonctionnalité de l’éditeur de propriété personnalisée qui inclut les attributs de code qui utilisent des chaînes codées en dur, par exemple WebDisplayName, Category et WebDescription. Pour remplacer les valeurs de chaîne pour ces attributs, créez une classe séparée qui dérive de la classe de l’attribut. Dans ces classes, définissez la propriété l’attribut. La propriété d’attribut dépend de la classe de base. Par exemple, la propriété d’attribut WebDisplayName est DisplayNameValue et la propriété d’attribut WebDescription est DescriptionValue.  
  
 Dans la classe dérivée, référencez l’ID de chaîne à partir du fichier de ressources et l’objet ResourceManager pour obtenir la valeur localisée pour l’ID de chaîne. Cette valeur de retour à l’attribut d’éditeur de propriétés.  
  
## <a name="see-also"></a>Voir aussi  
 [Comment : localiser une fonctionnalité](../sharepoint/how-to-localize-a-feature.md)   
 [Comment : localiser le balisage ASPX](../sharepoint/how-to-localize-aspx-markup.md)   
 [Comment : localiser du Code](../sharepoint/how-to-localize-code.md)   
 [Comment : ajouter un fichier de ressources](../sharepoint/how-to-add-a-resource-file.md)   
 [Guide pratique pour utiliser un fichier de ressources pour spécifier des noms localisés, propriétés et autorisations](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)  
  
  