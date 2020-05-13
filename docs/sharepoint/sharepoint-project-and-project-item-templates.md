---
title: Modèles de projets et d’éléments de projet SharePoint (fr) Microsoft Docs
ms.date: 02/22/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.SPE.FirstWizardPage
- VS.SharePointTools.SPE.ListInstance
- VS.SharePointTools.SPE.ListDefinition
- VS.SharePointTools.SPE.ListDefFromContentType
- VS.SharePointTools.SPE.ContentType
- SPE.Wizard
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, project and project item templates
- SharePoint development in Visual Studio, templates
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 2878bd2092e000cf63c2b4fcb531a502a470203e
ms.sourcegitcommit: ade07bd1cf69b8b494d171ae648cfdd54f7800d3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/21/2020
ms.locfileid: "81649224"
---
# <a name="sharepoint-project-and-project-item-templates"></a>Modèles de projet et d’élément de projet SharePoint
  Les sections suivantes décrivent les modèles de projets et d’éléments de projet SharePoint disponibles et la façon dont ils sont utilisés.

## <a name="project-and-project-item-templates-overview"></a>Aperçu des modèles de projet et d’élément de projet
 Lorsque vous créez un nouveau projet SharePoint dans Visual Studio, un projet SharePoint est ajouté à la solution ainsi que tous les éléments du projet requis par ce type de projet. Par exemple, si vous créez un projet Silverlight Web Part, Visual Studio crée une solution qui contient un élément de projet Visual Web Part et un élément de projet d’application Silverlight ainsi que tous les fichiers requis par ces éléments de projet. Les modèles d’éléments de projet sont utilisés pour ajouter des éléments de projet à un projet SharePoint existant, comme l’ajout d’un récepteur d’événement, d’une colonne de site ou d’une liste.

 Pour plus d’informations sur les fondamentaux de SharePoint, voir [SharePoint Foundation Building Blocks](/previous-versions/office/developer/sharepoint-2010/ee534971(v=office.14)). Les utilisateurs avancés peuvent créer des modèles de projets et d’éléments de projet personnalisés. Pour plus d’informations, consultez [le système de projet Extend the SharePoint](../sharepoint/extending-the-sharepoint-project-system.md).

## <a name="project-templates"></a>Modèles de projet
 Voici une liste des modèles de projet SharePoint. Pour voir les modèles de projet SharePoint dans Visual Studio, dans la boîte de dialogue **du nouveau projet,** étendre le nœud **SharePoint** sous **Visual C ou** Visual **Basic**, puis choisissez **2010**.

### <a name="sharepoint-2010-project"></a>Projet SharePoint 2010
 Le contenu d’un *projet SharePoint 2010* est inclus dans chaque modèle de projet SharePoint. Un projet SharePoint 2010 contient :

- Un dossier de projet.

- Une page de propriétés de projet.

- Un dossier **De références** répertoriant toutes les références d’assemblage du projet.

- Un dossier **Caractéristiques** qui contient un fichier de configuration *.feature,* utilisé pour déployer des fonctionnalités sur le serveur SharePoint.

- Un dossier **de paquet** qui contient un fichier *Package.package,* utilisé pour déployer la solution sur SharePoint.

- Un fichier key.snk (clé de nom fort) qui est utilisé pour signer l’assemblage avec un nom fort, pour une sécurité accrue.

### <a name="sharepoint-2010-silverlight-web-part"></a>SharePoint 2010 Silverlight web part
 Les projets *SharePoint 2010 Silverlight Web Part* vous permettent de créer des pièces Web pour SharePoint qui affichent des applications Silverlight. Lorsque vous créez ce projet, vous pouvez spécifier si vous y ajoutez une nouvelle application Silverlight ou si vous y faites référence. Pour plus d’informations, voir [Créer des parties Web pour SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md) et [Walkthrough: Créer une partie Web Silverlight qui affiche OData pour SharePoint](../sharepoint/walkthrough-creating-a-silverlight-web-part-that-displays-odata-for-sharepoint.md).

