---
title: Création de composants WebPart pour SharePoint | Microsoft Docs
ms.date: 02/02/2017
ms.topic: overview
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
helpviewer_keywords:
- SharePoint development in Visual Studio, Web Parts
- Web Parts [SharePoint development in Visual Studio], designing
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 3825ef7d2c1c90f63a90f5028063c74332543841
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "86015045"
---
# <a name="create-web-parts-for-sharepoint"></a>Créer des composants WebPart pour SharePoint
  À l’aide de composants WebPart, vous pouvez modifier le contenu, l’apparence et le comportement des pages d’un site SharePoint à l’aide d’un navigateur. Les composants WebPart sont des contrôles côté serveur qui s’exécutent dans une page de composants WebPart : ils sont les blocs de construction des pages qui s’affichent sur un site SharePoint. Consultez le [bloc de construction : composants WebPart](/previous-versions/office/developer/sharepoint-2010/ee535520(v=office.14)).

 Vous pouvez créer et déboguer des composants WebPart sur un site SharePoint à l’aide de modèles de Visual Studio.

## <a name="create-a-web-part-in-visual-studio"></a>Créer un composant WebPart dans Visual Studio
 Créez un composant WebPart en ajoutant un élément **WebPart** à un projet SharePoint. Vous pouvez utiliser un élément **WebPart** dans une solution bac à sable (sandbox) ou une solution de batterie de serveurs.

 Si vous souhaitez concevoir visuellement un composant WebPart à l’aide d’un concepteur, créez un projet de **composant Visual Web part** ou ajoutez un élément **Visual WebPart** à un projet SharePoint. Vous pouvez utiliser un élément de **composant Visual Web part** dans une solution de batterie de serveurs uniquement.

### <a name="web-part-item"></a>Élément WebPart
 Un élément **WebPart** fournit des fichiers que vous pouvez utiliser pour concevoir un composant WebPart pour un site SharePoint. Quand vous ajoutez un élément **WebPart** , Visual Studio crée un dossier dans votre projet, puis ajoute plusieurs fichiers au dossier. Le tableau suivant décrit chaque fichier.

|Fichier|Description|
|----------|-----------------|
|*Elements.xml*|Contient des informations que le fichier de définition de fonctionnalité dans votre projet utilise pour déployer le composant WebPart.|
|fichier. WebPart|Fournit des informations dont SharePoint a besoin pour afficher votre composant WebPart dans une galerie de composants WebPart.|
|Fichier de code|Contient des méthodes qui ajoutent des contrôles au composant WebPart et qui génèrent du contenu personnalisé dans le composant WebPart.|

 Pour plus d’informations, consultez [Comment : créer un composant WebPart SharePoint](../sharepoint/how-to-create-a-sharepoint-web-part.md).

### <a name="visual-web-part-item"></a>Élément Visual Web part
 Un composant Visual Web part est un composant WebPart que vous créez à l’aide du concepteur Visual Web Developer dans Visual Studio. Un composant WebPart visuel fonctionne de la même façon que n’importe quel autre composant WebPart. Pour ajouter des contrôles, tels que des boutons et des zones de texte, à un composant WebPart, vous ajoutez du code à un fichier XML. Toutefois, vous ajoutez des contrôles à un composant WebPart visuel en les faisant glisser ou en les copiant sur le composant WebPart à partir de la **boîte à outils**Visual Studio. Le concepteur génère ensuite le code requis dans le fichier XML. Consultez [Comment : créer un composant WebPart SharePoint à l’aide d’un concepteur](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md).

## <a name="sharepoint-controls"></a>Contrôles SharePoint
 Visual Studio fournit des contrôles pour créer des pages SharePoint, telles que des pages d’application. Ces contrôles apparaissent dans la **boîte à outils** sous **contrôles SharePoint**. Les fonctionnalités de ces contrôles dérivent de l’espace de noms [Microsoft. SharePoint. WebControls](/previous-versions/office/sharepoint-server/ms413880(v=office.15)) , qui contient les contrôles serveur ASP.net utilisés sur les pages de site et de liste SharePoint.

