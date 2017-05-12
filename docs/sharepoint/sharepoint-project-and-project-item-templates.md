---
title: "Mod&#232;les de projets et d&#39;&#233;l&#233;ments de projet SharePoint"
ms.custom: ""
ms.date: "02/22/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.SharePointTools.SPE.FirstWizardPage"
  - "VS.SharePointTools.SPE.ListInstance"
  - "VS.SharePointTools.SPE.ListDefinition"
  - "VS.SharePointTools.SPE.ListDefFromContentType"
  - "VS.SharePointTools.SPE.ContentType"
  - "SPE.Wizard"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "développement SharePoint dans Visual Studio, projet et modèles d'élément de projet"
  - "développement SharePoint dans Visual Studio, modèles"
ms.assetid: 54a7576f-d3f9-475d-8ed7-b675ad21cb53
caps.latest.revision: 41
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 40
---
# Mod&#232;les de projets et d&#39;&#233;l&#233;ments de projet SharePoint
  Les sections suivantes décrivent le projet SharePoint et modèles de projet élément et comment ils sont utilisés.  
  
 [!INCLUDE[autoOutline](../Token/autoOutline_md.md)]  
  
##  <a name="project_items_templates_overview"></a> Projet et vue d'ensemble des modèles d'élément de projet  
 Lorsque vous créez un projet SharePoint dans Visual Studio, un projet SharePoint est ajouté à la solution et tous les éléments de projet requises par ce type de projet.  Par exemple, si vous créez un projet de composant WebPart Silverlight, Visual Studio crée une solution qui contient un élément de projet Visual Web Part et un élément de projet d'application Silverlight ainsi que tous les fichiers requis par les éléments de projet.  Modèles d'élément de projet sont utilisés pour ajouter des éléments de projet à un projet SharePoint existant, comme l'ajout d'un récepteur d'événements, une colonne de site ou une liste.  
  
 Pour plus d'informations sur les principes de base de SharePoint, consultez  [blocs de construction de SharePoint Foundation](http://go.microsoft.com/fwlink/?LinkId=179404).  Les utilisateurs expérimentés peuvent créer projet personnalisé et des modèles d'élément de projet.  Pour plus d'informations, consultez  [Extending the SharePoint Project System](../sharepoint/extending-the-sharepoint-project-system.md).  
  
##  <a name="project_templates"></a> Modèles de projet  
 Voici une liste des modèles de projet SharePoint.  Pour afficher les modèles de projet SharePoint dans Visual Studio, dans le  **Nouveau projet** boîte de dialogue, développez la  **SharePoint** nœud sous une ou l'autre  **Visual C\#** ou  **Visual Basic**, puis cliquez sur  **2010**.  
  
### Projet de SharePoint 2010  
 Le contenu d'un  *SharePoint 2010 projet* sont inclus dans chaque modèle de projet SharePoint.  Un projet de SharePoint 2010 contient :  
  
-   Un fichier de projet.  
  
-   Page de propriétés du projet.  
  
-   A  **références** dossier répertoriant toutes les références d'assembly dans le projet.  
  
-   A  **fonctionnalités** dossier contenant un fichier de configuration .feature utilisé pour déployer des fonctionnalités sur le serveur SharePoint.  
  
-   A  **Package** dossier qui contient le fichier Package.package, utilisé pour déployer la solution vers SharePoint.  
  
-   Un fichier key.snk \(clé de nom fort\) utilisé pour signer l'assembly avec un nom fort, pour une sécurité améliorée.  
  
### Composant WebPart SharePoint 2010 Silverlight  
 *Composant WebPart SharePoint 2010 Silverlight* projets permettent de créer des composants WebPart pour SharePoint qui affichent des applications Silverlight.  Lorsque vous créez ce projet, vous pouvez spécifier si vous souhaitez ajouter une nouvelle application Silverlight ou faire référence à un.  Pour plus d'informations, consultez  [Création de composants WebPart pour SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)et   [Procédure pas à pas : création d'un composant WebPart Silverlight qui affiche OData pour SharePoint](../sharepoint/walkthrough-creating-a-silverlight-web-part-that-displays-odata-for-sharepoint.md).  
  
