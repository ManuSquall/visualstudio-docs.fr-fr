---
title: Empaquetage des informations de déploiement & dans les éléments de projet
description: Ajoutez des données d’empaquetage et de déploiement dans des éléments de projet SharePoint à l’aide des propriétés de fonctionnalité, des récepteurs de fonctionnalités, des références de sortie de projet et des entités de contrôle sécurisé.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.Project.SafeControlEntries
- VS.SharePointTools.Project.ProjectOutputReference
- VS.SharePointTools.Project.FeatureProperties
dev_langs:
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
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: f73d8727fb960cf519d368d928aa20cae38ae1a9
ms.sourcegitcommit: 02f14db142dce68d084dcb0a19ca41a16f5bccff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2020
ms.locfileid: "95970470"
---
# <a name="provide-packaging-and-deployment-information-in-project-items"></a>Fournir des informations d’empaquetage et de déploiement dans les éléments de projet
  Tous les éléments de projet SharePoint dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ont des propriétés que vous pouvez utiliser pour fournir des données supplémentaires lorsque le projet est déployé sur SharePoint. Ces propriétés sont les suivantes :

- Propriétés de fonctionnalité

- Récepteurs de fonctionnalités

- Références de sortie de projet

- Entrées de contrôle sécurisé

  Ces propriétés s’affichent dans la fenêtre **Propriétés** .

## <a name="feature-properties"></a>Propriétés de fonctionnalité
 Utilisez la propriété propriétés de la **fonctionnalité** pour spécifier les données utilisées par la fonctionnalité. Les données de propriétés de fonctionnalité sont un ensemble de valeurs (stockées sous forme de paires clé/valeur) qui est inclus avec une fonctionnalité lors de son déploiement sur SharePoint. Une fois la fonctionnalité déployée, vous pouvez accéder aux valeurs de propriété dans votre code.

 Lorsque vous ajoutez une valeur de propriété de fonctionnalité à un élément de projet, la valeur est ajoutée en tant qu’élément dans le manifeste de la fonctionnalité de l’élément. Dans un projet de modèle de connectivité de données métiers (BDC), par exemple, la propriété de fonctionnalité ModelFileName se présente comme suit :

```xml
<Property Key="ModelFileName" Value="BdcModel1\BdcModel1.bdcm" />
```

 Une fois que vous avez défini une valeur de propriété de fonctionnalité, elle est ajoutée en tant qu’élément FeatureProperty dans le fichier *. resdata* du projet. Pour plus d’informations sur l’accès aux propriétés dans SharePoint, consultez [SPFeaturePropertyCollection, classe](/previous-versions/office/sharepoint-server/ms461895(v=office.15)).

 Les valeurs de propriété de fonctionnalité identiques de tous les éléments de projet sont fusionnées dans le manifeste de fonctionnalité. Toutefois, si deux éléments de projet différents spécifient la même clé de propriété de fonctionnalité avec des valeurs qui ne correspondent pas, une erreur de validation se produit.

 Pour ajouter des propriétés de fonctionnalité directement au fichier de fonctionnalité (*. Feature*), appelez la [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] méthode du modèle d’objet SharePoint <xref:Microsoft.VisualStudio.SharePoint.Features.IPropertyCollection.Add%2A> . Si vous utilisez cette méthode, sachez que la même règle sur l’ajout de valeurs de propriété de fonctionnalité identiques dans les propriétés de fonctionnalité s’applique également aux propriétés ajoutées directement au fichier de fonctionnalité.

## <a name="feature-receiver"></a>Récepteur de fonctionnalité
 Les récepteurs de fonctionnalités sont du code qui s’exécute lorsque certains événements se produisent dans la fonctionnalité conteneur d’un élément de projet. Par exemple, vous pouvez définir des récepteurs de fonctionnalités qui s’exécutent lors de l’installation, de l’activation ou de la mise à niveau de la fonctionnalité. Une façon d’ajouter un récepteur de fonctionnalité consiste à l’ajouter directement à une fonctionnalité, comme décrit dans [procédure pas à pas : ajouter des récepteurs d’événements de fonctionnalité](../sharepoint/walkthrough-add-feature-event-receivers.md). Une autre méthode consiste à référencer un assembly et un nom de classe de récepteur de fonctionnalité dans la propriété de **récepteur de fonctionnalité** .

### <a name="direct-method"></a>Méthode directe
 Lorsque vous ajoutez directement un récepteur de fonctionnalité à une fonctionnalité, un fichier de code est placé sous le nœud **Feature** dans Explorateur de solutions. Lorsque vous générez votre solution SharePoint, le code est compilé dans un assembly et est déployé sur SharePoint. Par défaut, l' **assembly du récepteur** des propriétés de la fonctionnalité et la **classe Receiver** référencent le nom et l’assembly de la classe.