### <a name="sharepoint-2010-visual-web-part"></a>Pièce Web visuelle SharePoint 2010
 Un projet *SharePoint 2010 Visual Web Part* comprend un fichier de définition *Elements.xml,* un élément **De partie Web** et un élément de contrôle **utilisateur.** Vous pouvez concevoir l’apparence de la partie web visuelle en faisant glisser ou copier les commandes de la boîte à outils Visual Studio à la surface du contrôle de l’utilisateur. Pour plus d’informations, voir [Comment : Créer une partie Web SharePoint en utilisant un concepteur](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md) et un bloc de construction : Parties [Web](/previous-versions/office/developer/sharepoint-2010/ee535520(v=office.14)).

### <a name="import-sharepoint-2010-solution-package"></a>Forfait de solutions Import SharePoint 2010
 Les projets *import SharePoint 2010 Solution Package* vous permettent d’importer tout ou partie d’un site SharePoint 2010 existant, exporté vers une solution SharePoint (*.wsp*) fichier, dans Visual Studio. Une fois importé dans Visual Studio, vous pouvez personnaliser ses articles et les redéployer. Pour plus d’informations, voir [Articles d’importation à partir d’un site SharePoint existant](../sharepoint/importing-items-from-an-existing-sharepoint-site.md).

### <a name="import-reusable-sharepoint-2010-workflow"></a>Flux de travail SharePoint 2010 réutilisables à l’importation
 Les projets *De flux de travail Import Reusable SharePoint 2010* vous permettent d’importer un flux de travail réutilisable et déclaratif créé dans SharePoint Designer 2010 dans Visual Studio. Le flux de travail est exporté à partir du site SharePoint comme un fichier *.wsp.* Une fois importé dans Visual Studio, vous pouvez le personnaliser, y ajouter du code, puis le déployer sur un site SharePoint. Pour plus d’informations, voir [Procédure Pas à pas : Importer un flux de travail réutilisable de SharePoint Designer dans Visual Studio](../sharepoint/walkthrough-import-a-sharepoint-designer-reusable-workflow-into-visual-studio.md).

## <a name="project-item-templates"></a>Modèles d’éléments de projet
 Voici une liste des modèles d’éléments du projet SharePoint. Les modèles d’éléments de projet ajoutent des fichiers à la solution SharePoint pour prendre en charge les fonctionnalités SharePoint telles que les colonnes de sites, les listes et les types de contenu. Par exemple, l’ajout d’une colonne de site à votre solution ajoute un projet de colonne de site qui contient un fichier de définition *Elements.xml.* L’ajout d’une partie Web visuelle ajoute un projet de partie web visuelle à votre solution qui contient un fichier *Elements.xml,* un élément de contrôle utilisateur et un élément de partie Web visuelle.

 Pour voir les modèles d’élément du projet SharePoint, dans **Solution Explorer**, ouvrez le menu raccourci pour un projet SharePoint, puis choisissez **Ajouter**, **Nouvel article**. Élargissez le nœud **SharePoint** sous **Visual C ou** Visual **Basic,** puis choisissez **2010**.

### <a name="application-page-farm-solution-only"></a>Page d’application (solution agricole seulement)
 Un élément **de page d’application (Solution agricole uniquement)** vous permet de concevoir une [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] page Web pour un site SharePoint. Les pages d’applications ne peuvent être utilisées que dans les solutions agricoles. Vous pouvez ajouter cet élément de projet uniquement aux solutions agricoles. Pour plus d’informations, voir [Comment : Créer une page d’application](../sharepoint/how-to-create-an-application-page.md) et [l’application _layouts type de page](/previous-versions/office/aa979604(v=office.14)).

