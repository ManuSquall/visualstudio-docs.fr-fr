---
title: "Modèles d’élément de projet SharePoint et projet | Documents Microsoft"
ms.custom: 
ms.date: 02/22/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
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
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, project and project item templates
- SharePoint development in Visual Studio, templates
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 3890d7678fdc50a867e254edbbb7503acbebcd76
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/10/2018
---
# <a name="sharepoint-project-and-project-item-templates"></a>Modèles de projets et d'éléments de projet SharePoint
  Les sections suivantes décrivent le projet SharePoint et les modèles de projet élément et comment elles sont utilisées. 
  
##  <a name="project-and-project-item-templates-overview"></a>Vue d’ensemble des modèles d’élément de projet et de projet  
 Lorsque vous créez un projet SharePoint dans Visual Studio, un projet SharePoint est ajouté à la solution ainsi que tous les éléments de projet requis par ce type de projet. Par exemple, si vous créez un projet de composant WebPart Silverlight, Visual Studio crée une solution qui contient un élément de projet de composant Visual Web Part et d’un élément de projet d’application Silverlight, ainsi que tous les fichiers requis par les éléments de projet. Modèles d’élément de projet sont utilisés pour ajouter des éléments de projet à un projet existant de SharePoint, telles que l’ajout d’un récepteur d’événements, une colonne de site ou une liste.  
  
 Pour plus d’informations sur les notions de base de SharePoint, consultez [blocs de construction de SharePoint Foundation](http://go.microsoft.com/fwlink/?LinkId=179404). Utilisateurs avancés peuvent créer des modèles de projets et modèles d’élément de projet. Pour plus d’informations, consultez [extension du système de projet SharePoint](../sharepoint/extending-the-sharepoint-project-system.md).  
  
##  <a name="project-templates"></a>Modèles de projet  
 Voici une liste des modèles de projet SharePoint. Pour afficher les modèles de projet SharePoint dans Visual Studio, dans le **nouveau projet** boîte de dialogue, développez le **SharePoint** nœud sous **Visual C#** ou  **Visual Basic**, puis choisissez **2010**.  
  
### <a name="sharepoint-2010-project"></a>Projet SharePoint 2010  
 Le contenu d’un *projet SharePoint 2010* sont inclus dans chaque modèle de projet SharePoint. Un projet SharePoint 2010 contient :  
  
-   Un fichier projet.  
  
-   Une page de propriétés du projet.  
  
-   A **références** dossier répertoriant toutes les références d’assembly dans le projet.  
  
-   A **fonctionnalités** dossier qui contient un fichier de configuration .feature utilisé pour déployer des fonctionnalités sur le serveur SharePoint.  
  
-   A **Package** dossier qui contient un fichier de package, utilisé pour déployer la solution sur SharePoint.  
  
-   Un fichier key.snk (clé de nom fort) qui est utilisé pour signer l’assembly avec un nom fort, pour une sécurité renforcée.  
  
### <a name="sharepoint-2010-silverlight-web-part"></a>Composant WebPart Silverlight SharePoint 2010  
 *Composant WebPart SharePoint 2010 Silverlight* projets permettent de créer des composants WebPart pour SharePoint qui affichent des applications Silverlight. Lorsque vous créez ce projet, vous pouvez spécifier s’il faut ajouter une nouvelle application Silverlight ou référencer un existant. Pour plus d’informations, consultez [création de composants WebPart pour SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md) et [procédure pas à pas : création d’un composant WebPart Silverlight qui OData affiche pour SharePoint](../sharepoint/walkthrough-creating-a-silverlight-web-part-that-displays-odata-for-sharepoint.md).  
  
### <a name="sharepoint-2010-visual-web-part"></a>Composant Visual WebPart SharePoint 2010  
 A *2010 Visual WebPart SharePoint* projet inclut un fichier de définition Elements.xml, un **WebPart** élément et un **contrôle utilisateur** élément. Vous pouvez concevoir l’apparence du composant visual WebPart en faisant glisser ou en copiant des contrôles à partir de la boîte à outils Visual Studio à la surface du contrôle utilisateur. Pour plus d’informations, consultez [Comment : créer un composant WebPart SharePoint à l’aide d’un concepteur](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md) et [bloc de construction : composants WebPart](http://go.microsoft.com/fwlink/?LinkId=179438).  
  
### <a name="import-sharepoint-2010-solution-package"></a>Importer le package de solution 2010 SharePoint  
 *Importer le Package de Solution SharePoint 2010* projets vous permettent d’importer tout ou partie d’un site SharePoint 2010 existant, exporté vers un fichier de solution (.wsp) SharePoint dans Visual Studio. Une fois importé dans Visual Studio, vous pouvez personnaliser ses éléments et de les redéployer. Pour plus d’informations, consultez [l’importation d’éléments à partir d’un SharePoint Site existant](../sharepoint/importing-items-from-an-existing-sharepoint-site.md).  
  
### <a name="import-reusable-sharepoint-2010-workflow"></a>Importer le flux de travail SharePoint 2010 réutilisable  
 *Importer des flux de travail SharePoint 2010 réutilisable* projets vous permettent d’importer un flux de travail déclaratif, réutilisable créé dans SharePoint Designer 2010 dans Visual Studio. Le flux de travail est exporté à partir du site SharePoint comme un fichier .wsp. Une fois importé dans Visual Studio, vous pouvez le personnaliser, ajouter du code et déployez-le sur un site SharePoint. Pour plus d’informations, consultez [procédure pas à pas : importation de flux de travail réutilisable SharePoint Designer dans Visual Studio](../sharepoint/walkthrough-import-a-sharepoint-designer-reusable-workflow-into-visual-studio.md).  
  
##  <a name="project-item-templates"></a>Modèles d’élément de projet  
 Voici une liste de modèles d’élément de projet de SharePoint. Modèles d’élément de projet ajoutent des fichiers à la solution SharePoint pour prendre en charge des fonctionnalités telles que les colonnes de site, les listes et les types de contenu SharePoint. Par exemple, l’ajout d’une colonne de site à votre solution ajoute un projet colonne de site qui contient un fichier de définition Elements.xml. Ajout d’un composant visual web part d’ajoute un projet de composant WebPart visual à votre solution qui contient un fichier Elements.xml, un élément de contrôle utilisateur et un élément de composant visual web.  
  
 Pour afficher les modèles d’élément de projet SharePoint dans **l’Explorateur de solutions**, ouvrez le menu contextuel pour un projet SharePoint, puis choisissez **ajouter**, **un nouvel élément**. Développez le **SharePoint** nœud sous **Visual C#** ou **Visual Basic**, puis choisissez **2010**.  
  
### <a name="application-page-farm-solution-only"></a>Page d’application (Solution de batterie uniquement)  
 Un **Page d’Application (Solution de batterie uniquement)** élément vous permet de concevoir un [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] page web pour un site SharePoint. Pages d’applications peuvent être utilisés uniquement dans les solutions de batterie de serveurs. Vous pouvez ajouter cet élément de projet uniquement pour les solutions de batterie de serveurs. Pour plus d’informations, consultez [Comment : créer une Page d’Application](../sharepoint/how-to-create-an-application-page.md) et [_layouts d’Application Type de Page](http://go.microsoft.com/fwlink/?LinkId=179434).  
  
### <a name="business-data-connectivity-model-farm-solution-only"></a>Modèle de connectivité de données métiers (Solution de batterie uniquement)  
 A **modèle de connectivité de données métiers (Solution de batterie uniquement)** élément permet d’intégrer des données métiers dans SharePoint. Données d’entreprise peuvent provenir d’applications de serveur principal, tel que [!INCLUDE[ssNoVersion](../sharepoint/includes/ssnoversion-md.md)], Siebel et Service Advertising Protocol (SAP). Des modèles de connectivité de données peuvent être utilisés uniquement dans les solutions de batterie de serveurs. Vous pouvez ajouter cet élément de projet uniquement pour les solutions de batterie de serveurs. Pour plus d’informations, consultez [Comment : créer un modèle BDC](../sharepoint/how-to-create-a-bdc-model.md), [Comment : utiliser un fichier de ressources pour spécifier les noms localisés, propriétés et autorisations](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md), et [Nouveautés : Business Connectivity Services](http://go.microsoft.com/fwlink/?LinkId=179411).  
  
### <a name="content-type"></a>Type de contenu  
 *Type de contenu* éléments vous permettent de créer des types de contenu personnalisés basés sur un type de contenu existant (base) comme un document, une annonce ou une tâche. Un type de contenu personnalisé fournit les mêmes attributs et champs comme type de contenu de base ainsi que toutes les colonnes de site (champs) que vous définissez. Par exemple, vous pouvez créer un type de contenu personnalisé de Contact qui est basé sur le type de contenu Contact base fourni dans SharePoint. Vous pouvez personnaliser le type de contenu en modifiant les colonnes de site existant ou en ajoutant plus de colonnes de site à celles déjà inclus dans le type de contenu de base.  
  
> [!NOTE]  
>  En raison d’une limitation de SharePoint, vous ne peut pas créer un type de contenu solution batterie basé sur un type de contenu de solution bac à sable.  
  
 Pour plus d’informations, consultez [procédure pas à pas : création d’une colonne de Site, le Type de contenu et la liste pour SharePoint](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md) et [bloc de construction : Type de contenu](http://go.microsoft.com/fwlink/?LinkId=179413).  
  
### <a name="empty-element"></a>Élément vide  
 *Éléments vides* sont souvent utilisées pour définir les éléments de projet SharePoint qui ne disposent pas d’un projet ou un modèle d’élément de projet dans Visual Studio. Lorsque vous ajoutez un élément vide à votre projet, un nœud appelé EmptyElement [x](where [x] is a unique number\) is created. EmptyElement [x] contient un fichier unique nommé Elements.xml. Utilisez [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] instructions pour définir les éléments souhaités dans Elements.xml.  
  
### <a name="event-receiver"></a>Récepteur d’événements  
 *Récepteurs d’événements* gérer les événements pour les éléments dans le site SharePoint, tels que lorsqu’un élément est ajouté à une liste, lors de la suppression d’un élément web, ou quand un flux de travail a démarré. Le modèle d’élément événement récepteur projet vous permet de gérer  
  
-   Liste des événements  
  
-   Événements de l’élément de liste  
  
-   Liste des événements de messagerie  
  
-   événements Web  
  
-   Liste des événements de flux de travail  
  
 L’élément de projet de récepteur d’événements crée un **récepteur d’événements** dossier avec un fichier de classe unique qui contient les gestionnaires d’événements pour tous les événements vous avez spécifié lorsque vous avez créé le projet dans le **personnalisation SharePoint Assistant**. La classe de récepteur d’événements peut gérer les événements qui se produisent sur le site SharePoint lorsque des éléments tels que des fichiers, champs, éléments, listes, les pièces jointes, composants WebPart et des flux de travail sont ajoutés, mis à jour, supprimées ou supprimés. Pour plus d’informations, consultez [Comment : créer un récepteur d’événements](../sharepoint/how-to-create-an-event-receiver.md) et [bloc de construction : gestion des événements](http://go.microsoft.com/fwlink/?LinkId=179416).  
  
### <a name="list"></a>Liste  
 Une liste est une instance d’une réutilisables base définition de liste SharePoint, par exemple un calendrier ou une liste de tâches. Après avoir ajouté une liste à votre solution, le Concepteur de liste vous permet d’ajouter des colonnes de site à la liste et créer des colonnes de liste personnalisée. Cela inclut des colonnes de site à partir des types de contenu. Vous pouvez spécifier le *vue* pour obtenir la liste, qui détermine les colonnes qui apparaîtront dans la liste. Pour plus d’informations, consultez [procédure pas à pas : création d’une colonne de Site, le Type de contenu et la liste pour SharePoint](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md) et [bloc de construction : listes et bibliothèques de documents](http://go.microsoft.com/fwlink/?LinkId=179421).  
  
### <a name="module"></a>Module  
 *Modules* (à ne pas confondre avec [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] modules) contient tous les fichiers que vous souhaitez déployer sur le serveur SharePoint, tels que des images ou des commentaires. L’élément de projet de module contient un **Module** nœud. Le nœud module contient deux modèles d’élément de projet : un fichier de définition XML, qui agit comme un manifeste pour le module, et un fichier sample.txt, un fichier d’espace réservé. Pour plus d’informations, consultez [à l’aide de Modules pour inclure des fichiers dans la Solution](../sharepoint/using-modules-to-include-files-in-the-solution.md) et [Modules](http://go.microsoft.com/fwlink/?LinkId=179425).  
  
### <a name="sequential-workflow-farm-solution-only"></a>Workflow séquentiel (Solution de batterie uniquement)  
 A *workflow séquentiel* est une série d’étapes de logique métier, effectuée dans l’ordre, jusqu'à ce que la dernière étape est terminée. Flux de travail séquentiels est utilisés pour gérer les processus qui impliquent des éléments SharePoint tels que des listes et des documents. Vous pouvez créer des flux de travail au niveau du site (global) ou de flux de travail (local) au niveau de la liste, et vous pouvez indiquer si un flux de travail démarre automatiquement ou manuellement. Cet élément de projet peut être utilisé uniquement dans les solutions de batterie de serveurs. Vous pouvez ajouter cet élément de projet uniquement pour les solutions de batterie de serveurs. Pour plus d’informations, consultez [création de Solutions de flux de travail SharePoint](../sharepoint/creating-sharepoint-workflow-solutions.md), [flux de travail dans SharePoint Server 2010](http://go.microsoft.com/fwlink/?LinkId=260555), et [Nouveautés : améliorations de flux de travail](http://go.microsoft.com/fwlink/?LinkId=179418).  
  
### <a name="silverlight-web-part"></a>Composant WebPart Silverlight  
 *Composant WebPart Silverlight* éléments de projet permettent de créer des composants WebPart pour SharePoint qui affichent des applications Silverlight. Lorsque vous ajoutez cet élément de projet à votre solution, vous pouvez choisir d’ajouter une nouvelle application Silverlight ou référencer un ultérieurement. Pour plus d’informations, consultez [création de composants WebPart pour SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md) et [procédure pas à pas : création d’un composant WebPart Silverlight qui OData affiche pour SharePoint](../sharepoint/walkthrough-creating-a-silverlight-web-part-that-displays-odata-for-sharepoint.md).  
  
### <a name="site-column"></a>Colonne de site  
 A *colonne de site*, également appelé un *champ*, est un des éléments plus critiques que vous pouvez ajouter à un projet SharePoint. Une colonne de site représente un type de données, comme un numéro de téléphone, un commentaire de texte ou le nom de la ville d’un contact dans une liste de contacts. Pour plus d’informations, consultez [création de colonnes de Site, les Types de contenu et listes pour SharePoint](../sharepoint/creating-site-columns-content-types-and-lists-for-sharepoint.md) et [colonnes](http://go.microsoft.com/fwlink/?LinkId=226840).  
  
### <a name="site-definition-farm-solution-only"></a>Définition de site (Solution de batterie uniquement)  
 *Définition du site* un dossier de définition de site qui inclut les fichiers suivants contiennent des éléments de projet :  
  
-   Une page .aspx par défaut, utilisée en tant que la page web par défaut pour le site.  
  
-   Un fichier onet.xml qui définit les composants du site.  
  
-   Un fichier xml webtemp qui spécifie les configurations de définition de site qui s’affichent dans le **sélection du modèle** section de la **nouveau SharePoint Site** page.  
  
 Après avoir ajouté une définition de site, vous ajoutez du code et les fichiers pour introduire une fonctionnalité. Cet élément de projet peut être utilisé uniquement dans les solutions de batterie de serveurs. Vous pouvez ajouter cet élément de projet uniquement pour les solutions de batterie de serveurs. Pour plus d’informations, consultez [création de définitions de Site pour SharePoint](../sharepoint/creating-site-definitions-for-sharepoint.md) et [définitions de Site et les Configurations](http://go.microsoft.com/fwlink/?LinkId=260554).  
  
### <a name="state-machine-workflow-farm-solution-only"></a>Flux de travail de Machine à états (Solution de batterie uniquement)  
 A *workflow d’ordinateur d’état* est un ensemble d’états de logique métier, les transitions et les actions. Les étapes d’un workflow de machine d’état ne sont pas effectuées dans la séquence ; au lieu de cela, elles sont déclenchées par des actions et des États. Comme un workflow séquentiel, workflows d’ordinateur d’état sont associés à des éléments tels que des listes et des documents SharePoint. Une fois encore, vous pouvez créer des flux de travail au niveau du site (global) ou au niveau de la liste de flux de travail (local). Vous pouvez également choisir un flux de travail démarre automatiquement ou manuellement. Cet élément de projet peut être utilisé uniquement dans les solutions de batterie de serveurs. Vous pouvez ajouter cet élément de projet uniquement pour les solutions de batterie de serveurs. Pour plus d’informations, consultez [création de Solutions de flux de travail SharePoint](../sharepoint/creating-sharepoint-workflow-solutions.md), [flux de travail dans SharePoint Server 2010](http://go.microsoft.com/fwlink/?LinkId=260555), et [Nouveautés : améliorations de flux de travail](http://go.microsoft.com/fwlink/?LinkId=179418).  
  
### <a name="user-control-farm-solution-only"></a>Contrôle utilisateur (Solution de batterie uniquement)  
 A *contrôle utilisateur* est un contrôle personnalisé et réutilisable à laquelle vous pouvez ajouter d’autres contrôles ASP.NET et des contrôles de SharePoint. Le contrôle utilisateur peut être ajouté à des pages d’application et les composants WebPart qui s’exécutent dans SharePoint. Cet élément de projet peut être utilisé uniquement dans les solutions de batterie de serveurs. Vous pouvez ajouter cet élément de projet uniquement pour les solutions de batterie de serveurs. Pour plus d’informations, consultez [création de contrôles réutilisables pour les composants WebPart ou les Pages d’Application](http://go.microsoft.com/fwlink/?LinkId=226841).  
  
### <a name="visual-web-part"></a>Composant Visual Web Part  
 A *composant visual web part* élément de projet inclut un fichier de définition Elements.xml, un **WebPart** élément et un **contrôle utilisateur** élément. Vous pouvez concevoir l’apparence du composant visual WebPart en faisant glisser ou en copiant des contrôles à partir de la boîte à outils Visual Studio à la surface du contrôle utilisateur. Pour plus d’informations, consultez [Comment : créer un composant WebPart SharePoint à l’aide d’un concepteur](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md) et [bloc de construction : composants WebPart](http://go.microsoft.com/fwlink/?LinkId=179438).  
  
### <a name="web-part"></a>Composant WebPart  
 A *WebPart* est un contrôle côté serveur qui s’exécute à l’intérieur d’un type spécial de la page appelée une Page WebPart. Ils sont les blocs de construction des pages qui s’affichent sur un site SharePoint. L’élément de la partie web fournit des fichiers qui vous permettent de concevoir un composant WebPart pour un site SharePoint. Pour plus d’informations, consultez [Comment : créer un composant WebPart SharePoint](../sharepoint/how-to-create-a-sharepoint-web-part.md) et [bloc de construction : composants WebPart](http://go.microsoft.com/fwlink/?LinkId=179438).  
  
## <a name="see-also"></a>Voir aussi  
 [Développement de Solutions SharePoint](../sharepoint/developing-sharepoint-solutions.md)   
 [Produits et technologies SharePoint](http://go.microsoft.com/fwlink/?LinkId=178818)  
  
  
