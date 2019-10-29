---
title: Modèles de projet et d’élément de projet SharePoint | Microsoft Docs
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
ms.openlocfilehash: 825e985820ac7a4d72bf321133491e312adb0a0e
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/28/2019
ms.locfileid: "72981948"
---
# <a name="sharepoint-project-and-project-item-templates"></a>Modèles de projet et d’élément de projet SharePoint
  Les sections suivantes décrivent les modèles de projet et d’élément de projet SharePoint disponibles, ainsi que leur utilisation.

## <a name="project-and-project-item-templates-overview"></a>Vue d’ensemble des modèles de projet et d’élément de projet
 Lorsque vous créez un projet SharePoint dans Visual Studio, un projet SharePoint est ajouté à la solution avec tous les éléments de projet requis par ce type de projet. Par exemple, si vous créez un projet de composant WebPart Silverlight, Visual Studio crée une solution qui contient un élément de projet de composant Visual Web part et un élément de projet d’application Silverlight, ainsi que tous les fichiers requis par ces éléments de projet. Les modèles d’élément de projet sont utilisés pour ajouter des éléments de projet à un projet SharePoint existant, tels que l’ajout d’un récepteur d’événements, d’une colonne de site ou d’une liste.

 Pour plus d’informations sur les notions de base de SharePoint, consultez [blocs de construction SharePoint Foundation](/previous-versions/office/developer/sharepoint-2010/ee534971(v=office.14)). Les utilisateurs avancés peuvent créer des modèles de projet et d’élément de projet personnalisés. Pour plus d’informations, consultez [étendre le système de projet SharePoint](../sharepoint/extending-the-sharepoint-project-system.md).

## <a name="project-templates"></a>Modèles de projet
 Voici une liste des modèles de projet SharePoint. Pour afficher les modèles de projet SharePoint dans Visual Studio, dans la boîte de dialogue **nouveau projet** , développez le nœud **SharePoint** sous  **C# Visual** ou **Visual Basic**, puis choisissez **2010**.

### <a name="sharepoint-2010-project"></a>Projet SharePoint 2010
 Le contenu d’un *projet sharepoint 2010* est inclus dans chaque modèle de projet SharePoint. Un projet SharePoint 2010 contient les éléments suivants :

- Fichier projet.

- Page de propriétés d’un projet.

- Un dossier **références** répertoriant toutes les références d’assembly dans le projet.

- Dossier de **fonctionnalités** qui contient un fichier de configuration *. Feature* , utilisé pour déployer des fonctionnalités sur SharePoint Server.

- Dossier de **package** qui contient un fichier *Package. Package* , utilisé pour déployer la solution dans SharePoint.

- Fichier Key. snk (clé de nom fort) utilisé pour signer l’assembly avec un nom fort, afin de renforcer la sécurité.

### <a name="sharepoint-2010-silverlight-web-part"></a>Composant WebPart Silverlight SharePoint 2010
 Les projets *WebPart Silverlight SharePoint 2010* vous permettent de créer des composants WebPart pour SharePoint qui affichent des applications Silverlight. Lorsque vous créez ce projet, vous pouvez spécifier s’il faut y ajouter une nouvelle application Silverlight ou en faire référence. Pour plus d’informations, consultez [créer des composants WebPart pour SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md) et [procédure pas à pas : créer un composant WebPart Silverlight qui affiche OData pour SharePoint](../sharepoint/walkthrough-creating-a-silverlight-web-part-that-displays-odata-for-sharepoint.md).

### <a name="sharepoint-2010-visual-web-part"></a>Composant Visual Web part de SharePoint 2010
 Un projet de *composant Visual Web Part SharePoint 2010* comprend un fichier de définition *Elements. xml* , un élément **WebPart** et un élément de **contrôle utilisateur** . Vous pouvez concevoir l’apparence du composant Visual Web part en faisant glisser ou en copiant des contrôles de la boîte à outils Visual Studio vers la surface du contrôle utilisateur. Pour plus d’informations, consultez [Comment : créer un composant WebPart SharePoint à l’aide d’un concepteur](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md) et d’un [bloc de construction : composants WebPart](/previous-versions/office/developer/sharepoint-2010/ee535520(v=office.14)).

