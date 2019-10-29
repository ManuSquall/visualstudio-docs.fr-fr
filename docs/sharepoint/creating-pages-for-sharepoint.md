---
title: Création de pages pour SharePoint | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, master pages
- SharePoint development in Visual Studio, page layouts
- SharePoint development in Visual Studio, content pages
- master pages[SharePoint development in Visual Studio], designing
- content pages[SharePoint development in Visual Studio], designing
- page layouts[SharePoint development in Visual Studio], designing
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 297ebf0e7c2ed1273dd5a8ac973ce497c4c64781
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/28/2019
ms.locfileid: "72986355"
---
# <a name="create-pages-for-sharepoint"></a>Créer des pages pour SharePoint
  Vous pouvez créer des pages d’application, des pages de site, des pages maîtres et des mises en page pour un site SharePoint.

 Vous pouvez créer des pages d’application à l’aide d’un modèle dans Visual Studio. Créez des pages de site, des pages maîtres et des mises en page à l’aide de SharePoint Designer. Ensuite, vous pouvez importer ces pages dans Visual Studio pour les utiliser dans un projet SharePoint.

 Vous pouvez également modifier l’apparence et le comportement des pages à l’aide de feuilles de style en cascade, ECMAScript et des thèmes.

## <a name="types-of-sharepoint-pages"></a>Types de pages SharePoint
 Le tableau suivant décrit les quatre principaux types de pages qu’un site SharePoint contient.

|Type de page|Description|
|---------------|-----------------|
|Pages d’application|Créer une page d’application si vous souhaitez que la page contienne du code personnalisé ou que vous souhaitiez que la page soit partagée entre plusieurs sites. Dans le cas contraire, une page de site peut être le meilleur choix.|
|Pages de site|Créez une page de site si vous souhaitez effectuer l’une des tâches suivantes :<br /><br /> -Ajoutez la page à une bibliothèque SharePoint.<br />-Activer la page pour héberger des fonctionnalités telles que des composants WebPart dynamiques et des zones de composants WebPart.<br />-Permettre aux utilisateurs de personnaliser la page à l’aide de SharePoint Designer.<br /><br /> Ne créez pas de page de site si vous souhaitez que la page contienne du code personnalisé. Bien que vous puissiez ajouter du code personnalisé à une page de site, le code cesse de s’exécuter lorsque l’utilisateur personnalise la page à l’aide de SharePoint Designer.|
|Pages maîtres|Créez une page maître si vous souhaitez définir une structure commune pour les pages de site et les pages d’application.|
|Mises en page|Les mises en page sont spécifiques à [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] et vous permettent de définir plus précisément une structure commune pour les pages de site et les pages d’application.|

 Pour obtenir une vue d’ensemble de chaque type de page, consultez [bloc de construction : pages et interface utilisateur](/previous-versions/office/developer/sharepoint-2010/ee539040(v=office.14)), et [mises en page et pages maîtres](/previous-versions/office/developer/sharepoint-2010/ms543497(v=office.14)).

## <a name="create-application-pages"></a>Créer des pages d’application
 Vous pouvez créer des pages d’application dans Visual Studio en ajoutant un élément de **page d’application** à un projet SharePoint. Vous pouvez ajouter des contrôles à la page, puis gérer les événements de contrôle en ajoutant du code.

 Vous pouvez définir des points d’arrêt dans le fichier de code de la page, démarrer le débogueur et tester la page sur un site SharePoint local sans effectuer aucune étape de configuration supplémentaire. Pour plus d’informations, consultez [création de pages d’application pour SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md).

## <a name="create-site-pages-master-pages-and-page-layouts"></a>Créer des pages de site, des pages maîtres et des mises en page
 Vous pouvez créer des pages de site, des pages maîtres et des mises en page à l’aide de SharePoint Designer. Vous pouvez ensuite importer ces pages dans Visual Studio. Importez vos pages si vous souhaitez tirer parti des fonctionnalités de déploiement ou de contrôle de code source disponibles dans Visual Studio. Pour plus d’informations, consultez [importation d’éléments à partir d’un site SharePoint existant](../sharepoint/importing-items-from-an-existing-sharepoint-site.md).

 Étant donné qu’il est difficile de modifier ces pages une fois que vous les avez importées, vous devez concevoir ces pages avant de les importer.

## <a name="create-cascading-style-sheets-ecmascript-and-themes"></a>Créer des feuilles de style en cascade, ECMAScript et des thèmes
 Visual Studio ne fournit pas de modèles pour le développement de fichiers feuilles de style en cascade (CSS), ECMAScript (JavaScript, JScript) ou de thème pour les sites SharePoint. Vous pouvez créer ces fichiers à l’aide des conseils disponibles dans le kit de développement logiciel (SDK) SharePoint ou à l’aide d’outils tels que SharePoint Designer.

 Vous pouvez ajouter ces fichiers directement à votre solution ou vous pouvez les importer. Dans les deux cas, vous devez créer les dossiers mappés appropriés pour chaque élément que vous ajoutez. Pour plus d’informations sur la création d’un dossier mappé, consultez [procédure : ajouter et supprimer des dossiers mappés](../sharepoint/how-to-add-and-remove-mapped-folders.md).

 Pour plus d’informations sur la création d’feuilles de style en cascade, consultez [feuilles de style en cascade de l’utilisation des classes dans SharePoint Foundation](/previous-versions/office/developer/sharepoint-2010/ms438349(v=office.14)). Pour plus d’informations sur la création de fichiers JavaScript et JScript pour une solution SharePoint, consultez [configuration d’une page aspx de base pour ECMAScript](/previous-versions/office/developer/sharepoint-2010/ee535709(v=office.14)). Pour plus d’informations sur les thèmes, voir [blocs de construction : pages et interface utilisateur](/previous-versions/office/developer/sharepoint-2010/ee539040(v=office.14)).

## <a name="related-topics"></a>Rubriques connexes

|Titre|Description|
|-----------|-----------------|
|[Créer des pages d’application pour SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md)|Décrit comment ajouter des pages d’applications : le contenu *. aspx* qui est fusionné avec une page maître SharePoint.|
|[Comment : créer une page d’application](../sharepoint/how-to-create-an-application-page.md)|Montre comment créer des pages ASP.NET qui s’exécutent sur un site SharePoint.|
|[Procédure pas à pas : créer une page d’application SharePoint](../sharepoint/walkthrough-creating-a-sharepoint-application-page.md)|Montre comment concevoir et déboguer une page Web ASP.NET pour un site SharePoint.|
