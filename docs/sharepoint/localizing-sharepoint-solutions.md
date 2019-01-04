---
title: Localisation de Solutions SharePoint | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.Project.GlobalAndFeatureResource
- VS.SharePoint.Project.AddResourceDialog
dev_langs:
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
ms.openlocfilehash: b653efc0cce8d8fb2b3e28b8e6c61e6371b4f6e9
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53837354"
---
# <a name="localize-sharepoint-solutions"></a>Localiser des solutions SharePoint

  Le processus de préparation de vos applications afin qu’elles puissent être utilisées mondialement est appelé localisation. La localisation est traduction de ressources pour une culture spécifique. Pour plus d’informations, consultez [Globalizing and Localizing Applications](../ide/globalizing-and-localizing-applications.md). Cette rubrique fournit une vue d’ensemble de la localisation d’une solution SharePoint.  
  
 Pour localiser une solution, vous supprimez des chaînes codées en dur à partir du code et les rendez abstraites dans des fichiers de ressources. Un fichier de ressources est un [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)]-en fonction du fichier avec un *.resx* extension. Le fichier de ressources contient les versions traduites des chaînes utilisées dans votre solution. Pour plus d’informations, consultez [ressources dans les Applications](http://go.microsoft.com/fwlink/?LinkID=155844).  
  
> [!NOTE]  
>  Ajouter des ressources de type chaîne uniquement aux fichiers de ressources de solution SharePoint. Bien que l’éditeur de ressources permet d’ajouter des ressources, des ressources ne déploient pas sur SharePoint.  
  
## <a name="resource-files"></a>Fichiers de ressources
 Il existe trois types de fichiers de ressources : par défaut, indépendant de la langue et spécifique à la langue.  
  
|Type de fichier de ressources|Description|  
|------------------------|-----------------|  
|Par défaut|Également appelé une ressource de secours, les fichiers de ressources par défaut contiennent des chaînes localisées pour la culture par défaut, par exemple l’anglais. Ils sont utilisés si aucun fichier de ressource localisée pour la langue spécifiée ne peut être trouvée. Ressources par défaut n’ont pas de fichiers distincts, ils sont stockés dans l’assembly principal de l’application.|  
|Indépendante du langage|Un fichier de ressources qui contient des chaînes localisées pour une langue, mais pas une culture spécifique. Par exemple, « fr » pour Français.|  
|Spécifique au langage|Un fichier de ressources qui contient des chaînes localisées pour une langue et une culture. Par exemple, « fr-CA » pour Français canadien.|  
  
 Pour plus d’informations, consultez [organisation hiérarchique des ressources pour la localisation](http://go.microsoft.com/fwlink/?LinkId=178360).  
  
 Pour spécifier les fichiers de ressources par défaut dans les projets SharePoint que vous développez dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], choisissez **langue indifférente (pays indifférent)** dans la liste de la culture de la **ajouter une ressource** boîte de dialogue lorsque vous Ajouter un fichier de ressources.  
  
## <a name="localize-visual-studio-sharepoint-solutions"></a>Localiser des solutions de Visual Studio SharePoint
 Lorsque vous localisez une solution, vous devez envisager toutes les informations textuelles que votre solution affiche aux utilisateurs. Messages d’information, messages d’erreur, et [!INCLUDE[TLA2#tla_ui](../sharepoint/includes/tla2sharptla-ui-md.md)] chaînes doivent être traduits et ces traductions placées dans les fichiers de ressources.  
  
 Chaque chaîne dans un fichier de ressources a un identificateur unique. Utilisez le même identificateur pour la chaîne traduite dans chaque fichier de ressources. Par exemple, si « String1 » est l’identificateur de la première chaîne dans le fichier de ressources par défaut, vous pouvez utiliser le même identificateur pour la première chaîne dans les fichiers de ressources linguistiques.  
  
 Il existe trois domaines vous localisez généralement dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] applications SharePoint : fonctionnalités, le balisage de page ASPX et le code. À des fins d’illustration, les sections suivantes supposent que d’une solution SharePoint que vous souhaitez localiser en allemand et japonais. La langue par défaut est l’anglaise.  
  
### <a name="localize-features"></a>Localiser des fonctionnalités
 Pour localiser une fonctionnalité, vous devez remplacer le titre codé en dur et la description de la fonctionnalité avec une expression qui référence le titre traduite et la chaîne dans le fichier de ressources localisées. Vous effectuez cette modification dans le **Concepteur de fonctionnalités** dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Pour plus d'informations, voir [Procédure : Localiser une fonctionnalité](../sharepoint/how-to-localize-a-feature.md).  
  
 Pour localiser votre fonctionnalité anglaise en allemand et en japonais, vous ajoutez trois éléments de projet de fichier de ressources à votre projet : un pour l’anglais, un pour l’allemand et un pour le japonais. Fichiers de ressources de fonctionnalité ne peut pas être utilisés pour localiser le balisage ASPX ou le code ; fichiers de ressources séparés sont nécessaires.  
  
 Après avoir créé la fonctionnalité fichiers de ressources, leur ajouter des chaînes traduites. Accéder aux chaînes localisées avec une expression au format suivant :  
  
```aspx-csharp  
$Resources:String ID  
```  
  
 Ressources de fonctionnalité dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] sont toujours nommées Resources. Si vous sélectionnez une langue autre que langue indifférente, puis une culture [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)] est ajouté au nom du fichier de ressources. Par exemple, si vous ajoutez un fichier de ressources de fonctionnalité de langue indifférente (par défaut), il est appelé *Resources.resx*. Si vous ajoutez une ressource de fonctionnalité de langage spécifique en sélectionnant la culture Japonais (Japon), le fichier est appelé *Resources.ja-JP.resx*. Noms de fichiers de ressources de fonctionnalité sont automatiquement assignés et ne peut pas être modifiés.  
  
 La portée des ressources de fonctionnalité est locale à la fonctionnalité, à qu'ils sont ajoutés. Pour créer des ressources qui peuvent être utilisées par n’importe quel fichier de fonctionnalité ou un élément dans la solution, ajoutez un **fichier de ressources Global** élément de projet au lieu d’un fichier de ressources de fonctionnalité. Le **fichier de ressources Global** élément de projet se trouve dans le **2010** dossier sous **SharePoint** dans le **ajouter un nouvel élément** boîte de dialogue. Déploiement des fichiers de ressources globales dans le dossier \Resources du dossier racine SharePoint.  
  
