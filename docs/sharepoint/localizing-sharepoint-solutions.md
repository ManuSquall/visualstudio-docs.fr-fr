---
title: Localisation de solutions SharePoint | Microsoft Docs
ms.date: 02/02/2017
ms.topic: overview
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
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 0a7b04ab1f77eba15f2bc617f89514a8d0952674
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: fr-FR
ms.lasthandoff: 07/06/2020
ms.locfileid: "86017142"
---
# <a name="localize-sharepoint-solutions"></a>Localiser des solutions SharePoint

  Le processus de préparation de vos applications afin qu’elles puissent être utilisées dans le monde entier est appelé localisation. La localisation traduit les ressources en une culture spécifique. Pour plus d’informations, consultez [globalisation et localisation d’applications](../ide/globalizing-and-localizing-applications.md). Cette rubrique fournit une vue d’ensemble de la localisation d’une solution SharePoint.

 Pour localiser une solution, vous supprimez les chaînes codées en dur du code et les extrayez dans des fichiers de ressources. Un fichier de ressources est un [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] fichier de base avec une extension *. resx* . Le fichier de ressources contient les versions traduites des chaînes utilisées dans votre solution. Pour plus d’informations, consultez [ressources dans les applications](/previous-versions/dotnet/netframework-4.0/f45fce5x(v=vs.100)).

> [!NOTE]
> Ajoutez uniquement des ressources de type chaîne aux fichiers de ressources de solution SharePoint. Bien que l’éditeur de ressources vous permette d’ajouter des ressources qui ne sont pas des chaînes, les ressources autres que des chaînes ne sont pas déployées sur SharePoint.

## <a name="resource-files"></a>Fichiers de ressources
 Il existe trois types de fichiers de ressources : par défaut, indépendant de la langue et spécifique à une langue.

|Type de fichier de ressources|Description|
|------------------------|-----------------|
|Default|Également appelée ressource de secours, les fichiers de ressources par défaut contiennent des chaînes localisées pour la culture par défaut, par exemple l’anglais. Elles sont utilisées si aucun fichier de ressources localisé pour la langue spécifiée n’est trouvé. Les ressources par défaut n’ont pas de fichiers distincts, elles sont stockées dans l’assembly d’application principal.|
|Indépendant de la langue|Fichier de ressources qui contient des chaînes localisées pour une langue, mais pas une culture spécifique. Par exemple, « fr » pour le français.|
|Spécifiques au langage|Fichier de ressources qui contient des chaînes localisées pour une langue et une culture. Par exemple, « fr-CA » pour le français canadien.|

 Pour plus d’informations, consultez [organisation hiérarchique des ressources pour la localisation](../ide/globalizing-and-localizing-applications.md).

 Pour spécifier les fichiers de ressources par défaut dans les projets SharePoint que vous développez dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , choisissez **Langue indifférente (pays indifférent)** dans la liste culture de la boîte de dialogue **Ajouter une ressource** lorsque vous ajoutez un fichier de ressources.