### Visual Web Part SharePoint 2010  
 A  *Visual Web Part SharePoint 2010* projet inclut un fichier de définition Elements.xml, un  **WebPart** élément et un  **Contrôle utilisateur** élément.  Vous pouvez concevoir l'aspect de l'élément visual web part en faisant glisser ou en copiant des contrôles à partir de la boîte à outils Visual Studio vers la surface du contrôle utilisateur.  Pour plus d'informations, consultez  [Comment : créer un composant WebPart SharePoint à l'aide d'un concepteur](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md)et   [bloc de construction : WebParts](http://go.microsoft.com/fwlink/?LinkId=179438).  
  
### Importer le Package de Solution SharePoint 2010  
 *Importer le Package de Solution SharePoint 2010* les projets vous permettent d'importer tout ou partie d'un site SharePoint 2010 existant, exporté vers un fichier de solution \(.wsp\) SharePoint dans Visual Studio.  Une fois importé dans Visual Studio, vous pouvez personnaliser ses éléments et de les redéployer.  Pour plus d'informations, consultez  [Importation d'éléments d'un site SharePoint existant](../sharepoint/importing-items-from-an-existing-sharepoint-site.md).  
  
### Importer des flux de travail réutilisable SharePoint 2010  
 *Importer des flux de travail réutilisable SharePoint 2010* les projets vous permettent d'importer un flux de travail déclaratif, réutilisable créé dans SharePoint Designer 2010 dans Visual Studio.  Le flux de travail est exporté à partir du site SharePoint sous la forme d'un fichier .wsp.  Une fois importé dans Visual Studio, vous pouvez le personnaliser, ajouter du code et puis le déployer sur un site SharePoint.  Pour plus d'informations, consultez  [Procédure pas à pas : importation d'un flux de travail réutilisable de SharePoint Designer dans Visual Studio](../sharepoint/walkthrough-import-a-sharepoint-designer-reusable-workflow-into-visual-studio.md).  
  
##  <a name="project_item_templates"></a> Modèles d'élément de projet  
 Voici une liste de modèles d'élément de projet SharePoint.  Modèles d'élément de projet ajoutent des fichiers à la solution SharePoint pour prendre en charge les fonctionnalités telles que les colonnes de site, les listes et les types de contenu SharePoint.  Par exemple, l'ajout d'une colonne de site pour votre solution ajoute un projet colonne de site qui contient un fichier de définition Elements.xml.  Ajout d'un composant visual web part ajoute un projet de composant WebPart visual à votre solution qui contient un fichier Elements.xml, un élément de contrôle utilisateur et d'un élément WebPart visual.  
  
 Pour afficher les modèles d'élément de projet SharePoint dans  **L'Explorateur de solutions**, ouvrez le menu contextuel pour un projet SharePoint et puis cliquez sur  **Ajouter**,  **Un nouvel élément**.  Développez le  **SharePoint** nœud sous une ou l'autre  **Visual C\#** ou  **Visual Basic**, puis cliquez sur  **2010**.  
  