|Nom du contrôle|Description|
|------------------|-----------------|
|[AspMenu](/previous-versions/office/sharepoint-server/ms454108(v=office.15))|Insère un menu ASP. Pour plus d’informations, consultez [vue d’ensemble du contrôle Menu](/previous-versions/ecs0x9w5(v=vs.140)).|
|[CssLink](/previous-versions/office/sharepoint-server/ms439048(v=office.15))|Insère un élément de **lien** dans la page *. aspx* et applique une ou plusieurs feuilles de style externes définies par **CssRegistration**.|
|[DateTimeControl](/previous-versions/office/sharepoint-server/ms414993(v=office.15))|Insère un contrôle DateTime dans la page *. aspx* .|
|[FormDigest](/previous-versions/office/sharepoint-server/ms416616(v=office.15))|Insère une validation de la sécurité dans la page *. aspx*|
|[ListProperty](/previous-versions/office/sharepoint-server/ms455032(v=office.15))|Retourne une propriété d’une liste spécifiée.|
|[ProjectProperty](/previous-versions/office/sharepoint-server/ms478990(v=office.15))|Retourne une propriété globale du site Web actuel.|
|[RssLink](/previous-versions/office/sharepoint-server/ms457574(v=office.15))|Insère un lien vers un flux RSS dans la page *. aspx* .|
|[ScriptLink](/previous-versions/office/sharepoint-server/ms411959(v=office.15))|Fournit des propriétés et des méthodes pour inscrire des ressources, telles que des scripts, sur une page afin qu’elles puissent être demandées lors du rendu de la page.|
|[Thème](/previous-versions/office/sharepoint-server/ms460735(v=office.15))|Applique un thème à la page *. aspx* .|

## <a name="debug-a-web-part"></a>Déboguer un composant WebPart
 Vous pouvez déboguer un projet SharePoint qui contient un composant WebPart de la même façon que vous le feriez pour d’autres projets Visual Studio. Quand vous démarrez le débogueur Visual Studio, Visual Studio ouvre le site SharePoint.

 Pour commencer à déboguer votre code, ajoutez le composant WebPart à une page de composant WebPart dans SharePoint.

 Pour plus d’informations sur le débogage des projets SharePoint, consultez [résoudre les problèmes liés aux solutions SharePoint](../sharepoint/troubleshooting-sharepoint-solutions.md).

## <a name="visual-web-part-limitations"></a>Limitations des composants Visual Web part
 À compter de Visual Studio, vous pouvez ajouter des composants Visual Web parts aux solutions de batterie de serveurs et solutions SharePoint bac à sable (sandbox). Toutefois, les composants Visual Web Parts présentent les limitations suivantes :

- Les composants Visual Web Parts ne prennent pas en charge les paramètres remplaçables. Pour plus d’informations, consultez [paramètres remplaçables](../sharepoint/replaceable-parameters.md).

- Les contrôles utilisateur ou les composants Visual Web Parts ne peuvent pas être déplacés ni copiés dans des composants Visual Web Parts. Cette action provoque une erreur de génération.

- Les composants Visual Web Parts ne prennent pas directement en charge les jetons SharePoint Server tels que les $SPUrl. Pour plus d’informations, consultez « restrictions de jeton dans les composants WebPart visuels sandbox » dans la rubrique [résolution des problèmes liés aux solutions SharePoint](../sharepoint/troubleshooting-sharepoint-solutions.md).

- Les composants Visual Web parts dans une solution bac à sable (sandbox) reçoivent parfois l’erreur « la demande d’exécution du code en mode bac à sable (sandbox) a été refusée car le service hôte de code sandbox était trop occupé pour traiter la demande. » Pour plus d’informations sur cette erreur, consultez ce billet sur le blog de l' [équipe de développement SharePoint](https://blogs.msdn.microsoft.com/sharepointdev/2011/02/08/error-the-sandboxed-code-execution-request-was-refused-because-the-sandboxed-code-host-service-was-too-busy-to-handle-the-request-ricky-kirkham/#10149157).

- Le débogage JavaScript côté serveur n’est pas pris en charge dans Visual Studio, mais le débogage JavaScript côté client est pris en charge.

   Bien que vous puissiez ajouter le code JavaScript Inline à un fichier de balisage côté serveur, le débogage n’est pas pris en charge pour les points d’arrêt ajoutés au balisage. Pour déboguer du code JavaScript, référencez un fichier JavaScript externe dans le fichier de balisage, puis définissez les points d’arrêt dans le fichier JavaScript.

