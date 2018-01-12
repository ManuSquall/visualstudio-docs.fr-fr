---
title: "En fournissant l’empaquetage et du déploiement dans les éléments de projet | Documents Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.SharePointTools.Project.SafeControlEntries
- VS.SharePointTools.Project.ProjectOutputReference
- VS.SharePointTools.Project.FeatureProperties
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, safe controls
- project output references [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, feature properties
- SharePoint development in Visual Studio, project output references
- SharePoint development in Visual Studio, advanced packaging tools
- feature properties [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, feature receiver
- feature receiver [SharePoint development in Visual Studio]
- safe controls [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: adc98932391e726e1704ebe88ec0a9120f7bb678
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/10/2018
---
# <a name="providing-packaging-and-deployment-information-in-project-items"></a>Fourniture d'informations de création de packages et de déploiement dans des éléments de projet
  Tous les éléments de projet SharePoint dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ont des propriétés que vous pouvez utiliser pour fournir des données supplémentaires lorsque le projet est déployé sur SharePoint. Ces propriétés sont les suivantes :  
  
-   Propriétés de la fonctionnalité  
  
-   Récepteurs de fonctionnalité  
  
-   Références de sortie de projet  
  
-   Entrées de contrôle sécurisé  
  
 Ces propriétés s’affichent dans le **propriétés** fenêtre.  
  
## <a name="feature-properties"></a>Propriétés de la fonctionnalité  
 Utilisez le **propriétés de la fonctionnalité** propriété pour spécifier les données que la fonctionnalité utilise. Les données de propriétés de fonctionnalité sont un ensemble de valeurs (stockées en tant que paires clé/valeur) qui est inclus avec une fonctionnalité lors de son déploiement sur SharePoint. Une fois la fonctionnalité déployée, vous pouvez accéder aux valeurs de propriété dans votre code.  
  
 Lorsque vous ajoutez une valeur de propriété de fonctionnalité à un élément de projet, la valeur est ajoutée en tant qu’élément dans le manifeste de fonctionnalité de l’élément. Dans un projet de modèle de connectivité de données métiers (BDC), par exemple, la propriété de fonctionnalité ModelFileName apparaît en tant que :  
  
```  
<Property Key="ModelFileName" Value="BdcModel1\BdcModel1.bdcm" />   
```  
  
 Après avoir défini une valeur de propriété de fonctionnalité, il est ajouté en tant qu’élément FeatureProperty dans le fichier du projet .spdata. Pour plus d’informations sur l’accès aux propriétés dans SharePoint, consultez [SPFeaturePropertyCollection, classe](http://go.microsoft.com/fwlink/?LinkId=177391).  
  
 Valeurs de propriété de fonctionnalité identiques de tous les éléments de projet sont fusionnées dans le manifeste de fonctionnalité. Toutefois, si deux éléments de projet différents spécifient la même clé de propriété de fonctionnalité avec des valeurs non correspondantes, une erreur de validation se produit.  
  
 Pour ajouter des propriétés de la fonctionnalité directement dans le fichier de fonctionnalité (* .feature), appelez le [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] méthode du modèle objet SharePoint <xref:Microsoft.VisualStudio.SharePoint.Features.IPropertyCollection.Add%2A>. Si vous utilisez cette méthode, sachez que la même règle sur l’ajout de valeurs de propriété de fonctionnalité identiques dans les propriétés de la fonctionnalité s’applique également aux propriétés ajoutées directement au fichier de fonctionnalité.  
  
## <a name="feature-receiver"></a>Récepteur de fonctionnalité  
 Les récepteurs de fonctionnalité sont fonctionnalité qui contient le code qui s’exécute lorsque certains événements se produisent à un élément de projet. Par exemple, vous pouvez définir des récepteurs de fonctionnalité qui s’exécutent lorsque la fonctionnalité est installée, activée ou mis à niveau. Pour ajouter un récepteur de fonctionnalité consiste à ajouter directement à une fonctionnalité comme décrit dans [procédure pas à pas : ajouter des récepteurs d’événements fonctionnalité](../sharepoint/walkthrough-add-feature-event-receivers.md). Une autre méthode consiste à faire référence à un nom de classe de récepteur de fonctionnalité et d’un assembly dans le **récepteur de fonctionnalité** propriété.  
  
### <a name="direct-method"></a>Méthode directe  
 Lorsque vous ajoutez directement un récepteur de fonctionnalité à une fonctionnalité, un fichier de code est placé sous le **fonctionnalité** nœud dans l’Explorateur de solutions. Lorsque vous générez votre solution SharePoint, le code se compile dans un assembly et déploie sur SharePoint. Par défaut, les propriétés de fonctionnalité **Assembly du récepteur** et **classe de récepteur** référencer le nom de la classe et l’assembly.  
  
### <a name="reference-method"></a>Reference (méthode)  
 Une autre consiste à ajouter un récepteur de fonctionnalité à l’aide de la **récepteur de fonctionnalité** propriété d’un élément de projet pour référencer un assembly de récepteur de fonctionnalité. La valeur de propriété de récepteur de fonctionnalité a deux sous-propriétés : **Assembly** et **nom de la classe**. L’assembly doit utiliser ses complet, le nom « fort » et le nom de classe doivent être le nom de type complet. Pour plus d’informations, consultez [Assemblys avec nom fort](http://go.microsoft.com/fwlink/?LinkID=169573). Après avoir déployé la solution vers SharePoint, la fonctionnalité utilise le récepteur de fonctionnalité référencé pour gérer les événements de fonctionnalité.  
  
 Au moment de build de solution, les valeurs de propriété de récepteur de fonctionnalité dans la fonctionnalité et ses projets fusionnent pour définir les attributs ReceiverAssembly et ReceiverClass de l’élément de fonctionnalité dans le manifeste de fonctionnalité du fichier de solution (.wsp) SharePoint. Par conséquent, si les valeurs de propriété Assembly et le nom de la classe d’élément de projet et une fonction sont tous deux spécifiés, les valeurs de propriété de fonctionnalité et d’élément de projet doivent correspondre. Si les valeurs ne correspondent pas, vous recevrez une erreur de validation. Si vous souhaitez un élément de projet pour faire référence à un assembly de récepteur de fonctionnalité différente de celle sa fonctionnalité, déplacez-le vers une autre fonctionnalité.  
  
 Si vous référencez un assembly de récepteur de fonctionnalité qui n’est pas déjà sur le serveur, vous devez également inclure le fichier d’assembly dans le package ; [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ne l’ajoutez pas pour vous. Lorsque vous déployez la fonctionnalité, le fichier d’assembly est copié pour que le système [!INCLUDE[TLA#tla_gac](../sharepoint/includes/tlasharptla-gac-md.md)] ou le dossier Bin dans le répertoire physique SharePoint. Pour plus d’informations, consultez Comment : [Comment : ajouter et supprimer des assemblys supplémentaires](../sharepoint/how-to-add-and-remove-additional-assemblies.md).  
  
 Pour plus d’informations sur les récepteurs, consultez [récepteur d’événements de fonctionnalité](http://go.microsoft.com/fwlink/?LinkID=169574) et [événements de fonctionnalité](http://go.microsoft.com/fwlink/?LinkID=169575).  
  
## <a name="project-output-references"></a>Références de sortie de projet  
 La propriété de références de sortie de projet spécifie une dépendance, telle qu’un assembly, que votre élément de projet doit exécuter. Par exemple, supposons que votre solution contient un projet BDC et un projet de classe. Si le projet BDC a une dépendance sur l’assembly qui est générée par le projet de classe, vous pouvez référencer l’assembly dans la propriété de références de sortie de projet du projet BDC. Lorsque le projet BDC est empaqueté, l’assembly dépendant est inclus dans le package.  
  
 Références de sortie de projet sont généralement des assemblys, mais dans certains cas (par exemple, les projets Silverlight) peuvent être des autres types de fichiers.  
  
 Pour plus d’informations, consultez [Comment : ajouter une référence de sortie de projet](../sharepoint/how-to-add-a-project-output-reference.md).  
  
## <a name="safe-control-entries"></a>Entrées de contrôle sécurisé  
 SharePoint fournit un mécanisme de sécurité, appelé entrées de contrôle sécurisé, pour limiter l’accès des utilisateurs non autorisés à certains contrôles. Par conception, SharePoint permet à des utilisateurs non autorisés à télécharger et à créer des pages ASPX sur le serveur SharePoint. Pour empêcher ces utilisateurs d’ajouter du code unsafe aux pages ASPX, SharePoint limite leur accès aux *contrôles sécurisés*. Contrôles sécurisés sont des contrôles ASPX et composants WebPart désignés comme sécurisés et qui peut être utilisé par tous les utilisateurs de votre site. Pour plus d’informations, consultez [étape 4 : ajouter votre composant WebPart à la liste des contrôles](http://go.microsoft.com/fwlink/?LinkID=171014).  
  
 Chaque élément de projet SharePoint dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] a une propriété appelée **entrées de contrôle sécurisé** qui a deux sous-propriétés booléennes : **Safe** et **protégé contre les scripts**. La propriété sécurisé Spécifie si les utilisateurs non fiables peuvent accéder à un contrôle. La propriété protégé contre les scripts spécifie si les utilisateurs non autorisés peuvent visualiser et modifier les propriétés d’un contrôle.  
  
 Entrées de contrôle sécurisé sont référencées dans une base de l’assembly. Vous ajoutez des entrées de contrôle sécurisé à l’assembly d’un projet en les entrant dans l’élément de projet **entrées de contrôle sécurisé** propriété. Toutefois, vous pouvez également ajouter des entrées de contrôle sécurisé à l’assembly d’un projet via la **avancé** onglet dans le **Concepteur de packages** lorsque vous ajoutez un assembly supplémentaire au package. Pour plus d’informations, consultez [Comment : marquer des contrôles comme des contrôles sécurisés](../sharepoint/how-to-mark-controls-as-safe-controls.md) ou [l’inscription d’un Assembly de composant WebPart en tant que](http://go.microsoft.com/fwlink/?LinkID=171013).  
  
### <a name="xml-entries-for-safe-controls"></a>Entrées XML pour les contrôles sécurisés  
 Lorsque vous ajoutez une entrée de contrôle sécurisé à un élément de projet ou à l’assembly du projet, une référence est écrite dans le manifeste du package au format suivant :  
  
```xml  
<Assemblies>  
    <Assembly Location="<assembly name>.dll"     
      DeploymentTarget="<'GlobalAssemblyCache' or 'WebApplication'">>  
        <SafeControls>  
            <SafeControl Assembly="<assembly name>.dll" Namespace=  
              "<SharePoint project name>" Safe="<true/false>"     
                TypeName="<control name>"   
                SafeAgainstScript="<true/false>" />  
        </SafeControls>  
    </Assembly>  
</Assemblies>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Empaquetage et déploiement de Solutions SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)   
 [Utilisation de Modules pour inclure des fichiers dans la Solution](../sharepoint/using-modules-to-include-files-in-the-solution.md)   
 [Extension de la création de packages et du déploiement SharePoint](../sharepoint/extending-sharepoint-packaging-and-deployment.md)  
  