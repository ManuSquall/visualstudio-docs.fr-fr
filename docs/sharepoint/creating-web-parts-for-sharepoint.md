---
title: Création de composants WebPart pour SharePoint | Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
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
manager: douge
ms.workload:
- office
ms.openlocfilehash: cd92e4e4b5f4a0ae77cfae393d2d51446e17bcfe
ms.sourcegitcommit: e6b13898cfbd89449f786c2e8f3e3e7377afcf25
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/22/2018
ms.locfileid: "36327214"
---
# <a name="create-web-parts-for-sharepoint"></a>Créer des composants WebPart pour SharePoint
  À l’aide de composants WebPart, vous pouvez modifier le contenu, l’apparence et comportement des pages d’un site SharePoint à l’aide d’un navigateur. Composants WebPart sont des contrôles côté serveur qui s’exécutent à l’intérieur d’une page WebPart : ils sont les blocs de construction des pages qui s’affichent sur un site SharePoint. Consultez [bloc de construction : composants WebPart](http://go.microsoft.com/fwlink/?LinkID=182097).  
  
 Vous pouvez créer et déboguer des composants WebPart sur un site SharePoint à l’aide de modèles à partir de Visual Studio.  
  
## <a name="create-a-web-part-in-visual-studio"></a>Créer un composant WebPart dans Visual Studio
 Créer un composant WebPart en ajoutant un **WebPart** élément à un projet SharePoint. Vous pouvez utiliser un **WebPart** élément dans une solution bac à sable ou une solution de batterie de serveurs.  
  
 Si vous souhaitez concevoir un composant WebPart visuellement à l’aide d’un concepteur, créez un **composant Visual Web Part** de projet ou ajouter **composant Visual Web Part** élément à un projet SharePoint. Vous pouvez utiliser un **composant Visual Web Part** élément dans une solution de batterie de serveurs uniquement.  
  
### <a name="web-part-item"></a>Élément WebPart
 Un **WebPart** élément fournit des fichiers que vous pouvez utiliser pour concevoir un composant WebPart pour un site SharePoint. Lorsque vous ajoutez un **WebPart** élément, Visual Studio crée un dossier dans votre projet et puis ajoute plusieurs fichiers au dossier. Le tableau suivant décrit chaque fichier.  
  
|Fichier|Description|  
|----------|-----------------|  
|*Elements.Xml*|Contient des informations que le fichier de définition de fonctionnalité dans votre projet utilise pour déployer le composant WebPart.|  
|fichier .webpart|Fournit les informations nécessaires pour afficher votre composant WebPart dans une galerie de composants WebPart SharePoint.|  
|Fichier de code|Contient des méthodes qui ajoutent des contrôles au composant WebPart et qui génèrent du contenu personnalisé dans le composant WebPart.|  
  
 Pour plus d’informations, consultez [Comment : créer un composant WebPart SharePoint](../sharepoint/how-to-create-a-sharepoint-web-part.md).  
  
### <a name="visual-web-part-item"></a>Élément Visual WebPart
 Un composant visual web part est un composant WebPart que vous créez à l’aide du concepteur Visual Web Developer dans Visual Studio. Un composant visual WebPart fonctionne comme tout autre composant WebPart. Pour ajouter des contrôles, tels que des boutons et des zones de texte, à un composant WebPart, vous ajoutez le code dans un fichier XML. Toutefois, ajouter des contrôles à un composant visual web part en faisant glisser ou en les copiant sur le composant WebPart à partir de Visual Studio **boîte à outils**. Le concepteur génère ensuite le code requis dans le fichier XML. Consultez [Comment : composant WebPart SharePoint de créer à l’aide d’un concepteur](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md).  
  
## <a name="sharepoint-controls"></a>Contrôles SharePoint
 Visual Studio fournit certains contrôles pour créer des pages SharePoint, tels que des pages d’application. Ces contrôles apparaissent dans le **boîte à outils** sous **contrôles SharePoint**. Les fonctionnalités de ces contrôles dérive le [Microsoft.SharePoint.WebControls](http://go.microsoft.com/fwlink/?LinkId=235315) espace de noms qui contient des contrôles serveur ASP.NET qui sont utilisés sur les pages de site et de liste SharePoint.  
  
|Nom du contrôle|Description|  
|------------------|-----------------|  
|[AspMenu](http://go.microsoft.com/fwlink/?LinkId=235307)|Insère un menu ASP. Pour plus d’informations, consultez [vue d’ensemble du contrôle de Menu](http://go.microsoft.com/fwlink/?LinkId=235316).|  
|[CssLink](http://go.microsoft.com/fwlink/?LinkId=235308)|Insère un **lien** élément dans le *.aspx* page et s’applique à un ou plusieurs feuilles de style externes définies par **CssRegistration**.|  
|[DateTimeControl](http://go.microsoft.com/fwlink/?LinkId=235306)|Insère un contrôle DateTime dans le *.aspx* page.|  
|[FormDigest](http://go.microsoft.com/fwlink/?LinkId=235309)|Insère une validation de la sécurité dans le *.aspx* page|  
|[ListProperty](http://go.microsoft.com/fwlink/?LinkId=235310)|Retourne une propriété d’une liste spécifiée.|  
|[ProjectProperty](http://go.microsoft.com/fwlink/?LinkId=235311)|Retourne une propriété globale du site Web actuel.|  
|[RssLink](http://go.microsoft.com/fwlink/?LinkId=235312)|Insère un lien vers un flux RSS dans le *.aspx* page.|  
|[ScriptLink](http://go.microsoft.com/fwlink/?LinkId=235313)|Fournit des propriétés et méthodes pour l’inscription de ressources, tels que les scripts, sur une page afin qu’elles puissent être demandées lorsque la page est affichée.|  
|[Thème](http://go.microsoft.com/fwlink/?LinkId=235314)|Applique un thème pour le *.aspx* page.|  
  
## <a name="debug-a-web-part"></a>Déboguer un composant WebPart
 Vous pouvez déboguer un projet SharePoint qui contient un composant WebPart même manière que vous le feriez avec d’autres projets Visual Studio. Lorsque vous démarrez le débogueur Visual Studio, Visual Studio ouvre le site SharePoint.  
  
 Pour commencer à déboguer votre code, ajoutez le composant WebPart à une page WebPart dans SharePoint.  
  
 Pour plus d’informations sur le débogage de projets SharePoint, consultez [solutions SharePoint de résoudre les problèmes](../sharepoint/troubleshooting-sharepoint-solutions.md).  
  
## <a name="visual-web-part-limitations"></a>Limitations de partie de Visual web
 À partir de Visual Studio, vous pouvez ajouter des composants visual web parts à des solutions SharePoint sandbox et des solutions de batterie de serveurs. Toutefois, les composants visual web parts présentent les limitations suivantes :  
  
-   Composants WebPart visuels ne prennent pas en charge les paramètres remplaçables. Pour plus d’informations, consultez [paramètres remplaçables](../sharepoint/replaceable-parameters.md).  
  
-   Contrôles utilisateur visual WebPart ne peut pas être déplacé et supprimé ou copié sur les composants visual web parts. Cette action provoque une erreur de build.  
  
-   Composants WebPart visuels ne prennent directement en charge les jetons du serveur SharePoint tels que $SPUrl. Pour plus d’informations, consultez « Jeton Restrictions dans sandbox Visual WebPart » dans la rubrique [solutions SharePoint de résoudre les problèmes](../sharepoint/troubleshooting-sharepoint-solutions.md).  
  
-   Composants Visual web parts dans une solution bac à sable obtiennent parfois l’erreur, « la demande d’exécution de code en mode sandbox a été refusée car le Service hôte de Code sandbox était trop occupé pour traiter la demande. » Pour plus d’informations sur cette erreur, consultez ce billet dans le [Blog de l’équipe SharePoint développeur](http://go.microsoft.com/fwlink/?LinkId=225932).  
  
-   Débogage de JavaScript côté serveur n’est pas pris en charge dans Visual Studio, mais le débogage de JavaScript côté client est prise en charge.  
  
     Bien que vous pouvez ajouter le code JavaScript intégré dans un fichier de balises côté serveur, le débogage n’est pas pris en charge pour les points d’arrêt ajoutés au balisage. Pour déboguer du code JavaScript, référencer un fichier JavaScript externe dans le fichier de balisage, puis définissez les points d’arrêt dans le fichier JavaScript.  
  
-   Débogage d’inline [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] code doit être effectué dans le fichier de code généré au lieu de dans le fichier de balisage.  
  
-   Composants WebPart visuels ne prennent pas en charge l’utilisation de la `<@ Assembly Src=` directive.  
  
-   Contrôles web SharePoint et certains [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] contrôles ne sont pas pris en charge dans l’environnement sandbox de SharePoint. Si les contrôles non pris en charge sont utilisés sur un composant visual web part dans une solution bac à sable, l’erreur, « Le type ou espace de noms nom « Thème » n’existe pas dans l’espace de noms 'Microsoft.SharePoint.WebControls' » s’affiche.  
  
 Pour plus d’informations sur les solutions bac à sable, consultez [différences entre sandbox et les solutions de batterie](../sharepoint/differences-between-sandboxed-and-farm-solutions.md).  
  
## <a name="create-older-style-sharepoint-based-web-parts"></a>Créer des parties du site web SharePoint de type ancien
 Vous pouvez utiliser les modèles dans Visual Studio pour créer des [!INCLUDE[vstecasplong](../sharepoint/includes/vstecasplong-md.md)] WebPart pour SharePoint. [!INCLUDE[vstecasplong](../sharepoint/includes/vstecasplong-md.md)] composants WebPart s’appuient sur le [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] infrastructure WebPart et le type est recommandé pour les nouveaux projets.  
  
 Dans quelques rares cas, vous devrez créer un composant WebPart à l’aide de l’ancien style WebPart basées sur SharePoint. Vous pouvez utiliser Visual Studio pour créer ces types de composants WebPart, mais Visual Studio ne fournit pas de modèles qui sont spécifiquement conçues pour vous aider à les créer.  
  
 Pour plus d’informations sur lorsque vous souhaiterez créer un composant WebPart basé sur SharePoint, consultez [Infrastructure de composant WebPart dans Windows SharePoint Services](http://go.microsoft.com/fwlink/?LinkId=169290). Pour plus d’informations sur la création d’un composant WebPart à l’aide de la partie du site web SharePoint de type ancien, consultez [procédure pas à pas la création d’un composant WebPart SharePoint de base](http://go.microsoft.com/fwlink/?LinkId=169288).  
  
## <a name="related-topics"></a>Rubriques connexes
  
|Titre|Description|  
|-----------|-----------------|  
|[Comment : créer un composant WebPart SharePoint](../sharepoint/how-to-create-a-sharepoint-web-part.md)|Vous montre comment créer des composants WebPart pour des pages SharePoint.|  
|[Comment : créer un composant WebPart SharePoint à l’aide d’un concepteur](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md)|Vous montre comment créer des composants WebPart pour SharePoint à l’aide d’une aire de conception visuelle.|  
|[Comment : créer un contrôle utilisateur pour une application SharePoint partie web ou de page](../sharepoint/how-to-create-a-user-control-for-a-sharepoint-application-page-or-web-part.md)|Vous montre comment créer des contrôles personnalisés et réutilisables qui peuvent être utilisés par les pages d’application et les composants WebPart qui s’exécutent dans SharePoint.|  
|[Procédure pas à pas : Créer un composant WebPart pour SharePoint](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint.md)|Décrit comment concevoir un composant WebPart pour SharePoint.|  
|[Procédure pas à pas : Créer un composant WebPart pour SharePoint à l’aide d’un concepteur](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint-by-using-a-designer.md)|Décrit comment concevoir un composant WebPart pour SharePoint en faisant glisser des contrôles à une aire de conception visuelle.|  
|[Procédure pas à pas : Créer le composant WebPart Silverlight qui affiche OData pour SharePoint](../sharepoint/walkthrough-creating-a-silverlight-web-part-that-displays-odata-for-sharepoint.md)|Décrit comment concevoir un composant WebPart pour SharePoint qui héberge une application Silverlight et affiche les données à partir de listes SharePoint.|  
  
