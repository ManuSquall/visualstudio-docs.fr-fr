---
title: ProjectItem, élément | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ProjectItem element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 44fc1b918960f0268d916ccfa560f118cea47144
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85536875"
---
# <a name="projectitem-element"></a>ProjectItem (élément)
  Représente un élément de projet SharePoint. Cet élément est l’élément racine requis du fichier *. les données* .

## <a name="syntax"></a>Syntaxe

```xml
<ProjectItem DefaultFile = "File that opens in the editor when you open the project item"
    FeatureReceiverClass = "Class that implements a feature receiver for the project item"
    FeatureReceiverAssembly = "Assembly that defines a feature receiver for the project item"
    SupportedTrustLevels = "Trust levels that the project item supports"
    SupportedDeploymentScopes = "Deployment scopes that the project item supports"
    Type="Identifier for the project item">
  <Files>...</Files>
  <ProjectItemFolder>...</ProjectItemFolder>
  <SafeControls>...</SafeControls>
  <FeatureProperties>...</FeatureProperties>
  <ExtensionData>...</ExtensionData>
</ProjectItem>
```

## <a name="attributes-and-elements"></a>Attributs et éléments
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.

### <a name="attributes"></a>Attributs

|Attribut|Description|
|---------------|-----------------|
|**DefaultFile**|Attribut **XS : String** facultatif.<br /><br /> Chemin d’accès relatif, y compris le nom de fichier, du fichier qui s’ouvre dans l’éditeur Visual Studio lorsque vous ouvrez l’élément de projet SharePoint dans **Explorateur de solutions**. Le chemin d’accès est relatif à partir du dossier qui contient le fichier *. resdonnées* .|
|**FeatureReceiverClass**|Attribut **XS : String** facultatif.<br /><br /> Nom qualifié complet d’une classe de récepteur de fonctionnalité pour cet élément de projet SharePoint. Pour plus d’informations sur les récepteurs de fonctionnalités, consultez [fournir des informations sur l’empaquetage et le déploiement dans les éléments de projet](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).|
|**FeatureReceiverAssembly**|Attribut **XS : String** facultatif.<br /><br /> Spécifie le nom qualifié complet d’un assembly qui définit un récepteur de fonctionnalité pour cet élément de projet SharePoint. Pour plus d’informations sur les récepteurs de fonctionnalités, consultez [fournir des informations sur l’empaquetage et le déploiement dans les éléments de projet](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md). Pour plus d’informations sur les noms d’assembly qualifiés complets, consultez [noms d’assemblys](/dotnet/framework/app-domains/assembly-names).|
|**SupportedTrustLevels**|Attribut **XS : String** facultatif.<br /><br /> Spécifie les niveaux de confiance que cet élément de projet SharePoint prend en charge. Cette valeur peut être l’une des chaînes suivantes : Sandboxed, FullTrust ou All. La valeur All spécifie All Sandboxed et FullTrust.<br /><br /> Dans un type d’élément de projet SharePoint personnalisé, la valeur de cet attribut correspond à la valeur que vous affectez à la <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition.SupportedTrustLevels%2A> propriété dans votre implémentation de la <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> méthode. Si vous spécifiez une valeur différente pour cet attribut, Visual Studio remplace la valeur afin qu’elle spécifie le même niveau de confiance que celui que vous spécifiez dans la <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition.SupportedTrustLevels%2A> propriété.|
|**SupportedDeploymentScopes**|Attribut **XS : String** facultatif.<br /><br /> Spécifie les portées de déploiement que cet élément de projet SharePoint prend en charge. Cette valeur est une chaîne délimitée par des virgules qui se compose d’une ou plusieurs des chaînes suivantes : batterie de serveurs, site, Web, application Web ou package. Par exemple : `Web, Site`<br /><br /> Dans un type d’élément de projet SharePoint personnalisé, la valeur de cet attribut correspond à la valeur que vous affectez à la <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition.SupportedDeploymentScopes%2A> propriété dans votre implémentation de la <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> méthode. Si vous spécifiez une valeur différente pour cet attribut, Visual Studio remplace la valeur afin qu’elle spécifie le même niveau de confiance que celui que vous spécifiez dans la <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition.SupportedDeploymentScopes%2A> propriété.|
|**Type**|Attribut **XS : String** requis.<br /><br /> Identificateur de l’élément de projet SharePoint. Dans un type d’élément de projet SharePoint personnalisé, l’identificateur est la chaîne que vous transmettez au <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute> . Pour plus d’informations, consultez [Comment : définir un type d’élément de projet SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md).<br /><br /> Pour obtenir la liste des identificateurs des éléments de projet SharePoint intégrés inclus dans Visual Studio, consultez étendre les [éléments de projet SharePoint](../sharepoint/extending-sharepoint-project-items.md).|

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|[ExtensionData](../sharepoint/extensiondata-element.md)|Élément facultatif.<br /><br /> Représente une collection d’éléments de données personnalisés associés à l’élément de projet SharePoint.<br /><br /> Vous ne pouvez inclure qu’un seul élément **ExtensionData** .|
|[FeatureProperties](../sharepoint/featureproperties-element.md)|Élément facultatif.<br /><br /> Représente une collection de valeurs de propriétés qui sont incluses avec une fonctionnalité lorsqu’elle est déployée sur SharePoint.<br /><br /> Vous ne pouvez inclure qu’un seul élément **FeatureProperties** .|
|[Fichiers](../sharepoint/files-element.md)|Élément **FileCollectionType** facultatif.<br /><br /> Spécifie les fichiers à déployer avec l’élément de projet SharePoint, tels que les fichiers d’élément de fonctionnalité et la sortie des projets non SharePoint dépendants.<br /><br /> Incluez un **fichier** ou un élément **ProjectItemFolder,** , mais pas les deux.|
|[ProjectItemFolder,](../sharepoint/projectitemfolder-element.md)|Élément **ProjectItemFolderType** facultatif.<br /><br /> Représente un dossier mappé.<br /><br /> Incluez un **fichier** ou un élément **ProjectItemFolder,** , mais pas les deux.|
|[SafeControls](../sharepoint/safecontrols-element.md)|Élément facultatif.<br /><br /> Représente une collection de contrôles ASPX et composants WebPart désignés comme sécurisés pour n’importe quel utilisateur à accéder à n’importe quelle page ASPX sur le site SharePoint.<br /><br /> Vous ne pouvez inclure qu’un seul élément **SafeControls** .|

### <a name="parent-elements"></a>Éléments parents
 Aucun.

## <a name="element-information"></a>Informations sur les éléments

|Propriété|Valeur|
|-|-|
|**Espace de noms**|http : \/ \/ schemas.Microsoft.com/VisualStudio/<br>2010/SharePointTools/SharePointProjectItemModel|
|**Nom du schéma**|Schéma d’élément de projet SharePoint|
|**Fichier de validation**|ProjectItemModelSchema. xsd|
|**Peut être vide**|Non|

## <a name="see-also"></a>Voir aussi
[Schéma d’élément de projet SharePoint rseference](../sharepoint/sharepoint-project-item-schema-reference.md)
