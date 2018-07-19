---
title: Création d’élément modèles et les modèles de projet pour les éléments de projet SharePoint | Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 0d2d7d14b1e87a584da9f789c5092373db5519d5
ms.sourcegitcommit: e6b13898cfbd89449f786c2e8f3e3e7377afcf25
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/22/2018
ms.locfileid: "36327139"
---
# <a name="create-item-templates-and-project-templates-for-sharepoint-project-items"></a>Créer des modèles d’élément et les modèles de projet pour les éléments de projet SharePoint
  Lorsque vous définissez un type d’élément de projet SharePoint personnalisé, vous pouvez l’associer avec un modèle d’élément ou un modèle de projet. Cette association permet d’autres développeurs d’utiliser l’élément de projet dans Visual Studio. Vous pouvez également créer un Assistant pour le modèle.

 Par exemple, Visual Studio n’inclut pas de modèle de projet ou modèle d’élément pour l’ajout d’un champ à un site SharePoint. Vous pouvez définir un type d’élément de projet SharePoint qui représente un champ et puis construire un modèle d’élément autres développeurs peuvent utiliser pour ajouter l’élément de champ à un projet SharePoint. Ou bien, vous pouvez construire un modèle de projet afin que les développeurs peuvent créer un nouveau projet SharePoint qui possède l’élément de champ. Dans les deux cas, vous pouvez également fournir un Assistant qui s’affiche lorsque les développeurs utilisent votre modèle. Cet Assistant peut collecter des informations des développeurs pour configurer le nouvel élément ou un projet.

 Modèles d’élément et les modèles de projet sont *.zip* fichiers qui contiennent des fichiers qui sont utilisés par Visual Studio pour créer un élément de projet ou le projet. Pour plus d’informations sur les principes fondamentaux de modèles d’élément et les modèles de projet, consultez [créer des modèles de projet et d’élément](../ide/creating-project-and-item-templates.md).

## <a name="create-item-templates"></a>Créer des modèles d’élément
 Lorsque vous créez un modèle d’élément pour un élément de projet SharePoint, il existe certains fichiers sont toujours requis et les fichiers facultatifs qui peuvent être utilisées par certains types d’éléments de projet. Pour une procédure pas à pas qui montre comment définir un type d’élément de projet SharePoint et créer un modèle d’élément pour elle, consultez [procédure pas à pas : créer un élément de projet d’action personnalisé avec un modèle d’élément, partie 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md).

 Le tableau suivant répertorie les fichiers requis pour créer un modèle d’élément pour un élément de projet SharePoint.

