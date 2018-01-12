---
title: "Création de composants WebPart pour SharePoint | Documents Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- Microsoft.SharePoint.WebControls.DateTimeControl
- Microsoft.SharePoint.WebControls.CssLink
- Microsoft.SharePoint.WebControls.RssLink
- Microsoft.SharePoint.WebControls.Theme
- Microsoft.SharePoint.WebControls.AspMenu
- Microsoft.SharePoint.WebControls.ListProperty
- Microsoft.SharePoint.WebControls.ProjectProperty
- Microsoft.SharePoint.WebControls.FormsDigest
- Microsoft.SharePoint.WebControls.ScriptLink
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, Web Parts
- Web Parts [SharePoint development in Visual Studio], designing
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: d0c5acfac06702894f67a8bfc1547462a0069e15
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/10/2018
---
# <a name="creating-web-parts-for-sharepoint"></a>Création de composants WebPart pour SharePoint
  À l’aide de composants WebPart, vous pouvez modifier le contenu, l’apparence et comportement des pages d’un site SharePoint à l’aide d’un navigateur. Composants WebPart sont des contrôles côté serveur qui s’exécutent à l’intérieur d’une page WebPart : ils sont les blocs de construction des pages qui s’affichent sur un site SharePoint. Consultez [bloc de construction : composants WebPart](http://go.microsoft.com/fwlink/?LinkID=182097).  
  
 Vous pouvez créer et déboguer des composants WebPart sur un site SharePoint à l’aide de modèles à partir de Visual Studio.  
  
## <a name="creating-a-web-part-in-visual-studio"></a>Création d’un composant WebPart dans Visual Studio  
 Créer un composant WebPart en ajoutant un **WebPart** élément à un projet SharePoint. Vous pouvez utiliser un **WebPart** élément dans une solution bac à sable ou une solution de batterie de serveurs.  
  
 Si vous souhaitez concevoir un composant WebPart visuellement à l’aide d’un concepteur, créez un **composant Visual Web Part** ou ajoutez **composant Visual Web Part** élément à un projet SharePoint. Vous pouvez utiliser un **composant Visual Web Part** élément dans une solution de batterie de serveurs uniquement.  
  
### <a name="web-part-item"></a>Élément WebPart  
 A **WebPart** élément fournit les fichiers que vous pouvez utiliser pour concevoir un composant WebPart pour un site SharePoint. Lorsque vous ajoutez un **WebPart** article, Visual Studio crée un dossier dans votre projet et puis ajoute plusieurs fichiers au dossier. Le tableau suivant décrit chaque fichier.  
  
|Fichier|Description|  
|----------|-----------------|  
|Elements.Xml|Contient des informations utilisées par le fichier de définition de fonction dans votre projet pour déployer le composant WebPart.|  
|fichier .webpart|Fournit les informations nécessaires pour afficher votre composant WebPart dans une galerie de composants WebPart SharePoint.|  
|Fichier de code|Contient des méthodes qui ajoutent des contrôles au composant WebPart et qui génèrent du contenu personnalisé dans le composant WebPart.|  
  
 Pour plus d’informations, consultez [Comment : créer un composant WebPart SharePoint](../sharepoint/how-to-create-a-sharepoint-web-part.md).  
  
### <a name="visual-web-part-item"></a>Élément Visual WebPart  
 Un composant visual WebPart est un composant WebPart que vous créez à l’aide du concepteur Visual Web Developer dans Visual Studio. Un composant visual WebPart fonctionne comme tout autre composant WebPart. Pour ajouter des contrôles, tels que des boutons et des zones de texte, à un composant WebPart, vous ajoutez le code dans un fichier XML. Toutefois, ajouter des contrôles à un composant visual WebPart en faisant glisser ou en les copiant dans le composant WebPart à partir de Visual Studio **boîte à outils**. Le concepteur génère ensuite le code requis dans le fichier XML. Consultez [Comment : créer un composant WebPart SharePoint à l’aide d’un concepteur](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md).  
  
## <a name="sharepoint-controls"></a>Contrôles SharePoint  
 Visual Studio fournit certains contrôles pour créer des pages SharePoint, tels que des pages d’application. Ces contrôles s’affichent dans le **boîte à outils** sous **contrôles SharePoint**. Les fonctionnalités de ces contrôles dérivant le [Microsoft.SharePoint.WebControls](http://go.microsoft.com/fwlink/?LinkId=235315) espace de noms qui contient des contrôles serveur ASP.NET qui sont utilisés sur les pages de site et de liste SharePoint.  
  
|Nom du contrôle|Description|  
|------------------|-----------------|  
|[AspMenu](http://go.microsoft.com/fwlink/?LinkId=235307)|Insère un menu ASP. Pour plus d’informations, consultez [vue d’ensemble du contrôle de Menu](http://go.microsoft.com/fwlink/?LinkId=235316).|  
|[CssLink](http://go.microsoft.com/fwlink/?LinkId=235308)|Insère un **lien** élément dans la page .aspx et applique une ou plusieurs feuilles de style externes définies par **CssRegistration**.|  
|[DateTimeControl](http://go.microsoft.com/fwlink/?LinkId=235306)|Insère un contrôle de date/heure dans la page .aspx.|  
|[FormDigest](http://go.microsoft.com/fwlink/?LinkId=235309)|Insère une validation de la sécurité dans la page .aspx|  
|[ListProperty](http://go.microsoft.com/fwlink/?LinkId=235310)|Retourne une propriété d’une liste spécifiée.|  
|[ProjectProperty](http://go.microsoft.com/fwlink/?LinkId=235311)|Retourne une propriété globale du site Web en cours.|  
|[RssLink](http://go.microsoft.com/fwlink/?LinkId=235312)|Insère un lien vers un flux RSS dans la page .aspx.|  
|[ScriptLink](http://go.microsoft.com/fwlink/?LinkId=235313)|Fournit des propriétés et méthodes pour l’inscription des ressources, telles que des scripts, d’une page afin que doit être demandés lorsque la page est rendue.|  
|[Thème](http://go.microsoft.com/fwlink/?LinkId=235314)|Applique un thème à la page .aspx.|  
  
## <a name="debugging-a-web-part"></a>Débogage d’un composant WebPart  
 Vous pouvez déboguer un projet SharePoint qui contient un composant WebPart, comme vous le feriez autres projets Visual Studio. Lorsque vous démarrez le débogueur Visual Studio, Visual Studio ouvre le site SharePoint.  
  
 Pour commencer à déboguer votre code, ajoutez le composant WebPart à une page WebPart dans SharePoint.  
  
 Pour plus d’informations sur la façon de déboguer des projets SharePoint, consultez [dépannage des Solutions SharePoint](../sharepoint/troubleshooting-sharepoint-solutions.md).  
  
## <a name="visual-web-part-limitations"></a>Limitations des composants Web Part visuels  
 À partir de Visual Studio, vous pouvez ajouter des composants visual web parts pour les solutions bac à sable de SharePoint et les solutions de batterie de serveurs. Toutefois, les composants visual web parts présentent les limitations suivantes :  
  
-   Composants Visual web parts ne prennent pas en charge les paramètres remplaçables. Pour plus d’informations, consultez [paramètres remplaçables](../sharepoint/replaceable-parameters.md).  
  
-   Contrôles utilisateur visual WebPart ne peut pas être déplacé et supprimés ou copié sur les composants visual web parts. Cette action provoque une erreur de build.  
  
-   Visual WebPart ne prend directement en charge les jetons du serveur SharePoint tels que $SPUrl. Pour plus d’informations, voir « Jeton Restrictions de bac à sable Visual WebPart » dans la rubrique [dépannage des Solutions SharePoint](../sharepoint/troubleshooting-sharepoint-solutions.md).  
  
-   Visual WebPart dans une solution bac à sable parfois obtenir l’erreur, « la demande d’exécution de code sandbox a été refusée car le Service hôte de Code bac à sable était trop occupé pour traiter la demande ». Pour plus d’informations sur cette erreur, consultez le billet dans le [Blog de l’équipe SharePoint développeur](http://go.microsoft.com/fwlink/?LinkId=225932).  
  
-   Débogage de JavaScript côté serveur n’est pas pris en charge dans Visual Studio, mais que le débogage de JavaScript côté client est prise en charge.  
  
     Bien que vous pouvez ajouter inline JavaScript dans un fichier de balisage du côté serveur, le débogage n’est pas pris en charge pour les points d’arrêt ajoutés au balisage. Pour déboguer du code JavaScript, référencer un fichier JavaScript externe dans le fichier de balisage, puis définissez les points d’arrêt dans le fichier JavaScript.  
  
-   Débogage d’inline [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] code doit être effectué dans le fichier de code généré plutôt que dans le fichier de balisage.  
  
-   Composants Visual web parts ne prennent pas en charge l’utilisation de la `<@ Assembly Src=` la directive.  
  
-   SharePoint contrôles web et certaines [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] contrôles ne sont pas pris en charge dans l’environnement de bac à sable SharePoint. Si les contrôles non pris en charge sont utilisés sur un composant visual web part dans une solution bac à sable, l’erreur, « Nom du type ou espace de noms 'Theme' n’existe pas dans l’espace de noms 'Microsoft.SharePoint.WebControls' » s’affiche.  
  
 Pour plus d’informations sur les solutions bac à sable, consultez [les différences entre bac à sable et les Solutions de batterie de serveurs](../sharepoint/differences-between-sandboxed-and-farm-solutions.md).  
  
## <a name="creating-older-style-sharepoint-based-web-parts"></a>Création de composants de site Web SharePoint de Style plus anciens  
 Vous pouvez utiliser les modèles dans Visual Studio pour créer des [!INCLUDE[vstecasplong](../sharepoint/includes/vstecasplong-md.md)] des composants WebPart pour SharePoint. [!INCLUDE[vstecasplong](../sharepoint/includes/vstecasplong-md.md)]composants WebPart reposent sur la [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] infrastructure de composant WebPart et sont le type recommandé pour les nouveaux projets.  
  
 Dans rares cas, vous devrez créer un composant WebPart à l’aide de l’ancien style WebPart basé sur SharePoint. Vous pouvez utiliser Visual Studio pour créer ces types de composants WebPart, mais Visual Studio ne fournit pas tous les modèles qui sont spécifiquement conçues pour vous aider à les créer.  
  
 Pour plus d’informations sur quand vous pouvez souhaiter créer un composant WebPart basé sur SharePoint, consultez [Infrastructure de composant WebPart dans Windows SharePoint Services](http://go.microsoft.com/fwlink/?LinkId=169290). Pour plus d’informations sur la création d’un composant WebPart à l’aide de l’ancien style WebPart basé sur SharePoint, consultez [procédure pas à pas la création d’un composant WebPart SharePoint de base](http://go.microsoft.com/fwlink/?LinkId=169288).  
  
## <a name="related-topics"></a>Rubriques connexes  
  
|Titre|Description|  
|-----------|-----------------|  
|[Guide pratique pour créer un composant WebPart SharePoint](../sharepoint/how-to-create-a-sharepoint-web-part.md)|Vous montre comment créer des composants WebPart pour des pages SharePoint.|  
|[Guide pratique pour créer un composant WebPart SharePoint à l’aide d’un concepteur](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md)|Vous montre comment créer des composants WebPart pour SharePoint à l’aide d’une aire de conception visuelle.|  
|[Guide pratique pour créer un contrôle utilisateur pour un composant WebPart ou une page d’application SharePoint](../sharepoint/how-to-create-a-user-control-for-a-sharepoint-application-page-or-web-part.md)|Vous montre comment créer des contrôles personnalisés et réutilisables qui peuvent être utilisés par les pages d’application et les composants WebPart qui s’exécutent dans SharePoint.|  
|[Procédure pas à pas : création d’un composant WebPart pour SharePoint](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint.md)|Décrit comment concevoir un composant WebPart pour SharePoint.|  
|[Procédure pas à pas : création d’un composant WebPart pour SharePoint à l’aide d’un concepteur](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint-by-using-a-designer.md)|Décrit comment concevoir un composant WebPart pour SharePoint en faisant glisser des contrôles sur une aire de conception visuelle.|  
|[Procédure pas à pas : création d’un composant WebPart Silverlight qui affiche OData pour SharePoint](../sharepoint/walkthrough-creating-a-silverlight-web-part-that-displays-odata-for-sharepoint.md)|Décrit comment concevoir un composant WebPart pour SharePoint qui héberge une application Silverlight et affiche les données des listes SharePoint.|  
  
  