### <a name="import-sharepoint-2010-solution-package"></a>Importer le package de solution SharePoint 2010
 Importer des projets de *package de solution sharepoint 2010* vous permet d’importer la totalité ou une partie d’un site SharePoint 2010 existant, exporté vers un fichier de solution SharePoint ( *. wsp*), dans Visual Studio. Une fois importés dans Visual Studio, vous pouvez personnaliser ses éléments et les redéployer. Pour plus d’informations, consultez [importer des éléments à partir d’un site SharePoint existant](../sharepoint/importing-items-from-an-existing-sharepoint-site.md).

### <a name="import-reusable-sharepoint-2010-workflow"></a>Importer un flux de travail SharePoint 2010 réutilisable
 Importer des projets de *flux de travail SharePoint 2010 réutilisables* vous permet d’importer un flux de travail réutilisable déclaratif créé dans sharepoint Designer 2010 dans Visual Studio. Le flux de travail est exporté à partir du site SharePoint sous la forme d’un fichier *. wsp* . Une fois importé dans Visual Studio, vous pouvez le personnaliser, y ajouter du code, puis le déployer sur un site SharePoint. Pour plus d’informations, consultez [procédure pas à pas : importation d’un flux de travail réutilisable SharePoint Designer dans Visual Studio](../sharepoint/walkthrough-import-a-sharepoint-designer-reusable-workflow-into-visual-studio.md).

## <a name="project-item-templates"></a>Modèles d’élément de projet
 Voici une liste des modèles d’élément de projet SharePoint. Les modèles d’élément de projet ajoutent des fichiers à la solution SharePoint pour prendre en charge les fonctionnalités SharePoint telles que les colonnes de site, les listes et les types de contenu. Par exemple, l’ajout d’une colonne de site à votre solution ajoute un projet de colonne de site qui contient un fichier de définition *Elements. xml* . L’ajout d’un composant Visual Web part ajoute un projet de composant Visual Web part à votre solution qui contient un fichier *Elements. xml* , un élément de contrôle utilisateur et un élément Visual Web part.

 Pour afficher les modèles d’élément de projet SharePoint, dans **Explorateur de solutions**, ouvrez le menu contextuel d’un projet SharePoint, puis choisissez **Ajouter**, **nouvel élément**. Développez le nœud **SharePoint** sous **Visual C#**  ou **Visual Basic**, puis choisissez **2010**.

### <a name="application-page-farm-solution-only"></a>Page application (solution de batterie uniquement)
 Un élément de **page d’application (solution de batterie uniquement)** vous permet de concevoir une page Web [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] pour un site SharePoint. Les pages d’applications ne peuvent être utilisées que dans les solutions de batterie. Vous pouvez ajouter cet élément de projet uniquement aux solutions de batterie de serveurs. Pour plus d’informations, consultez Guide pratique [pour créer une page d’application et un](../sharepoint/how-to-create-an-application-page.md) [type de page _ layouts d’application](/previous-versions/office/aa979604(v=office.14)).

### <a name="business-data-connectivity-model-farm-solution-only"></a>Modèle de connectivité de données métiers (solution de batterie uniquement)
 Un élément de **modèle de connectivité de données métiers (solution de batterie uniquement)** vous permet d’intégrer des données métier dans SharePoint. Les données métier peuvent provenir d’applications serveur principales, telles que [!INCLUDE[ssNoVersion](../sharepoint/includes/ssnoversion-md.md)], Siebel et SAP (Service Advertising Protocol). Les modèles de connectivité de données métiers ne peuvent être utilisés que dans les solutions de batterie. Vous pouvez ajouter cet élément de projet uniquement aux solutions de batterie de serveurs. Pour plus d’informations, consultez [procédure : créer un modèle BDC](../sharepoint/how-to-create-a-bdc-model.md), [procédure : utiliser un fichier de ressources pour spécifier des noms localisés, des propriétés et des autorisations](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md), et [Nouveautés : Business Connectivity Services](/previous-versions/office/developer/sharepoint-2010/ee534979(v=office.14)).

