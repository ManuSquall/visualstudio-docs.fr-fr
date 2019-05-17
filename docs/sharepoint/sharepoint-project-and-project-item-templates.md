---
title: Modèles d’élément de projet SharePoint et Project | Microsoft Docs
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
ms.openlocfilehash: 245a6c994d87ecfa9c5ef877563b70100e5eef6f
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63438995"
---
# <a name="sharepoint-project-and-project-item-templates"></a>Projets et modèles d’élément de projet SharePoint
  Les sections suivantes décrivent le projet SharePoint et l’élément de projet modèles et comment elles sont utilisées.

## <a name="project-and-project-item-templates-overview"></a>Présentation des modèles de projet élément et projet
 Lorsque vous créez un nouveau projet SharePoint dans Visual Studio, un projet SharePoint est ajouté à la solution ainsi que tous les éléments de projet requis par ce type de projet. Par exemple, si vous créez un projet de composant WebPart Silverlight, Visual Studio crée une solution qui contient un élément de projet composant Visual Web Part et d’un élément de projet d’application Silverlight, ainsi que tous les fichiers requis par ces éléments de projet. Modèles d’élément de projet sont utilisés pour ajouter des éléments de projet à un projet SharePoint existant, telles que l’ajout d’un récepteur d’événements, la colonne de site ou la liste.

 Pour plus d’informations sur les notions fondamentales de SharePoint, consultez [blocs de construction de SharePoint Foundation](http://go.microsoft.com/fwlink/?LinkId=179404). Utilisateurs avancés peuvent créer un projet personnalisé et des modèles d’élément de projet. Pour plus d’informations, consultez [étendre le système de projet SharePoint](../sharepoint/extending-the-sharepoint-project-system.md).

## <a name="project-templates"></a>Modèles de projet
 Voici une liste de modèles de projet SharePoint. Pour afficher les modèles de projet SharePoint dans Visual Studio, dans le **nouveau projet** boîte de dialogue, développez le **SharePoint** nœud sous **Visual C#**  ou  **Visual Basic**, puis choisissez **2010**.

### <a name="sharepoint-2010-project"></a>Projet SharePoint 2010
 Le contenu d’un *projet SharePoint 2010* sont inclus dans chaque modèle de projet SharePoint. Un projet SharePoint 2010 contient :

- Un fichier projet.

- Une page de propriétés de projet.

- Un **références** dossier répertoriant toutes les références d’assembly dans le projet.

- Un **fonctionnalités** dossier qui contient un *.feature* fichier de configuration utilisé pour déployer des fonctionnalités sur le serveur SharePoint.

- Un **Package** dossier qui contient un *package* fichier utilisé pour déployer la solution sur SharePoint.

- Un fichier key.snk (clé de nom fort) qui est utilisé pour signer l’assembly avec un nom fort, pour une sécurité améliorée.

### <a name="sharepoint-2010-silverlight-web-part"></a>Composant WebPart Silverlight SharePoint 2010
 *Composant WebPart SharePoint 2010 Silverlight* projets vous permettent de créer WebPart pour SharePoint qui affichent des applications Silverlight. Lorsque vous créez ce projet, vous pouvez spécifier s’il faut ajouter une nouvelle application Silverlight ou référencer un existant. Pour plus d’informations, consultez [créer des composants WebPart pour SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md) et [procédure pas à pas : Créer un composant WebPart Silverlight qui affiche OData pour SharePoint](../sharepoint/walkthrough-creating-a-silverlight-web-part-that-displays-odata-for-sharepoint.md).

### <a name="sharepoint-2010-visual-web-part"></a>Visual WebPart pour SharePoint 2010
 Un *2010 Visual WebPart SharePoint* projet inclut un *Elements.xml* fichier de définition, un **WebPart** élément et un **contrôle utilisateur** élément . Vous pouvez concevoir l’apparence du composant visual WebPart en faisant glisser ou en copiant des contrôles à partir de la boîte à outils Visual Studio à la surface du contrôle utilisateur. Pour plus d'informations, voir [Procédure : Créer un composant WebPart SharePoint à l’aide d’un concepteur](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md) et [bloc de construction : Composants WebPart](http://go.microsoft.com/fwlink/?LinkId=179438).

### <a name="import-sharepoint-2010-solution-package"></a>Importer le package de solution SharePoint 2010
 *Importer le Package de Solution SharePoint 2010* projets vous permettent d’importer tout ou partie d’un site SharePoint 2010 existant, exporté vers une solution SharePoint (*.wsp*) fichier, dans Visual Studio. Une fois importé dans Visual Studio, vous pouvez personnaliser ses éléments et de les redéployer. Pour plus d’informations, consultez [importer des éléments à partir d’un site SharePoint existant](../sharepoint/importing-items-from-an-existing-sharepoint-site.md).

### <a name="import-reusable-sharepoint-2010-workflow"></a>Importer des flux de travail SharePoint 2010 réutilisable
 *Importer des flux de travail SharePoint 2010 réutilisable* projets vous permettent d’importer un flux de travail déclaratif, réutilisable créé dans SharePoint Designer 2010 dans Visual Studio. Le flux de travail est exporté à partir du site SharePoint en tant qu’un *.wsp* fichier. Une fois importé dans Visual Studio, vous pouvez personnaliser il, ajouter du code et puis le déployer sur un site SharePoint. Pour plus d’informations, consultez [Procédure pas à pas : Importer un flux de travail réutilisable de SharePoint Designer dans Visual Studio](../sharepoint/walkthrough-import-a-sharepoint-designer-reusable-workflow-into-visual-studio.md).

## <a name="project-item-templates"></a>Modèles d’élément de projet
 Voici une liste de modèles d’élément de projet de SharePoint. Modèles d’élément de projet ajoutent des fichiers à la solution SharePoint pour prendre en charge des fonctionnalités de SharePoint telles que les colonnes de site, les listes et les types de contenu. Par exemple, l’ajout d’une colonne de site à votre solution ajoute un projet colonne de site qui contient un *Elements.xml* fichier de définition. Ajout d’un composant visual web part ajoute un projet de composant WebPart visuel à votre solution qui contient un *Elements.xml* fichier, un élément de contrôle utilisateur et un élément visual WebPart.

 Pour afficher les modèles d’élément de projet SharePoint dans **l’Explorateur de solutions**, ouvrez le menu contextuel pour un projet SharePoint, puis choisissez **ajouter**, **un nouvel élément**. Développez le **SharePoint** nœud sous **Visual C#** ou **Visual Basic**, puis choisissez **2010**.

### <a name="application-page-farm-solution-only"></a>Page de l’application (solution de batterie uniquement)
 Un **Page Application (Solution de batterie uniquement)** élément vous permet de concevoir un [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] page web pour un site SharePoint. Pages d’applications peuvent être utilisés uniquement dans les solutions de batterie de serveurs. Vous pouvez ajouter cet élément de projet uniquement aux solutions de batterie de serveurs. Pour plus d'informations, voir [Procédure : Créer une page d’application](../sharepoint/how-to-create-an-application-page.md) et [dispositions d’Application Type de Page](http://go.microsoft.com/fwlink/?LinkId=179434).

### <a name="business-data-connectivity-model-farm-solution-only"></a>Modèle de connectivité de données métiers (solution de batterie uniquement)
 Un **modèle de connectivité de données métiers (Solution de batterie uniquement)** élément vous permet d’intégration de données d’entreprise dans SharePoint. Données d’entreprise peuvent provenir d’applications de serveur principal, tel que [!INCLUDE[ssNoVersion](../sharepoint/includes/ssnoversion-md.md)], Siebel et Service SAP (Advertising Protocol). Modèles de connectivité de données métiers peuvent être utilisés uniquement dans les solutions de batterie de serveurs. Vous pouvez ajouter cet élément de projet uniquement aux solutions de batterie de serveurs. Pour plus d'informations, voir [Procédure : Créer un modèle BDC](../sharepoint/how-to-create-a-bdc-model.md), [Comment : Utilisez un fichier de ressources pour spécifier des noms localisés, propriétés et autorisations](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md), et [quelles sont les nouveautés : Business Connectivity Services](/previous-versions/office/developer/sharepoint-2010/ee534979(v=office.14)).

### <a name="content-type"></a>Type de contenu
 *Type de contenu* éléments vous permettent de créer des types de contenu personnalisés basés sur un type de contenu (base) existant comme un document, une annonce ou une tâche. Un type de contenu personnalisé fournit les mêmes attributs et champs comme type de contenu de base avec des colonnes de site (champs) que vous définissez. Par exemple, vous pouvez créer un type de contenu personnalisé de Contact qui est basé sur le type de contenu Contact base qui est fourni dans SharePoint. Vous pouvez personnaliser le type de contenu en modifiant les colonnes de site existant ou en ajoutant plus de colonnes de site à celles déjà inclus dans le type de contenu de base.

> [!NOTE]
> Impossible de créer un type de contenu solution batterie de serveurs basé sur un type de contenu de solution bac à sable en raison d’une limitation de SharePoint.

 Pour plus d’informations, consultez [Procédure pas à pas : Créer une colonne de site, le type de contenu et la liste pour SharePoint](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md) et [bloc de construction : Type de contenu](http://go.microsoft.com/fwlink/?LinkId=179413).

### <a name="empty-element"></a>élément vide ;
 *Éléments vides* sont souvent utilisées pour définir les éléments de projet SharePoint qui ne disposent pas d’un projet ou un modèle d’élément de projet dans Visual Studio. Lorsque vous ajoutez un élément vide à votre projet, un nœud appelé EmptyElement [x](where [x] is a unique number\) is created. EmptyElement [x] contient un fichier unique qui est nommé *Elements.xml.* Utilisez [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] instructions pour définir les éléments voulus dans *Elements.xml*.

### <a name="event-receiver"></a>Récepteur d’événements
 *Récepteurs d’événements* gérer les événements pour les éléments dans le site SharePoint, tels que lorsqu’un élément est ajouté à une liste, lors de la suppression d’un élément web, ou quand un flux de travail est démarré. Le modèle d’élément événement récepteur projet vous permet de traiter

- Liste des événements

- Événements de l’élément de liste

- Liste des événements de messagerie

- événements Web

- Liste des événements de flux de travail

  L’élément de projet de récepteur d’événements crée un **récepteur d’événements** dossier avec un fichier de classe unique qui contient les gestionnaires d’événements pour tous les événements que vous avez spécifié lorsque vous avez créé le projet dans le **personnalisation de SharePoint Assistant**. La classe de récepteur d’événements peut gérer des événements qui se produisent sur le site SharePoint lorsque des éléments tels que des fichiers, des champs, éléments, listes, les pièces jointes, composants WebPart et des flux de travail sont ajoutés, mis à jour, supprimées ou supprimés. Pour plus d'informations, voir [Procédure : Créer un récepteur d’événements](../sharepoint/how-to-create-an-event-receiver.md) et [bloc de construction : Gestion des événements](http://go.microsoft.com/fwlink/?LinkId=179416).

### <a name="list"></a>Liste
 Une liste est une instance d’une base SharePoint liste Définition réutilisable, par exemple un calendrier ou une liste de tâches. Après avoir ajouté une liste à votre solution, le Concepteur de liste vous permet d’ajouter des colonnes de site à la liste et créer des colonnes de liste personnalisée. Cela inclut des colonnes de site à partir de types de contenu. Vous pouvez spécifier le *vue* pour obtenir la liste, qui détermine les colonnes qui apparaîtront dans la liste. Pour plus d’informations, consultez [Procédure pas à pas : Créer une colonne de site, le type de contenu et la liste pour SharePoint](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md) et [bloc de construction : Listes et bibliothèques de documents](http://go.microsoft.com/fwlink/?LinkId=179421).

### <a name="module"></a>Module
 *Modules* (à ne pas confondre avec [!include[vbprvb](../sharepoint/includes/vbprvb-md.md)] modules) contient tous les fichiers que vous souhaitez déployer sur le serveur SharePoint, tels que des images ou des notes de publication. L’élément de projet de module contient un **Module** nœud. Le nœud du module contient deux modèles d’élément de projet : un fichier de définition XML, qui agit comme un manifeste pour le module, et un *sample.txt* , un fichier d’espace réservé. Pour plus d’informations, consultez [utilisation des Modules pour inclure des fichiers dans la Solution](../sharepoint/using-modules-to-include-files-in-the-solution.md) et [Modules](http://go.microsoft.com/fwlink/?LinkId=179425).

### <a name="sequential-workflow-farm-solution-only"></a>Workflow séquentiel (solution de batterie uniquement)
 Un *workflow séquentiel* est une série d’étapes de logique métier, exécutées en séquence, jusqu'à ce que la dernière étape est terminée. Flux de travail séquentiels est utilisés pour gérer les processus qui impliquent des éléments SharePoint tels que des listes et des documents. Vous pouvez créer des flux de travail au niveau du site (global) ou au niveau de la liste de flux de travail (local), et vous pouvez indiquer si un flux de travail démarre automatiquement ou manuellement. Cet élément de projet peut être utilisé uniquement dans les solutions de batterie de serveurs. Vous pouvez ajouter cet élément de projet uniquement aux solutions de batterie de serveurs. Pour plus d’informations, consultez [solutions de flux de travail SharePoint créer](../sharepoint/creating-sharepoint-workflow-solutions.md), [des flux de travail dans SharePoint Server 2010](http://go.microsoft.com/fwlink/?LinkId=260555), et [quelles sont les nouveautés : Améliorations de flux de travail](/previous-versions/office/developer/sharepoint-2010/ee537015(v=office.14)).

### <a name="silverlight-web-part"></a>Composant WebPart Silverlight
 *Composant WebPart Silverlight* éléments de projet vous permettent de créer WebPart pour SharePoint qui affichent des applications Silverlight. Lorsque vous ajoutez cet élément de projet à votre solution, vous pouvez choisir s’il faut ajouter une nouvelle application Silverlight ou référencer un ultérieurement. Pour plus d’informations, consultez [créer des composants WebPart pour SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md) et [procédure pas à pas : Créer un composant WebPart Silverlight qui affiche OData pour SharePoint](../sharepoint/walkthrough-creating-a-silverlight-web-part-that-displays-odata-for-sharepoint.md).

### <a name="site-column"></a>Colonne de site
 Un *colonne de site*, également appelé un *champ*, est un des éléments plus critiques que vous pouvez ajouter à un projet SharePoint. Une colonne de site représente un type de données, comme un numéro de téléphone, un commentaire de texte ou le nom de ville d’un contact dans une liste de contacts. Pour plus d’informations, consultez [créer des colonnes de site, les types de contenu et listes pour SharePoint](../sharepoint/creating-site-columns-content-types-and-lists-for-sharepoint.md) et [colonnes](http://go.microsoft.com/fwlink/?LinkId=226840).

### <a name="site-definition-farm-solution-only"></a>Définition de site (solution de batterie uniquement)
 *Définition de site* éléments de projet contient un dossier de définition de site qui inclut les fichiers suivants :

- Une page .aspx par défaut, utilisée en tant que la page web par défaut pour le site.

- Un *onet.xml* fichier qui définit les composants du site.

- Un fichier xml webtemp qui spécifie les configurations de définition de site qui s’affichent dans le **sélection du modèle** section de la **nouveau SharePoint Site** page.

  Une fois que vous ajoutez une définition de site, vous ajoutez code et fichiers pour introduire une fonctionnalité. Cet élément de projet peut être utilisé uniquement dans les solutions de batterie de serveurs. Vous pouvez ajouter cet élément de projet uniquement aux solutions de batterie de serveurs. Pour plus d’informations, consultez [créer des définitions de site pour SharePoint](../sharepoint/creating-site-definitions-for-sharepoint.md) et [définitions de Site et les Configurations](http://go.microsoft.com/fwlink/?LinkId=260554).

### <a name="state-machine-workflow-farm-solution-only"></a>Flux de travail de machine à états (solution de batterie uniquement)
 Un *workflow d’ordinateur d’état* est un ensemble d’états de logique métier, de transitions et d’actions. Les étapes décrites dans un workflow d’ordinateur d’état ne sont pas effectuées dans la séquence ; au lieu de cela, elles sont déclenchées par des actions et des États. Comme un workflow séquentiel, les workflows machine à états sont associés à des éléments SharePoint tels que des listes et des documents. Une fois encore, vous pouvez créer des flux de travail au niveau du site (global) ou au niveau de la liste de flux de travail (local). Vous pouvez également choisir un flux de travail démarre automatiquement ou manuellement. Cet élément de projet peut être utilisé uniquement dans les solutions de batterie de serveurs. Vous pouvez ajouter cet élément de projet uniquement aux solutions de batterie de serveurs. Pour plus d’informations, consultez [solutions de flux de travail SharePoint créer](../sharepoint/creating-sharepoint-workflow-solutions.md), [des flux de travail dans SharePoint Server 2010](http://go.microsoft.com/fwlink/?LinkId=260555), et [quelles sont les nouveautés : Améliorations de flux de travail](/previous-versions/office/developer/sharepoint-2010/ee537015(v=office.14)).

### <a name="user-control-farm-solution-only"></a>Contrôle utilisateur (solution de batterie uniquement)
 Un *contrôle utilisateur* est un contrôle personnalisé et réutilisable à laquelle vous pouvez ajouter d’autres contrôles ASP.NET et les contrôles de SharePoint. Le contrôle utilisateur peut être ajouté à des pages d’application et les composants WebPart qui s’exécutent dans SharePoint. Cet élément de projet peut être utilisé uniquement dans les solutions de batterie de serveurs. Vous pouvez ajouter cet élément de projet uniquement aux solutions de batterie de serveurs. Pour plus d’informations, consultez [création de contrôles réutilisables pour les composants WebPart ou les Pages d’Application](http://go.microsoft.com/fwlink/?LinkId=226841).

### <a name="visual-web-part"></a>Composant Visual web part
 Un *composant visual web part* élément de projet inclut un *Elements.xml* fichier de définition, un **WebPart** élément et un **contrôle utilisateur** élément. Vous pouvez concevoir l’apparence du composant visual WebPart en faisant glisser ou en copiant des contrôles à partir de la boîte à outils Visual Studio à la surface du contrôle utilisateur. Pour plus d'informations, voir [Procédure : Créer un composant WebPart SharePoint à l’aide d’un concepteur](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md) et [bloc de construction : Composants WebPart](http://go.microsoft.com/fwlink/?LinkId=179438).

### <a name="web-part"></a>Composant WebPart
 Un *WebPart* est un contrôle côté serveur qui s’exécute au sein d’un type spécial de page appelé une Page WebPart. Ils sont les blocs de construction des pages qui s’affichent sur un site SharePoint. L’élément de la partie web fournit des fichiers qui vous permettent de concevoir un composant WebPart pour un site SharePoint. Pour plus d'informations, voir [Procédure : Créer un composant WebPart SharePoint](../sharepoint/how-to-create-a-sharepoint-web-part.md) et [bloc de construction : Composants WebPart](http://go.microsoft.com/fwlink/?LinkId=179438).

## <a name="see-also"></a>Voir aussi
- [Développer des solutions SharePoint](../sharepoint/developing-sharepoint-solutions.md)
- [Produits et technologies SharePoint](http://go.microsoft.com/fwlink/?LinkId=178818)
