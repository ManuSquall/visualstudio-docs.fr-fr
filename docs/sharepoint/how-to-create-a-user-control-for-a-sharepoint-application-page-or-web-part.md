---
title: Créer un contrôle utilisateur pour une page d’application SharePoint ou un composant WebPart
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- user controls [SharePoint development in Visual Studio], creating
- user controls [SharePoint development in Visual Studio], adding
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 2fbf1b646ae9e7fb697fcab93adfb8661a4372c6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "86016971"
---
# <a name="how-to-create-a-user-control-for-a-sharepoint-application-page-or-web-part"></a>Comment : créer un contrôle utilisateur pour une page d’application SharePoint ou un composant WebPart
  Vous pouvez créer des contrôles utilisateur personnalisés qui fournissent des fonctionnalités personnalisées pour votre solution SharePoint, et vous pouvez réutiliser cette fonctionnalité dans votre projet. Vous pouvez inclure les contrôles utilisateur dans un composant WebPart ou une page d’application, ajouter d’autres contrôles ASP.NET et contrôles SharePoint, et définir des propriétés et des méthodes pour le contrôle. Pour plus d’informations sur les contrôles utilisateur, consultez [créer des contrôles réutilisables pour des composants WebPart ou des pages d’application](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md) , ainsi que des contrôles [utilisateur et des contrôles serveur dans SharePoint](https://blogs.msdn.microsoft.com/kaevans/2011/04/28/user-controls-and-server-controls-in-sharepoint/).

### <a name="to-create-a-user-control-for-sharepoint"></a>Pour créer un contrôle utilisateur pour SharePoint

1. Dans Visual Studio, ouvrez ou créez un projet SharePoint.

     Consultez [modèles de projet et d’élément de projet SharePoint](../sharepoint/sharepoint-project-and-project-item-templates.md).

2. Dans l' **Explorateur de solutions**, choisissez le nœud du projet.

3. Dans la barre de menus, choisissez **projet**  >  **Ajouter un nouvel élément**.

     La boîte de dialogue **Ajouter un nouvel élément** s’ouvre.

4. Dans le volet **installé** , choisissez le nœud **Office/SharePoint** .

5. Dans la liste des modèles SharePoint, choisissez **contrôle utilisateur (solution de batterie uniquement)**.

    > [!NOTE]
    > Les contrôles utilisateur fonctionnent uniquement dans les solutions de batterie de serveurs.

6. Dans la zone **nom** , spécifiez un nom pour le contrôle utilisateur, puis cliquez sur le bouton **Ajouter** .

     Visual Studio ajoute plusieurs dossiers et fichiers à votre projet. Pour plus d’informations sur ces fichiers, consultez [créer des contrôles réutilisables pour des composants WebPart ou des pages d’application](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md).

     Par défaut, le fichier de contrôle utilisateur s’affiche dans la vue **source** du concepteur Visual Web Developer. Dans cette vue, vous pouvez modifier le balisage XML du contrôle. Vous pouvez basculer en mode **Design** si vous souhaitez concevoir le contrôle visuellement en faisant glisser des contrôles à partir de la **boîte à outils**. Consultez [mode Design, concepteur de pages Web](/previous-versions/aspnet/ms178149\(v\=vs.100\)).

7. Si vous souhaitez gérer des événements qui se produisent dans le contrôle, ajoutez du code au fichier de code du contrôle utilisateur.

     Ce fichier apparaît dans **Explorateur de solutions** sous le fichier de contrôle utilisateur et a une extension *. cs* ou *. vb* , selon la langue du projet.

## <a name="see-also"></a>Voir aussi
- [Créer des contrôles réutilisables pour les composants WebPart ou les pages d’application](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)
- [Créer des pages d’application pour SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md)
- [Créer des composants WebPart pour SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)