### <a name="localize-aspx-page-markup"></a>Localiser le balisage de page ASPX
 Pour localiser [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] pages, vous ajoutez trois éléments de projet de fichier de ressources à votre projet : un pour l’anglais, un pour l’allemand et un pour le japonais. Si vous n’avez pas de localiser le code en plus du balisage, vous pouvez ajouter à la place les fichiers de ressources globales.  
  
 Fournissez un nom pour le fichier de ressources de langue par défaut. Donner les fichiers de ressources localisés le même nom que celui ajouté avec la culture spécifique au langage [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)]. Par exemple, *MyAppResources.de-de.resx* pour l’allemand et *MyAppResources.ja-JP.resx* pour le japonais.  
  
 Définir le **Type de déploiement** propriété de chaque fichier de ressources à **AppGlobalResource**. Cela entraîne des fichiers de ressources à déployer dans le dossier App_GlobalResources, où ils sont disponibles pour toutes les pages ASPX et les contrôles dans la solution. Le dossier App_GlobalResources se trouve dans C:\inetpub\wwwroot\wss\VirtualDirectories\\< numéro de port\>\App_GlobalResources.  
  
> [!NOTE]  
>  Si vous utilisez des fichiers de ressources non globales, déplacez-les vers le dossier d’éléments de projet pour activer la propriété Type de déploiement et autres propriétés spécifiques à SharePoint.  
  
 Fichiers de ressources de balisage ASPX peuvent également être utilisés pour localiser le code. Si vous utilisez les ressources pour localiser le code en plus du balisage ASPX, conservez le paramètre de propriété Action de génération de chaque fichier en tant que ressource incorporée afin que la ressource à compiler dans un assembly satellite. Toutefois, si vous utilisez les fichiers de ressources uniquement pour localiser le balisage, vous pouvez éventuellement modifier Action de génération au contenu pour empêcher que le fichier qui est compilé dans l’assembly principal de l’application.  
  
 Remplacez toutes les chaînes de propriété codées en dur dans votre balisage de pages et contrôles ASPX par une expression au format suivant :  
  
```aspx-csharp  
<asp:<class> runat="server" Text="<%$Resources:<Resource File Name>, <String ID>%>" />  
```  
  
 Exemple :  
  
```aspx-csharp  
<asp:Button ID="btn1" runat="server" onclick="btn1_Click" Text="<%$Resources:Resource1,String7%>"></asp:Button>  
```  
  
 Pour ASPX comme texte, utilisez une expression au format suivant :  
  
```aspx-csharp  
<asp:literal ID="<ID>" runat="server" Text="<%$Resources:<Resource File Name>, <String ID>%>" />  
```  
  
 Exemple :  
  