## <a name="localize-visual-studio-sharepoint-solutions"></a>Localiser des solutions Visual Studio SharePoint
 Lorsque vous localisez une solution, vous devez prendre en compte toutes les informations textuelles que votre solution affiche aux utilisateurs. Les messages d’information, les messages d’erreur et les [!INCLUDE[TLA2#tla_ui](../sharepoint/includes/tla2sharptla-ui-md.md)] chaînes doivent être traduits et les traductions placées dans les fichiers de ressources.

 Chaque chaîne dans un fichier de ressources a un identificateur unique. Utilisez le même identificateur pour la chaîne traduite dans chaque fichier de ressources. Par exemple, si « chaîne1 » est l’identificateur de la première chaîne dans le fichier de ressources par défaut, utilisez le même identificateur pour la première chaîne dans les fichiers de ressources spécifiques à une langue.

 Il existe trois zones que vous localisez généralement dans les [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] applications SharePoint : les fonctionnalités, le balisage de page aspx et le code. À des fins d’illustration, les sections suivantes supposent que vous avez une solution SharePoint que vous souhaitez localiser en allemand et en japonais. La langue par défaut est l'anglais.

### <a name="localize-features"></a>Localiser les fonctionnalités
 Pour localiser une fonctionnalité, vous devez remplacer le titre et la description codés en dur de la fonctionnalité par une expression qui fait référence au titre et à la chaîne traduits dans le fichier de ressources localisé. Vous apportez cette modification dans le **Concepteur de fonctionnalités** de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . Pour plus d’informations, consultez [Comment : localiser une fonctionnalité](../sharepoint/how-to-localize-a-feature.md).

 Pour localiser votre fonctionnalité en anglais en allemand et en japonais, vous ajoutez trois éléments de projet de fichier de ressources à votre projet : un pour l’anglais, un pour l’allemand et un pour le japonais. Les fichiers de ressources de fonctionnalité ne peuvent pas être utilisés pour localiser le code ou le balisage ASPX ; des fichiers de ressources distincts sont requis pour eux.

 Après avoir créé les fichiers de ressources de fonctionnalité, ajoutez-y des chaînes traduites. Accédez aux chaînes localisées avec une expression au format suivant :

```aspx-csharp
$Resources:String ID
```

 Les ressources de fonctionnalités dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] sont toujours nommées ressources. Si vous sélectionnez une langue autre que la langue indifférente, une culture [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)] est ajoutée au nom du fichier de ressources. Par exemple, si vous ajoutez un fichier de ressources de fonctionnalité de langue indifférente (par défaut), il est appelé *Resources. resx*. Si vous ajoutez une ressource de fonctionnalité spécifique à une langue en sélectionnant une culture japonaise (Japon), le fichier est appelé *Resources. ja-JP. resx*. Les noms des fichiers de ressources de fonctionnalités sont automatiquement attribués et ne peuvent pas être modifiés.

 L’étendue des ressources de fonctionnalités est locale à la fonctionnalité à laquelle elles sont ajoutées. Pour créer des ressources qui peuvent être utilisées par n’importe quel fichier de fonctionnalité ou d’élément dans la solution, ajoutez un élément de projet de **fichier de ressources globales** au lieu d’un fichier de ressources de fonctionnalité. L’élément de projet de **fichier de ressources global** se trouve dans le dossier **2010** sous **SharePoint** dans la boîte de dialogue **Ajouter un nouvel élément** . Les fichiers de ressources globales sont déployés dans le dossier \Resources du dossier racine SharePoint.

### <a name="localize-aspx-page-markup"></a>Localiser le balisage de page ASPX
 Pour localiser des [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] pages, vous ajoutez trois éléments de projet de fichier de ressources à votre projet : un pour l’anglais, un pour l’allemand et un pour le japonais. Si vous n’avez pas besoin de localiser du code en plus du balisage, vous pouvez ajouter des fichiers de ressources globales.

 Fournissez un nom pour le fichier de ressources de langue par défaut. Donnez aux fichiers de ressources localisés le même nom que celui ajouté à la culture spécifique à la langue [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)] . Par exemple, *MyAppResources.de-de. resx* pour l’allemand et *MyAppResources. ja-JP. resx pour le* japonais.

 Définissez la propriété **type de déploiement** de chaque fichier de ressources sur **AppGlobalResource**. Les fichiers de ressources sont alors déployés dans le dossier App_GlobalResources, où ils sont disponibles pour toutes les pages et tous les contrôles ASPX de la solution. Le dossier App_GlobalResources se trouve dans C:\inetpub\wwwroot\wss\VirtualDirectories \\<numéro de port \> \ App_GlobalResources.

> [!NOTE]
> Si vous utilisez des fichiers de ressources non globaux, déplacez-les dans le dossier d’éléments de projet pour activer la propriété type de déploiement et d’autres propriétés spécifiques à SharePoint.

 Les fichiers de ressources de balisage ASPX peuvent également servir à localiser du code. Si vous utilisez les ressources pour localiser le code en plus du balisage ASPX, laissez la valeur de la propriété action de génération de chaque fichier en tant que ressource incorporée pour que la ressource soit compilée dans un assembly satellite. Toutefois, si vous utilisez les fichiers de ressources uniquement pour localiser le balisage, vous pouvez éventuellement modifier action de génération en contenu pour empêcher la compilation du fichier dans l’assembly d’application principal.

 Remplacez toutes les chaînes de propriété codées en dur dans le balisage des pages et des contrôles ASPX par une expression au format suivant :

```aspx-csharp
<asp:<class> runat="server" Text="<%$Resources:<Resource File Name>, <String ID>%>" />
```

 Par exemple :

```aspx-csharp
<asp:Button ID="btn1" runat="server" onclick="btn1_Click" Text="<%$Resources:Resource1,String7%>"></asp:Button>
```

 Pour ASPX en tant que texte, utilisez une expression au format suivant :

```aspx-csharp
<asp:literal ID="<ID>" runat="server" Text="<%$Resources:<Resource File Name>, <String ID>%>" />
```

 Par exemple :