### <a name="business-data-connectivity-model-farm-solution-only"></a>Modèle de connectivité des données d’entreprise (solution agricole seulement)
 Un élément **de modèle de connectivité de données d’entreprise (solution agricole uniquement)** vous permet d’intégrer les données d’entreprise dans SharePoint. Les données commerciales peuvent provenir d’applications serveur back-end, telles que [!INCLUDE[ssNoVersion](../sharepoint/includes/ssnoversion-md.md)], Siebel, et Service Advertising Protocol (SAP). Les modèles de connectivité des données d’entreprise ne peuvent être utilisés que dans les solutions agricoles. Vous pouvez ajouter cet élément de projet uniquement aux solutions agricoles. Pour plus d’informations, voir [Comment : Créer un modèle BDC](../sharepoint/how-to-create-a-bdc-model.md), comment : utiliser un fichier de ressources pour [spécifier les noms, les propriétés et les autorisations localisés,](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)et [ce qui est nouveau : Services de connectivité d’entreprise.](/previous-versions/office/developer/sharepoint-2010/ee534979(v=office.14))

### <a name="content-type"></a>Type de contenu
 *Les* éléments de type de contenu vous permettent de créer des types de contenu personnalisés basés sur un type de contenu existant (base) tel qu’un document, une annonce ou une tâche. Un type de contenu personnalisé fournit les mêmes attributs et champs que le type de contenu de base ainsi que toutes les colonnes de site (champs) que vous définissez. Par exemple, vous pouvez créer un type de contenu Contact personnalisé basé sur le type de contenu de base Contact qui vient dans SharePoint. Vous pouvez personnaliser le type de contenu en modifiant les colonnes de site existantes ou en ajoutant plus de colonnes de site à celles déjà incluses dans le type de contenu de base.

> [!NOTE]
> En raison d’une limitation SharePoint, vous ne pouvez pas créer un type de contenu de solution agricole basé sur un type de contenu de solution bac à sable.

 Pour plus d’informations, voir [Procédure Pas à pas : Créez une colonne de site, un type de contenu et une liste pour SharePoint](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md) et Building [Block: Content Type](/previous-versions/office/developer/sharepoint-2010/ee535063(v=office.14)).

### <a name="empty-element"></a>élément vide ;
 *Les éléments vides* sont le plus souvent utilisés pour définir les éléments du projet SharePoint qui n’ont pas de modèle de projet ou d’élément de projet dans Visual Studio. Lorsque vous ajoutez un élément vide à votre projet, un nœud nommé EmptyElement[x] (où [x] est un nombre\) unique est créé. EmptyElement[x] contient un seul fichier qui s’appelle *Elements.xml.* Utilisez [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] des instructions pour définir les éléments souhaités dans *Elements.xml*.

### <a name="event-receiver"></a>Récepteur de l’événement
 *Les récepteurs d’événements* gèrent les événements pour les éléments du site SharePoint, comme lorsqu’un élément est ajouté à une liste, lorsqu’un élément Web est supprimé ou lorsqu’un flux de travail a commencé. Le modèle d’élément de projet de récepteur d’événement vous permet de gérer

- Lister les événements

- Liste des événements d’objets

- Liste des événements par courriel

- événements Web

- Liste des événements de flux de travail

  L’élément du projet de récepteur d’événement crée un dossier **de récepteur d’événement** avec un fichier de classe unique qui contient des gestionnaires d’événements pour tous les événements que vous avez spécifiés lorsque vous avez créé le projet dans le **SharePoint Customization Wizard**. La classe de récepteur d’événements peut gérer les événements qui se produisent sur le site SharePoint lorsque des éléments tels que des fichiers, des champs, des éléments, des listes, des pièces jointes, des pièces Web et des flux de travail sont ajoutés, mis à jour, supprimés ou supprimés. Pour plus d’informations, voir [Comment : Créer un récepteur d’événement](../sharepoint/how-to-create-an-event-receiver.md) et un bloc de construction : Gestion [d’événements.](/previous-versions/office/developer/sharepoint-2010/ee535057(v=office.14))

### <a name="list"></a>List
 Une liste est une instance d’une définition réutilisable de liste SharePoint de base, comme un calendrier ou une liste de tâches. Après avoir ajouté une liste à votre solution, le concepteur de liste vous permet d’ajouter des colonnes de site à la liste et de créer des colonnes de liste personnalisées. Cela comprend les colonnes de site provenant de types de contenu. Vous pouvez spécifier la *vue* de la liste, qui détermine les colonnes qui apparaîtront dans la liste. Pour plus d’informations, voir [Procédure Pas à pas : Créez une colonne de site, un type de contenu et une liste pour SharePoint](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md) et Building [Block: Lists and Document Libraries](/previous-versions/office/developer/sharepoint-2010/ee534985(v=office.14)).