```aspx-csharp  
<asp:literal ID="Literal1" runat="server" Text="<%$Resources:Resource1, String9%>" />  
```  
  
 Pour plus d'informations, voir [Procédure : Localiser le balisage ASPX](../sharepoint/how-to-localize-aspx-markup.md).  
  
### <a name="localize-code"></a>Localiser le code
 Outre la localisation des chaînes de fonctionnalité et [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] balisage, vous devez également localiser les chaînes de message et les chaînes d’erreur qui s’affichent dans le code de votre solution. D’information localisés et les messages d’erreur sont contenus dans des assemblys satellites. Les assemblys satellites contiennent des chaînes qui sont visibles aux utilisateurs, tel que [!INCLUDE[TLA2#tla_ui](../sharepoint/includes/tla2sharptla-ui-md.md)] messages texte et de sortie comme les exceptions.  
  
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] utilise le modèle de hub- and -spoke .NET Framework standard. Le hub, ou assembly de programme principal, contient les ressources de langue par défaut. Les spokes, ou assemblys satellites, contiennent les ressources spécifiques au langage. Pour plus d’informations, consultez [Empaquetage et déploiement de ressources](http://go.microsoft.com/fwlink/?LinkId=179280). Les assemblys satellites sont compilés à partir de la ressource (*.resx*) les fichiers. Lorsque vous ajoutez des fichiers de ressources spécifiques à la langue à votre projet et le package de solution, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] compile les fichiers de ressources dans des assemblys satellites nommés *{nom_projet}.resources.dll*.  
  
 Comme avec le balisage ASPX, localisez le code d’application SharePoint en ajoutant des éléments de projet de fichier de ressources distincts pour votre projet ; un pour la langue par défaut et un pour chaque langue est localisée. Toutefois, comme mentionné précédemment, si vous avez déjà des fichiers de ressources pour la localisation du balisage ASPX, vous pouvez les réutiliser pour la localisation du code. Si vous avez besoin créer des fichiers de ressources, nommez le fichier de ressources de langue par défaut de votre choix, avec un *.resx* extension. Nommez les fichiers de ressources localisés le même nom que celui ajouté avec la culture spécifique au langage [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)]. La propriété Action de génération de chaque fichier de ressources la valeur ressource incorporée pour permettre la création d’assemblys de ressources satellites.  
  
 Pour créer les assemblys satellites, générez le projet, puis ajoutez les fichiers comme assemblys supplémentaires via le **avancé** onglet de la **Concepteur de packages**. Lorsque vous ajoutez les assemblys, ajoutez une culture [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)] dossier pour le chemin d’accès de l’emplacement, tel que *fr-fr\\{nom d’élément de projet}.resources.dll*. Cela permet au package contenir les fichiers qui ont le même nom.  
  
 Dans votre code, remplacez les chaînes codées en dur avec les appels à la <xref:System.Web.HttpContext.GetGlobalResourceObject%2A> méthode à l’aide de la syntaxe suivante :  
  
```aspx-csharp  
HttpContext.GetGlobalResourceObject("<Resource File Name>", "<String ID>")  
```  
  
 Pour plus d'informations, voir [Procédure : Localiser le code](../sharepoint/how-to-localize-code.md).  
  
#### <a name="web-part-code-localization"></a>Localisation du code Web partie
 Composants WebPart inclure une fonctionnalité d’éditeur de propriété personnalisée qui inclut des attributs de code qui utilisent des chaînes codées en dur, par exemple WebDisplayName, Category et WebDescription. Pour remplacer les valeurs de chaîne pour ces attributs, créez une classe séparée qui dérive de la classe de l’attribut. Dans ces classes, définissez la propriété de l’attribut. La propriété d’attribut dépend de la classe de base. Par exemple, la propriété d’attribut WebDisplayName est DisplayNameValue et la propriété d’attribut WebDescription est DescriptionValue.  
  
 Dans la classe dérivée, référencez l’ID de chaîne à partir du fichier de ressources et l’objet ResourceManager pour obtenir la valeur localisée pour l’ID de chaîne. Retourne cette valeur à l’attribut d’éditeur de propriété.  
  
## <a name="see-also"></a>Voir aussi
 [Guide pratique pour Localiser une fonctionnalité](../sharepoint/how-to-localize-a-feature.md)   
 [Guide pratique pour Localiser le balisage ASPX](../sharepoint/how-to-localize-aspx-markup.md)   
 [Guide pratique pour Localiser le code](../sharepoint/how-to-localize-code.md)   
 [Guide pratique pour Ajouter un fichier de ressources](../sharepoint/how-to-add-a-resource-file.md)   
 [Guide pratique pour Utilisez un fichier de ressources pour spécifier des autorisations, les propriétés et les noms localisés](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)  