### <a name="content-type"></a>Type de contenu
 Les éléments de *type de contenu* vous permettent de créer des types de contenu personnalisés basés sur un type de contenu (de base) existant, tel qu’un document, une annonce ou une tâche. Un type de contenu personnalisé fournit les mêmes attributs et champs que le type de contenu de base, ainsi que les colonnes de site (champs) que vous définissez. Par exemple, vous pouvez créer un type de contenu contact personnalisé basé sur le type de contenu contact de base fourni dans SharePoint. Vous pouvez personnaliser le type de contenu en modifiant les colonnes de site existantes ou en ajoutant d’autres colonnes de site à celles déjà incluses dans le type de contenu de base.

> [!NOTE]
> En raison d’une limitation SharePoint, vous ne pouvez pas créer un type de contenu de solution de batterie de serveurs basé sur un type de contenu de solution bac à sable (sandbox).

 Pour plus d’informations, consultez [procédure pas à pas : création d’une colonne de site, type de contenu et liste pour SharePoint](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md) et [bloc de construction : type de contenu](/previous-versions/office/developer/sharepoint-2010/ee535063(v=office.14)).

### <a name="empty-element"></a>élément vide ;
 Les *éléments vides* sont le plus souvent utilisés pour définir des éléments de projet SharePoint qui n’ont pas de modèle de projet ou d’élément de projet dans Visual Studio. Lorsque vous ajoutez un élément vide à votre projet, un nœud nommé EmptyElement [x] (où [x] est un nombre unique\) est créé. EmptyElement [x] contient un seul fichier nommé *Elements. Xml.* Utilisez [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] instructions pour définir les éléments souhaités dans *Elements. xml*.

### <a name="event-receiver"></a>Récepteur d’événements
 Les *récepteurs d’événements* gèrent les événements des éléments du site SharePoint, par exemple lorsqu’un élément est ajouté à une liste, lorsqu’un élément Web est supprimé ou lorsqu’un flux de travail a démarré. Le modèle d’élément de projet de récepteur d’événements vous permet de gérer

- Répertorier les événements

- Événements d’élément de liste

- Répertorier les événements de courrier électronique

- événements Web

- Répertorier les événements de workflow

  L’élément de projet récepteur d’événements crée un dossier de **récepteur** d’événements avec un fichier de classe unique qui contient les gestionnaires d’événements pour tous les événements que vous avez spécifiés lors de la création du projet dans l' **Assistant Personnalisation de SharePoint**. La classe de récepteur d’événements peut gérer les événements qui se produisent sur le site SharePoint lorsque des éléments tels que des fichiers, des champs, des éléments, des listes, des pièces jointes, des composants WebPart et des flux de travail sont ajoutés, mis à jour, supprimés ou supprimés. Pour plus d’informations, consultez [Comment : créer un récepteur d’événements et un](../sharepoint/how-to-create-an-event-receiver.md) [bloc de construction : gestion des événements](/previous-versions/office/developer/sharepoint-2010/ee535057(v=office.14)).

### <a name="list"></a>List
 Une liste est une instance d’une définition de liste SharePoint de base réutilisable, telle qu’un calendrier ou une liste de tâches. Après avoir ajouté une liste à votre solution, le concepteur de listes vous permet d’ajouter des colonnes de site à la liste et de créer des colonnes de liste personnalisées. Cela comprend les colonnes de site des types de contenu. Vous pouvez spécifier la *vue* de la liste, qui détermine les colonnes qui s’affichent dans la liste. Pour plus d’informations, consultez [procédure pas à pas : création d’une colonne de site, type de contenu et liste pour SharePoint](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md) et [bloc de construction : listes et bibliothèques de documents](/previous-versions/office/developer/sharepoint-2010/ee534985(v=office.14)).