### Page de l'application \(Solution de batterie uniquement\)  
 Un  **Page de l'Application \(Solution de batterie de serveurs uniquement\)** élément vous permet de concevoir un  [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)]page web d'un site SharePoint.  Pages d'applications peuvent être utilisés uniquement dans les solutions de batterie de serveurs.  Vous pouvez ajouter cet élément de projet uniquement pour les solutions de batterie.  Pour plus d'informations, consultez  [Comment : créer une page d'application](../sharepoint/how-to-create-an-application-page.md)et   [\_layouts d'Application Type de Page](http://go.microsoft.com/fwlink/?LinkId=179434).  
  
### Modèle de connectivité de données métiers \(Solution de batterie uniquement\)  
 A  **Modèle BDC \(Solution de batterie de serveurs uniquement\)** élément vous permet d'intégrer des données métiers dans SharePoint.  Données métiers peuvent provenir d'applications serveur back\-end, tel que  [!INCLUDE[ssNoVersion](../sharepoint/includes/ssnoversion-md.md)], Siebel et protocole SAP \(Service Advertising\).  Les modèles Business data connectivity peuvent être utilisés uniquement dans les solutions de batterie de serveurs.  Vous pouvez ajouter cet élément de projet uniquement pour les solutions de batterie.  Pour plus d'informations, consultez  [Comment : créer un modèle BDC](../sharepoint/how-to-create-a-bdc-model.md),   [Comment : utiliser un fichier de ressources pour spécifier des noms localisés, propriétés et autorisations](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md), et   [What's New : Services Business Connectivity](http://go.microsoft.com/fwlink/?LinkId=179411).  
  
### Type de contenu  
 *Type de contenu* éléments vous permettent de créer des types de contenu personnalisés basés sur un type de contenu existant \(de base\) tel qu'un document, une annonce ou une tâche.  Un type de contenu personnalisé fournit les mêmes attributs et champs en tant que type de contenu de base ainsi que les colonnes de site \(champs\) que vous définissez.  Par exemple, vous pouvez créer un type de contenu Contact personnalisé est basé sur le type de contenu Contact base fourni dans SharePoint.  Vous pouvez personnaliser le type de contenu en modifiant les colonnes de site existantes ou en ajoutant des colonnes de site à celles déjà incluses dans le type de contenu de base.  
  
> [!NOTE]  
>  En raison d'une restriction SharePoint, vous ne pouvez pas créer un type de contenu solution batterie basé sur un type de contenu de solution bac à sable.  
  
 Pour plus d'informations, consultez  [Procédure pas à pas : création d'une colonne de site, d'un type de contenu et d'une liste pour SharePoint](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md)et   [bloc de construction : Type de contenu](http://go.microsoft.com/fwlink/?LinkId=179413).  
  
### Élément vide  
 *Éléments vides* sont plus souvent utilisées pour définir des éléments de projet SharePoint qui ne disposent pas d'un projet ou un modèle d'élément de projet dans Visual Studio.  Lorsque vous ajoutez un élément vide à votre projet, un nœud appelé EmptyElement \[x\]\(où \[x\] est un nombre unique\) est créée.  EmptyElement \[x\] contient un fichier unique nommé Elements.xml.  Utilisez  [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)]instructions pour définir les éléments souhaités dans Elements.xml.  
  
### Récepteur d'événements  
 *Récepteurs d'événements* gérer les événements liés aux éléments du site SharePoint, par exemple lorsqu'un élément est ajouté à une liste, lors de la suppression d'un élément web ou lorsqu'un workflow est démarré.  Le modèle d'élément événement récepteur projet vous permet de gérer les  
  
-   Liste des événements  
  
-   Les événements d'élément de liste  
  
-   Liste d'événement par e\-mail  
  
-   Événements Web  
  