### <a name="module"></a>Module
 *Les modules* (à [!include[vbprvb](../sharepoint/includes/vbprvb-md.md)] ne pas confondre avec les modules) contiennent tous les fichiers que vous souhaitez déployer sur le serveur SharePoint, tels que des images ou des notes. L’élément du projet de module contient un nœud **module.** Le nœud du module contient deux modèles d’élément de projet : un fichier de définition XML, qui agit comme un manifeste pour le module, et un fichier *sample.txt,* un fichier de placeholder. Pour plus d’informations, voir [Utilisez des modules pour inclure des fichiers dans la solution](../sharepoint/using-modules-to-include-files-in-the-solution.md) et les [modules](/previous-versions/office/developer/sharepoint-2010/ms453137(v=office.14)).

### <a name="sequential-workflow-farm-solution-only"></a>Flux de travail séquentiel (solution agricole seulement)
 Un *flux de travail séquentiel* est une série d’étapes logiques d’affaires, exécutées dans l’ordre, jusqu’à ce que la dernière étape soit terminée. Les flux de travail séquentiels sont utilisés pour gérer les processus qui impliquent des éléments SharePoint tels que des listes et des documents. Vous pouvez créer des flux de travail (globaux) au niveau du site ou des flux de travail (locaux) au niveau de la liste, et vous pouvez choisir si un flux de travail démarre automatiquement ou manuellement. Cet élément de projet ne peut être utilisé que dans les solutions agricoles. Vous pouvez ajouter cet élément de projet uniquement aux solutions agricoles. Pour plus d’informations, voir [Create SharePoint solutions de flux de travail](../sharepoint/creating-sharepoint-workflow-solutions.md), [Workflows dans SharePoint Server 2010](/previous-versions/office/developer/sharepoint-2010/ms549489(v=office.14)), et [What’s New: Workflow Improvements](/previous-versions/office/developer/sharepoint-2010/ee537015(v=office.14)).

### <a name="silverlight-web-part"></a>Pièce Web Silverlight
 Les éléments du projet *de partie Web Silverlight* vous permettent de créer des pièces Web pour SharePoint qui affichent des applications Silverlight. Lorsque vous ajoutez cet élément de projet à votre solution, vous pouvez choisir d’ajouter une nouvelle application Silverlight ou de référencer une application existante plus tard. Pour plus d’informations, voir [Créer des parties Web pour SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md) et [Walkthrough: Créer une partie Web Silverlight qui affiche OData pour SharePoint](../sharepoint/walkthrough-creating-a-silverlight-web-part-that-displays-odata-for-sharepoint.md).

### <a name="site-column"></a>Colonne du site
 Une *colonne de site*, également connu sous le nom de *champ*, est l’un des éléments les plus basiques que vous pouvez ajouter à un projet SharePoint. Une colonne de site représente un type de données, comme un numéro de téléphone, un commentaire texte ou le nom de la ville d’un contact dans une liste de contacts. Pour plus d’informations, consultez [les colonnes de sites, les types de contenu et les listes de SharePoint](../sharepoint/creating-site-columns-content-types-and-lists-for-sharepoint.md) et [De Columns](/previous-versions/office/developer/sharepoint-2010/ms196085(v=office.14)).

### <a name="site-definition-farm-solution-only"></a>Définition du site (solution agricole seulement)
 *Les* éléments du projet de définition du site contiennent un dossier de définition du site qui comprend les fichiers suivants :

- Une page .aspx par défaut, utilisée comme page Web par défaut pour le site.

- Un fichier *onet.xml* qui définit les composants du site.