### <a name="module"></a>Module
 Les *modules* (à ne pas confondre avec les modules [!include[vbprvb](../sharepoint/includes/vbprvb-md.md)]) contiennent tous les fichiers que vous souhaitez déployer sur le serveur SharePoint, tels que des images ou des notes. L’élément de projet de module contient un nœud de **module** . Le nœud de module contient deux modèles d’élément de projet : un fichier de définition XML, qui agit comme un manifeste pour le module et un fichier *Sample. txt* , un fichier d’espace réservé. Pour plus d’informations, consultez [utiliser des modules pour inclure des fichiers dans la solution et les](../sharepoint/using-modules-to-include-files-in-the-solution.md) [modules](/previous-versions/office/developer/sharepoint-2010/ms453137(v=office.14)).

### <a name="sequential-workflow-farm-solution-only"></a>Workflow séquentiel (solution de batterie uniquement)
 Un *flux de travail séquentiel* est une série d’étapes de logique métier exécutées dans l’ordre, jusqu’à ce que la dernière étape soit terminée. Les workflows séquentiels permettent de gérer les processus qui impliquent des éléments SharePoint, tels que des listes et des documents. Vous pouvez créer des flux de travail au niveau du site (Global) ou des flux de travail au niveau de la liste (local). vous pouvez aussi choisir si un flux de travail démarre automatiquement ou manuellement. Cet élément de projet ne peut être utilisé que dans les solutions de batterie. Vous pouvez ajouter cet élément de projet uniquement aux solutions de batterie de serveurs. Pour plus d’informations, consultez [créer des solutions de flux de travail SharePoint](../sharepoint/creating-sharepoint-workflow-solutions.md), [flux de travail dans SharePoint Server 2010](/previous-versions/office/developer/sharepoint-2010/ms549489(v=office.14))et [Nouveautés : améliorations du flux](/previous-versions/office/developer/sharepoint-2010/ee537015(v=office.14))de travail.

### <a name="silverlight-web-part"></a>Composant WebPart Silverlight
 Les éléments de projet de *composant WebPart Silverlight* vous permettent de créer des composants WebPart pour SharePoint qui affichent des applications Silverlight. Lorsque vous ajoutez cet élément de projet à votre solution, vous pouvez choisir d’ajouter une nouvelle application Silverlight ou de faire référence à une application existante ultérieurement. Pour plus d’informations, consultez [créer des composants WebPart pour SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md) et [procédure pas à pas : créer un composant WebPart Silverlight qui affiche OData pour SharePoint](../sharepoint/walkthrough-creating-a-silverlight-web-part-that-displays-odata-for-sharepoint.md).

### <a name="site-column"></a>Colonne de site
 Une *colonne de site*, également appelée « *champ*», est l’un des éléments les plus basiques que vous pouvez ajouter à un projet SharePoint. Une colonne de site représente un type de données, tel qu’un numéro de téléphone, un commentaire de texte ou le nom de ville d’un contact dans une liste de contacts. Pour plus d’informations, consultez [créer des colonnes de site, des types de contenu et des listes pour SharePoint](../sharepoint/creating-site-columns-content-types-and-lists-for-sharepoint.md) et les [colonnes](/previous-versions/office/developer/sharepoint-2010/ms196085(v=office.14)).

### <a name="site-definition-farm-solution-only"></a>Définition de site (solution de batterie uniquement)
 Les éléments de projet de *définition de site* contiennent un dossier de définition de site qui comprend les fichiers suivants :

- Page default. aspx, utilisée comme page Web par défaut pour le site.

- Fichier *Onet. xml* qui définit les composants du site.

- Fichier XML WebTemp qui spécifie les configurations de définition de site qui s’affichent dans la section **sélection du modèle** de la page **nouveau site SharePoint** .

  Une fois que vous avez ajouté une définition de site, vous ajoutez du code et des fichiers pour introduire des fonctionnalités. Cet élément de projet ne peut être utilisé que dans les solutions de batterie. Vous pouvez ajouter cet élément de projet uniquement aux solutions de batterie de serveurs. Pour plus d’informations, consultez [créer des définitions de site pour SharePoint](../sharepoint/creating-site-definitions-for-sharepoint.md) et les [définitions de site et les configurations](/previous-versions/office/developer/sharepoint-2010/aa978512(v=office.14)).