-   Liste des événements de workflow  
  
 L'élément de projet récepteur d'événements crée un  **Récepteur d'événements** dossier avec un seul fichier de classe qui contient les gestionnaires d'événements pour tous les événements vous avez spécifié lorsque vous avez créé le projet dans le  **Assistant Personnalisation de SharePoint**.  Le  event receiverclasse peut gérer des événements qui se produisent sur le site SharePoint lorsque des éléments tels que des fichiers, champs, éléments, listes, les pièces jointes, des composants WebPart et des flux de travail sont ajoutés, mis à jour, supprimés ou supprimés.  Pour plus d'informations, consultez  [Comment : créer un récepteur d'événements](../sharepoint/how-to-create-an-event-receiver.md)et   [bloc de construction : Gestion des événements](http://go.microsoft.com/fwlink/?LinkId=179416).  
  
### Liste  
 Une liste est une instance d'une base SharePoint liste Définition réutilisable, comme un calendrier ou une liste de tâches.  Après l'ajout d'une liste à votre solution, le Concepteur de la liste vous permet d'ajouter des colonnes de site à la liste et de créer des colonnes de la liste personnalisée.  Cela inclut des colonnes de site à partir de types de contenu.  Vous pouvez spécifier le  *mode* pour la liste, qui détermine les colonnes qui s'affichent dans la liste.  Pour plus d'informations, consultez  [Procédure pas à pas : création d'une colonne de site, d'un type de contenu et d'une liste pour SharePoint](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md)et   [bloc de construction : Listes et bibliothèques de documents](http://go.microsoft.com/fwlink/?LinkId=179421).  
  
### Module  
 *Modules de* \(à ne pas confondre avec  [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)]modules\) contiennent tous les fichiers que vous souhaitez déployer sur le serveur SharePoint, comme des images ou des notes.  L'élément de projet du module contient un  **Module** nœud.  Le nœud module contient deux modèles d'élément de projet : un fichier de définition XML, qui fait Office de manifeste pour le module, et un fichier sample.txt, un fichier d'espaces réservés.  Pour plus d'informations, consultez  [Utilisation de modules pour inclure des fichiers dans la solution](../sharepoint/using-modules-to-include-files-in-the-solution.md)et   [Modules](http://go.microsoft.com/fwlink/?LinkId=179425).  
  
### Flux de travail séquentiel \(Solution de batterie uniquement\)  
 A  *flux de travail séquentiel* est une série d'étapes de logique métier, exécutées dans l'ordre, jusqu'à ce que la dernière étape est terminée.  Flux de travail séquentiels est utilisés pour gérer les processus qui impliquent des éléments SharePoint tels que des listes et des documents.  Vous pouvez créer des flux de travail au niveau du site \(global\) ou au niveau de la liste de flux de travail \(local\), et vous pouvez indiquer si un flux de travail démarre automatiquement ou manuellement.  Cet élément de projet peut être utilisé uniquement dans les solutions de batterie de serveurs.  Vous pouvez ajouter cet élément de projet uniquement pour les solutions de batterie.  Pour plus d'informations, consultez  [Création de solutions de flux de travail SharePoint](../sharepoint/creating-sharepoint-workflow-solutions.md),   [Workflows dans SharePoint Server 2010](http://go.microsoft.com/fwlink/?LinkId=260555), et  [What's New : Amélioration du workflow](http://go.microsoft.com/fwlink/?LinkId=179418).  
  
### Composant WebPart Silverlight  
 *Composant WebPart Silverlight* éléments de projet permettent de créer des composants WebPart pour SharePoint qui affichent des applications Silverlight.  Lorsque vous ajoutez cet élément de projet à votre solution, vous pouvez choisir d'ajouter une nouvelle application Silverlight ou référencer un ultérieurement.  Pour plus d'informations, consultez  [Création de composants WebPart pour SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)et   [Procédure pas à pas : création d'un composant WebPart Silverlight qui affiche OData pour SharePoint](../sharepoint/walkthrough-creating-a-silverlight-web-part-that-displays-odata-for-sharepoint.md).  
  
### Colonne de site  
 A  *colonne de site*, également appelé un  *champ*, est l'un des éléments de base que vous pouvez ajouter à un projet SharePoint.  Une colonne de site représente un type de données, comme un numéro de téléphone, un commentaire de texte ou le nom de la ville d'un contact dans une liste de contacts.  Pour plus d'informations, consultez  [Création de colonnes de sites, de types de contenu et de listes pour SharePoint](../sharepoint/creating-site-columns-content-types-and-lists-for-sharepoint.md)et   [colonnes](http://go.microsoft.com/fwlink/?LinkId=226840).  
  
### Définition du site \(Solution de batterie uniquement\)  
 *Définition du site*  un dossier de définition de site qui comprend les fichiers suivants contiennent des éléments de projet :  
  
-   Une page .aspx par défaut, utilisée en tant que page web par défaut pour le site.  
  
-   Un fichier onet.xml qui définit les composants du site.  
  
-   Un ficher xml webtemp qui spécifie les configurations de définition de site qui s'affichent dans le  **Sélection du modèle** section de la  **Nouveau SharePoint Site** page.  
  
 Après avoir ajouté une définition de site, vous ajoutez des fichiers présenter les fonctionnalités et le code.  Cet élément de projet peut être utilisé uniquement dans les solutions de batterie de serveurs.  Vous pouvez ajouter cet élément de projet uniquement pour les solutions de batterie.  Pour plus d'informations, consultez  [Création de définitions de site pour SharePoint](../sharepoint/creating-site-definitions-for-sharepoint.md)et   [définitions de sites et de Configurations de](http://go.microsoft.com/fwlink/?LinkId=260554).  
  
### Flux de travail de Machine d'état \(Solution de batterie uniquement\)  
 A  *workflow de machine d'état* est un ensemble d'états de logique métier, de transitions et d'actions.  Les étapes d'un workflow de machine d'état ne sont pas effectuées dans l'ordre ; au lieu de cela, elles sont déclenchées par des actions et des États.  Comme un flux de travail séquentiel, les workflows de machine d'état sont associés à des éléments SharePoint tels que des listes et des documents.  Une fois de plus, vous pouvez créer des flux de travail au niveau du site \(global\) ou au niveau de la liste \(local\).  Vous pouvez également choisir un flux de travail démarre automatiquement ou manuellement.  Cet élément de projet peut être utilisé uniquement dans les solutions de batterie de serveurs.  Vous pouvez ajouter cet élément de projet uniquement pour les solutions de batterie.  Pour plus d'informations, consultez  [Création de solutions de flux de travail SharePoint](../sharepoint/creating-sharepoint-workflow-solutions.md),   [Workflows dans SharePoint Server 2010](http://go.microsoft.com/fwlink/?LinkId=260555), et  [What's New : Amélioration du workflow](http://go.microsoft.com/fwlink/?LinkId=179418).  
  
### Contrôle utilisateur \(Solution de batterie uniquement\)  
 A  *contrôle utilisateur* est un contrôle personnalisé et réutilisable à laquelle vous pouvez ajouter d'autres contrôles ASP.NET et des contrôles SharePoint.  Le contrôle utilisateur peut être ajouté aux pages d'application et les composants WebPart qui s'exécutent dans SharePoint.  Cet élément de projet peut être utilisé uniquement dans les solutions de batterie de serveurs.  Vous pouvez ajouter cet élément de projet uniquement pour les solutions de batterie.  Pour plus d'informations, consultez  [Création de contrôles réutilisables pour les Pages d'Application ou de WebParts](http://go.microsoft.com/fwlink/?LinkId=226841).  
  
### Composant Visual Web Part  
 A  *composant visual web part* élément de projet inclut un fichier de définition Elements.xml, un  **WebPart** élément et un  **Contrôle utilisateur** élément.  Vous pouvez concevoir l'aspect de l'élément visual web part en faisant glisser ou en copiant des contrôles à partir de la boîte à outils Visual Studio vers la surface du contrôle utilisateur.  Pour plus d'informations, consultez  [Comment : créer un composant WebPart SharePoint à l'aide d'un concepteur](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md)et   [bloc de construction : WebParts](http://go.microsoft.com/fwlink/?LinkId=179438).  
  
### Composant WebPart  
 A  *WebPart* est un contrôle côté serveur qui s'exécute à l'intérieur d'un type spécial de page appelé une Page de composants WebPart.  Ils sont les blocs de construction des pages qui s'affichent sur un site SharePoint.  L'élément WebPart fournit des fichiers qui vous permettent de concevoir un composant WebPart pour un site SharePoint.  Pour plus d'informations, consultez  [Comment : créer un composant WebPart SharePoint](../sharepoint/how-to-create-a-sharepoint-web-part.md)et   [bloc de construction : WebParts](http://go.microsoft.com/fwlink/?LinkId=179438).  
  
## Voir aussi  
 [Developing SharePoint Solutions](../sharepoint/developing-sharepoint-solutions.md)   
 [Produits et Technologies SharePoint](http://go.microsoft.com/fwlink/?LinkId=178818)  
  
  