### <a name="reference-method"></a>Reference (méthode)
 Une autre façon d’ajouter un récepteur de fonctionnalité consiste à utiliser la propriété de **récepteur de fonctionnalité** d’un élément de projet pour référencer un assembly de récepteur de fonctionnalité. La valeur de la propriété du récepteur de fonctionnalité a deux sous-propriétés : **assembly** et nom de la **classe**. L’assembly doit utiliser son nom « fort » qualifié complet et le nom de la classe doit être le nom de type complet. Pour plus d’informations, consultez [Assemblys avec nom fort](/previous-versions/dotnet/netframework-4.0/wd40t7ad(v=vs.100)). Une fois la solution déployée sur SharePoint, la fonctionnalité utilise le récepteur de fonctionnalités référencé pour gérer les événements de fonctionnalité.

 Au moment de la génération de la solution, les valeurs de propriété du récepteur de la fonctionnalité dans la fonctionnalité et ses projets fusionnent pour définir les attributs ReceiverAssembly et ReceiverClass de l’élément de fonctionnalité dans le manifeste de fonctionnalité du fichier de solution SharePoint (*. wsp*). Par conséquent, si les valeurs de la propriété assembly et nom de classe d’un élément de projet et d’une fonctionnalité sont toutes deux spécifiées, les valeurs des propriétés des éléments de projet et des fonctionnalités doivent correspondre. Si les valeurs ne correspondent pas, vous recevrez une erreur de validation. Si vous souhaitez qu’un élément de projet fasse référence à un assembly de récepteur de fonctionnalités autre que celui utilisé par sa fonctionnalité, déplacez-le vers une autre fonctionnalité.

 Si vous référencez un assembly de récepteur de fonctionnalité qui ne se trouve pas déjà sur le serveur, vous devez également inclure le fichier d’assembly dans le package ; [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ne l’ajoute pas pour vous. Lorsque vous déployez la fonctionnalité, le fichier d’assembly est copié dans le [!INCLUDE[TLA#tla_gac](../sharepoint/includes/tlasharptla-gac-md.md)] dossier du système ou dans le dossier bin du répertoire physique SharePoint. Pour plus d’informations, consultez Comment [: ajouter et supprimer des assemblys supplémentaires](../sharepoint/how-to-add-and-remove-additional-assemblies.md).

 Pour plus d’informations sur les récepteurs de fonctionnalités, consultez [composant récepteur d’événements de fonctionnalité](/previous-versions/office/developer/sharepoint-2007/bb862634(v=office.12)) et [événements de fonctionnalité](/previous-versions/office/developer/sharepoint-2010/ms469501(v=office.14)).

## <a name="project-output-references"></a>Références de sortie de projet
 La propriété références de sortie du projet spécifie une dépendance, telle qu’un assembly, que votre élément de projet doit exécuter. Par exemple, supposons que votre solution possède un projet BDC et un projet de classe. Si le projet BDC a une dépendance sur l’assembly qui est généré par le projet de classe, vous pouvez référencer l’assembly dans la propriété références de sortie du projet du projet BDC. Lorsque le projet BDC est empaqueté, l’assembly dépendant est inclus dans le package.

 Les références de sortie de projet sont généralement des assemblys, mais dans certains cas (tels que les projets Silverlight) peuvent être d’autres types de fichiers.

 Pour plus d’informations, consultez [Comment : ajouter une référence de sortie de projet](../sharepoint/how-to-add-a-project-output-reference.md).

## <a name="safe-control-entries"></a>Entrées de contrôle sécurisé
 SharePoint fournit un mécanisme de sécurité, appelé entrées de contrôle sécurisé, pour limiter l’accès des utilisateurs non approuvés à certains contrôles. Par défaut, SharePoint permet aux utilisateurs non autorisés de télécharger et de créer des pages ASPX sur le serveur SharePoint. Pour empêcher ces utilisateurs d’ajouter du code non sécurisé aux pages ASPX, SharePoint limite leur accès aux *contrôles sécurisés*. Les contrôles sécurisés sont des contrôles ASPX et des composants WebPart désignés comme sécurisés et pouvant être utilisés par n’importe quel utilisateur sur votre site. Pour plus d’informations, consultez [Step 4 : Add Your WebPart to the Safe Controls List](/previous-versions/office/developer/sharepoint-2007/ms581321(v=office.12)).

 Chaque élément de projet SharePoint dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] a une propriété appelée **entrées de contrôle sécurisé** avec deux sous-propriétés booléennes : **Safe** et **Safe par rapport à un script**. La propriété Safe spécifie si les utilisateurs non fiables peuvent accéder à un contrôle. La propriété protégé contre les scripts spécifie si les utilisateurs non fiables peuvent afficher et modifier les propriétés d’un contrôle.

 Les entrées de contrôle sécurisé sont référencées sur la base d’un assembly. Vous ajoutez des entrées de contrôle sécurisé à l’assembly d’un projet en les entrant dans la propriété **entrées de contrôle sécurisé** de l’élément de projet. Toutefois, vous pouvez également ajouter des entrées de contrôle sécurisé à l’assembly d’un projet via l’onglet **avancé** dans le **Concepteur de packages** lorsque vous ajoutez un assembly supplémentaire au package. Pour plus d’informations, consultez [Comment : marquer des contrôles en tant que contrôles sécurisés](../sharepoint/how-to-mark-controls-as-safe-controls.md) ou [inscrire un assembly WebPart en tant que contrôle sécurisé](/previous-versions/office/developer/sharepoint2003/dd587360(v=office.11)).

### <a name="xml-entries-for-safe-controls"></a>Entrées XML pour les contrôles sécurisés
 Quand vous ajoutez une entrée de contrôle sécurisé à un élément de projet ou à l’assembly du projet, une référence est écrite dans le manifeste du package au format suivant :

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
- [Empaqueter et déployer des solutions SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
- [Utiliser des modules pour inclure des fichiers dans la solution](../sharepoint/using-modules-to-include-files-in-the-solution.md)
- [Étendre le déploiement et l’empaquetage SharePoint](../sharepoint/extending-sharepoint-packaging-and-deployment.md)