### <a name="state-machine-workflow-farm-solution-only"></a>Workflow de l’ordinateur d’État (solution de batterie uniquement)
 Un *flux de travail d’ordinateur d’État* est un ensemble d’États, de transitions et d’actions de logique métier. Les étapes d’un workflow d’ordinateur d’État ne sont pas effectuées dans l’ordre. au lieu de cela, ils sont déclenchés par des actions et des États. À l’instar d’un workflow séquentiel, les flux de travail d’ordinateur d’État sont associés à des éléments SharePoint, tels que des listes et des documents. Une fois encore, vous pouvez créer des flux de travail au niveau du site (Global) ou des flux de travail au niveau de la liste (local). Vous pouvez également choisir si un flux de travail démarre automatiquement ou manuellement. Cet élément de projet ne peut être utilisé que dans les solutions de batterie. Vous pouvez ajouter cet élément de projet uniquement aux solutions de batterie de serveurs. Pour plus d’informations, consultez [créer des solutions de flux de travail SharePoint](../sharepoint/creating-sharepoint-workflow-solutions.md), [flux de travail dans SharePoint Server 2010](/previous-versions/office/developer/sharepoint-2010/ms549489(v=office.14))et [Nouveautés : améliorations du flux](/previous-versions/office/developer/sharepoint-2010/ee537015(v=office.14))de travail.

### <a name="user-control-farm-solution-only"></a>Contrôle utilisateur (solution de batterie uniquement)
 Un *contrôle utilisateur* est un contrôle personnalisé, réutilisable, auquel vous pouvez ajouter d’autres contrôles ASP.net et contrôles SharePoint. Le contrôle utilisateur peut être ajouté aux pages d’application et aux composants WebPart qui s’exécutent dans SharePoint. Cet élément de projet ne peut être utilisé que dans les solutions de batterie. Vous pouvez ajouter cet élément de projet uniquement aux solutions de batterie de serveurs. Pour plus d’informations, consultez [création de contrôles réutilisables pour des composants WebPart ou des pages d’application](/visualstudio/sharepoint/creating-reusable-controls-for-web-parts-or-application-pages&view=vs-2019).

### <a name="visual-web-part"></a>Composant Visual Web part
 Un élément de projet *Visual Web part* comprend un fichier de définition *Elements. xml* , un élément **WebPart** et un élément de **contrôle utilisateur** . Vous pouvez concevoir l’apparence du composant Visual Web part en faisant glisser ou en copiant des contrôles de la boîte à outils Visual Studio vers la surface du contrôle utilisateur. Pour plus d’informations, consultez [Comment : créer un composant WebPart SharePoint à l’aide d’un concepteur](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md) et d’un [bloc de construction : composants WebPart](/previous-versions/office/developer/sharepoint-2010/ee535520(v=office.14)).

### <a name="web-part"></a>Composant WebPart
 Un *composant WebPart* est un contrôle côté serveur qui s’exécute à l’intérieur d’un type de page spécial appelé page de composants WebPart. Il s’agit des blocs de construction des pages qui s’affichent sur un site SharePoint. L’élément WebPart fournit des fichiers qui vous permettent de concevoir un composant WebPart pour un site SharePoint. Pour plus d’informations, consultez [procédure : créer un composant WebPart SharePoint et un](../sharepoint/how-to-create-a-sharepoint-web-part.md) [bloc de construction : composants WebPart](/previous-versions/office/developer/sharepoint-2010/ee535520(v=office.14)).

## <a name="see-also"></a>Voir aussi
- [Développer des solutions SharePoint](../sharepoint/developing-sharepoint-solutions.md)
- [Produits et technologies SharePoint](/previous-versions/office/developer/sharepoint-2010/dd776256(v=office.12))