- Le débogage du code inline [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] doit être effectué dans le fichier de code généré et non dans le fichier de balisage.

- Les composants WebPart visuels ne prennent pas en charge l’utilisation de la `<@ Assembly Src=` directive.

- Les contrôles Web SharePoint et certains [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] contrôles ne sont pas pris en charge dans l’environnement de bac à sable (sandbox) SharePoint. Si des contrôles non pris en charge sont utilisés sur un composant WebPart visuel dans une solution bac à sable (sandbox), l’erreur « le type ou le nom de l’espace de noms’Theme’n’existe pas dans l’espace de noms’Microsoft. SharePoint. WebControls' » s’affiche.

  Pour plus d’informations sur les solutions bac à sable (sandbox), consultez [différences entre les solutions sandbox et les solutions de batterie de serveurs](../sharepoint/differences-between-sandboxed-and-farm-solutions.md).

## <a name="create-older-style-sharepoint-based-web-parts"></a>Créer des composants WebPart SharePoint de type ancien
 Vous pouvez utiliser les modèles dans Visual Studio pour créer [!INCLUDE[vstecasplong](../sharepoint/includes/vstecasplong-md.md)] des composants WebPart personnalisés pour SharePoint. [!INCLUDE[vstecasplong](../sharepoint/includes/vstecasplong-md.md)] les composants WebPart sont basés sur l' [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] infrastructure de composants WebPart et sont le type recommandé pour les nouveaux projets.

 Dans très rares cas, vous devrez peut-être créer un composant WebPart à l’aide de l’ancien composant WebPart SharePoint. Vous pouvez utiliser Visual Studio pour créer ces types de composants WebPart, mais Visual Studio ne fournit pas de modèles conçus spécifiquement pour vous aider à les créer.

 Pour plus d’informations sur le moment où vous pourriez vouloir créer un composant WebPart SharePoint de type ancien, consultez [infrastructure de composants WebPart dans Windows SharePoint Services](/previous-versions/office/developer/sharepoint-2010/ms415560(v=office.14)). Pour plus d’informations sur la création d’un composant WebPart à l’aide de l’ancien composant WebPart SharePoint basé sur SharePoint, consultez [procédure pas à pas : création d’un composant WebPart SharePoint de base](/previous-versions/office/ms452873(v=office.14)).

## <a name="related-topics"></a>Rubriques connexes

|Titre|Description|
|-----------|-----------------|
|[Comment : créer un composant WebPart SharePoint](../sharepoint/how-to-create-a-sharepoint-web-part.md)|Montre comment créer des composants WebPart pour les pages SharePoint.|
|[Comment : créer un composant WebPart SharePoint à l’aide d’un concepteur](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md)|Montre comment créer des composants WebPart pour SharePoint à l’aide d’une aire de conception visuelle.|
|[Comment : créer un contrôle utilisateur pour une page d’application SharePoint ou un composant WebPart](../sharepoint/how-to-create-a-user-control-for-a-sharepoint-application-page-or-web-part.md)|Montre comment créer des contrôles personnalisés et réutilisables qui peuvent être utilisés par les pages d’application et les composants WebPart qui s’exécutent dans SharePoint.|
|[Procédure pas à pas : créer un composant WebPart pour SharePoint](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint.md)|Décrit comment concevoir un composant WebPart pour SharePoint.|
|[Procédure pas à pas : créer un composant WebPart pour SharePoint à l’aide d’un concepteur](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint-by-using-a-designer.md)|Décrit comment concevoir un composant WebPart pour SharePoint en faisant glisser des contrôles vers une aire de conception visuelle.|
|[Procédure pas à pas : créer un composant WebPart Silverlight qui affiche OData pour SharePoint](../sharepoint/walkthrough-creating-a-silverlight-web-part-that-displays-odata-for-sharepoint.md)|Décrit comment concevoir un composant WebPart pour SharePoint qui héberge une application Silverlight et affiche des données à partir de listes SharePoint.|
