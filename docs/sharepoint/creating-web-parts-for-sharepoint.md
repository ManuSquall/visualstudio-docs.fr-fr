---
title: "Cr&#233;ation de composants WebPart pour SharePoint"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "Microsoft.SharePoint.WebControls.DateTimeControl"
  - "Microsoft.SharePoint.WebControls.CssLink"
  - "Microsoft.SharePoint.WebControls.RssLink"
  - "Microsoft.SharePoint.WebControls.Theme"
  - "Microsoft.SharePoint.WebControls.AspMenu"
  - "Microsoft.SharePoint.WebControls.ListProperty"
  - "Microsoft.SharePoint.WebControls.ProjectProperty"
  - "Microsoft.SharePoint.WebControls.FormsDigest"
  - "Microsoft.SharePoint.WebControls.ScriptLink"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "développement SharePoint dans Visual Studio, WebParts"
  - "WebParts (développement SharePoint dans Visual Studio), concevoir"
ms.assetid: a6349e85-45cf-4766-b856-e25c9f1ffd34
caps.latest.revision: 42
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 41
---
# Cr&#233;ation de composants WebPart pour SharePoint
  En utilisant des composants WebPart, vous pouvez modifier le contenu, l'apparence et le comportement des pages d'un site SharePoint à l'aide d'un navigateur.  Les composants WebPart sont des contrôles côté serveur qui s'exécutent dans une page WebPart : ce sont les blocs de construction des pages qui s'affichent sur un site SharePoint.  Consultez [Bloc de construction : Composants WebPart](http://go.microsoft.com/fwlink/?LinkID=182097).  
  
 Vous pouvez créer et déboguer des composants WebPart sur un site SharePoint en utilisant les modèles de Visual Studio.  
  
## Création d'un composant WebPart dans Visual Studio  
 Créez un composant WebPart en ajoutant un élément **WebPart** à un projet SharePoint.  Vous pouvez utiliser un élément **WebPart** dans une solution bac à sable \(sandbox\) ou une solution de batterie.  
  
 Si vous souhaitez concevoir visuellement un composant WebPart à l'aide d'un concepteur, créez un projet **Composant Visual WebPart** ou ajoutez l'élément **Composant Visual WebPart** à un projet SharePoint.  Vous ne pouvez utiliser un élément **Composant Visual WebPart** que dans une solution de batterie.  
  
### Élément WebPart  
 Un élément **WebPart** fournit des fichiers que vous pouvez utiliser pour concevoir un composant WebPart pour un site SharePoint.  Lorsque vous ajoutez un élément **WebPart**, Visual Studio crée un dossier dans votre projet, puis ajoute plusieurs fichiers à ce dossier.  Le tableau suivant décrit chaque fichier.  
  
|Fichier|Description|  
|-------------|-----------------|  
|Elements.xml|Contient des informations que le fichier de définition de fonctionnalité dans votre projet utilise pour déployer le composant WebPart.|  
|.webpart|Fournit des informations dont SharePoint a besoin pour afficher votre composant WebPart dans une galerie de composants WebPart.|  
|Fichier de code|Contient des méthodes qui ajoutent des contrôles au composant WebPart et qui génèrent du contenu personnalisé à l'intérieur du composant WebPart.|  
  
 Pour plus d'informations, consultez [Comment : créer un composant WebPart SharePoint](../sharepoint/how-to-create-a-sharepoint-web-part.md).  
  
### Élément Composant Visual WebPart  
 Un composant Visual Web Part est un composant WebPart que vous créez à l'aide du concepteur Visual Web Developer dans Visual Studio.  Consultez [Visual Studio Web Development Content Map](http://msdn.microsoft.com/fr-fr/9c31f93b-c8fb-4599-9b14-6194ec8c7539).  
  
 Un composant WebPart visuel fonctionne comme tout autre composant WebPart.  Pour ajouter des contrôles, tels que des boutons et des zones de texte, à un composant WebPart, vous ajoutez du code à un fichier XML.  Toutefois, vous ajoutez des contrôles à un composant WebPart visuel en les faisant glisser ou en les copiant sur le composant WebPart dans la **Boîte à outils** Visual Studio.  Le concepteur génère ensuite le code requis dans le fichier XML.  Consultez [Comment : créer un composant WebPart SharePoint à l'aide d'un concepteur](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md).  
  
## Contrôles SharePoint  
 Visual Studio fournit certains contrôles pour créer les pages SharePoint, telles que les pages d'application.  Ces contrôles apparaissent dans la **Boîte à outils** sous **Commandes SharePoint**.  Les fonctionnalités de ces contrôles dérivent de l'espace de noms [Microsoft.SharePoint.WebControls](http://go.microsoft.com/fwlink/?LinkId=235315), qui contient les contrôles serveur ASP.NET utilisés sur les pages de site et de liste SharePoint.  
  
|Nom du contrôle|Description|  
|---------------------|-----------------|  
|[AspMenu](http://go.microsoft.com/fwlink/?LinkId=235307)|Insère un menu ASP.  Pour plus d'informations, consultez [Vue d'ensemble des contrôles de menu](http://go.microsoft.com/fwlink/?LinkId=235316).|  
|[CssLink](http://go.microsoft.com/fwlink/?LinkId=235308)|Insère un élément **LINK** dans la page .aspx et applique une ou plusieurs feuilles de style externes définies par **CssRegistration**.|  
|[DateTimeControl](http://go.microsoft.com/fwlink/?LinkId=235306)|Insère un contrôle DateTime dans la page .aspx.|  
|[FormDigest](http://go.microsoft.com/fwlink/?LinkId=235309)|Insère une validation de sécurité dans la page .aspx|  
|[ListProperty](http://go.microsoft.com/fwlink/?LinkId=235310)|Retourne une propriété d'une liste spécifiée.|  
|[ProjectProperty](http://go.microsoft.com/fwlink/?LinkId=235311)|Retourne une propriété globale du site Web actuel.|  
|[RssLink](http://go.microsoft.com/fwlink/?LinkId=235312)|Insère un lien vers un flux RSS dans la page .aspx.|  
|[ScriptLink](http://go.microsoft.com/fwlink/?LinkId=235313)|Fournit des propriétés et des méthodes pour l'inscription de ressources \(telles que les scripts\) dans une page, afin qu'elles puissent être demandées lorsque la page est affichée.|  
|[Thème](http://go.microsoft.com/fwlink/?LinkId=235314)|Applique un thème à la page .aspx.|  
  
## Débogage d'un composant WebPart  
 Vous pouvez déboguer un projet SharePoint qui contient un composant WebPart de la même manière que vous le feriez avec d'autres projets Visual Studio.  Lorsque vous démarrez le débogueur Visual Studio, Visual Studio ouvre le site SharePoint.  
  
 Pour commencer à déboguer votre code, ajoutez le composant WebPart à une page WebPart dans SharePoint.  
  
 Pour plus d'informations sur le débogage de projets SharePoint, consultez [Dépannage des solutions SharePoint](../sharepoint/troubleshooting-sharepoint-solutions.md).  
  
## Limitations des composants Web Part visuels  
 En démarrant dans Visual Studio, vous pouvez ajouter des composants Visual Web Part aux solutions SharePoint sandbox et aux solutions de batterie de serveurs.  Toutefois, les composants WebPart visuels ont les limitations suivantes :  
  
-   Les composants WebPart visuels ne prennent pas en charge les paramètres remplaçables.  Pour plus d'informations, consultez [Paramètres remplaçables](../sharepoint/replaceable-parameters.md).  
  
-   Les contrôles utilisateur ou les composants WebPart visuels ne peuvent pas être glissés et déplacés, ou copiés sur des composants WebPart visuels.  Cette action entraîne une erreur de build.  
  
-   Les composants WebPart visuels ne prennent pas en charge les jetons serveur SharePoint, tels que $SPUrl.  Pour plus d'informations, consultez « Restrictions relatives aux jetons dans les composants WebPart visuels bac à sable \(sandbox\) » dans la rubrique [Dépannage des solutions SharePoint](../sharepoint/troubleshooting-sharepoint-solutions.md).  
  
-   Les composants WebPart visuels d'une solution bac à sable obtiennent parfois l'erreur suivante : « La demande d’exécution du code en mode bac à sable a été refusée, car le service d’exécution du code en mode bac à sable sur l’ordinateur hôte a été arrêté. » Pour plus d'informations sur cette erreur, consultez cette publication dans le [Blog de l'équipe de développement SharePoint](http://go.microsoft.com/fwlink/?LinkId=225932).  
  
-   Le débogage JavaScript côté serveur n'est pas pris en charge dans Visual Studio, mais le débogage JavaScript côté client est pris en charge.  
  
     Bien que vous puissiez ajouter du code JavaScript intégré à un fichier de balisage côté serveur, le débogage n'est pas pris en charge pour les points d'arrêt ajoutés au balisage.  Pour déboguer JavaScript, référencez un fichier externe JavaScript dans le fichier de balisage, puis définissez les points d'arrêt dans le fichier JavaScript.  
  
-   Le débogage de code intégré [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] doit être effectué dans le fichier de code généré au lieu du fichier de balisage.  
  
-   Les composants WebPart visuels ne prennent pas en charge l'utilisation de la directive `<@ Assembly Src=`.  
  
-   Les contrôles Web SharePoint et certains contrôles [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] ne sont pas pris en charge dans l'environnement sandbox de SharePoint.  Si des contrôles non pris en charge sont utilisés sur un composant WebPart visuel dans une solution bac à sable \(sandbox\), l'erreur « Le nom de type ou d'espace de noms Theme n'existe pas dans l'espace de noms Microsoft.SharePoint.WebControls » apparaît.  
  
 Pour plus d'informations sur les solutions bac à sable \(sandbox\), consultez [Différences entre les solutions bac à sable &#40;sandbox&#41; et les solutions de batterie](../sharepoint/differences-between-sandboxed-and-farm-solutions.md).  
  
## Création de composants WebPart SharePoint de type ancien  
 Vous pouvez utiliser les exemples figurant dans Visual Studio pour créer des composants WebPart [!INCLUDE[vstecasplong](../sharepoint/includes/vstecasplong-md.md)] personnalisés pour SharePoint.  Les composants WebPart [!INCLUDE[vstecasplong](../sharepoint/includes/vstecasplong-md.md)] sont construits sur l'infrastructure WebPart [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)]. Ce type est recommandé pour les nouveaux projets.  
  
 Vous serez très rarement amené à créer un composant WebPart à l'aide d'un composant WebPart SharePoint de type ancien.  Vous pouvez utiliser Visual Studio pour créer ces types de composants WebPart, mais Visual Studio ne fournit pas de modèles qui sont conçus spécifiquement pour vous aider à les créer.  
  
 Pour savoir quand vous pouvez créer un composant WebPart SharePoint de type ancien, consultez [Infrastructure de composant WebPart dans Windows SharePoint Services](http://go.microsoft.com/fwlink/?LinkId=169290).  Pour plus d'informations sur la création d'un composant WebPart à l'aide d'un composant WebPart SharePoint de type ancien, consultez la page relative à la [Procédure pas à pas : création d'un composant Web Part SharePoint de base](http://go.microsoft.com/fwlink/?LinkId=169288).  
  
## Rubriques connexes  
  
|Titre|Description|  
|-----------|-----------------|  
|[Comment : créer un composant WebPart SharePoint](../sharepoint/how-to-create-a-sharepoint-web-part.md)|Explique comment créer des composants WebPart pour des pages SharePoint.|  
|[Comment : créer un composant WebPart SharePoint à l'aide d'un concepteur](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md)|Indique comment créer des composants WebPart pour SharePoint à l'aide d'une aire de conception visuelle.|  
|[Comment : créer un contrôle utilisateur pour un composant WebPart ou une page d'application SharePoint](../sharepoint/how-to-create-a-user-control-for-a-sharepoint-application-page-or-web-part.md)|Explique comment créer des contrôles personnalisés et réutilisables qui peuvent être utilisés par des pages d'application et des composants WebPart s'exécutant dans SharePoint.|  
|[Procédure pas à pas : création d'un composant WebPart pour SharePoint](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint.md)|Décrit comment concevoir un composant WebPart pour SharePoint.|  
|[Procédure pas à pas : création d'un composant WebPart pour SharePoint à l'aide d'un concepteur](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint-by-using-a-designer.md)|Décrit comment concevoir un composant WebPart pour SharePoint en faisant glisser des contrôles vers une aire de conception visuelle.|  
|[Procédure pas à pas : création d'un composant WebPart Silverlight qui affiche OData pour SharePoint](../sharepoint/walkthrough-creating-a-silverlight-web-part-that-displays-odata-for-sharepoint.md)|Décrit comment concevoir un composant WebPart pour SharePoint qui héberge une application Silverlight et affiche les données des listes SharePoint.|  
|[Utilisation de Visual Web Developer](http://msdn.microsoft.com/fr-fr/9c31f93b-c8fb-4599-9b14-6194ec8c7539)|Explique comment utiliser le concepteur qui s'affiche lorsque vous ouvrez une page Web dans votre projet.|  
  
  