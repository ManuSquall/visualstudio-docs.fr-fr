---
title: Modèles d’élément/modèles de projet pour les éléments de projet SharePoint
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint project items, creating custom templates
- .spdata files
- projects [SharePoint development in Visual Studio], creating custom templates
- SharePoint projects, creating custom templates
- SharePoint development in Visual Studio, creating custom project and item templates
- project items [SharePoint development in Visual Studio], creating custom templates
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: ec97eb2dfab7ab92c1e324c89fd044c1a50c2173
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/30/2020
ms.locfileid: "91585613"
---
# <a name="create-item-templates-and-project-templates-for-sharepoint-project-items"></a>Créer des modèles d’élément et des modèles de projet pour les éléments de projet SharePoint

Quand vous définissez un type d’élément de projet SharePoint personnalisé, vous pouvez l’associer à un modèle d’élément ou à un modèle de projet. Cette association permet à d’autres développeurs d’utiliser l’élément de projet dans Visual Studio. Vous pouvez également créer un Assistant pour le modèle.

Par exemple, Visual Studio n’inclut pas de modèle de projet ou de modèle d’élément pour l’ajout d’un champ à un site SharePoint. Vous pouvez définir un type d’élément de projet SharePoint qui représente un champ, puis construire un modèle d’élément que d’autres développeurs peuvent utiliser pour ajouter l’élément de champ à un projet SharePoint. Ou bien, vous pouvez construire un modèle de projet afin que les développeurs puissent créer un projet SharePoint qui possède l’élément de champ. Dans les deux cas, vous pouvez également fournir un assistant qui s’affiche lorsque les développeurs utilisent votre modèle. Cet Assistant peut collecter des informations de la part des développeurs pour configurer le nouvel élément ou le nouveau projet.

Les modèles d’élément et les modèles de projet sont des fichiers *. zip* qui contiennent des fichiers qui sont utilisés par Visual Studio pour créer un projet ou un élément de projet. Pour plus d’informations sur les notions de base des modèles d’élément et des modèles de projet, consultez [créer des modèles de projet et d’élément](../ide/creating-project-and-item-templates.md).

## <a name="create-item-templates"></a>Créer des modèles d’élément
 Lorsque vous créez un modèle d’élément pour un élément de projet SharePoint, certains fichiers sont toujours requis, ainsi que les fichiers facultatifs qui peuvent être utilisés par certains types d’éléments de projet. Pour obtenir une procédure pas à pas qui montre comment définir un type d’élément de projet SharePoint et créer un modèle d’élément pour celui-ci, consultez [procédure pas à pas : créer un élément de projet d’action personnalisée avec un modèle d’élément, partie 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md).

 Le tableau suivant répertorie les fichiers requis pour créer un modèle d’élément pour un élément de projet SharePoint.

|Fichier obligatoire|Description|
|-------------------|-----------------|
|Un fichier *. les données*|Ce fichier XML spécifie le contenu et le comportement par défaut de l’élément de projet. Ce fichier doit être inclus dans le modèle d’élément. Pour plus d’informations sur le contenu des fichiers *. resdonnées* , consultez [Référence du schéma d’élément de projet SharePoint](../sharepoint/sharepoint-project-item-schema-reference.md).|
|Un fichier *. vstemplate* .|Ce fichier fournit à Visual Studio les informations nécessaires pour afficher le modèle dans la boîte de dialogue **Ajouter un nouvel élément** et pour créer un élément de projet à partir du modèle. Ce fichier doit être inclus dans le modèle d’élément. Pour plus d’informations, consultez [fichiers de métadonnées de modèle Visual Studio](/previous-versions/visualstudio/visual-studio-2010/xsxc3ete\(v\=vs.100\)).|
|Assembly d’extension Visual Studio qui implémente l' <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> interface.|Cet assembly définit le comportement au moment de l’exécution de l’élément de projet. Cet assembly doit être inclus dans le package VSIX avec le modèle d’élément. Pour plus d’informations, consultez [définir des types d’éléments de projet SharePoint personnalisés](../sharepoint/defining-custom-sharepoint-project-item-types.md) et [déployer des extensions pour les outils SharePoint dans Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).|

 Le tableau suivant répertorie certains des fichiers facultatifs les plus courants qui peuvent être inclus dans le modèle d’élément. Certains types d’éléments de projet peuvent nécessiter d’autres fichiers non répertoriés ici.

