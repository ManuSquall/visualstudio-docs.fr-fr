---
title: Création de pages d’application pour SharePoint | Microsoft Docs
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
ms.openlocfilehash: 47f403f4eec6ec66563ae88bec226e073f625716
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/28/2019
ms.locfileid: "72981097"
---
# <a name="create-application-pages-for-sharepoint"></a>Créer des pages d’application pour SharePoint
  Une *page d’application* est une page Web ASP.net conçue pour être utilisée sur un site Web SharePoint. Les pages d’application sont un type spécialisé de page ASP.NET. La principale différence entre une page d’application et une page ASP.NET standard est qu’une page d’application contient du contenu fusionné avec une page maître SharePoint. Une page maître permet aux pages d’application de partager la même apparence et le même comportement que les autres pages d’un site.

 Visual Studio vous permet de concevoir des pages d’application à l’aide d’un concepteur. Le concepteur affiche une zone de contenu pour chaque espace réservé de contenu défini dans une page maître. Vous pouvez concevoir la page d’application en faisant glisser des contrôles vers ces zones de contenu.

## <a name="application-pages"></a>Pages d’application
 Les pages d’application sont partagées entre tous les sites sur le serveur, alors qu’une page de site est spécifique à un site. Pour plus d’informations, retrouvez les [types de pages SharePoint](/previous-versions/office/developer/sharepoint-2010/aa979592(v=office.14)).

 Par défaut, la plupart des pages qui s’affichent lorsque vous créez un site SharePoint sont des pages de site. Une page de site peut être ajoutée à une bibliothèque de pages SharePoint. Les utilisateurs peuvent personnaliser une page de site à l’aide d’outils tels que SharePoint Designer. Une page de site peut également héberger des fonctionnalités telles que des composants WebPart dynamiques et des zones de composants WebPart.

 Les pages d’application ne peuvent pas effectuer ces opérations. Toutefois, une page d’application est le meilleur type de page à créer si vous souhaitez que la page contienne du code personnalisé. Bien que vous puissiez ajouter du code personnalisé à une page de site, le code cesse de s’exécuter lorsque l’utilisateur personnalise la page à l’aide d’outils tels que SharePoint Designer.

> [!NOTE]
> Visual Studio ne fournit pas de modèles qui vous aident à créer des pages de site pour un site SharePoint. Pour plus d’informations, consultez [types de pages SharePoint](/previous-versions/office/developer/sharepoint-2010/aa979592(v=office.14)).

## <a name="create-an-application-page"></a>Page créer une application
 Pour créer une page d’application, ajoutez un élément de **page d’application** à un projet SharePoint. Lorsque vous créez une page d’application, Visual Studio ajoute les dossiers suivants à votre projet :

|Dossier|Description|
|------------|-----------------|
|Dispositions|Mappe sur le répertoire virtuel _ layouts du système de fichiers SharePoint.|
|Sous-dossier dispositions|Contient les fichiers qui composent la page de l’application. Par défaut, ce dossier porte le même nom que votre projet. Vous pouvez renommer ce dossier à tout moment. Quand vous exécutez le projet, Visual Studio déploie ce dossier dans le répertoire virtuel _ layouts du système de fichiers SharePoint.|

 Visual Studio ajoute les fichiers suivants à votre projet :

|Fichier|Description|
|----------|-----------------|
|Fichier de page ASP.NET ( *. aspx*)|Contient le balisage XML qui définit la page.|
|Fichier de code de la page d’application|Contient le code-behind de la page de l’application. Ajoutez du code qui gère les événements à ce fichier.|
|Fichier de code du concepteur de pages d’application|Contient le code généré par le concepteur. Ne modifiez pas ce fichier directement.|

## <a name="design-and-debug-an-application-page"></a>Concevoir et déboguer une page d’application
 Concevez le contenu d’une page d’application à l’aide du mode concepteur dans Visual Studio. Ce concepteur s’affiche lorsque vous ouvrez la page d’application dans votre projet (en double-cliquant dessus ou en ouvrant le menu contextuel, puis en choisissant **ouvrir**), puis en sélectionnant le bouton **conception** en bas de l’éditeur.

> [!NOTE]
> Vous pouvez concevoir la page uniquement dans la vue **source** du concepteur. Le mode **Design** du concepteur est désactivé pour les pages d’application.

 Vous pouvez déboguer une page d’application comme vous le feriez pour d’autres éléments de projet SharePoint dans Visual Studio. Quand vous démarrez le débogueur Visual Studio, Visual Studio ouvre le site SharePoint.

 Pour afficher la page de l’application, vous devez accéder manuellement à l’emplacement de la page de l’application (par exemple : http://<em>nom_serveur</em>/_layouts/*PROJECT_NAME*/ApplicationPage1.aspx).

 Pour plus d’informations sur le débogage des projets SharePoint, consultez [résoudre les problèmes liés aux solutions SharePoint](../sharepoint/troubleshooting-sharepoint-solutions.md).

## <a name="choose-a-master-page"></a>Choisir une page maître
 Par défaut, un élément de **page d’application** fait référence à la page maître du site que vous utilisez pour déboguer votre projet. Cette page est nommée v4. Master et vous pouvez la trouver dans la **Galerie de pages maîtres** du site SharePoint.

 Vous pouvez modifier explicitement la page maître utilisée par la page de l’application en définissant l’attribut `MasterPageFile` de l’élément `Page` de l’application. (Par exemple : `MasterPageFile="~/_layouts/applicationv4.master"`). En fait, vous devez définir cet attribut si les pages maîtres dynamiques ne sont pas activées sur le serveur SharePoint. Pour plus d’informations sur les pages maîtres dans SharePoint, consultez [pages maîtres](/previous-versions/office/developer/sharepoint-2010/ms443795(v=office.14)).

## <a name="see-also"></a>Voir aussi
- [Développement SharePoint Foundation en profondeur](/previous-versions/office/developer/sharepoint-2010/ee539092(v=office.14))
- [Vue d'ensemble d’ASP.NET](/aspnet/overview)
- [Pages Web ASP.NET](/aspnet/web-pages/index)
