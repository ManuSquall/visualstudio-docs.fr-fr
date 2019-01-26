---
title: Création de Pages d’Application pour SharePoint | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, Web pages
- SharePoint development in Visual Studio, content pages
- SharePoint development in Visual Studio, application pages
- application pages [SharePoint development in Visual Studio], developing
- application pages [SharePoint development in Visual Studio], creating
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 815d48d7e7874ea5bd34d840ceecadcc4edb8dda
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2019
ms.locfileid: "54865071"
---
# <a name="create-application-pages-for-sharepoint"></a>Créer des pages d’application pour SharePoint
  Un *page application* est une page Web ASP.NET qui est conçue pour une utilisation dans un site SharePoint Web. Pages d’application sont un type spécialisé de page ASP.NET. La principale différence entre une page d’application et une page ASP.NET standard est qu’une page d’application contient du contenu est fusionné avec une page maître SharePoint. Une page maître permet aux pages d’application à partager la même apparence et le même comportement que les autres pages sur un site.  
  
 Visual Studio vous permet de concevoir des pages d’application à l’aide d’un concepteur. Le concepteur affiche une zone de contenu pour chaque espace réservé de contenu qui est défini dans une page maître. Vous pouvez concevoir la page d’application en faisant glisser des contrôles à ces zones de contenu.  
  
## <a name="application-pages"></a>Pages d’application
 Pages d’application sont partagées entre tous les sites sur le serveur, tandis qu’une page de site est spécifique à un seul site. Pour plus d’informations, [les Types de pages SharePoint](http://go.microsoft.com/fwlink/?LinkID=211584).  
  
 Par défaut, la plupart des pages qui s’affichent lorsque vous créez un site SharePoint sont des pages de site. Une page de site peut être ajoutée à une bibliothèque de pages SharePoint. Les utilisateurs peuvent personnaliser une page de site à l’aide des outils tels que SharePoint Designer. Une page de site peut également héberger des fonctionnalités telles que les composants WebPart dynamiques et les Zones WebPart.  
  
 Pages d’application ne peut pas effectuer les opérations suivantes. Toutefois, une page d’application est le meilleur type de page pour créer si vous souhaitez que la page contienne du code personnalisé. Bien que vous pouvez ajouter du code personnalisé à une page de site, le code s’arrête lorsque l’utilisateur personnalise la page à l’aide des outils tels que SharePoint Designer.  
  
> [!NOTE]  
>  Visual Studio ne fournit pas les modèles qui vous aident à créer des pages de site pour un site SharePoint. Pour plus d’informations, consultez [les Types de pages SharePoint](http://go.microsoft.com/fwlink/?LinkID=211584).  
  
## <a name="create-an-application-page"></a>Créer une page d’application
 Pour créer une page d’application, ajoutez un **Page Application** élément à un projet SharePoint. Lorsque vous créez une page d’application, Visual Studio ajoute les dossiers suivants à votre projet :  
  
|Dossier|Description|  
|------------|-----------------|  
|Dispositions|Correspond au répertoire virtuel _layouts du système de fichiers SharePoint.|  
|Sous-dossier dispositions|Contient les fichiers qui composent la page d’application. Par défaut, ce dossier a le même nom que votre projet. Vous pouvez renommer ce dossier à tout moment. Lorsque vous exécutez le projet, Visual Studio déploie ce dossier sur le répertoire virtuel _layouts du système de fichiers SharePoint.|  
  
 Visual Studio ajoute les fichiers suivants à votre projet :  
  
|Fichier|Description|  
|----------|-----------------|  
|Fichier de page ASP.NET (*.aspx*)|Contient le balisage XML qui définit la page.|  
|Fichier de code de page application|Contient le code-behind de la page d’application. Ajoutez le code qui gère les événements à ce fichier.|  
|Fichier de code du Concepteur de page application|Contient le code qui est généré par le concepteur. Ne modifiez pas directement ce fichier.|  
  
## <a name="design-and-debug-an-application-page"></a>Conception et le débogage d’une page d’application
 Concevoir le contenu d’une page d’application à l’aide de la vue de concepteur dans Visual Studio. Ce concepteur s’affiche lorsque vous ouvrez la page d’application dans votre projet (en double-cliquant dessus ou en ouvrant le menu contextuel, puis en choisissant **ouvrir**), puis choisissez le **conception** bouton en bas de l’éditeur.  
  
> [!NOTE]  
>  Vous pouvez concevoir la page uniquement dans le **Source** vue du concepteur. Le **conception** vue du concepteur est désactivé pour les pages d’application.  
  
 Vous pouvez déboguer une page d’application même manière que vous le feriez avec d’autres éléments de projet SharePoint dans Visual Studio. Lorsque vous démarrez le débogueur Visual Studio, Visual Studio ouvre le site SharePoint.  
  
 Pour afficher la page d’application, vous devez accéder manuellement à l’emplacement de la page d’application (par exemple : http://<em>nom_serveur</em>/_layouts/*Project_Name*  /ApplicationPage1.aspx).  
  
 Pour plus d’informations sur le débogage de projets SharePoint, consultez [solutions SharePoint de résoudre les problèmes](../sharepoint/troubleshooting-sharepoint-solutions.md).  
  
## <a name="choose-a-master-page"></a>Choisissez une page maître
 Par défaut, un **Page Application** élément fait référence à la page maître du site que vous utilisez pour déboguer votre projet. Que la page nommée V4.master, et vous le trouverez répertoriés dans le **galerie de pages maîtres** du site SharePoint.  
  
 Vous pouvez modifier explicitement la page maître qui est utilisé par la page d’application en définissant le `MasterPageFile` attribut de l’application `Page` élément. (Par exemple : `MasterPageFile="~/_layouts/applicationv4.master"`). En fait, vous devez définir cet attribut si des pages maîtres dynamiques ne sont pas activées sur le serveur SharePoint. Pour plus d’informations sur les pages maîtres dans SharePoint, consultez [Pages maîtres](http://go.microsoft.com/fwlink/?LinkID=169281).  
  
## <a name="see-also"></a>Voir aussi
 [Développement SharePoint Foundation en profondeur](http://go.microsoft.com/fwlink/?LinkID=182103)   
 [Vue d’ensemble d’ASP.NET](/aspnet/overview)   
 [Pages Web ASP.NET](/aspnet/web-pages/index)   