| Fichier facultatif | Description |
|----------------------| - |
| *Elements.xml* | Fichier d' *élément de fonctionnalité* . Ce fichier définit l’interface utilisateur et le comportement de la personnalisation créée par l’élément de projet. Chaque type de personnalisation, comme les instances de liste, les types de contenu ou les actions personnalisées, a un schéma différent qui définit le contenu de ce fichier. Pour plus d’informations, consultez [bloc de construction : fonctionnalités](/previous-versions/office/developer/sharepoint-2010/ee537350(v=office.14)) et [schémas](/previous-versions/office/developer/sharepoint-2010/ms414322(v=office.14))de fonctionnalités. |
| *Schema.xml* | Fichier de schéma pour les définitions de liste. Pour plus d’informations, consultez [bloc de construction : listes et bibliothèques de documents](/previous-versions/office/developer/sharepoint-2010/ee534985(v=office.14)) et [Schema.xml](/previous-versions/office/developer/sharepoint-2010/ms459356(v=office.14)). |
| *. WebPart* | Fichier de *définition de composant WebPart* . Ce fichier contient les paramètres de propriété d’un composant WebPart. Pour plus d’informations, consultez [bloc de construction : composants WebPart](/previous-versions/office/developer/sharepoint-2010/ee535520(v=office.14)). |
| *.ascx* | Fichier UserControl ASP.NET. Ce fichier définit l’interface utilisateur d’un composant Visual Web part. |
| *.aspx* | Fichier de page ASP.NET. Ce fichier contient un balisage XML qui définit une page d’application. |
| fichiers *. cs* ou *. vb* | Ces fichiers de code définissent le comportement des personnalisations SharePoint qui ont un modèle de programmation accessible à partir de Visual C# ou de Visual Basic Code, tels que les pages d’application, les composants WebPart et les flux de travail. |

## <a name="create-project-templates"></a>Créer des modèles de projet
 Lorsque vous créez un modèle de projet SharePoint, certains fichiers sont toujours requis, ainsi que des fichiers facultatifs qui peuvent être utilisés par certains types de projets. En règle générale, les projets SharePoint incluent au moins un élément de projet SharePoint. Cependant, cette condition n'est pas requise. Par exemple, vous pouvez définir un modèle de projet SharePoint qui est destiné à être utilisé uniquement pour déployer des solutions SharePoint créées dans d’autres projets.

 Pour obtenir une procédure pas à pas qui montre comment définir un type d’élément de projet SharePoint et créer un modèle de projet pour celui-ci, consultez [procédure pas à pas : création d’un élément de projet colonne de site avec un modèle de projet, partie 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md).

 Le tableau suivant répertorie les fichiers qui doivent être inclus dans un modèle de projet SharePoint.

|Fichier obligatoire|Description|
|-------------------|-----------------|
|Un fichier *. vstemplate*|Ce fichier fournit à Visual Studio les informations nécessaires pour afficher le modèle dans la boîte de dialogue **nouveau projet** et pour créer un projet à partir du modèle. Pour plus d’informations, consultez [fichiers de métadonnées de modèle Visual Studio](/previous-versions/visualstudio/visual-studio-2010/xsxc3ete\(v\=vs.100\)).|
|Un fichier *. csproj* ou *. vbproj*|Il s’agit du fichier projet. Il définit le contenu et les paramètres de configuration du projet.|
|*Package. Package*|Ce fichier définit le package de déploiement pour le projet. Lorsque vous utilisez le concepteur de packages pour personnaliser le package de solution pour votre projet, Visual Studio stocke les données relatives au package de solution dans ce fichier.<br /><br /> Lorsque vous créez un modèle de projet SharePoint personnalisé, nous vous recommandons d’inclure uniquement le contenu minimal requis dans le fichier *Package. Package* et de configurer le package de solution à l’aide des API de l' <xref:Microsoft.VisualStudio.SharePoint.Packages> espace de noms dans une extension associée au modèle de projet. Si vous procédez ainsi, votre modèle de projet est protégé contre les futures modifications apportées à la structure du fichier *Package. Package* . Pour obtenir un exemple qui montre comment créer un fichier *Package. Package* avec uniquement le contenu requis minimal, consultez [procédure pas à pas : création d’un élément de projet colonne de site avec un modèle de projet, partie 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md).<br /><br /> Si vous souhaitez modifier directement le fichier *Package. Package* , vous pouvez vérifier son contenu à l’aide du schéma dans *% Program Files (x86)% \ Microsoft Visual Studio 11.0 \ Xml\Schemas\PackageModelSchema.xsd*.|
|*Package.Template.xml*|Ce fichier fournit la base du fichier manifeste de la solution (*manifest.xml*) pour le package de solution SharePoint (*. wsp*) généré à partir du projet. Vous pouvez ajouter du contenu à ce fichier si vous souhaitez spécifier un comportement qui n’est pas destiné à être modifié par les utilisateurs de votre type de projet. Pour plus d’informations, consultez [bloc de construction : solutions](/previous-versions/office/developer/sharepoint-2010/ee537008(v=office.14)) et [schéma de solution](/sharepoint/dev/schema/solution-schema).<br /><br /> Quand vous générez un package de solution à partir du projet, Visual Studio fusionne le contenu du package *. Package* et les fichiers *Package.Template.xml* dans le fichier manifeste de la solution. Pour plus d’informations sur la création de packages de solution, consultez [Comment : créer un package de solution SharePoint à l’aide de tâches MSBuild](../sharepoint/how-to-create-a-sharepoint-solution-package-by-using-msbuild-tasks.md).|

 Le tableau suivant répertorie les fichiers facultatifs qui peuvent être inclus dans le modèle de projet.