- Un fichier webtemp xml qui spécifie les configurations de définition du site qui apparaissent dans la section **Template Selection** de la page Nouveau **site SharePoint.**

  Après avoir ajouté une définition de site, vous ajoutez du code et des fichiers pour introduire des fonctionnalités. Cet élément de projet ne peut être utilisé que dans les solutions agricoles. Vous pouvez ajouter cet élément de projet uniquement aux solutions agricoles. Pour plus d’informations, consultez [les définitions de site Create pour SharePoint](../sharepoint/creating-site-definitions-for-sharepoint.md) et [Les définitions et configurations de sites](/previous-versions/office/developer/sharepoint-2010/aa978512(v=office.14)).

### <a name="state-machine-workflow-farm-solution-only"></a>Flux de travail de machine d’état (solution de ferme seulement)
 Un *flux de travail de machine d’état* est un ensemble d’états de logique d’affaires, de transitions, et d’actions. Les étapes d’un flux de travail de machine d’état ne sont pas exécutées dans l’ordre ; au lieu de cela, ils sont déclenchés par des actions et des États. Comme un flux de travail séquentiel, les flux de travail des machines d’état sont associés à des éléments SharePoint tels que des listes et des documents. Une fois de plus, vous pouvez créer des flux de travail (globaux) au niveau du site ou des flux de travail (locaux) au niveau de la liste. Vous pouvez également choisir si un flux de travail démarre automatiquement ou manuellement. Cet élément de projet ne peut être utilisé que dans les solutions agricoles. Vous pouvez ajouter cet élément de projet uniquement aux solutions agricoles. Pour plus d’informations, voir [Create SharePoint solutions de flux de travail](../sharepoint/creating-sharepoint-workflow-solutions.md), [Workflows dans SharePoint Server 2010](/previous-versions/office/developer/sharepoint-2010/ms549489(v=office.14)), et [What’s New: Workflow Improvements](/previous-versions/office/developer/sharepoint-2010/ee537015(v=office.14)).

### <a name="user-control-farm-solution-only"></a>Contrôle des utilisateurs (solution agricole seulement)
 Un *contrôle utilisateur* est un contrôle personnalisé et réutilisable auquel vous pouvez ajouter d’autres contrôles ASP.NET et des contrôles SharePoint. Le contrôle utilisateur peut être ajouté aux pages d’application et aux parties Web qui s’exécutent dans SharePoint. Cet élément de projet ne peut être utilisé que dans les solutions agricoles. Vous pouvez ajouter cet élément de projet uniquement aux solutions agricoles. Pour plus d’informations, voir [Créer des contrôles réutilisables pour les parties Web ou les pages d’application](creating-reusable-controls-for-web-parts-or-application-pages.md).

### <a name="visual-web-part"></a>Partie web visuelle
 Un élément visuel du projet *de partie Web* comprend un fichier de définition *Elements.xml,* un élément **de partie Web** et un élément de **contrôle utilisateur.** Vous pouvez concevoir l’apparence de la partie web visuelle en faisant glisser ou copier les commandes de la boîte à outils Visual Studio à la surface du contrôle de l’utilisateur. Pour plus d’informations, voir [Comment : Créer une partie Web SharePoint en utilisant un concepteur](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md) et un bloc de construction : Parties [Web](/previous-versions/office/developer/sharepoint-2010/ee535520(v=office.14)).

### <a name="web-part"></a>Composant WebPart
 Une *partie web* est un contrôle côté serveur qui s’exécute à l’intérieur d’un type spécial de page appelée page Web Part. Ce sont les éléments constitutifs des pages qui apparaissent sur un site SharePoint. L’élément de partie Web fournit des fichiers qui vous permettent de concevoir une pièce Web pour un site SharePoint. Pour plus d’informations, voir [Comment : Créer une partie Web SharePoint](../sharepoint/how-to-create-a-sharepoint-web-part.md) et construire un bloc : Parties [Web](/previous-versions/office/developer/sharepoint-2010/ee535520(v=office.14)).

## <a name="see-also"></a>Voir aussi
- [Développer des solutions SharePoint](../sharepoint/developing-sharepoint-solutions.md)
- [produits et technologies SharePoint](/previous-versions/office/developer/sharepoint-2010/dd776256(v=office.12))