```aspx-csharp
<asp:literal ID="Literal1" runat="server" Text="<%$Resources:Resource1, String9%>" />
```

 Pour plus d’informations, consultez Guide pratique [pour localiser le balisage aspx](../sharepoint/how-to-localize-aspx-markup.md).

### <a name="localize-code"></a>Localiser du code
 En plus de la localisation des chaînes de fonctionnalités et [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] du balisage, vous devez également localiser les chaînes de message et d’erreur qui s’affichent dans le code de votre solution. Les messages d’information et d’erreur localisés sont contenus dans des assemblys satellites. Les assemblys satellites contiennent des chaînes qui sont visibles par les utilisateurs, telles que [!INCLUDE[TLA2#tla_ui](../sharepoint/includes/tla2sharptla-ui-md.md)] des messages texte et de sortie tels que des exceptions.

 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]utilise le modèle Hub et spoke de .NET Framework standard. Le concentrateur, ou assembly de programme principal, contient les ressources de langue par défaut. Les spokes, ou assemblys satellites, contiennent les ressources spécifiques à une langue. Pour plus d’informations, consultez [Empaquetage et déploiement de ressources](/previous-versions/dotnet/netframework-4.0/sb6a8618(v=vs.100)). Les assemblys satellites sont compilés à partir de fichiers de ressources (*. resx*). Lorsque vous ajoutez des fichiers de ressources spécifiques à une langue à votre projet et au package de solution, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] compile les fichiers de ressources dans des assemblys satellites nommés *{Project Name} .resources.dll*.

 Comme avec le balisage ASPX, localisez le code de l’application SharePoint en ajoutant des éléments de projet de fichier de ressources séparés à votre projet. une pour la langue par défaut et une pour chaque langue localisée. Toutefois, comme mentionné précédemment, si vous avez déjà des fichiers de ressources pour la localisation du balisage ASPX, vous pouvez les réutiliser pour localiser le code. Si vous devez créer des fichiers de ressources, attribuez au fichier de ressources de langue par défaut le nom de votre choix, ajouté avec une extension *. resx* . Nommez les fichiers de ressources localisés dont le nom est identique à celui de la culture spécifique à la langue [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)] . Affectez à la propriété action de génération de chaque fichier de ressources la valeur ressource incorporée pour permettre la création d’assemblys de ressources satellites.

 Pour créer les assemblys satellites, générez le projet, puis ajoutez les fichiers en tant qu’assemblys supplémentaires via l’onglet **avancé** du **Concepteur de packages**. Lorsque vous ajoutez les assemblys, ajoutez un [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)] dossier culture au chemin d’accès de l’emplacement, par exemple, *DE-de \\ {nom de l’élément de projet} .resources.dll*. Cela permet au package de contenir des fichiers portant le même nom.

 Dans votre code, remplacez les chaînes codées en dur par des appels à la <xref:System.Web.HttpContext.GetGlobalResourceObject%2A> méthode à l’aide de la syntaxe suivante :

```aspx-csharp
HttpContext.GetGlobalResourceObject("<Resource File Name>", "<String ID>")
```

 Pour plus d’informations, consultez [Comment : localiser du code](../sharepoint/how-to-localize-code.md).

#### <a name="web-part-code-localization"></a>Localisation du code du composant WebPart
 Les composants WebPart incluent une fonctionnalité d’éditeur de propriétés personnalisée qui inclut des attributs de code qui utilisent des chaînes codées en dur, telles que WebDisplayName, Category et WebDescription. Pour remplacer les valeurs de chaîne de ces attributs, créez une classe distincte qui dérive de la classe de l’attribut. Dans ces classes, définissez la propriété de l’attribut. La propriété d’attribut dépend de la classe de base. Par exemple, la propriété d’attribut WebDisplayName est DisplayNameValue et la propriété d’attribut WebDescription est DescriptionValue.

 Dans la classe dérivée, référencez l’ID de chaîne à partir du fichier de ressources et l’objet ResourceManager pour obtenir la valeur localisée de l’ID de chaîne. Retourne cette valeur à l’attribut de l’éditeur de propriétés.

## <a name="see-also"></a>Voir aussi
- [Comment : localiser une fonctionnalité](../sharepoint/how-to-localize-a-feature.md)
- [Comment : localiser le balisage ASPX](../sharepoint/how-to-localize-aspx-markup.md)
- [Comment : localiser du code](../sharepoint/how-to-localize-code.md)
- [Comment : ajouter un fichier de ressources](../sharepoint/how-to-add-a-resource-file.md)
- [Comment : utiliser un fichier de ressources pour spécifier des noms localisés, des propriétés et des autorisations](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)