|Fichier obligatoire|Description|
|-------------------|-----------------|
|Un *.spdata* fichier|Ce fichier XML spécifie le contenu et le comportement par défaut de l’élément de projet. Ce fichier doit être inclus dans le modèle d’élément. Pour plus d’informations sur le contenu de *.spdata* de fichiers, consultez [référence de schéma élément de projet SharePoint](../sharepoint/sharepoint-project-item-schema-reference.md).|
|Un *.vstemplate* fichier.|Ce fichier fournit à Visual Studio avec les informations requises pour afficher le modèle dans le **ajouter un nouvel élément** boîte de dialogue et créer un élément de projet à partir du modèle. Ce fichier doit être inclus dans le modèle d’élément. Pour plus d’informations, consultez [fichiers métadonnées de modèle Visual Studio](http://msdn.microsoft.com/en-us/129d59b5-7f9c-4daf-9832-eaedb3c4c961).|
|Un assembly d’extension Visual Studio qui implémente le <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> interface.|Cet assembly définit le comportement de l’exécution de l’élément de projet. Cet assembly doit être inclus dans le package VSIX avec le modèle d’élément. Pour plus d’informations, consultez [définissent les types d’éléments de projet SharePoint personnalisés](../sharepoint/defining-custom-sharepoint-project-item-types.md) et [déployer des extensions pour les outils SharePoint dans Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).|

 Le tableau suivant répertorie certains des fichiers courants facultatifs qui peuvent être inclus dans le modèle d’élément. Certains types d’éléments de projet peuvent nécessiter d’autres fichiers non répertoriées ici.

|Fichier facultatif|Description|
|-------------------|-----------------|
|*Elements.Xml*|Un *élément de fonctionnalité* fichier. Ce fichier définit l’interface utilisateur et le comportement de la personnalisation créée par l’élément de projet. Chaque type de personnalisation, telles que les instances de listes, les types de contenu ou des actions personnalisées, a un schéma différent qui définit le contenu de ce fichier. Pour plus d’informations, consultez [bloc de construction : fonctionnalités](http://go.microsoft.com/fwlink/?LinkId=169183) et [schémas](http://go.microsoft.com/fwlink/?LinkId=169192).|
|*Schema.Xml*|Le fichier de schéma pour les définitions de liste. Pour plus d’informations, consultez [bloc de construction : listes et bibliothèques de documents](http://go.microsoft.com/fwlink/?LinkId=177792) et [Schema.xml](http://go.microsoft.com/fwlink/?LinkId=177793).|
|*.WebPart*|Un *définition WebPart* fichier. Ce fichier contient les paramètres de propriété pour un composant WebPart. Pour plus d’informations, consultez [bloc de construction : composants WebPart](http://go.microsoft.com/fwlink/?LinkId=177791).|
|*.ascx*|Un fichier de contrôle utilisateur ASP.NET. Ce fichier définit l’interface utilisateur d’un composant Visual Web Part.|
|*.aspx*|Un fichier de page ASP.NET. Ce fichier contient le balisage XML qui définit une page d’application.|
|*.cs* ou *.vb* fichiers|Ces fichiers de code définissent le comportement des personnalisations de SharePoint qui ont un modèle de programmation qui est accessible à partir de Visual c# ou Visual Basic code, par exemple les pages d’application, les composants WebPart et les workflows.|
## <a name="create-project-templates"></a>Créer des modèles de projet
 Lorsque vous créez un modèle de projet SharePoint, il existe certains fichiers sont toujours les fichiers requis et facultatifs qui peuvent être utilisées par certains types de projets. En règle générale, les projets SharePoint incluent au moins un élément de projet SharePoint. Toutefois, cela n’est pas nécessaire. Par exemple, vous pouvez définir un modèle de projet SharePoint qui est destiné à être utilisé que pour déployer des solutions SharePoint créées dans d’autres projets.

 Pour une procédure pas à pas qui montre comment définir un type d’élément de projet SharePoint et créer un modèle de projet pour qu’il, consultez [procédure pas à pas : créer un élément de projet de colonne de site avec un modèle de projet, partie 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md).

 Le tableau suivant répertorie les fichiers qui doivent être inclus dans un modèle de projet SharePoint.

|Fichier obligatoire|Description|
|-------------------|-----------------|
|Un *.vstemplate* fichier|Ce fichier fournit à Visual Studio avec les informations requises pour afficher le modèle dans le **nouveau projet** boîte de dialogue et créer un projet à partir du modèle. Pour plus d’informations, consultez [fichiers métadonnées de modèle Visual Studio](http://msdn.microsoft.com/en-us/129d59b5-7f9c-4daf-9832-eaedb3c4c961).|
|Un *.csproj* ou *.vbproj* fichier|Il s’agit du fichier projet. Il définit le contenu et les paramètres de configuration du projet.|
|*Package*|Ce fichier définit le package de déploiement pour le projet. Lorsque vous utilisez le Concepteur de packages pour personnaliser le package de solution pour votre projet, Visual Studio stocke les données sur le package de solution dans ce fichier.<br /><br /> Lorsque vous créez un modèle de projet SharePoint personnalisé, nous vous recommandons d’inclure uniquement le contenu obligatoire minimum dans le *package* fichier, et que vous configurez le package de solution en utilisant les API dans le <xref:Microsoft.VisualStudio.SharePoint.Packages> espace de noms dans une extension qui est associée au modèle de projet. Dans ce cas, votre modèle de projet est protégé contre les futures modifications de la structure de la *package* fichier. Pour obtenir un exemple qui montre comment créer un *package* contenu du fichier avec uniquement la condition minimale requise, consultez [procédure pas à pas : créer un élément de projet de colonne de site avec un modèle de projet, partie 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md).<br /><br /> Si vous souhaitez modifier le *package* fichier directement, vous pouvez vérifier le contenu en utilisant le schéma à *% Program Files (x86)%\Microsoft Visual Studio 11.0\Xml\Schemas\PackageModelSchema.xsd* .|
|*Package.Template.xml*|Ce fichier fournit la base pour le fichier de manifeste de solution (*manifest.xml*) pour le package de solution SharePoint (*.wsp*) qui est généré à partir du projet. Vous pouvez ajouter du contenu à ce fichier si vous souhaitez spécifier un comportement qui n’est pas destiné à être modifié par les utilisateurs de votre type de projet. Pour plus d’informations, consultez [bloc de construction : Solutions](http://go.microsoft.com/fwlink/?LinkId=169186) et [schéma de la Solution](http://go.microsoft.com/fwlink/?LinkId=177794).<br /><br /> Lorsque vous générez un package de solution à partir du projet, Visual Studio fusionne le contenu de la *package* et *Package.Template.xml* fichier manifeste de fichiers dans la solution. Pour plus d’informations sur la création de packages de solution, consultez [Comment : créer un Package de Solution SharePoint à l’aide de tâches MSBuild](../sharepoint/how-to-create-a-sharepoint-solution-package-by-using-msbuild-tasks.md).|

 Le tableau suivant répertorie les fichiers facultatifs qui peuvent être inclus dans le modèle de projet.

|Fichier facultatif|Description|
|-------------------|-----------------|
|éléments de projet SharePoint|Vous pouvez inclure un ou plusieurs fichiers .spdata qui définissent les types d’éléments de projet SharePoint. Chaque *.spdata* fichier doit avoir une correspondance <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> implémentation dans un assembly d’extension qui est inclus dans le package VSIX avec le modèle de projet. Pour plus d’informations, consultez [création de modèles d’élément](#creatingitemtemplates).<br /><br /> En règle générale, les projets SharePoint incluent au moins un élément de projet SharePoint. Toutefois, cela n’est pas nécessaire.|
|*\<featureName > .feature*|Ce fichier définit une fonctionnalité SharePoint qui permet de regrouper plusieurs éléments de projet pour le déploiement. Lorsque vous utilisez le Concepteur de fonctionnalités pour personnaliser une fonctionnalité dans votre projet, Visual Studio stocke les données relatives à la fonctionnalité dans ce fichier. Si vous souhaitez regrouper les éléments de projet dans différentes fonctionnalités, vous pouvez inclure plusieurs *.feature* fichiers.<br /><br /> Lorsque vous créez un modèle de projet SharePoint personnalisé, nous vous recommandons d’inclure uniquement le contenu obligatoire minimum dans chaque *.feature* fichier, et configurer les fonctionnalités à l’aide de l’API dans le <xref:Microsoft.VisualStudio.SharePoint.Features> espace de noms dans un extension est associée au modèle de projet. Dans ce cas, votre modèle de projet est protégé contre les futures modifications de la structure de la *.feature* fichier. Pour obtenir un exemple qui montre comment créer un *.feature* contenu du fichier avec uniquement la condition minimale requise, consultez [procédure pas à pas : créer un élément de projet de colonne de site avec un modèle de projet, partie 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md).<br /><br /> Si vous souhaitez modifier un *.feature* fichier directement, vous pouvez vérifier le contenu en utilisant le schéma à *% Program Files (x86)%\Microsoft Visual Studio 11.0\Xml\Schemas\FeatureModelSchema.xsd*.|
|*\<featureName >. Template.Xml*|Ce fichier fournit la base pour le fichier de manifeste de fonctionnalité (*Feature.xml*) pour chaque fonctionnalité qui est générée à partir du projet. Vous pouvez ajouter du contenu à ce fichier si vous souhaitez spécifier un comportement qui n’est pas destiné à être modifié par les utilisateurs de votre type de projet. Pour plus d’informations, consultez [bloc de construction : fonctionnalités](http://go.microsoft.com/fwlink/?LinkId=169183) et [Feature.xml](http://go.microsoft.com/fwlink/?LinkId=177795) fichiers.<br /><br /> Lorsque vous générez un package de solution à partir du projet, Visual Studio fusionne le contenu de chaque paire de  *\<featureName > .feature* fichier et  *\<featureName >. Template.XML* fichier manifeste de fichiers dans une fonctionnalité. Pour plus d’informations sur la création de packages de solution, consultez [Comment : créer un Package de Solution SharePoint à l’aide de tâches MSBuild](../sharepoint/how-to-create-a-sharepoint-solution-package-by-using-msbuild-tasks.md).|

## <a name="create-wizards-for-item-templates-and-project-templates"></a>Créer des Assistants pour les modèles d’élément et les modèles de projet
 Une fois que vous définissez un type d’élément de projet SharePoint et l’associez à un modèle d’élément ou un projet, vous pouvez également créer un Assistant. L’Assistant affiche lorsqu’un développeur utilise le modèle d’élément pour ajouter l’élément de projet SharePoint à un projet, ou lorsqu’un développeur utilise le modèle de projet pour créer un projet qui contient l’élément de projet SharePoint. L’Assistant peut être utilisé pour collecter des informations des développeurs et pour initialiser le nouvel élément de projet SharePoint.

 Pour les procédures pas à pas qui montrent comment créer des Assistants pour les modèles d’élément et les modèles de projet, consultez [procédure pas à pas : créer un élément de projet d’action personnalisé avec un modèle d’élément, partie 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md) et [procédure pas à pas : création d’un site élément de projet colonne avec un modèle de projet, partie 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md).

## <a name="see-also"></a>Voir aussi

- [Définir les types d’éléments de projet SharePoint personnalisés](../sharepoint/defining-custom-sharepoint-project-item-types.md)
- [Procédure pas à pas : Créer un élément de projet d’action personnalisé avec un modèle d’élément, partie 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)
- [Procédure pas à pas : Créer un élément de projet d’action personnalisé avec un modèle d’élément, partie 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)
- [Procédure pas à pas : Créer un élément de projet de colonne de site avec un modèle de projet, partie 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)
- [Procédure pas à pas : Créer un élément de projet de colonne de site avec un modèle de projet, partie 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)
- [Créer des modèles de projet et d’élément](../ide/creating-project-and-item-templates.md)