|Fichier facultatif|Description|
|-------------------|-----------------|
|éléments de projet SharePoint|Vous pouvez inclure un ou plusieurs fichiers. resdonnées qui définissent les types d’éléments de projet SharePoint. Chaque fichier *. resdonnées* doit avoir une <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> implémentation correspondante dans un assembly d’extension qui est inclus dans le package VSIX avec le modèle de projet. Pour plus d’informations, consultez [créer des modèles d’élément](#create-item-templates).<br /><br /> En règle générale, les projets SharePoint incluent au moins un élément de projet SharePoint. Cependant, cette condition n'est pas requise.|
|*\<featureName>. fonctionnalité*|Ce fichier définit une fonctionnalité SharePoint utilisée pour regrouper plusieurs éléments de projet à des fins de déploiement. Quand vous utilisez le concepteur de fonctionnalités pour personnaliser une fonctionnalité dans votre projet, Visual Studio stocke les données relatives à la fonctionnalité dans ce fichier. Si vous souhaitez regrouper les éléments de projet dans des fonctionnalités différentes, vous pouvez inclure plusieurs fichiers *. Feature* .<br /><br /> Lorsque vous créez un modèle de projet SharePoint personnalisé, nous vous recommandons d’inclure uniquement le contenu minimal requis dans chaque fichier *. Feature* , et de configurer des fonctionnalités à l’aide des API de l' <xref:Microsoft.VisualStudio.SharePoint.Features> espace de noms dans une extension associée au modèle de projet. Si vous procédez ainsi, votre modèle de projet est protégé contre les futures modifications apportées à la structure du fichier *. Feature* . Pour obtenir un exemple qui montre comment créer un fichier *. Feature* avec uniquement le contenu requis minimal, consultez [procédure pas à pas : création d’un élément de projet colonne de site avec un modèle de projet, partie 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md).<br /><br /> Si vous souhaitez modifier un fichier *. Feature* directement, vous pouvez vérifier le contenu à l’aide du schéma dans *% Program Files (x86)% \ Microsoft Visual Studio 11.0 \ Xml\Schemas\FeatureModelSchema.xsd*.|
|*\<featureName>.Template.xml*|Ce fichier fournit la base du fichier manifeste de fonctionnalité (*Feature.xml*) pour chaque fonctionnalité générée à partir du projet. Vous pouvez ajouter du contenu à ce fichier si vous souhaitez spécifier un comportement qui n’est pas destiné à être modifié par les utilisateurs de votre type de projet. Pour plus d’informations, consultez [bloc de construction : fonctionnalités](/previous-versions/office/developer/sharepoint-2010/ee537350(v=office.14)) et fichiers de [Feature.xml](/sharepoint/dev/schema/feature-xml-files) .<br /><br /> Quand vous générez un package de solution à partir du projet, Visual Studio fusionne le contenu de chaque paire de fichiers * \<featureName> . Feature* et de fichiers de * \<featureName>.Template.xml* dans un fichier manifeste de fonctionnalité. Pour plus d’informations sur la création de packages de solution, consultez [Comment : créer un package de solution SharePoint à l’aide de tâches MSBuild](../sharepoint/how-to-create-a-sharepoint-solution-package-by-using-msbuild-tasks.md).|

## <a name="create-wizards-for-item-templates-and-project-templates"></a>Créer des assistants pour les modèles d’élément et les modèles de projet
 Une fois que vous avez défini un type d’élément de projet SharePoint et que vous l’avez associé à un élément ou à un modèle de projet, vous pouvez également créer un Assistant. L’Assistant s’affiche lorsqu’un développeur utilise le modèle d’élément pour ajouter l’élément de projet SharePoint à un projet, ou lorsqu’un développeur utilise le modèle de projet pour créer un nouveau projet qui contient l’élément de projet SharePoint. L’Assistant peut être utilisé pour collecter des informations de la part des développeurs et pour initialiser le nouvel élément de projet SharePoint.

 Pour obtenir des procédures pas à pas qui montrent comment créer des assistants pour les modèles d’élément et les modèles de projet, consultez [procédure pas à pas : création d’un élément de projet d’action personnalisé avec un modèle d’élément, partie 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md) et [procédure pas à pas : créer un élément de projet de colonne de site avec un modèle de projet, deuxième partie](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md).

## <a name="see-also"></a>Voir aussi

- [Définir des types d’éléments de projet SharePoint personnalisés](../sharepoint/defining-custom-sharepoint-project-item-types.md)
- [Procédure pas à pas : création d’un élément de projet d’action personnalisé avec un modèle d’élément, partie 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)
- [Procédure pas à pas : création d’un élément de projet d’action personnalisé avec un modèle d’élément, partie 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)
- [Procédure pas à pas : création d’un élément de projet colonne de site avec un modèle de projet, partie 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)
- [Procédure pas à pas : création d’un élément de projet colonne de site avec un modèle de projet, partie 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)
- [Créer des modèles de projet et d’élément](../ide/creating-project-and-item-templates.md)
